---
title: Use OneDrive and SharePoint for meeting recordings
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
appliesto: 
  - Microsoft Teams
---

# Use OneDrive for Business and SharePoint or Stream for meeting recordings

> [!Note]
> ​​The change from using Microsoft Stream to OneDrive for Business and SharePoint for meeting recordings will be a phased approach. At launch you'll be able to opt-in to this experience, in November you'll have to opt-out if you want to continue using Stream, and some time in early 2021 we'll require all customers to use OneDrive for Business and SharePoint for new meeting recordings.

Microsoft Teams has a new method for saving meeting recordings. As a departure from Stream, the method uses Microsoft OneDrive and SharePoint in Microsoft 365 and offers many benefits:

The benefits of using OneDrive for Business and SharePoint for storing recordings include:

- Retention policies for Teams meeting recording (TMR) (S+C E5 auto-retention labels)
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

There are a some limitations to consider:

- There will be English-only closed captions and transcripts​.
- You won't be able to search transcripts or their content​.
- You won’t be able to edit the transcripts, but you'll be able to toggle captions off/on.
- You can control with whom you share the recording, but you won't be able to block people with shared access from downloading the recording.
- You'll not get an email when the recording finishes saving, but the recording will appear in the meeting chat once it’s finished. This will happen much quicker than it did in Stream previously

## Set up the meeting recording option for OneDrive for Business and SharePoint

1. Install the Skype For Business Online Powershell admin console.

    a. Download [Sype for Business Online Powershell](https://docs.microsoft.com/microsoft-365/enterprise/manage-skype-for-business-online-with-microsoft-365-powershell?view=o365-worldwide).

    b. Follow the prompts to install it.

    c. Restart your machine.

2. Launch Powershell as an admin

3. Import the SkypeOnline Connector and log in as a Teams admin.

```PowerShell
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
```

4. Use [set-csteamsmeetingpolicy](https://docs.microsoft.com/powershell/module/skype/set-csteamsmeetingpolicy?view=skype-ps) to set a Teams Meeting Policy to transition from the Stream storage to ODSP.

```PowerShell
   Set-CsTeamsMeetingPolicy -Identity Global -RecordingStorageMode "OneDriveForBusiness"
```

## Opt out of OneDrive for Business and SharePoint to continue using Stream

Even if a policy says it’s already set to **Stream**, it might not be set. If it's set to nothing, then the default is Stream. If you want to opt-out you **must** reset the policy to **Stream** to ensure that Stream is the default.

```PowerShell
   Set-CsTeamsMeetingPolicy -Identity Global -RecordingStorageMode "Stream"
```

## Frequently asked questions

**Where will the meeting recording be stored?**

- For non-Channel meetings, the recording is stored in a folder named **Recordings** that is at the top level of the OneDrive that belongs to the person who started the meeting recording. Example:

  <i>recorder's OneDrive for Business</i>/**Recordings**

- For Channel meetings, the recording is stored in the Teams site documentation library in a folder named **Recordings**. Example:

  <i>Teams name - Channel name</i>/**Documents**/**Recordings**

**Who has the permissions to view the meeting recording?**

- For non-Channel meetings, all meeting invitees, except for external users, will automatically get a personally shared link. External users will need to be explicitly added to the shared list by the meeting organizer or the person who started the meeting recording.

- For Channel meetings, permissions are inherited from the owners and members list in the channel.

**How can I manage transcripts?**

Customers opting in to this preview will not have closed captions available on their Teams Meeting Recordings that are migrated to OneDrive and SharePoint.  We're working to add captioning, beginning with closed captions in English, to meeting recordings in October 2020.

Closed captions will be available on Teams Meeting Recordings for customers who've opted in to allow transcripts as described in [Teams cloud recordings](cloud-recording.md)

Captions help create inclusive content for viewers of all abilities. As an owner, you can hide captions, although the transcript will still be available on Teams unless you delete the captions from Teams. See [how to turn on or off meeting recordings](cloud-recording.md#turn-on-or-turn-off-recording-transcription.md)

Closed captions are supported for Teams meeting recordings for 60 days from when the meeting is recorded.

**How will my storage quota be impacted**

Teams meeting recording files live in OneDrive for Business and SharePoint and are included in your quota for those services. See
[SharePoint quota](https://docs.microsoft.com/sharepoint/sites/plan-site-maintenance-and-management#quotas) and [OneDrive for Business quota] (https://docs.microsoft.com/onedrive/set-default-storage-space).

**How can I play a Teams meeting recording?**

Your video will play on the video player of OneDrive for Business or SharePoint depending on where you access the file.
