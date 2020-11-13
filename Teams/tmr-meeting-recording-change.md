---
title: Use OneDrive for Business and SharePoint for meeting recordings
author: cichur
ms.author: v-cichur
ms.reviewer: hao.moy
manager: serdars
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: MET150
description: Learn how to switch from Stream to OneDrive for Business and SharePoint meeting recording storage in Microsoft Teams.
localization_priority: Normal
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
appliesto: 
  - Microsoft Teams
---

# Use OneDrive for Business and SharePoint or Stream for meeting recordings

> [!Note]
> The change from using Microsoft Stream to OneDrive for Business and Microsoft SharePoint for meeting recordings will be a phased approach.

|<div style="width:200px">Date</div> |Event                                 |
|------------------------------------------------------------|-------------------------------------------------------------------------|
|October 5, 2020 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;        | You can enable the Teams Meeting policy to have meeting recordings saved to OneDrive for Business and SharePoint instead of Microsoft Stream (Classic)|
|Rolling out starting January 11, 2021 &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;        |All new Teams meeting recordings will be saved to OneDrive for Business and SharePoint unless you delay this change by modifying your organization’s Teams Meeting policies and explicitly setting them to **Stream**. Seeing the policy reporting as Stream is not enough. You need to explicitly set the policy value to **Stream**.|
|Rolling out starting March 1, 2021 &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;      |**Enterprise customers**<br>No new meeting recordings can be saved to Microsoft Stream (Classic); all customers will automatically have meeting recordings saved to OneDrive for Business and SharePoint even if they’ve changed their Teams meeting policies to **Stream**. We recommend that customers roll this feature out before this date so that they can control the timing of the release. |
|Rolling out starting July 7, 2021 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;     |**Education customers**<br>No new meeting recordings can be saved to Microsoft Stream (Classic); all customers will automatically have meeting recordings saved to OneDrive for Business and SharePoint even if they’ve changed their Teams meeting policies to **Stream**. We recommend that customers roll this feature out before this date so that they can control the timing of the release. We have updated this schedule to provide education customers the ability to complete in-progress semesters. |

> [!Note]
> We recommend that Enterprise and Educational customers, to better control the change in your organization, opt in whenever you're comfortable with the change rather than wait for it to happen. 

Microsoft Teams has a new method for saving meeting recordings. As the first phase of a transition from classic Microsoft Stream to the [new Stream](https://docs.microsoft.com/stream/streamnew/new-stream), this method stores recordings on Microsoft OneDrive for Business and SharePoint in Microsoft 365 and offers many benefits.

The benefits of using OneDrive for Business and SharePoint for storing recordings include:

- Retention policies for Teams meeting recording (TMR) (S+C E5 autoretention labels)
- Benefit from OneDrive for Business and SharePoint information governance
- Easy to set permissions and sharing
- Share recordings with guests (external users) with explicit share only
- Request access flow
- Provide OneDrive for Business and SharePoint shared links
- Increased quota
- Meeting  recordings are available faster
- **Go local** tenant support
- Multi-geo support – recordings are stored in a region specific to that user
- Bring your own key (BYOK) support
- Improved Transcript quality and speaker attribution

There are some limitations to consider:

- There will be English-only closed captions and transcripts​.
- You won't be able to search transcripts or their content​.
- You won’t be able to edit the transcripts, but you'll be able to toggle captions off/on.
- You can control with whom you share the recording, but you won't be able to block people with shared access from downloading the recording.
- You'll not get an email when the recording finishes saving, but the recording will appear in the meeting chat once it’s finished. This will happen much quicker than it did in Stream previously

Watch "Meeting Recording" for more information.

> [!VIDEO https://www.youtube.com/embed/8iol0KfCeL8]

## Set up the meeting recording option for OneDrive for Business and SharePoint

> [!Note]
> The meeting recording option is a setting at the Teams policy level. The following example shows how to set the Global policy. Make sure that you set the meeting recording option for the policy or policies that you've assigned to your users.
> Teams meeting policy changes take awhile to propagate. Check back after a few hours of setting it, then sign out and sign in again.

1. Install Skype For Business Online PowerShell.
**Note**: Skype for Business Online Connector is currently part of the latest Teams PowerShell module. If you're using the latest Teams PowerShell public release, you don't need to install the Skype for Business Online Connector. See [Manage Skype for Business Online with PowerShell](https://docs.microsoft.com/microsoft-365/enterprise/manage-skype-for-business-online-with-microsoft-365-powershell?view=o365-worldwide&preserve-view=true).

    a. Download [Skype for Business Online PowerShell](https://docs.microsoft.com/microsoft-365/enterprise/manage-skype-for-business-online-with-microsoft-365-powershell?view=o365-worldwide&preserve-view=true).

    b. Follow the prompts to install it.

    c. Restart your machine.

2. Launch PowerShell as an admin

3. Import the SkypeOnline Connector and log in as a Teams admin.

   ```powershell
   Import-Module SkypeOnlineConnector
   $sfbSession = New-CsOnlineSession
   Import-PSSession $sfbSession
   ```

4. Use [set-csteamsmeetingpolicy](https://docs.microsoft.com/powershell/module/skype/set-csteamsmeetingpolicy?view=skype-ps&preserve-view=true) to set a Teams Meeting Policy to transition from the Stream storage to OneDrive for Business and SharePoint.

   ```powershell
   Set-CsTeamsMeetingPolicy -Identity Global -RecordingStorageMode "OneDriveForBusiness"
   ```

## Opt out of OneDrive for Business and SharePoint to continue using Stream

Even if a policy says it's set to **Stream**, it might not be set. Typically, if the policy isn't set, then the default setting is **Stream**. However, with this new change, if you want to opt-out of using SharePoint or OneDrive for Business, then you must reset the policy to **Stream** to ensure that it's the default.

```PowerShell
Set-CsTeamsMeetingPolicy -Identity Global -RecordingStorageMode "Stream"
```

## Permissions or role-based access

|Meeting type                               | Who clicked on Record?| Where does the recording land?                               |Who has access? R/W, R or sharing                                                                                                                                                                                                                                                     |
|-------------------------------------------|-----------------------|--------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|1:1 call with internal parties             |Caller                 |Caller’s OneDrive for Business account                        |Caller is owner, has full rights <br /><br />Callee (if in the same tenant) has read only access, no sharing access <br /><br /> Callee (if in different tenant) has no access. Caller must share it to the Callee|
|1:1 call with internal parties             |Callee                 |Callee’s OneDrive for Business account                        |Callee is owner, has full rights <br /><br />Caller (if in the same tenant has read only access, no sharing access <br /><br />Caller (if in different tenant) has no access. Callee must share it to the Callee|
|1:1 call with an external call             |Caller                 |Caller’s OneDrive for Business account                        |Caller is owner, has full rights<br /> <br />Callee has no access. Caller must share it to the Callee|
|1:1 call with an external call             |Callee                 |Callee’s OneDrive for Business account                        | Callee is owner, has full rights<br /><br />Caller has no access. Callee must share it to the Caller|
|Group call                                 |Any member of the call |Member who clicked on Record’s OneDrive for Business account  |Member who clicked on Record has full rights <br /><br /> Other members from the same tenant have Read rights <br /><br /> Other members from different tenant have no rights to it.|
|Adhoc/Scheduled meeting                    |Organizer              |Organizer’s OneDrive for Business account                     | Organizer has full rights to the recording <br /><br /> All other members of the meeting have read access|
|Adhoc/Scheduled meeting                    |Other meeting member   |Member who clicked on Record                                  | Member who clicked on Record has full rights to the recording <br />Organizer has edit rights and can share <br /><br /> All other members have read access|
|Adhoc/Scheduled meeting with external users|Organizer              |Organizer’s OneDrive for Business account                     |Organizer has full rights to the recording<br /> <br /> All other members of the meeting from the same tenant as the organizer have read access <br /><br /> All other external members have no access and the Organizer must share it to them|
|Adhoc/Scheduled meeting with external users|Other meeting member   |Member who clicked on Record                                  | Member who clicked on Record has full rights to the recording - Organizer has edit rights and can share <br /><br /> All other members of the meeting from the same tenant as the organizer have read access <br /><br />All other external members have no access and the Organizer must share it to them|
|Channel meeting                            |Channel Member         |Teams' SharePoint location for that channel                   | Member who clicked on Record has edit rights to the recording <br /> <br />Every other member’s permissions are based off of the Channel SharePoint permissions|


## Frequently asked questions

**Where will the meeting recording be stored?**

- For non-Channel meetings, the recording is stored in a folder named **Recordings** that is at the top level of the OneDrive for Business that belongs to the person who started the meeting recording. Example:

  <i>recorder's OneDrive for Business</i>/**Recordings**

- For Channel meetings, the recording is stored in the Teams site documentation library in a folder named **Recordings**. Example:

  <i>Teams name - Channel name</i>/**Documents**/**Recordings**

**How do I handle recordings from former employees?**

Since videos are just like any other file in OneDrive for Business and SharePoint, handling ownership and retention after an employee leaves will follow the normal [OneDrive for Business and SharePoint process]( https://docs.microsoft.com/onedrive/retention-and-deletion#the-onedrive-deletion-process).

**Who has the permissions to view the meeting recording?**

- For non-Channel meetings, all meeting invitees, except for external users, will automatically get a personally shared link. External users will need to be explicitly added to the shared list by the meeting organizer or the person who started the meeting recording.

- For Channel meetings, permissions are inherited from the owners and members list in the channel.

**How can I manage transcripts?**

Customers opting in to this preview will not have closed captions available on their Teams Meeting Recordings that are migrated to OneDrive for Business and SharePoint.  We're working to add captioning, beginning with closed captions in English, to meeting recordings in October 2020.

Closed captions will be available on Teams Meeting Recordings for customers who have opted in to allow transcripts as described in [Teams cloud recordings](cloud-recording.md)

Captions help create inclusive content for viewers of all abilities. As an owner, you can hide captions, although the transcript will still be available on Teams unless you delete the captions from Teams. See [how to turn on or off meeting recordings](cloud-recording.md#set-up-teams-cloud-meeting-recording-for-users-in-your-organization)

Closed captions are supported for Teams meeting recordings for 60 days from when the meeting is recorded.

Closed captions are not fully supported if the Teams Meeting Recording is moved or copied from its original location on OneDrive for Business or SharePoint.

**How will my storage quota be impacted**

Teams meeting recording files live in OneDrive for Business and SharePoint and are included in your quota for those services. See
[SharePoint quota](https://docs.microsoft.com/sharepoint/sites/plan-site-maintenance-and-management#quotas) and [OneDrive for Business quota] (https://docs.microsoft.com/onedrive/set-default-storage-space).

**How can I play a Teams meeting recording?**

Your video will play on the video player of OneDrive for Business or SharePoint depending on where you access the file.

**If you plan on deprecating adding to Stream, will existing videos stay as is and for how long?**

Stream as a platform won't be deprecated in the near future. The videos that currently live in Stream will stay there until we start migrating. Upon migration, those videos will be migrated to OneDrive for Business or SharePoint as well. Check [here](https://docs.microsoft.com/stream/streamnew/classic-migration) for more information.

**How do I apply a retention label?**

See [How to auto-apply a retention label](https://docs.microsoft.com/microsoft-365/compliance/apply-retention-labels-automatically?view=o365-worldwide#microsoft-teams-meeting-recordings).
