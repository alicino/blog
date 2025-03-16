---
layout: single
title: "Safety DNS: Protecting You and Your Family"
tags:
  - DNS
  - security
  - beginner
category:
  - cybersecurity
---

### The DNS Concept

If you're not an IT professional or familiar with how the Internet works, there are some key concepts worth understanding. One of the most important is how your browser directs you to a website, given that the Internet operates through IP (Internet Protocol) addresses.

For example, the domain **www.google.com** is a user-friendly way to access an IP address like **142.250.113.139**. This makes navigation easier for everyone, but with millions (or even billions) of domains on the Internet, we need a system to translate domain names into IP addresses. This is where **DNS (Domain Name System) servers** come in.

I’ll skip some technical details, as my focus here is practical: how DNS can enhance security for you and your family. When you type a domain in your browser, the first step is to query a **DNS server** to resolve the domain into an IP address. There are many DNS servers worldwide, and if you don’t configure one manually, your **Internet Service Provider (ISP)** assigns one automatically.

### DNS Servers

Today, we have several reliable and fast DNS servers. Here are some commonly used ones:

| Name | Primary IP | Secondary IP |
| --- | --- | --- |
| Google | 8.8.8.8 | 8.8.4.4 |
| Quad9 | 9.9.9.9 | 149.112.112.112 |
| Cloudflare | 1.1.1.1 | 1.0.0.1 |

While these DNS servers are **fast and secure**, they do **not** filter content for safety. This brings us to the main point: **safe DNS options for families**.

### Safe DNS Options for Families

Some DNS providers offer content filtering to block malicious websites and inappropriate content. Here are some good options:

| Name | Primary IP | Secondary IP | Protection Type |
| --- | --- | --- | --- |
| Cloudflare Family | 1.1.1.3 | 1.0.0.3 | Malware + Adult Content |
| CleanBrowsing | 185.228.168.168 | 185.228.169.168 | Malware/Phishing + Pornography |
| OpenDNS FamilyShield | 208.67.222.123 | 208.67.220.123 | Pornography + Adult Content |

If you want a deeper understanding of **DNS security** and recommendations from experts, I suggest reading ["Introducing 1.1.1.1 for Families"](https://blog.cloudflare.com/introducing-1-1-1-1-for-families/) by **Matthew Prince**, CEO of Cloudflare.

### Why Is This Important?

DNS acts as the **gateway** to all websites you visit. The risk associated with **malicious content, phishing attacks, and inappropriate websites** is significant, especially for children. Blocking access to adult content and dangerous sites is a proactive way to protect your household.

I plan to cover **how to configure safe DNS settings on your home network** in a future post. For now, just keep in mind that **DNS works as a list of internet addresses, regardless of whether they are safe or malicious**. The DNS providers I listed focus on enhancing security, and using them is a smart way to **protect yourself and your family online**.

---

Let me know if you have any questions or need help setting up a safer DNS for your home!
