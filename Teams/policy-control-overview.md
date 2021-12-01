---
title: Policy control overview for Microsoft Teams
author: MicrosoftHeidi
ms.author: heidip
manager: serdars
ms.topic: reference
ms.service: msteams
audience: admin
ms.reviewer: majaisin
description: An overview of the policy controls for Microsoft Teams.
ms.localizationpriority: high
search.appverid: MET150
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---
# Policy control overview for Microsoft Teams

Microsoft is committed to providing you with the information and controls you need to make choices about how your data is collected and used when you’re using Microsoft Teams, a part of Microsoft 365.

This article is intended to provide you with information about privacy controls for the following areas:

- **Diagnostic data** that is collected and sent to Microsoft about Teams and Office software being used on computers running Windows in your organization.
- **Connected experiences** that use cloud-based functionality to provide enhanced Teams and Office features to you and your users.

As part of these changes, there are new and updated user interface (UI) elements and policy settings

> [!IMPORTANT]
> For further reading, please review [Overview of privacy controls for Microsoft 365 Apps for enterprise](/deployoffice/privacy/overview-privacy-controls).

## Diagnostic data sent from Microsoft 365 Apps for enterprise to Microsoft

Diagnostic data is used to:

- Keep Teams secure and up-to-date.
- Detect, diagnose, and remediate problems.
- Make product improvements.

An example of some of the collected data includes:

- Application language
- User type
- Build version of the OS

## Clients that adhere to diagnostic controls

The following clients adhere to diagnostic controls and will submit data:

- iOS
- Android
- Desktop (only the component that is using the win32 API)

To see a list of required diagnostic data events and their properties, see the following articles:

- [Required mobile diagnostic data for Microsoft Teams](policy-control-diagnostic-data-mobile.md)
- [Required desktop diagnostic data for Microsoft Teams](policy-control-diagnostic-data-desktop.md)

## Diagnostic data sent from the Teams app to Microsoft

This diagnostic data is collected and sent to Microsoft about Teams software being used on computers running Windows in your organization.

There are three levels of diagnostic data for Teams software that you can choose from:

- **Required** The minimum data necessary to help keep Office secure, up-to-date, and performing as expected on the device it’s installed on.
- **Optional** Additional data that helps us make product improvements and provides enhanced information to help us detect, diagnose, and remediate issues.
- **Neither** No diagnostic data about Teams software running on the user’s device is collected and sent to us. This option, however, significantly limits our ability to detect, diagnose, and remediate problems your users may encounter using Teams.

Required diagnostic data could include, for example, information about the version of Teams client installed on the device, or include information that indicates that the Teams application is crashing when trying to join a meeting. Optional diagnostic data could include information about the time it takes to initiate a phone call, which could indicate an issue with connectivity or network performance.

If you choose to send us optional diagnostic data, required diagnostic data is also included.

As an admin for your organization, you’ll be able to use a policy setting to choose which level of diagnostic data is sent to us. Optional diagnostic data will be sent to Microsoft unless you change the setting. Providing optional diagnostic data better enables the Office engineering team at Microsoft to detect, diagnose, and mitigate issues to reduce impacts to your organization. 

To choose which level of diagnostic data is sent to us, use the [Office cloud policy service](/deployoffice/overview-office-cloud-policy-service) and configure the *Configure the level of client software diagnostic data sent by Office to Microsoft* policy setting. This is the same policy setting that is used to configure which level of diagnostic data is sent by other Office apps (such as Word, Excel, and PowerPoint) that come with Microsoft 365 Apps for enterprise.

Your users won’t be able to change the diagnostic data level for their devices if they are signed in to Teams with their organizational credentials, which is sometimes referred to as a work or school account.

This diagnostic data doesn’t include names of users, their email addresses, or other user content, such as Office files shared in Teams, a chat message sent in Teams, or the text of a post published in a Teams channel. Our system creates a unique ID that it associates with your user’s diagnostic data. When we receive diagnostic data showing that the Teams app crashed 100 times, this unique ID lets us determine if it was a single user who crashed 100 times or if it was 100 different users who each crashed once. We don’t use this unique ID to identify a specific user.

To see what diagnostic data is being sent to Microsoft, you can use the Diagnostic Data Viewer, which you can download and install for free from the Microsoft Store. For more information, see [Using the Diagnostic Data Viewer with Office](https://support.microsoft.com/topic/cf761ce9-d805-4c60-a339-4e07f3182855).

## Required service data for connected experiences

Required service data is data that enables us to deliver these cloud-based connected experiences and help make these experiences secure and perform as expected. You can choose to not offer this functionality to your users, in which case this information will not be provided to Microsoft to support the functionality of connected experiences. You can learn more about [required service data](/deployoffice/privacy/required-service-data).

## Essential services for Microsoft Teams

There is also a set of services that are essential to how Microsoft 365 Apps for enterprise functions and cannot be disabled. For example, the licensing service that confirms that you are properly licensed to use Microsoft 365 Apps for enterprise. Required service data about these services is collected and sent to Microsoft, regardless of any other policy settings that you have configured.

For more information, see [Essential services for Office](/deployoffice/privacy/essential-services).
