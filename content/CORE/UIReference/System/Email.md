---
title: "Email"
description: "This article provides information on how to set up system email on TrueNAS CORE."
weight: 50
tags:
- coreemail
---

{{< toc >}}

## General Options

{{< include file="static/includes/Reference/SystemEmailFields.md.part" markdown="true" >}}

## Send Mail Method

### SMTP

![System Email SMTP Options](/images/CORE/12.0/SystemEmailSMTPOptions.png "System Email SMTP Options")

| Name | Description |
|------|-------------|
| Outgoing Mail Server | Hostname or IP address of SMTP server used for sending email. |
| Mail Server Port | SMTP port number. Typically 25/465 (secure SMTP), or 587 (submission). |
| Security | Choose an encryption type. Choices are *Plain (No Encryption)*, *SSL (Implicit TLS)*, or *TLS (STARTTLS)*. |
| SMTP Authentication | Set when the SMTP server uses authentication credentials. Shows additional credentials options. |

### GMail OAuth

![SystemEmailGMailOAuth](/images/CORE/12.0/SystemEmailGMailOAuth.png "GMail OAuth Options")

| Name | Description |
|------|-------------|
| LOG IN TO GMAIL | Login to Gmail using OAuth. |

{{< taglist tag="coreemail" limit="10" >}}
