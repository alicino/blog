---
layout: single
title: "The Power of OSINT – What the Internet Knows About You?"
tags:
  - data privacy
  - beginner
  - OSINT
category:
  - data protection
  - privacy tips
---

**OSINT** is the acronyms for Open-Source Intelligence. It is a method to search information (investigate) with the focus to take decisions. Usually it is a strategy very usefull, but in otherwise demonstrate people have to take care about what is expost in the internet.

{% include figure image_path="assets/images/2023-05-11-the-power-of-osint-what-the-internet-knows-about-you.png" alt="The Power of OSINT – What the Internet Knows About You?" class="align-center" width="400" %}

Although the information is public, not everything should be available. It's important to mention some data (or information) is public for a misconfiguration for any dumb reason. After read this post you can understand through example the consequences for you, and the same time how to find out what is available for everyone.

**Disclaimer**
OSINT is the intelligence where we get information from public source. In other words, it means open source about a company or a person.

## Why OSINT is important?
Basically for some reasons:
- Digital safety (what is public about you, for example)
- Investigation (companies, national safety)
- Take decision (check fact or information, competitor analysis)
- Fond hidden people

## OSINT sources
Okay. So far so good. BUt where and how can we find this information? It's simple and I recommend doing the search about yourself first.
Common websites could be:
- Internet through sites, blogs, social media, videos, etc
- Public registers (Notary Public)
- Domains (such as WHOIS info)
- Specific tool searches

## Tools
- [Shodan](https://shodan.io) is a search tool for connected devices and opened
- [Maltego](https://www.maltego.com/) is a company to provide a visualization of connected net among website, people, and company
- [whois.com](https://whois.com) and [Who.is](https://who.is), and [Registro.br](https://registro.br/tecnologia/ferramentas/whois/) are example of whois about domains or IP addresses. Whois command is also available in Linux terminal. Example: `whois domain.com`
- _Spiderfoot_ and _TheHarvester_ are two tools available on Kali Linux
- [ExifTool](https://exiftool.org/) a toll for read, write, and edit picture metadata.
- [Webmii](https://webmii.com/) an engine tools with focus on people public information.
- [Wayback Marchine](https://web.archive.org/) an excellent tool to find old website versions.
- [Censys](https://censys.com/) similar to Shodan, but focused on scan security in detail, very helpful for certificates and open services
- [IntelligenceX](https://intelx.io/) searches data leake, WHOIS register, public files, and storage media social archived.
- Google Dorks - an advanced search on [Google](https://google.com/)

About Google Dorks, some example of advanced searches you may use to get assertive result:

```bash
site:domain.com intext:laptop
```
It's a search within the domain.com with the word laptop

```bash
intext:"Elon Musk" filetype:jpg
```
Searching for Elon Musk and a picture (.jpg)

```bash
intitle:"Report" filetype:pdf
```
Searching a webpage with the name "Report" and contain a file .pdf extension

If you need to know more about this resource of search on Google, I recommend the post [Google Dorks: Top Tips and Tricks for Advanced Search Intelligence](https://www.recordedfuture.com/threat-intelligence-101/threat-analysis-techniques/google-dorks)

## Some Considerations
First of all, the ethic side and the responsability of each information
Remember: collect data is not the same invade others, and the same way OSINT is a skill to protect and not to attack.
The aware use is always very imporant

The OSINT can show private aspects, so you have to deal with it properly in a ethic way.
The problem is not find, but how you use these information.

---
**Did you find this guide useful?** Share it with friends and family. Let’s build a safer internet—together.

