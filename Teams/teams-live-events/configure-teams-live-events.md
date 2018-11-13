---
title: Configure live events in Microsoft Teams
author: tonysmith
ms.author: tonysmit
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: tonysmit
search.appverid: MET150
description: Learn how to configure live event settings in Microsoft Teams, including setting attendee visibility and recording options.
appliesto: 
- Microsoft Teams
---

# Configure live events in Microsoft Teams
> [!INCLUDE [Preview customer token](../includes/preview-feature.md)]

## Set up event support link
This is the link that will be shown to the live event attendees. 

In Windows PowerShell, run the following:
```
Set-CsTeamsMeetingBroadcastConfiguration -SupportURL “{your URL}” 
```
## Configure attendee visibility options
This allows live event organizers to create events with appropriate attendee visibility.

|**Values**  |**Behavior**  |
|---------|---------|
|Everyone     |The user has an option to create live events with the following attendee visibility: Public, Everyone in company, and Specific people. |
|EveryoneInCompany     |The user has an option to create live events with the following attendee visibility: Everyone in company and Specific people. The user cannot create live events that can be attended by anonymous users.|
|InvitedUsers |The user can only create live events that are limited to specific people as entered by the event organizer. The user cannot create live events with Public and Everyone in company authentication. |

Use the setting BroadcastAttendeeVisibility in TeamsMeetingBroadcastPolicy in PowerShell to control whether the users can schedule broadcast events that can be watched by anonymous attendees. 

Unless you have assigned a custom policy to the users, the users get Global policy, which has default set to EveryoneInCompany. 
 
In Windows PowerShell, run the following to allow users to create anonymous events in the global policy:
```
Set-CsTeamsMeetingBroadcastPolicy -Identity Global -BroadcastAttendeeVisibility Everyone  
```
## Configure recording options
> [!NOTE]
> This option is applicable to events that use the Quick start production method only.

This allows admins to control whether the live events are always recorded, never recorded, or whether the event organizer can decide to record the event or not.  

|**Values**  |**Behavior**  |
|---------|---------|
|Always enabled |The live events organized by this user are always recorded. The user doesn’t have an option to override. If the live event is recorded, the event team members are able to download the recording after the event, and the attendees can watch the event after the event is over. |
|AlwaysDisabled |The live events organized by this user are never recorded. The user doesn’t have an option to override. If the live event is recorded, no recording is created for the event team members, and the attendees cannot watch the event after it is over. |
|UserOverride |User can decide whether the live event is recorded so that a recording file can be created for the event team members, and attendees can watch the event after the event is over. |

Use the setting *BroadcastRecordingMode* in **TeamsMeetingBroadcastPolicy** in PowerShell to control recording options of the live events created by the live event organizer.

In Windows PowerShell, run the following cmdlet to update recording mode in the global policy:
```
Set-CsTeamsMeetingBroadcastPolicy -Identity Global -BroadcastRecordingMode AlwaysDisabled 
```
## Configure real-time transcription and translation in Teams live events (coming soon)
> [!NOTE]
> This option is applicable to events that use the Quick start production method only.

This allows live event organizers to turn on real-time captions and translation for the live event attendees. 

Use the setting *AllowBroadcastTranscription* in **TeamsMeetingBroadcastPolicy** in PowerShell to control whether the live event attendees will be able to see transcription and translation. You can learn more about managing **TeamsMeetingBroadcastPolicy** with Office 365 PowerShell here.  

Unless you have assigned a custom policy to the users, the users get Global policy, which has transcription and translation disabled by default.

In Windows PowerShell, run the following cmdlet to turn transcription and translation on for event attendees in the global policy:
```
Set-CsTeamsMeetingBroadcastPolicy -Identity Global -AllowBroadcastTranscription $true 
```
## Administrative tools 
Although Microsoft directly controls all Office 365 Online data centers and is responsible for overall system performance, it can control only a portion of the elements that combine to provide the total experience for Office 365 users. Organizations themselves are responsible for the network connections to the data centers, the customer’s wide area network (WAN), and the customer's local area networks (LANs). Additionally, they are in charge of user devices and their configuration. They are also responsible for maintaining the required licensing per user for any desired feature, including, but not limited to, the ability to manage these features, for as long as the user needs access to the feature.

Customers can use the following tools to manage a variety of Teams live events related tasks.
- [Microsoft Office 365 admin center](https://technet.microsoft.com/library/exchange-online-administration-and-management.aspx?f=255&MSPPError=-2147217396#BKMK_Office365admincenterl)
- [Microsoft Teams and Skype for Business Online admin center](https://technet.microsoft.com/library/exchange-online-administration-and-management.aspx?f=255&MSPPError=-2147217396#BKMK_ExchangeAdministrationCenter)
- [Microsoft Stream admin center](https://stream.microsoft.com)
- [Remote Windows PowerShell](https://technet.microsoft.com/library/exchange-online-administration-and-management.aspx?f=255&MSPPError=-2147217396#BKMK_RemoteWindowsPowerShell)

## Want to know more about Windows PowerShell?
When it comes to Windows PowerShell, it's all about managing users and what users are allowed or not allowed to do. With Windows PowerShell, you can manage Office 365 and Skype for Business Online using a single point of administration that can simplify your daily work when you have multiple tasks to do. To get started with Windows PowerShell, see these topics:
 - [An introduction to Windows PowerShell and Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525039)
 - [Why you need to use Office 365 PowerShell](https://go.microsoft.com/fwlink/?LinkId=525041)

Windows PowerShell has many advantages in speed, simplicity, and productivity over only using the Office 365 admin center such as when you are making setting changes for many users at one time. Learn about these advantages in the following topics:
 - [Best ways to manage Office 365 with Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=525142)
 - [Using Windows PowerShell to manage Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525453)
 - [Using Windows PowerShell to do common Skype for Business Online management tasks](https://go.microsoft.com/fwlink/?LinkId=525038)
