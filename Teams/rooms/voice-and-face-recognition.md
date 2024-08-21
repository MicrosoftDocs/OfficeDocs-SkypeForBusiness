---
title: Overview of voice and face enrollment
ms.author: tonysmit
author: mstonysmith
manager: pamgreen
ms.reviewer: parisataheri  
ms.date: 05/02/2024  
ms.topic: article
audience: admin
appliesto: 
  - Microsoft Teams
ms.service: msteams
ms.subservice: itpro-rooms
ms.collection: 
  - M365-collaboration
  - teams-rooms-consoles
  - Tier1
f1.keywords: 
  - NOCSH                           
search.appverid: MET150
ms.localizationpriority: medium
ms.custom: QuickDraft
description: Learn how admins can manage and control voice and face enrollment in Microsoft Teams to ensure data privacy and a better user experience.
---

# Overview of voice and face enrollment

Voice and face enrollment is a feature in Microsoft Teams that allows users to create a voice and face profile. Voice and face enrollment is used to improve the audio quality and user experience of Teams meetings and calls. This feature helps to reduce background noise and secondary speakers and provides speaker attribution and Microsoft CoPilot accuracy in meeting rooms equipped with Microsoft Teams Rooms devices. Admins and security teams can manage and control this feature and ensure for which user the enrollment and usage of the profile are turned on.

Users can unenroll their profile, even if the admin disables enrollment for them. Users can save their information by staying enrolled so they are in full control of their voice and face data. See [Create Recognition profiles for Microsoft IntelliFrame](https://support.microsoft.com/office/create-recognition-profiles-for-microsoft-intelliframe-f0084478-52a7-4c52-bcdc-9063ed0e0bc0).

This article covers:

- [Enrollment process](#enrollment-process): Users can use the enrollment process to get started.
- [Data handling](#data-handling): The duration that Microsoft Teams stores and processes the voice and face data of users.
- [Data retention](#data-retention): The duration that Microsoft Teams keeps the voice and face profiles of users.
- [Admin settings](#admin-settings): Admins can turn on or off voice and face enrollment for specific users, groups of users, or the whole organization. They can configure the feature using PowerShell.

- [Data export](#data-export): Admins can export the voice and face profiles of users for backup 

- [Frequently asked questions](#frequently-asked-questions): Common questions and answers.

By providing detailed information on how Microsoft Teams stores and handles user data, this article aims to ensure peace of mind and control for IT admins, security teams, and legal teams.

> [!NOTE]
> Microsoft doesn't use the voice and face profiles of users to train any models or for any other purposes other than providing the voice and face enrollment feature in Microsoft Teams.

## Enrollment process

If the policy turns on enrollment for users and they're already enrolled, they can update their Voice and Face profile using the Teams Desktop app to make their experience even better.

By default, recognition tab in the Microsoft Teams app is disabled. In the Teams app users go to **Setting** > **Recognition** to enroll their voice first, and then their face. Users must enroll their voice first before they can enroll their face. They can't however, only enroll their face. If a user removes their voice profile, their face profile is removed automatically along with it. However, if users remove their face profile, only their face profile is removed and their voice profile is still there.

Users can delete their voice and face profile at any time using the Teams desktop app, even if the policy for enrollment was turned off.

### Supported languages for enrollment

The language of the Teams app that is installed determines the voice enrollment languages. These are the localized versions that are available:

- en-us
- en-gb
- en-ca
- en-in
- en-au
- en-nz
- ar-sa
- da-dk
- de-de
- es-es
- es-mx
- fi-fi
- fr-ca
- fr-fr
- it-it
- ja-jp
- ko-kr
- nb-no
- nl-nl
- pl-pl
- pt-br
- ru-ru
- sv-se
- zh-cn
- zh-tw

> [!NOTE]
> There is no language requirement for face enrollment, but you need to create your voice profile before you can enroll your face.

> [!IMPORTANT]
> If the language you are looking for isn't supported for enrolling your voice, Microsoft is currently exploring fallback options.

## Data handling

When a user enrolls in voice and face enrollment, Microsoft Teams captures their voice and face data to create a unique profile that is associated with their identity. The profile consists of a set of biometric features that can be used to enhance the user's voice in Teams meetings and calls and recognize them in meeting rooms with their voice and face.

The voice and face data for users is stored in the same region as their Microsoft Teams data. For example, if a user's Teams data is stored in the European Union, their voice and face data is stored and processed in the European Union. This ensures compliance with data sovereignty and privacy regulations in different regions.

The voice and face data for users is encrypted at rest and in transit and is protected by Microsoft's security and privacy policies and practices. Microsoft doesn't access or share the voice and face data of users with any third parties, unless required by law or with the user's consent.

## Data retention

When a user is enrolled in the feature and has an active Teams account, Microsoft keeps their voice and face profiles. Their voice and face profile is removed right away if they unenroll from the feature. Their voice and face profile is removed within 90 days if their Teams account is deleted. Admins can download voice and face profiles of users manually, using the Teams Admin Center. 

If users enroll their voice or face profile, they can always choose to unenroll it later, even if the current assigned admin policy doesn't let them enroll.

A voice and face profile that isn't used for one year will be removed automatically. The user has to enroll again if they want to use the features.

When a user also uses Voice Isolation on their device, a local copy of the voice signature is stored encrypted. This signature expires after 14 days and will be replaced with a new download.

If users leave the organization, the customer data is deleted accordingly with the customer's data retention policy.

## Admin settings

Please connect to PowerShell and ensure you are running the latest version. For detailed instructions and the update command, refer to the [Install Microsoft Teams PowerShell ](/microsoftteams/teams-powershell-install) article.

Admins can turn on or off voice and face enrollment for specific users, or groups using the [Team meeting policy](/powershell/module/teams/set-csteamsmeetingpolicy). By default, voice and face enrollment is disabled for all users in the organization, but admins can change this setting using PowerShell:

```Powershell
Set-CsTeamsMeetingPolicy -Identity Global -EnrollUserOverride Enabled 
```


```Powershell
Set-CsTeamsMeetingPolicy -Identity Global -EnrollUserOverride Disabled 
```

To enable or disable voice and face enrollment for specific users, admins can either assign a custom meeting policy to the users or use the following PowerShell cmdlet:

```Powershell
Set-CsTeamsMeetingPolicy -Identity -PolicyName -EnrollUserOverride Enabled
```

 


```Powershell
Set-CsTeamsMeetingPolicy -Identity -PolicyName -EnrollUserOverride Disabled 
```

 

Admins can manage how voice and face profiles are used to turn off Voice Isolation for users to enhance noise and voice background reduction admins can switch off voice isolation with PowerShell in the meeting policy.

```powershell
  -VoiceIsolation Enabled 
```


```Powershell

  -VoiceIsolation Disabled
```

 

To prevent recognition of users in meeting rooms, admins can turn off (default) face and voice identification on the Microsoft Teams room account in the meeting policy.

- roomPeopleNameUserOverride = On | Off (default)
- roomAttributeUserOverride = Off (default) | Distinguish | Attribute

## Data export

Admins can export the voice and face profiles of users for backup, using Teams Admin Center. The exported profiles are in the form of ZIP files that contain the voice sample and face images of the user.

To export the voice and face profiles of users using the Teams Admin Center, admins can go to **Users > Manage users > Account > Biometric Profile > Download biometric profile**. 

## Frequently asked questions

**Question:** With regard to the user's voice enrollments, where do you store the data?  
**Answer:** Voice data is stored in the Office 365 trusted compliance store.

**Question:** Can both users and admins control the data being saved?  
**Answer:** Yes, both users and admins have control over the data being saved. Users are able to unenroll their voice. If users need to access their data, they would need to contact their admin. Users have full control of when to remove the data, and when a user selects unenroll from the Teams app, the data will be immediately deleted.

**Question:** For how long do you keep the data?  
**Answer:** The retention policy is one year. User's data will be deleted if it isn't used for one year.

**Question:** How is data stored and processed for cross tenants?  

**Answer:** We don't support getting data cross-tenant. We only retrieve data for their tenant only.

