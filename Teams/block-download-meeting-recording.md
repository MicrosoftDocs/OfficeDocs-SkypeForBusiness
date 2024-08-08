---
title: Block the download of Teams meeting recording and transcript files from SharePoint or OneDrive 
ms.reviewer: samust
ms.author: wlibebe
author: wlibebe
manager: pamgreen
recommendations: true
audience: Admin
f1.keywords: NOCSH
ms.topic: article
ms.service: msteams
ms.localizationpriority: medium
ms.date: 12/11/2023
ms.collection:
- Tier1
- Highpri
- Tier1
- m365initiative-meetings
search.appverid:
- SPO160
- MET150
- BSA160
description: Learn how administrators can block the download of Teams meeting recording and transcript files from SharePoint and OneDrive.
---

# Block the download of Teams meeting recording files from SharePoint or OneDrive

[!INCLUDE[Advanced Management](includes/advanced-management.md)]

You can block the download of Teams meeting recording and transcript files from SharePoint or OneDrive. This allows users to remain productive while addressing the risk of accidental data loss. Users have browser-only access to play the meeting recordings or view transcripts with no ability to download or sync files or access them through apps.

This policy applies to new meeting recordings and transcripts across the entire organization. You can exempt people who are members of specified security groups from the policy. This allows you to specify governance or compliance specialists who should have download access to meeting recordings and transcripts.

When the policy is enabled, any new Teams meeting recording and transcript files saved in SharePoint and OneDrive are blocked from download.

Because this policy affects meeting recordings stored in OneDrive and SharePoint, you must be a SharePoint Administrator to configure it. To learn more about meeting recording in OneDrive and SharePoint, see [Use OneDrive and SharePoint for meeting recordings](tmr-meeting-recording-change.md). To learn more about how your users use transcripts, see [View live transcription in Microsoft Teams meetings](https://support.microsoft.com/office/view-live-transcription-in-microsoft-teams-meetings-dc1a8f23-2e20-4684-885e-2152e06a4a8b).

This policy doesn't apply to manually uploaded meeting recording and transcript files.  

> [!IMPORTANT]
> This feature doesn't prevent the download of files that were uploaded by Teams prior to turning the policy on. If you would like to prevent download of these files, you can open a support ticket.

## Requirements

This feature requires a Microsoft Syntex - SharePoint Advanced Management license.

## Turn on the policy for your organization

Open the SharePoint Online Management Shell and connect to SharePoint as a SharePoint Administrator. To learn how, see [Get started with SharePoint Online Management Shell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

Run the following command:

```PowerShell
Set-SPOTenant -BlockDownloadFileTypePolicy <$true/$false(default)>  -BlockDownloadFileTypeIds  TeamsMeetingRecording
```

To enable this feature on, run this script:

```PowerShell
Set-SPOTenant -BlockDownloadFileTypePolicy $true  -BlockDownloadFileTypeIds TeamsMeetingRecording
```

## Exempt users in specified security groups from the policy

The following parameter can be used with this cmdlet if necessary:

`-ExcludedBlockDownloadGroupIds <comma separated security group IDs>`
  
This parameter exempts users in the specified security groups from this policy so that they can download meeting recording and transcript files.

## App impact

Blocking the download of Teams meeting recording and transcript files might affect the user experience in some apps, including some Office apps. We recommend that you enable the policy for some users and test the experience with the apps used in your organization.

> [!NOTE]
> Apps that run in "app-only" mode, like antivirus apps and search crawlers, are exempted from the policy.

## Need more help?

- [SharePoint Q&A](/answers/topics/office-sharepoint-online.html)

## Related topics

- [Block download policy for SharePoint sites and OneDrive](/sharepoint/block-download-from-sites)
- [Policy recommendations for securing SharePoint sites and files](/microsoft-365/enterprise/sharepoint-file-access-policies)
- [Admins- Manage transcription and captions for Teams meetings](meeting-transcription-captions.md)
- [Use OneDrive and SharePoint for meeting recordings](tmr-meeting-recording-change.md)
- [Teams meeting recording](meeting-recording.md)
