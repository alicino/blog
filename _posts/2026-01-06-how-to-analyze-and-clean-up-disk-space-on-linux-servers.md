---
layout: single
title: "How to Analyze and Clean Up Disk Space on Linux Servers"
description: "A practical, step-by-step guide to diagnosing and cleaning up disk space issues on Linux servers, based on real-world troubleshooting."
tags:
  - terminal
  - linux
  - disk
  - troubleshooting
category:
  - linux
  - sysadmin
---

In the past, storage was a big problem, and disk management was a routine. Today it is not an issue due to the price of storage and the new technologies, such as SSD, M.2, and the storage capacity. Besides that, I have an instance on GCP with only 10GB. The other day I had an issue with the disk in this instance, so I created this routine to analyze and clean up my disk. Let's see how to solve this kind of issue.

{% include figure image_path="assets/images/2026-01-06-cleanup-disk-linux-server.png" alt="Cleaning up disk on Linux Server" class="align-center" width="400" %}

Let's get started. I typed the command to check the space available, and it was the output.

```bash
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/root       9.6G  9.5G     0 100% /
tmpfs           475M     0  475M   0% /dev/shm
```

Here is a step-by-step guide to investigating and cleaning up a Linux server that has hit 100% disk usage.

## 1. Identify the Largest Directories

First, you need to drill down from the top to see which directory is consuming the most space. Run this command to see the size of the top-level directories:

```bash
# Check root directories, sorted by size
sudo du -h --max-depth=1 / 2>/dev/null | sort -hr
```

Note: `2>/dev/null` hides "permission denied" errors to keep the output clean.

Once you see the largest folder (usually `/var`, `/usr`, or `/home`), repeat the command on that folder to drill down further:

```bash
sudo du -h --max-depth=1 /var | sort -hr
```

## 2. Find the Largest Individual Files

Sometimes a single massive file (like an old backup or a runaway log file) is the issue. Run this to find all files larger than 100MB on the root partition:

```bash
sudo find / -xdev -type f -size +100M -exec ls -lh {} \; | sort -k 5 -rh
```

`-xdev`: Ensures find only searches the root partition (ignoring `/dev`, `/run`, etc.).

`sort -k 5 -rh`: Sorts the results by file size.

## 3. Common Cleanup Targets

Based on typical server issues, here are the most likely areas you can clean immediately.

### A. System Logs (/var/log)

Check for large text logs in `/var/log/` (like `syslog`, `kern.log`, `nginx/access.log`).

**Warning:** Do not `rm` (delete) an active log file while the service is writing to it. The system won't release the space until the service restarts. Instead, *truncate* it:

```bash
sudo truncate -s 0 /var/log/nginx/access.log
```

You can also clean the systemd journal:

```bash 
# Check usage
journalctl --disk-usage

# Keep only the last 100MB
sudo journalctl --vacuum-size=100M

# OR keep only the last 2 days
sudo journalctl --vacuum-time=2d
```

### B. Package Manager Cache (APT)

If this is an Ubuntu/Debian system, apt stores downloaded package files that are no longer needed.

```bash
sudo apt clean
sudo apt autoremove
```

(If you are on CentOS/RHEL, use `sudo yum clean all`)

## 4. The "Snap" Problem (Ubuntu)

If you use Snap packages, this is often the biggest culprit. Snap keeps old versions of packages and caches downloads by default.

### Step 1: Remove "Disabled" Packages

Snap keeps older versions of software installed as backups (labeled "disabled"). You can remove them to free up space.

Check your list:

```bash
sudo snap list --all
```
This is the output I got from my instance:

```bash
$ sudo snap list --all
Name              Version        Rev    Tracking         Publisher          Notes
core20            20250822       2682   latest/stable    canonical✓         base,disabled
core20            20251031       2686   latest/stable    canonical✓         base
core22            20250923       2139   latest/stable    canonical✓         base,disabled
core22            20251009       2163   latest/stable    canonical✓         base
google-cloud-cli  549.0.1        410    latest/stable/…  google-cloud-sdk✓  disabled,classic
google-cloud-cli  550.0.0        412    latest/stable/…  google-cloud-sdk✓  classic
lxd               5.0.5-5c60378  36558  5.0/stable/…     canonical✓         disabled
lxd               5.0.5-68251b5  36918  5.0/stable/…     canonical✓         -
snapd             2.71           25202  latest/stable    canonical✓         snapd,disabled
snapd             2.72           25577  latest/stable    canonical✓         snapd
```

If you see many rows labeled disabled, you can remove them manually:

```bash
sudo snap remove core20 --revision=2682
```

**Automation Script:**<br>
Instead of typing them manually, use this script to find and remove all disabled snaps automatically:

```bash
sudo snap list --all | awk '/disabled/{print $1, $3}' | \
    while read snapname revision; do \
        sudo snap remove "$snapname" --revision="$revision"; \
    done
```

### Step 2: The Hidden Cache (The Easy Win)

Snap stores download caches in /var/lib/snapd/cache/. These are just installers and can be safely deleted.

```bash
# Check the size
sudo ls -lh /var/lib/snapd/cache/
```

**How to delete them properly:**<br>
If you run `sudo rm -f /var/lib/snapd/cache/*`, it might fail silently.

**Why?** <br>
When you type `*`, your current user tries to expand the list of files. Since the folder is owned by root, your user can't see inside, so the wildcard fails.

**The Solution:**<br>
Wrap the command in a sub-shell so root handles the wildcard expansion:

```bash
sudo sh -c 'rm -rf /var/lib/snapd/cache/*'
```

In this step, I deleted about 4GB. Below is the command output before the deletion.

```bash
$ sudo ls -lh /var/lib/snapd/cache/
total 4.1G
-rw------- 1 root root  64M Nov  8 05:28 0b4bd533601c1e9db5297d16a9e84bb6f936cea2f2d942ag3c38bfa75e9d2cb1e2523872383f723b05
-rw------- 1 root root  51M Aug 23 03:37 11398a49b9e36ef9da377b1fdf39d6ee68f2267978c991725e1762eace92ecb5554849b63ad52fa1fb
-rw------- 1 root root 453M Nov 13 01:13 2774c3cf24a1d36512d7c75639adae8d2328325c563824f85c3f094f0c346a6b48537079498741fe18
-rw------- 1 root root  74M Oct 20 14:27 2f758f0ad4d7e65bdd0e52084f0c7995108d42b30aa0abd15c3d7745c08c7e150dfa4abade826960ef
-rw------- 1 root root 454M Nov  8 05:28 37e9cd3c53dc0a8219251de3921895fb45a4856c0a9d4f99ce7eaf2059b2c7e723521c18a174bf50f9
-rw------- 2 root root  92M Dec  4 01:33 67e6348964950305971a2f61789ad2f9003ae2850fc7fb220af4a6989022a1d9d889695e9b792da65d
-rw------- 2 root root 455M Dec 18 03:58 9172f95d3c7605038b8a7642d825670bf15fe7c1f6be0d4fc9cd96c7e28d4e296eafe6267bd84a10c7
-rw------- 2 root root  64M Dec 17 11:28 94f05a3e38da4da4c3e733492e1089aa04f70d60a8ed6eaebbc2c65041d560295be6589c6c110e5664
-rw------- 2 root root  74M Nov 17 05:43 a0a7b4d2f3acb0fc4e4213a057bccac9f122ddcb205aadbaf4f33d6e97508ab4de838342eb1f7c4f3d
-rw------- 1 root root 455M Dec  9 20:48 e9197569c2b81de08e21187cdf47ab2e67fcdb2247df9e9494790f544a6677525df95101ad08b684e4
-rw------- 1 root root 455M Dec 10 03:58 c5d1b896c7c46a533f4bb4f0b55b99a892a32eb0cf7b0acec350c87d170826c648325894900085731d
-rw------- 1 root root 455M Dec 11 20:48 cc0f24b32468fbf2515a4b63574e98a114e08a78b8d636b272d91bb5d96ca906a7d3ad41ce3ec6a0ee
-rw------- 2 root root  51M Oct 21 16:13 ccd031b5fdf884f24cbef5e41a045e2ea51c89b7bb55fa8a762326c5d04be8d2fd77b9efbbd6d526a2
-rw------- 1 root root 438M Nov  2 12:48 c2f4aa15904d24f21ce47b3485ee2294b62f69ea6fcf3c658616b36eab715364572bbfa0c74507d3bb
-rw------- 1 root root 454M Nov 19 10:38 d1484d84009eb696b80c563df64155c3cf4686351953fb17061ab9e0fe56b5efcd98738b486890cda6
-rw------- 1 root root  92M Nov 21 03:18 d819a91da606a0fcdef05724b1cb499f79f7be8272ed49491ca751a80332a30405cef41ef37cf50dfd
```

### Step 3: Delete Old Snapshots

Snapshots are backups of user data. Check if you have any unused snapshots:

```bash
sudo snap saved
```

If the list is huge, you can delete a specific set (e.g., set #1):

```bash
sudo snap forget 1
```

### Step 4: Prevent Future Issues

By default, Snap keeps 3 versions of every package. Limit this to 2 (active + 1 backup) to save space in the future:

```bash
sudo snap set system refresh.retain=2
```

## 5. Docker Cleanup

If you use Docker, you likely have old containers and images wasting space.

**Safety Check:**<br>
Run `sudo docker ps -a`.

If you see containers listed as "Exited" that you need (e.g., a stopped database), do NOT run the prune command blindly.

If you only see "Exited" containers that you don't care about, proceed.

**The Prune Command:**

```bash
sudo docker system prune
```

What this removes:<br>
- Stopped Containers: Anything not currently running.
- Dangling Images: Old layers from previous builds/updates.
- Unused Networks: Virtual networks not attached to containers.

## 6. The "Ghost" Files (Open but Deleted)

If you deleted files but df -h still says 100%, a running process might be holding onto a deleted file. The space won't be freed until that process restarts.

Check for these "open" deleted files:

```bash
sudo lsof +L1
```

If you see a large file listed there (often a log file), note the PID (Process ID) and restart that service. Example:

```bash
sudo systemctl restart nginx
# OR
sudo systemctl restart snapd
```

---

## Summary Checklist

1. Run du to find the heavy folder.
2. Run find to spot massive single files.
3. Clean apt/yum caches and vacuum journalctl.
4. Clean Snap cache and remove disabled versions.
5. Prune Docker system (carefully).
6. Restart services if space isn't freeing up (Ghost files).

This workflow covers the most common real-world disk exhaustion scenarios.

