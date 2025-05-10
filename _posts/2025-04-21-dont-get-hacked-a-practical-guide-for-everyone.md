---
layout: single
title: "The Power of OSINT – What the Internet Knows About You"
tags:
  - data privacy
  - beginner
  - OSINT
category:
  - data protection
  - privacy tips
---

**OSINT** stands for **Open-Source Intelligence**.  
It is a method of gathering information (investigating) with the purpose of supporting decision-making.  
While it is an extremely useful strategy, it also highlights the need for individuals to be cautious about what they expose on the internet.

{% include figure image_path="assets/images/2023-05-11-the-power-of-osint-what-the-internet-knows-about-you.png" alt="The Power of OSINT – What the Internet Knows About You" class="align-center" width="400" %}

Although the information collected through OSINT is public, not everything should necessarily be accessible.  
It is important to note that some data becomes public due to misconfigurations or simple oversight.  
By the end of this article, you will understand—through examples—the potential consequences for individuals, and at the same time, learn how to discover what information is available about yourself.

---

## Disclaimer

OSINT refers to the collection of information from publicly available sources.  
In other words, it involves open-source data about a company, organization, or individual.

---

## Why is OSINT Important?

Several reasons highlight the relevance of OSINT today:

- **Digital Safety** (understanding what information about you is publicly accessible)
- **Investigations** (corporate investigations, journalism, national security)
- **Decision-Making** (fact-checking, competitive intelligence)
- **Finding Hidden Information** (locating individuals or hard-to-find details)

---

## OSINT Sources

At this point, you may wonder: where and how can this information be found?  
The answer is simple—and a good starting point is searching for information about yourself.

Common sources include:

- Public websites, blogs, social media platforms, videos
- Official public registries (such as notary public records)
- Domain and IP ownership data (WHOIS information)
- Specialized search tools

---

## Common OSINT Tools

Here are some tools that professionals frequently use for OSINT activities:

- [**Shodan**](https://shodan.io): Search engine for discovering devices connected to the internet and open services.
- [**Maltego**](https://www.maltego.com/): Platform for visually mapping the relationships between websites, companies, and individuals.
- [**Whois.com**](https://whois.com), [**Who.is**](https://who.is), [**Registro.br**](https://registro.br/tecnologia/ferramentas/whois/): Tools for retrieving ownership and administrative data about domains and IPs.  
  (_Tip: the `whois` command is also available in Linux terminals: `whois domain.com`._)
- **Spiderfoot** and **TheHarvester**: Tools available on Kali Linux for automated information gathering.
- [**ExifTool**](https://exiftool.org/): Utility for reading, writing, and editing metadata in images and files.
- [**Webmii**](https://webmii.com/): Search engine specializing in publicly available information about individuals.
- [**Wayback Machine**](https://web.archive.org/): Platform for viewing historical versions of websites.
- [**Censys**](https://censys.com/): A search engine similar to Shodan, but focused on detailed security scanning and certificate information.
- [**Intelligence X**](https://intelx.io/): Search platform for leaked data, WHOIS records, public files, and archived social media content.
- **Google Dorks**: Advanced search techniques using [Google](https://google.com) itself.

---

### Examples of Google Dorks

Some examples of advanced queries to make searches more precise:

```
site:domain.com intext:laptop
```
_Search for pages within domain.com containing the word "laptop"._

```
intext:"Elon Musk" filetype:jpg
```
_Search for publicly available `.jpg` images containing the text "Elon Musk"._

```
intitle:"Report" filetype:pdf
```
_Search for webpages with "Report" in the title that contain PDF files._

For more detailed tips, you may refer to:  
[Google Dorks: Top Tips and Tricks for Advanced Search Intelligence](https://www.recordedfuture.com/threat-intelligence-101/threat-analysis-techniques/google-dorks).

---

## Important Considerations

Ethics and responsibility are essential when practicing OSINT.  
Collecting information is not the same as breaching privacy, and it is crucial to understand that OSINT should be used as a tool for protection—not for harm.

Even though OSINT may reveal private aspects about individuals or organizations, what matters is how the information is handled and used.  
Responsible and ethical use of collected data is fundamental.

---

**Did you find this article useful?**  
If so, consider sharing it with colleagues, friends, and family.  
Awareness is the first step toward a safer and more responsible internet.