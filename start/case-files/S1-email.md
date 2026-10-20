# S1. The email as the gateway kept it

*Case file · start set · TLP:AMBER · from `hta-1005-email.eml`*

The mail gateway (`mail-gw1.hta.invalid`) keeps the headers of every message and a trace of each attachment it removes, not the attachment. This is the copy delivered to the first of the three recipients.

```
Return-Path: <support@quillfeather-support.invalid>
Received: from relay7.mailbridge.invalid (relay7.mailbridge.invalid [198.51.100.52])
        by mail-gw1.hta.invalid (Gateway 7.2) with ESMTPS id 4F9C01A2
        for <pip.rookwood@hta.invalid>; Mon, 5 Oct 2026 07:41:09 +0000
Received: from [192.0.2.77] (helo=desk-4) by relay7.mailbridge.invalid
        with ESMTPSA id 1kQ7xV-0004Zy-3b; Mon, 5 Oct 2026 07:41:02 +0000
Received-SPF: softfail (mail-gw1.hta.invalid: domain of transitioning
        support@quillfeather-support.invalid does not designate 198.51.100.52 as permitted sender)
Authentication-Results: mail-gw1.hta.invalid; spf=softfail
        smtp.mailfrom=quillfeather-support.invalid; dkim=none; dmarc=none
From: Quillfeather Support <support@quillfeather-support.invalid>
To: Pip Rookwood <pip.rookwood@hta.invalid>, Tessa Brinehart <tessa.brinehart@hta.invalid>, Corin Floe <corin.floe@hta.invalid>
Subject: QF-400 governor firmware 4.2.1: update procedure required before Thursday's maintenance window
Date: Mon, 5 Oct 2026 07:41:00 +0000
Message-ID: <20261005074100.7F3A2C1@relay7.mailbridge.invalid>
MIME-Version: 1.0
Content-Type: multipart/mixed; boundary="=_qfs_0001"
X-Gw-Verdict: delivered
X-Gw-Policy: strip-office-from-unverified
X-Gw-Attachment: name="QF400_4.2.1_Update_Instructions.docx"; size=6842; sha256-prefix=1d6212a97685; stripped=yes
```

**Body (text part)**

> Dear engineer,
>
> Quillfeather Controls is releasing governor firmware 4.2.1 for the QF-400. Sites that run the Mk II governor must apply it before their next maintenance window. HTA's window is this Thursday, 8 October.
>
> The attached document describes the update procedure. Please follow it in full, and reply to this address if you meet any problem.
>
> Quillfeather Controls, Technical Support

**Gateway annotation**

> Attachment 1 of 1 removed by policy `strip-office-from-unverified`. The message was delivered without it. The recorded trace is the `X-Gw-Attachment` header above (name, size in bytes, the first twelve hex characters of the SHA-256 of the removed file).
