---
title: Use OneDrive for Business and SharePoint for meeting recordings
author: CarolynRowe
ms.author: crowe
ms.reviewer: debhag
manager: serdars
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: MET150
description: Learn how to switch from Stream to OneDrive for Business and SharePoint meeting recording storage in Microsoft Teams.
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
appliesto: 
  - Microsoft Teams
---

# Use OneDrive for Business and SharePoint or Stream for meeting recordings

> [!NOTE]
> The change of storing Teams meeting recordings from Classic Stream to OneDrive and SharePoint (ODSP) has been completed as of August 30th, 2021. All recordings are now stored in ODSP. This change overrides the RecordingStorageMode policy, and modifying the setting in PowerShell no longer has any impact.

|Date&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|Event&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;                                                                                                                                                                                                                                                                                                             |
|:-----------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|October 5, 2020<br> *(Complete)* &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;| You enable the Teams Meeting policy to have meeting recordings saved to OneDrive for Business and SharePoint instead of Microsoft Stream (Classic)|
|Rolling out starting January 7, 2021<br> *(Complete)* &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|All new Teams meeting recordings will be saved to OneDrive for Business and SharePoint unless you delay this change by modifying your organization’s Teams Meeting policies and explicitly setting them to **Stream**. Seeing the policy reporting as Stream isn't enough. You need to explicitly set the policy value to **Stream**.|
|Rolling out starting January 11, 2021<br> *(Complete)* &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|**GCC only**<br> While GCC customers can opt out starting October 5, you're unable to opt in. This feature will be rolled out to all GCC customers starting January 11, 2021, unless you've opted-out.<br>  <br>Starting on January 11, 2021, all new Teams meeting recordings for GCC customers will be saved to OneDrive for Business and SharePoint unless you delay this change by modifying your organization’s Teams Meeting policies and explicitly setting them to **Stream**. <br><br>If you've opted-out but are ready to turn on this feature, you may do so by setting your Teams Meeting Policy explicitly to **OneDrive for Business**. |
|Rolling out starting March 1, 2021<br> *(Complete)*  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|**GCC-High and DoD only**<br> Customers can now enable cloud meeting recordings in their Microsoft Teams for the first time. These recordings will be stored and played on OneDrive and SharePoint by default. |
|Rolling out incrementally starting August 16, 2021<br> *(Complete)* &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|**All customers (Enterprise, Education, and GCC)**<br>No new meeting recordings can be saved to Microsoft Stream (Classic); all customers will automatically have meeting recordings saved to OneDrive for Business and SharePoint even if they’ve changed their Teams meeting policies to Stream.<br><br> We recommend that customers, to better control the change in your organization, opt in whenever you're comfortable with the change rather than wait for it to happen. |

Microsoft Teams has a new method for saving meeting recordings. As the first phase of a transition from classic Microsoft Stream to the [new Stream](/stream/streamnew/new-stream), this method stores recordings on Microsoft OneDrive for Business and SharePoint in Microsoft 365 and offers many benefits.

> [!NOTE]
> If a Teams meeting recording fails to successfully upload to OneDrive/SharePoint, a "The recording ended unexpectedly" error message will appear and the recording will instead be temporarily saved to Azure Media Services (AMS). Once stored in AMS, no retry attempts are made to automatically upload the recording to OneDrive/SharePoint or Stream.

Meeting recordings stored in AMS are available for 21 days before being automatically deleted. Users can download the video from AMS if they need to keep a copy.

The benefits of using OneDrive for Business and SharePoint for storing recordings include:

- Retention policies for Teams meeting recording (TMR) (S+C E5 autoretention labels)
- Benefit from OneDrive for Business and SharePoint information governance
- Easy to set permissions and sharing
- Share recordings with guests with explicit share only
- Request access flow
- Provide OneDrive for Business and SharePoint shared links
- Meeting  recordings are available faster
- **Go local** tenant support
- Multi-geo support – recordings are stored in a region specific to that user
- Bring your own key (BYOK) support

See the full list of [features available today and what to expect over time](/stream/streamnew/features-new-version-stream).

Watch "What's New for Microsoft Teams Meeting Recordings" for more information.

> [!VIDEO https://www.youtube.com/embed/8iol0KfCeL8]

## Set up the meeting recording option for OneDrive for Business and SharePoint

The meeting recording option is a setting at the Teams policy level. The following example shows how to set the Global policy. Make sure that you set the meeting recording option for the policy or policies that you've assigned to your users.

> [!NOTE]
> Teams meeting policy changes take a while to propagate. Check back after a few hours of setting it, then sign out and sign in to the Teams Desktop app again or simply restart your computer.

1. Install Teams PowerShell.

   > [!NOTE]
   > Skype for Business Online Connector is currently part of the latest Teams PowerShell module. If you're using the latest Teams PowerShell public release, you don't need to install the Skype for Business Online Connector. See [Manage Skype for Business Online with PowerShell](/microsoft-365/enterprise/manage-skype-for-business-online-with-microsoft-365-powershell?preserve-view=true&view=o365-worldwide).

2. Launch PowerShell as an admin.

3. Install [Teams PowerShell module](./teams-powershell-install.md).

4. Import the MicrosoftTeams module and sign in as a Teams admin.

   ```powershell
   # When using Teams PowerShell Module
   
   Import-Module MicrosoftTeams
   $credential = Get-Credential
   Connect-MicrosoftTeams -Credential $credential
   ```

5. Use [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy) to set a Teams Meeting Policy to transition from the Stream storage to OneDrive for Business and SharePoint.

   ```powershell
   Set-CsTeamsMeetingPolicy -Identity Global -RecordingStorageMode "OneDriveForBusiness"
   ```

> [!NOTE]
> If some of your users have assigned a per-organizer or per-user policy, you must set this setting on this policy if you want them to also store the meeting recordings in OneDrive for Business and SharePoint. For more information, see [Manage meeting policies in Teams](meeting-policies-overview.md).

## Permissions or role-based access

> [!NOTE]
> We recommend that the recipient is required to be a logged-in user when sharing Teams meeting recordings. Select the **People in (Your Organization)** option when you share the file as documented in [Share SharePoint files or folders](https://support.microsoft.com/office/1fe37332-0f9a-4719-970e-d2578da4941c). External sharing isn't designed for the distribution of large files or a large number of files.

|Meeting type                               | Who clicked on Record?| Where does the recording land?                               |Who has access? R/W, R, or sharing                                                                                                                                                                                                                                                     |
|-------------------------------------------|-----------------------|--------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|1:1 call with internal parties             |Caller                 |Caller’s OneDrive for Business account                        |Caller is owner and has full rights. <br /><br />Callee (if in the same tenant) has read-only access. No sharing access. <br /><br /> Callee (if in different tenant) has no access. Caller must share it to the Callee.|
|1:1 call with internal parties             |Callee                 |Callee’s OneDrive for Business account                        |Callee is owner and has full rights. <br /><br />Caller (if in the same tenant has read-only access. No sharing access. <br /><br />Caller (if in different tenant) has no access. Callee must share it to the Caller.|
|1:1 call with an external call             |Caller                 |Caller’s OneDrive for Business account                        |Caller is owner and has full rights.<br /> <br />Callee has no access. Caller must share it to the Callee.|
|1:1 call with an external call             |Callee                 |Callee’s OneDrive for Business account                        |Callee is owner and has full rights.<br /><br />Caller has no access. Callee must share it to the Caller.|
|Group call                                 |Any member of the call |Group member who clicked on Record’s OneDrive for Business account  |Member who clicked on Record has full rights. <br /><br /> Other group members from the same tenant have Read rights. <br /><br /> Other group members from different tenant have no rights to it.|
|Adhoc/Scheduled meeting                    |Organizer              |Organizer’s OneDrive for Business account                     |Organizer has full rights to the recording. <br /><br /> All other members of the meeting have read access.|
|Adhoc/Scheduled meeting                    |Other meeting member   |Meeting member who clicked on Record                                  |Member who clicked on Record has full rights to the recording. <br /><br />Organizer has edit rights and can share.<br /><br /> All other meeting members have read access.|
|Adhoc/Scheduled meeting with external participants|Organizer              |Organizer’s OneDrive for Business account                     |Organizer has full rights to the recording.<br /> <br /> All other members of the meeting from the same tenant as the organizer have read access. <br /><br /> All other external participants have no access, and the Organizer must share it to them.|
|Adhoc/Scheduled meeting with external participants|Other meeting member   |Member who clicked on Record                                  |Member who clicked on Record has full rights to the recording. Organizer has edit rights and can share. <br /><br /> All other members of the meeting from the same tenant as the organizer have read access. <br /><br />All other external participants have no access, and the Organizer must share it to them.|
|Channel meeting                            |Channel Member         |Teams SharePoint location for that channel. **Note**: Channel meeting recording upload to SharePoint is not supported for IP-based restrictions. We recommend using [Azure conditional access](/azure/active-directory/conditional-access/overview). |Member who clicked on Record has edit rights to the recording. <br /> <br />Every other member’s permissions are based on the Channel SharePoint permissions.|

## Frequently asked questions

**Where will the meeting recording be stored?**

- For non-Channel meetings, the recording is stored in a folder named **Recordings** that's at the top level of the OneDrive for Business that belongs to the person who started the meeting recording. Example:

  *recorder's OneDrive for Business*/**Recordings**

- For Channel meetings, the recording is stored in the Teams site documentation library in a folder named **Recordings**. Example:

  *Teams name - Channel name*/**Documents**/**Recordings**

**When Stream files (such as recordings) are stored in SharePoint/OneDrive, how is it decided where they go? Does the admin have the ability to change where it goes?**

By default, all recording files will go to the OneDrive account of the user who selected **Record**. For channel meetings, the recording will always go to the SharePoint site of the channel. The admin can't change where the recording is stored.

**How do I handle recordings from former employees?**

Since videos are just like any other file in OneDrive for Business and SharePoint, handling ownership and retention after an employee leaves will follow the normal [OneDrive for Business and SharePoint process](/onedrive/retention-and-deletion).

**Who has the permissions to view the meeting recording?**

- For non-Channel meetings, all meeting invitees, except for external participants, will automatically get a personally shared link. External participants will need to be explicitly added to the shared list by the meeting organizer or the person who started the meeting recording.

- For Channel meetings, permissions are inherited from the owners and members list in the channel.

> [!NOTE]
> You'll not get an email when the recording finishes saving, but the recording will appear in the meeting chat once it’s finished. This will happen much quicker than it did in Stream previously.

**How can I manage captions?**

Closed captions for Teams meeting recordings will be available during playback only if the user had transcription turned on at the time of recording. Admins must [turn on recording transcription](meetings-policies-recording-and-transcription.md#transcription) to ensure their users have the option to record meetings with transcription.

Captions help create inclusive content for viewers of all abilities. As an owner, you can hide captions on the meeting recording, although the meeting transcript will still be available on Teams unless you delete it there.

Closed captions are supported for Teams meeting recordings for 60 days from when the meeting is recorded.

Closed captions aren't fully supported if the Teams Meeting Recording is moved or copied from its original location on OneDrive for Business or SharePoint.

> [!NOTE]
> There will be English-only closed captions (meeting transcription is not yet available in GCC).

**How will my storage quota be impacted?**

Teams meeting recording files live in OneDrive for Business and SharePoint and are included in your quota for those services. See
[SharePoint quota](/sharepoint/sites/plan-site-maintenance-and-management#quotas) and [OneDrive for Business quota](/onedrive/set-default-storage-space).

You get more storage with [OneDrive for Business](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits) compared with Stream and more fungible storage with SharePoint.

**How can I play a Teams meeting recording?**

Your video will play on the video player of OneDrive for Business or SharePoint depending on where you access the file.

**If you plan on deprecating adding to Stream, will existing videos stay as is and for how long?**

Stream as a platform won't be deprecated in the near future. The videos that currently live in Stream will stay there until we start migrating. Upon migration, those videos will be migrated to OneDrive for Business or SharePoint as well. Check [Migration details](/stream/streamnew/migration-details) for more information.

**How do I apply a retention label to Microsoft Teams meeting recordings?**

See [How to auto-apply a retention label](/microsoft-365/compliance/apply-retention-labels-automatically).

**How do I assign policies to my users in Microsoft Teams and which policies take precedence?**

See [Which policy takes precedence?](./policy-assignment-overview.md#which-policy-takes-precedence).

**Where does the recording go if the user doesn't have OneDrive for Business or SharePoint, or the storage quota is full?**

The recording will land in our temporary storage location where it will be held for 21 days. During that time, the organizer must download the recording. If not downloaded within 21 days, the recording is deleted.
