---
title: Create indicators for files
ms.reviewer: 
description: Create indicators for a file hash that define the detection, prevention, and exclusion of entities.
keywords: file, hash, manage, allowed, blocked, block, clean, malicious, file hash, ip address, urls, domain
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
---

# Create indicators for files

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Applies to:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)



> [!TIP]
> Want to experience Defender for Endpoint? [Sign up for a free trial.](https://www.microsoft.com/en-us/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

You can prevent further propagation of an attack in your organization by banning potentially malicious files or suspected malware. If you know a potentially malicious portable executable (PE) file, you can block it. This operation will prevent it from being read, written, or executed on machines in your organization.

There are two ways you can create indicators for files:
- By creating an indicator through the settings page
- By creating a contextual indicator using the add indicator button from the file details page

### Before you begin
It's important to understand the following prerequisites prior to creating indicators for files:

- This feature is available if your organization uses Windows Defender Antivirus and Cloud-based protection is enabled. For more information, see [Use next-generation technologies in Microsoft Defender Antivirus through cloud-delivered protection](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/utilize-microsoft-cloud-protection-microsoft-defender-antivirus).
- The Antimalware client version must be 4.18.1901.x or later.
- Supported on machines on Windows 10, version 1703 or later, Windows server 2016 and 2019.
- To start blocking files, you first need to [turn the **Block or allow** feature on](advanced-features.md) in Settings.
- This feature is designed to prevent suspected malware (or potentially malicious files) from being downloaded from the web. It currently supports portable executable (PE) files, including _.exe_ and _.dll_ files. The coverage will be extended over time.

Performance can be affected if you are copying large files from a network share onto your local device, especially over a VPN connection. 

> [!IMPORTANT]
> - The allow or block function cannot be done on files if the file's classification exists on the device's cache prior to the allow or block action 
> - Trusted signed files will be treated differently. Defender for Endpoint is optimized to handle malicious files. Trying to block trusted signed files, in some cases, may have performance implications.
> - Typically, file blocks are enforced within a couple of minutes, but can take upwards of 30 minutes.
> - If there are conflicting file indicator policies, the enforcement policy of the more secure policy is applied. For example, a SHA-256 file hash indicator policy takes precedence over an MD5 file hash indicator policy if both hash types define the same file.

### Create an indicator for files from the settings page

1. In the navigation pane, select **Settings** > **Indicators**.  

2. Select the **File hash** tab.

3. Select **Add indicator**.

4. Specify the following details:
   - Indicator - Specify the entity details and define the expiration of the indicator.
   - Action - Specify the action to be taken and provide a description.
   - Scope - Define the scope of the machine group.

5. Review the details in the Summary tab, then click **Save**.

### Create a contextual indicator from the file details page
One of the options when taking [response actions on a file](respond-file-alerts.md) is adding an indicator for the file. 

When you add an indicator hash for a file, you can choose to raise an alert and block the file whenever a machine in your organization attempts to run it.

Files automatically blocked by an indicator won't show up in the file's Action center, but the alerts will still be visible in the Alerts queue.


## Related topics
- [Create indicators](manage-indicators.md)
- [Create indicators for IPs and URLs/domains](indicator-ip-domain.md)
- [Create indicators based on certificates](indicator-certificates.md)
- [Manage indicators](indicator-manage.md)
