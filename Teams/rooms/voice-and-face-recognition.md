---
title: Turning on or off voice and face enrollment
ms.author: tonysmit
author: tonysmit
manager: pamgreen
ms.reviewer: parisataheri  
ms.date: 04/21/2024  
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
ai-usage:  
- ai-assisted  
description: Learn how admins can manage and control voice and face enrollment in Microsoft Teams to ensure data privacy and a better user experience.
---

## Voice and face enrollment

Voice and face enrollment is a feature in Microsoft Teams that allows users to create a voice and face profile that can be used to improve the audio quality and user experience of Teams meetings and calls. This feature can help to reduce background noise and secondary speakers, as well as provide speaker attribution and CoPilot accuracy in meeting rooms that are equipped with Microsoft Teams Rooms devices. IT Admins and Security teams can manage and control this feature and ensure for which user the enrollment and usage of the profile are enabled.

Users always have the option to unenroll their profile, even if the admin disables enrollment for them, to keep the user in full control of their voice and face data. See [Create Recognition profiles for Microsoft IntelliFrame](office/create-recognition-profiles-for-microsoft-intelliframe).

In this article we will cover:

- [Enrollment process](#enrollment-process)
- [Data handling](#data-handling) how Microsoft Teams stores and processes the voice and face data of users
- [Data retention](#data-retention) how long Microsoft Teams keeps the voice and face profiles of users
- [Admin settings](#admin-settings) how IT Admins can enable or disable voice and face enrollment for their organization or specific users, and how they can configure the feature via Teams Admin Center and PowerShell
- [Data export:](#data-export) how IT Admins can export the voice and face profiles of users for backup or migration purposes
- [Frequently asked questions](#frequently-asked-questions)

By providing detailed information on how Microsoft Teams stores and handles user data, this article aims to ensure peace of mind and control for IT admins, security teams, and legal teams.

NOTE: Microsoft doesn't use the voice and face profiles of users to train any models or for any other purposes than providing the voice and face enrollment feature in Microsoft Teams and the above functionalities.

## Enrollment process

Users can enroll their voice and face under settings-\> Recognition in the Microsoft Teams client if these policies are enabled for them (default). Users have to enroll their voice before they can enroll their face; they cannot enroll only the face. If users remove their voice profile, their face profile is also removed automatically, but if users remove their face profile, only their face profile is removed. As long as users are already enrolled and have the policy enabled for enrollment, they can update their Voice and Face profile through their Teams Desktop Client to make their experience better. Users can always delete their Voice and Face profile through their Teams Desktop Client if they are already enrolled, even if the policy for enrollment is not enabled for them anymore.

### Supported languages for enrollment

The language of the local Teams client determines the voice enrollment languages, and these are the supported combinations:

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
>If the language you are looking for isn't supported for enrolling your voice, Microsoft is exploring fallback options to English or the closest language to what the user chooses.

## Data handling

When a user enrolls in voice and face enrollment, Microsoft Teams captures their voice and face data to create a unique profile that is associated with their identity. The profile consists of a set of biometric features that can be used to enhance the user's voice in Teams meetings and calls and recognize them in meeting rooms with their voice and face.

The voice and face data of users is stored and processed in the same region as their Teams data. For example, if a user's Teams data is stored in the European Union, their voice and face data will also be stored and processed in the European Union. This ensures compliance with data sovereignty and privacy regulations in different regions.

The voice and face data of users is encrypted at rest and in transit and is protected by Microsoft's security and privacy policies and practices. Microsoft does not access or share the voice and face data of users with any third parties, unless required by law or with the user's consent.

## Data retention

When a user is enrolled in the feature and has an active Teams account, Microsoft keeps their voice and face profiles. Their voice and face profile is removed right away if they unenroll from the feature. Their voice and face profile is removed within 90 days if their Teams account is deleted. IT Admins can also remove the voice and face profiles of users manually, either one by one or in bulk, via Teams Admin Center or PowerShell. This action is permanent and cannot be reversed.

If users enroll their voice or face profile, they can always choose to unenroll it later, even if the current assigned IT-Admin policy doesn't let them enroll.

A voice and face profile that is not used for one year will be removed automatically, and the user will have to enroll again to use the features.

When a user also uses Voice Isolation, a local copy of the voice signature is stored encrypted in the users profile on the computer. This signature expires after 30 days and will be replaced with a new download.

If users leave the company, the customer data will be deleted accordingly following the Customer data policy.

## Admin settings

Admins can enable or disable voice and face enrollment for their organization or specific users, depending on their audio and user experience needs. By default, voice and face enrollment is enabled for all users in the organization, but IT Admins can change this setting via Teams Admin Center or PowerShell.

To enable or disable voice and face enrollment for the entire organization, IT Admins can go to **Teams Admin Center > Meetings > Meeting policies > Global (Org-wide default) > Voice and face enrollment**, and toggle the switch on or off. Alternatively, they can use the following PowerShell cmdlet:

``` Powershell
Set-CsTeamsMeetingPolicy -Identity Global -AllowVoiceAndFaceEnrollment $true or $false
```

To enable or disable voice and face enrollment for specific users, IT Admins can either assign a custom meeting policy to the users or use the following PowerShell cmdlet:

``` Powershell
Grant-CsTeamsMeetingPolicy -Identity  -PolicyName  -AllowVoiceAndFaceEnrollment $true or $false
```

Admins have the option to manage how voice and face profiles are used to turn off Voice Isolation for users to enhance noise and voice background reduction admins can switch off voice isolation with PowerShell in the meeting policy.

    -VoiceIsolation

Determines whether you provide support for your users to enable voice isolation in Teams meeting calls.

Possible values are: Enabled (default) \| Disabled

To prevent recognition of users in meeting rooms, admins can turn off (default) face and voice identification on the Microsoft Teams room account in the meeting policy.

    roomPeopleNameUserOverride = On | Off (default)
    roomAttributeUserOverride = Attribute | Off (default)

## Data export

Admins (including TenantAdministrator, TeamsServiceAdministrator, and GlobalReader) can export the voice and face profiles of users for backup or migration purposes, either individually or in bulk, using Teams Admin Center or PowerShell. The exported profiles are in the form of ZIP files that contain the voice samples and face images of the users, as well as a metadata file that contains the user's identity and profile ID.

To export the voice and face profiles of users using the Teams Admin Center, admins can go to **Users > select the users > Voice and face enrollment > Export profiles**. Alternatively, they can use the following PowerShell cmdlet:

``` Powershell
Export-CsTeamsVoiceAndFaceProfile -Identity  -Path 
```
## Frequently asked questions

**Question:** With regards to the user's voice enrollments, where do you store the data?  
**Answer:** Voice data is stored in the O365 trusted compliance store.

**Question:** Can both users and admins control the data being saved?  
**Answer:** Yes, both users and admins have control over the data being saved. Users will be able to unenroll their voice. If users need to access their data, they would need to contact their IT admin. Users have full control of when to remove the data, and when a user selects un-enroll from the Teams client, the data will be deleted immediately.

**Question:** For how long do you keep the data?  
**Answer:** The retention policy is 1 year. User's data will be deleted if not used for 1 year.

**Question:** How is GDPR compliance ensured?  
**Answer:** We will take care of the GDPR compliance, based on tenant regions mapping.

**Question:** How does data stored and processed for crossed tenants?  
**Answer:** We don't support cross-tenant, we only retrieve data for in-tenant only.

**Question:** Can users of different regions join meetings from different countries? How do we treat their data?  
**Answer:** Yes, we will span across the request across different coutries and regions.