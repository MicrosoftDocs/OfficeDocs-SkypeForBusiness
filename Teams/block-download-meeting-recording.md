---
title: Block the download of Teams meeting recording files from SharePoint or OneDrive (Preview)
ms.reviewer: samust
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
recommendations: true
audience: Admin
f1.keywords: NOCSH
ms.topic: article
ms.service: msteams
ms.localizationpriority: medium
ms.date: 03/01/2023
ms.collection:
- Tier1
- Highpri
- Tier1
- m365initiative-meetings
search.appverid:
- SPO160
- MET150
- BSA160
description: Learn how administrators can block the download of Teams meeting recording files from SharePoint and OneDrive.
---

# Block the download of Teams meeting recording files from SharePoint or OneDrive (Preview)

[!INCLUDE[Advanced Management](includes/advanced-management.md)]

You can block the download of Teams meeting recording files from SharePoint or OneDrive. This allows users to remain productive while addressing the risk of accidental data loss. Users have browser-only access to play the meeting recordings with no ability to download or sync files or access them through apps.

This policy applies to new meeting recordings across the entire organization. You can exempt people who are members of specified security groups from the policy. This allows you to specify governance or compliance specialists who should have download access to meeting recordings.

After the policy is turned on, any new Teams meeting recording files created by the Teams service and saved in SharePoint and OneDrive are blocked from download.

Because this policy affects meeting recordings stored in OneDrive and SharePoint, you must be a SharePoint administrator to configure it.

Note that this policy doesn't apply to manually uploaded meeting recording files.  

> [!IMPORTANT]
> This feature doesn't prevent the download of files that were uploaded by the Teams service prior to turning the policy on. If you would like to do so, you can open a support ticket.

## Requirements

This feature requires a Microsoft Syntex - SharePoint Advanced Management license.

## Turn on the policy for your organization

1. To use PowerShell, [download the latest SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251).

    > [!NOTE]
    > If you installed a previous version of SharePoint Online Management Shell, go to **Add or remove programs** and uninstall SharePoint Online Management Shell.
2. Connect to SharePoint as a Global administrator or SharePoint administrator. To learn how, see [Getting started with SharePoint Online Management Shell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

3.  Run the following command:

    ```PowerShell
    Set-SPOTenant -BlockDownloadFileTypePolicy <$true/$false(default)>  -BlockDownloadFileTypeIds  TeamsMeetingRecording
    ```
    For example, to turn this feature on, run `Set-SPOTenant -BlockDownloadFileTypePolicy $true  -BlockDownloadFileTypeIds  TeamsMeetingRecording`.

## Exempt users in specified security groups from the policy

The following parameter can be used with this cmdlet if required:

`-ExcludedBlockDownloadGroupIds <comma separated security group ids>`
  
This parameter exempts users in the specified security groups from this policy so that they can download meeting recording files.

## App impact

Blocking the download of Teams meeting recording files may impact the user experience in some apps, including some Office apps. We recommend that you turn the policy on for some users and test the experience with the apps used in your organization.

> [!NOTE]
> Apps that run in "app-only" mode in the service, like antivirus apps and search crawlers, are exempted from the policy.

## Need more help?

[SharePoint Q&A](/answers/topics/office-sharepoint-online.html)

## Related topics

[Block download policy for SharePoint sites and OneDrive](/sharepoint/block-download-from-sites)

[Policy recommendations for securing SharePoint sites and files](/microsoft-365/enterprise/sharepoint-file-access-policies)
