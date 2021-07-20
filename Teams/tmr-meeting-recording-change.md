---
title: Use OneDrive for Business and SharePoint Online for meeting recordings
author: cichur
ms.author: v-cichur
ms.reviewer: debhag
manager: serdars
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: MET150
description: Learn how to switch from Stream to OneDrive for Business and SharePoint Online meeting recording storage in Microsoft Teams.
localization_priority: Normal
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
appliesto: 
  - Microsoft Teams
---

# Use OneDrive for Business and SharePoint Online or Stream for meeting recordings

> [!Note]
> The change from using Microsoft Stream to OneDrive for Business and Microsoft SharePoint Online for meeting recordings will be a phased approach.

|<div style="width:290px">Date&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</div> |Event&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;                                                                                                                                                                                                                                                                                                             |
|:-----------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|October 5, 2020<br> *(Complete)* &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;| You enable the Teams Meeting policy to have meeting recordings saved to OneDrive for Business and SharePoint Online instead of Microsoft Stream (Classic)|
|Rolling out starting January 7, 2021<br> *(Complete)* &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|All new Teams meeting recordings will be saved to OneDrive for Business and SharePoint Online unless you delay this change by modifying your organization’s Teams Meeting policies and explicitly setting them to **Stream**. Seeing the policy reporting as Stream isn't enough. You need to explicitly set the policy value to **Stream**.|
|Rolling out starting January 11, 2021<br> *(Complete)* &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|**GCC only**<br> While GCC customers can opt out starting October 5, you're unable to opt in. This feature will be rolled out to all GCC customers starting January 11, 2021, unless you've opted-out.<br>  <br>Starting on January 11, 2021, all new Teams meeting recordings for GCC customers will be saved to OneDrive for Business and SharePoint Online unless you delay this change by modifying your organization’s Teams Meeting policies and explicitly setting them to **Stream**. <br><br>If you've opted-out but are ready to turn on this feature, you may do so by setting your Teams Meeting Policy explicitly to **OneDrive for Business**. |
|Rolling out starting March 1, 2021<br> *(Complete)*  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|**GCC-High and DoD only**<br> Customers can now enable cloud meeting recordings in their Microsoft Teams for the first time. These recordings will be stored and played on OneDrive and SharePoint Online by default. |
|Rolling out starting July 7, 2021<br> *(Complete)*  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|**All customers (Enterprise, Education, and GCC)**<br> For a Teams meeting that was recorded to OneDrive and SharePoint Online and was also transcribed live during the meeting, you can now search in Microsoft Search to find the meeting recording file based on the transcript. |
|Rolling out incrementally starting August 16, 2021 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|**All customers (Enterprise, Education, and GCC)**<br>No new meeting recordings can be saved to Microsoft Stream (Classic); all customers will automatically have meeting recordings saved to OneDrive for Business and SharePoint Online even if they’ve changed their Teams meeting policies to Stream.<br><br> We recommend that customers, to better control the change in your organization, opt in whenever you're comfortable with the change rather than wait for it to happen. |

Microsoft Teams has a new method for saving meeting recordings. As the first phase of a transition from classic Microsoft Stream to the [new Stream](/stream/streamnew/new-stream), this method stores recordings on Microsoft OneDrive for Business and SharePoint Online in Microsoft 365 and offers many benefits.

Stream (classic) as a platform won't be deprecated in the near future. The videos that currently live in Stream (classic) will stay there until a future migration tool is available to move them to OneDrive and SharePoint Online. Check [Stream classic migration](/stream/streamnew/classic-migration) for more information on our future plans.

> [!NOTE]
> If a Teams meeting recording fails to successfully upload to OneDrive/SharePoint Online, the recording will instead be temporarily saved to Azure Media Services (AMS). Once stored in AMS, no retry attempts are made to automatically upload the recording to OneDrive/SharePoint Online or Stream.

Meeting recordings stored in AMS are available for 21 days before being automatically deleted. Users can download the video from AMS if they need to keep a copy.

The benefits of using OneDrive for Business and SharePoint Online for storing recordings include:

- Retention policies for Teams meeting recording (TMR) (S+C E5 autoretention labels)
- Benefit from OneDrive for Business and SharePoint Online information governance
- Easy to set permissions and sharing
- Share recordings with guests (external users) with explicit share only
- Request access flow
- Provide OneDrive for Business and SharePoint Online shared links
- Meeting  recordings are available faster
- Search basis transcript recorded in your meeting
- **Go local** tenant support
- Multi-geo support – recordings are stored in a region specific to that user
- Bring your own key (BYOK) support

See the full list of [features available today and what to expect over time](/stream/streamnew/features-new-version-stream).

Watch "What's New for Microsoft Teams Meeting Recordings" for more information.

> [!VIDEO https://www.youtube.com/embed/8iol0KfCeL8]

## Set up the meeting recording option for OneDrive for Business and SharePoint Online

The meeting recording option is a setting at the Teams policy level. The following example shows how to set the Global policy. Make sure that you set the meeting recording option for the policy or policies that you've assigned to your users.

> [!Note]
> Teams meeting policy changes take a while to propagate. Check back after a few hours of setting it, then sign out and sign in to the Teams Desktop app again or simply restart your computer.

1. Install Teams PowerShell PowerShell.

   > [!NOTE]
   > Skype for Business Online Connector is currently part of the latest Teams PowerShell module. If you're using the latest Teams PowerShell public release, you don't need to install the Skype for Business Online Connector. See [Manage Skype for Business Online with PowerShell](/microsoft-365/enterprise/manage-skype-for-business-online-with-microsoft-365-powershell?preserve-view=true&view=o365-worldwide).

2. Launch PowerShell as an admin.

3. Install [Teams PowerShell module](./teams-powershell-install.md).

4. Import the MicrosoftTeams module and sign in as a Teams admin.

   ```powershell
   # When using Teams PowerShell Module
   
   Import-Module MicrosoftTeams
   Connect-MicrosoftTeams
   ```

5. Use [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy) to set a Teams Meeting Policy to transition from the Stream storage to OneDrive for Business and SharePoint Online.

   ```powershell
   Set-CsTeamsMeetingPolicy -Identity Global -RecordingStorageMode "OneDriveForBusiness"
   ```

> [!Note]
> If some of your users have assigned a per-organizer or per-user policy, you must set this setting on this policy if you want them to also store the meeting recordings in OneDrive for Business and SharePoint Online. For more information, see [Manage meeting policies in Teams](meeting-policies-in-teams.md).

## Learn more

To learn more about Teams cloud meeting recording read the [Teams cloud meeting recording](cloud-recording.md) article. In that article you can learn more about recording setup, managment, governance, permissions, and storage.