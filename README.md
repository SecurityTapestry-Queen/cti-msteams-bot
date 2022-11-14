# 🏴‍☠️🤖 Threat Intelligence Teams Bot

TITB is a fork from [Threat Intelligence Discord Bot from vx-underground](https://github.com/vxunderground/ThreatIntelligenceDiscordBot/) but for Microsoft Teams and modified to work as an hourly Github-Action 

> The vx-underground Threat Intelligence Discord Bot gets updates from various clearnet domains, ransomware threat actor domains This bot will check for updates in intervals of 1800 seconds.

[![MIT License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) ![Version](https://img.shields.io/badge/version-2.3.0-blue.svg)  [![Last Run](https://github.com/SecurityTapestry-Queen/cti-msteams-bot/actions/workflows/fetchCTI.yml/badge.svg)](.github/workflows/fetchCTI.yml)  [![CodeQL](https://github.com/SecurityTapestry-Queen/cti-msteams-bot/actions/workflows/codeql-analysis.yml/badge.svg)](.github/workflows/codeql-analysis.yml) 

## Description

* Written in Python 
   
   ⚠️ required version Python 3.10+ 
* Requires Teams Webhook

Threat Intelligence Teams Bot gets updates from various clearnet domains and ransomware threat actor domains. 

This bot will check for updates every 30 minutes. 

![](Screenshot.png)

## Installation

Clone the repository or download the [latest release](https://github.com/JMousqueton/CTI-MSTeams-Bot/releases/latest) 

Install all the modules in ```requirements.txt```
```
pip3 install -r requirements.txt
```
## Configuration

### Github Action 

* Create a MS-Teams WebHook  
* in an environment you will called `CI`, paste the created webhook url in a `MSTEAMS_WEBHOOK` variable. 

### On a server (Windows, MacOS, Linux) 

* Create a variable called ```MSTEAMS_WEBHOOK``` with the webhook URL

Example 

```
MSTEAMS_WEBHOOK=https://mousqueton.webhook.office.com/webhookb2/08589F1C-EEA2-4C92-A08B-66E59692FDE3/IncomingWebhook/3DEFFDD9-F3A8-4351-BDA7-142FAFB7473A
python3 TeamIntelBot.py -r -d 
```
* Schedule the script for example every hours via the crontab

*Note: the IDs have been generated with uuidgen for example purpose* 😛

## Usage 

```
python3 TeamsIntelBot.py -h
Usage: TeamsIntelBot.py [options]

Options:
  --version       show program's version number and exit
  -h, --help      show this help message and exit
  -q, --quiet     Quiet mode
  -D, --debug     Debug mode : only output on screen nothing send to MS Teams
  -d, --domain    Enable Red Flag Domains source
  -r, --reminder  Enable monthly reminder of Feeds
```

### Proxy

If you use a proxy don't forget to use the proxies variables : 
```
set https_proxy=http://x.x.x.x:port
set http_proxy=http://x.x.x.x:port
```

I've also add a script called ```checkFeed.py``` to check if feeds are valids and what is the last published date. This script read the ```Feed.csv``` file. 

```
python3 checkFeed.py 

✅ Modexp (Sun, 31 Jul 2022 00:01:53 +0000)
✅ James Forshaw (2022-07-16T21:49:00.000-07:00)
✅ Adam Chester (Sat, 09 Jul 2022 23:00:00 GMT)
✅ Microsoft Security (Thu, 11 Aug 2022 16:00:00 +0000)
✅ Recorded Future (Thu, 18 Aug 2022 00:00:00 GMT)
✅ SentinelOne (Wed, 11 May 2022 14:56:53 +0000)
✅ RedCanary (Thu, 18 Aug 2022 21:53:55 +0000)
✅ Cyber-News (Fri, 19 Aug 2022 15:14:56 +0000)
✅ Leak-Lookup (Fri, 19 Aug 2022 04:00:02 +0200)
✅ ATT (2022-08-17T10:00:00+00:00)
✅ US-CERT CISA (Tue, 16 Aug 2022 15:38:42 +0000)
✅ NCSC (Thu, 18 Aug 2022 23:00:00 GMT)
✅ Center of Internet Security (Thu, 18 Aug 2022 01:43:07 -0400)
✅ FR-CERT Alertes (Tue, 31 May 2022 11:12:01 +0000)
✅ FR-CERT Avis (Fri, 19 Aug 2022 11:22:29 +0000)
✅ EU-ENISA Publications (2022-07-27T10:00:00Z)
✅ Microsoft Sentinel (Thu, 18 Aug 2022 08:31:51 PDT)
```

