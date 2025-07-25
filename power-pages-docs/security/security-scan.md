---
title: Run security scan (preview)
description: Learn how to identify and address security vulnerabilities in Power Pages with security scan.
author: dmartens
ms.topic: how-to
ms.custom: 
ms.date: 11/13/2024
ms.subservice:
ms.author: bipuldeora
ms.reviewer: danamartens
contributors:
---

# Run security scan (preview)

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-banner.md)]

Use Power Pages security scan to enhance your site's resilience by identifying and addressing vulnerabilities, safeguarding it against potential threats, and ensuring a secure online environment for users.

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-note-pp.md)]

## Prerequisites

- Power Pages Core version 1.0.2403.84 or later.

## Run a security scan

Use the [Security workspace](../getting-started/use-security-workspace.md) to run the scan. You can also review the [third party notice](https://go.microsoft.com/fwlink/?linkid=2271056) prior to running the security scan.

To run a security scan:

1. Select the **Run Deep Scan** button.  

    By default, security scan only scans anonymous pages. 
    
    To include authenticated pages in the scan: 
    1. Select the check box next to **Include authenticated pages in scan**. A notification window appears in the workspace.
    1. Enter your username and password.

1. Select the **Continue** button to begin the scan.

    You can cancel the scan at any time by returning to the Security workspace and selecting the **Cancel scan** button.

Once the scan is complete, you'll receive an email. After you receive the email confirmation, you can view the scan report summary by returning to the **Run scan** section of the Security workspace.

## Review the summary report 

The summary report includes a list of failed checks and corresponding alerts with descriptions of how to fix the alerts. You can optionally download the report as a PDF. Report summaries for security scan are only supported in English-US language.



## Related information

[Run security scan with Power Pages (video)](https://youtu.be/Mj8oIRmSjjE?feature=shared)
