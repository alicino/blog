---
layout: single
title: "Step-by-Step SSH Connection via Cloudflare Zero Trust"
tags:
  - connectivity
  - intermediate
  - WARP
  - Cloudflare
category:
  - zero trust
  - ssh
---

Initial Considerations

This step-by-step guide refers to connecting to a remote server via the SSH protocol using the Cloudflare Zero Trust feature. The steps provided here are an adapted model based on the official documentation available at the link below.

This is one of the available models within the Zero Trust solution that can be used. Cloudflare also recommends three other models, which can be reviewed here.

It's important to note that Cloudflare does not recommend SSH access using username/password. Therefore, this guide will only cover the model using a public/private key pair as a means of ensuring security in the process.

Official documentation: [Connect with self-managed SSH keys](https://developers.cloudflare.com/cloudflare-one/connections/connect-networks/use-cases/ssh/ssh-warp-to-tunnel/)

---

### 1. Creating SSH Key Pairs
Open the terminal on your Linux client machine and generate the SSH key pair.

**Example:**
```bash
ssh-keygen -t rsa -f ~/.ssh/ssh-key-ztna -C <server_user_to_connect_as>
``` 
You don't need to provide any additional information if you prefer not to, such as a passphrase, etc.

Verify the creation of the keys with the command:
```bash
ls -lrt ~/.ssh/
```

Then, view the contents of the public key that was created (the file with the .pub extension):
```bash
cat ~/.ssh/ssh-key-ztna.pub
```

Save this value. We will copy it to the server we will connect to later.

--- 

### 2. Creating the Virtual Machine "Server" for Connection (Optional)
This step is optional if you have already created the server for this purpose. If not, refer to the appropriate guide for creating a VM within your hosting environment, such as:

Google Cloud: https://cloud.google.com/compute/docs/create-linux-vm-instance

Azure: https://learn.microsoft.com/en-us/azure/virtual-machines/linux/quick-create-portal?tabs=ubuntu

AWS EC2: https://aws.amazon.com/getting-started/launch-a-virtual-machine-B-0/

Oracle Cloud: https://docs.oracle.com/en-us/iaas/Content/GSG/Reference/overviewworkflow.htm

**Note:** Cloudflare does not provide support for this step as it involves third-party services.

**Important:** After creating the server, make sure to import the public key into the server. Each cloud provider handles this differently. For on-prem servers, there are various methods, such as copying and pasting the key into the `~/.ssh/`  folder or using the command:
```bash
ssh-copy-id username@server_address
```

---

### 3. Connect the Server to Cloudflare (cloudflared Tunnel)
The next step is to create a tunnel connection from the server you created—whether in a cloud or on-prem environment—to Cloudflare. For this, we will use cloudflared.

Log in to your Cloudflare management dashboard at:
[https://dash.cloudflare.com](https://dash.cloudflare.com)

Then, go to the left-side menu and follow the sequence:
**_Zero Trust > Networks > Tunnels > + Create a Tunnel_**

Give your tunnel a name of your choice.

Select the Linux operating system (Debian or Red Hat), then choose the architecture (32-bit or 64-bit). Copy the command shown in the gray box on the left-hand side.

For security reasons, the full command will not be displayed here—but you should copy it directly from the dashboard.

{% include figure image_path="assets/images/ztna-ssh-01.png" alt="ZTNA screenshot" class="align-center" %}

Run this command in the server’s terminal and wait for confirmation that it executed successfully. See example below:

{% include figure image_path="assets/images/ztna-ssh-02.png" alt="ZTNA screenshot" class="align-center" %}

At this point, you will see a connection established within the tunnel environment at the bottom of the screen, as shown below.

{% include figure image_path="assets/images/ztna-ssh-03.png" alt="ZTNA screenshot" class="align-center" %}

Click on the _“Private Networks”_ tab and enter the IP and CIDR of the server you want to connect to.

**Important:**

The IP must belong to the internal network of your environment (if you have more than one).

To connect to a single machine, use the IP with the /32 CIDR (1 host).

{% include figure image_path="assets/images/ztna-ssh-04.png" alt="ZTNA screenshot" class="align-center" %}

Click _“Save tunnel”_ on the bottom-right side of the screen.

You will now see your tunnel listed (if you have other tunnels already created, it will appear alongside them).

Example:

{% include figure image_path="assets/images/ztna-ssh-05.png" alt="ZTNA screenshot" class="align-center" %}

---

### 4. Client Machine Connection (Optional)
This step involves setting up WARP on the client machine to access the server through Cloudflare’s network control.

If you haven’t done this yet, follow the steps below:

To register your device using the WARP GUI (Windows, macOS, or Linux):

1. Download and install the WARP client. Click here to download.
2. Launch the WARP client.
3. Click the Cloudflare logo in the menu bar.
4. Select the gear icon.
5. Go to **_Preferences > Account_**.
6. Select Login with Cloudflare Zero Trust.
7. Enter your team name.
8. Complete the authentication steps required by your organization.

After authentication, you’ll see a success page and a dialog asking you to open WARP.
Click Open Cloudflare WARP.app to complete the registration.
The device is now protected by your organization’s Zero Trust policies.

Now let’s add Device Enrollment Permissions:

In the left-hand menu, go to: **_Zero Trust > Settings > Warp Client_**

Click _"Device enrollment permissions"_, then click Manage.

{% include figure image_path="assets/images/ztna-ssh-06.png" alt="ZTNA screenshot" class="align-center" %}

In the _“Rules”_ tab, we’ll create an authentication rule (temporarily for now). Click _“+ Add a rule”_.

Enter a name under _“Rule name”_.

For _“Rule Action”_, select _“Allow”_.

Under _“Include”_, configure it as follows:

Selector: `Emails ending in`

Value: `@company.com` (example – please adjust as needed)

Click _“Save”_ on the left side, in the blue box.

{% include figure image_path="assets/images/ztna-ssh-07.png" alt="ZTNA screenshot" class="align-center" %}

---

### 5. Routing Private Network IPs Through WARP (Agent)
This step is important because it enables or restricts network access within the environment through WARP.

By default, WARP excludes traffic destined for IP addresses used in private networks and not accessible via the Internet.
To allow traffic within your private network, you need to configure a Split Tunnel model so that your private network’s IP/CIDR is routed through WARP.

Check how Split Tunnels are handled in your network environment.

Go to the left-hand menu:
**_Zero Trust > Settings > Warp Client_**

Under **Device Settings**, locate the **Default** profile, click the three dots **(⋮)**, and then select _“Configure”_.

{% include figure image_path="assets/images/ztna-ssh-08.png" alt="ZTNA screenshot" class="align-center" %}

Scroll down to the _“Split Tunnels”_ section and check if the option _“Exclude IPs and domains”_ is enabled, as shown in the example below.

Then, click _“Manage”_ in blue on the right side.

{% include figure image_path="assets/images/ztna-ssh-09.png" alt="ZTNA screenshot" class="align-center" %}

Review the listed IP ranges.

If your server’s IP falls within any of these ranges, click on the entry and delete it from the list so that WARP can route traffic to that address.

In my example (see below), I had to delete the range `10.0.0.0/8` because my server’s IP was `10.206.xx.xx`.

Click the item, scroll up, select Action, then choose Confirm delete (1 selected).

{% include figure image_path="assets/images/ztna-ssh-10.png" alt="ZTNA screenshot" class="align-center" %}

---

### 6. User Connection
Now we’ll connect to the server from the client machine where we installed WARP.

To summarize, we have completed the following steps:

- Created an SSH key pair to establish a secure connection.
- Created the server instance and copied the public SSH key to it.
- Connected the server to Cloudflare using cloudflared (tunnel).
- Installed and configured WARP on the client machine.
- Configured split tunneling to allow private network traffic through Cloudflare.

Now, we’re ready to connect to the server. Using PuTTY, a terminal (such as WSL), or a similar tool, enter the following command:

```bash
ssh -i ~/.ssh/ssh-key-ztna <server_user>@<server_IP>
```

Reminder: The server IP should be the internal private network IP — usually starting with `10.x.x.x`, `172.16.x.x`, or `192.168.x.x`.

Once all steps are completed, the server will receive the connection request and grant terminal access using the SSH key pair generated in Step 1.

--- 

Need help setting up safer AI usage? Feel free to reach out — I’m here to help!
