---
title: Data and Privacy Information
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.date: 04/04/2024
ms.reviewer: srpall
ms.topic: article
audience: Admin
ms.service: msteams
ms.subservice: itpro-rooms
appliesto: 
  - Microsoft Teams
ms.collection: 
  - M365-collaboration
  - teams-rooms-devices
  - Tier1
ms.localizationpriority: medium
search.appverid: MET150
description: Data and Privacy Information
f1keywords: Microsoft Teams Rooms Managed Service Data and Privacy Information
---

# Approach

Customers using Microsoft Teams Rooms Pro Management entrust Microsoft with their most valuable asset—data. They trust that its privacy will be protected and that it will be used only in a way that is consistent with their expectations.

The technology follows privacy processes to make sure that it adheres to the customer promises in collecting and using data effectively running the service.
## Data collection and privacy

 Microsoft Teams Rooms Pro management monitors devices, collects customer content data, and remotely accesses and manages the devices as an administrator. Data that is collected is limited to information required to monitor the health, root cause, and mitigating issues identified in the enrolled rooms. Certain data collected is specific to a room account, not to individual users.

> [!Note]
> Incidental references to an individual user may be present in the activity log during use of the device.

## Who can access data

The Teams Rooms Pro management service takes strong measures to help protect customer data from inappropriate access or use by unauthorized persons. These measures include restricting access by Microsoft personnel and subcontractors.

## Zero Standing Access data storage

The Teams Rooms Pro management service mitigates risks associated with accounts with privileged access from malicious actors—both inside and outside an organization—through the principle of Zero Standing Access. This principle enables Teams Rooms Pro management to operate without any privileges available to any user by default. Combined with the principles of Just-In-Time and Just-Enough-Access, it provides a robust framework to be secure and compliant by default. Diagnostic data is available to the Microsoft service operations team via an internal portal.

## Data handling

Microsoft is governed by strict standards for data transmission, storage, use, and retention. Microsoft has data handling standard policies that regulate how data should be handled based on data classification.

## Technology description

Teams Rooms Pro management sends data to Microsoft for the purposes of monitoring, diagnosing, and mitigating any issues in the deployment. Examples include:

- Ensuring the device is up to date (including the app, OS, drivers, F/W)
- Ensuring the device is ready to use (signed in, all peripherals reporting healthy state, etc.)
- Ensuring the environment is ready (accounts provisioned, network speeds are fast enough, etc.)
- Determining if there may be hardware issues or installation issues (such as loose cabling)
- Heuristics to determine issues (excessive reboots, etc.)

Teams Rooms Pro management manages the device with the following actions:

- Update software
- Mitigate issues through reboots, resetting USB connections & states
- Collect specific logs to help diagnose issues

Teams Rooms Pro management doesn't monitor or record audio, video, media, or meeting content from solution kits.

### Service-collected data categories
 
|Category|Details|Reason for Query|
| :- | :- | :- |
|Ongoing data collection and management|IP Address, identity of the room account (Exchange, Skype for Business and/or Teams), Location coordinates, emails, and communication within portal with Microsoft or software|Identify and connect to the system under management; identify, diagnose, and mitigate failures; track usage, analytics, and insights; query and repair connectivity status|
|Ad hoc data collection and management|Event log information, user activity/Identity from the room user logged in log file along with diagnostics information, Windows system queries (Examples: List of USB devices, power state, etc.)|Identify, diagnose, and mitigate failures and for usage, analytics, and insights.|

Certain sensitive data in the Device Activity log is redacted out locally (not collected by Teams Rooms Pro management):

- Meeting subject and body
- Contact card information for meeting attendees (such as title, phone number, etc.)
- In Meeting IM message content

> [!NOTE]
> As Microsoft evolves the Teams Rooms Pro management service, the specific data is subject to change.
### Enrollment

Teams Rooms Pro management is registered with the online portal for automated monitoring and support services, including diagnostics and reporting. Enrollment is done through network communications encrypted using the device’s Trusted Platform Module (TPM) based public key.

### Unenrollment

The device can be unenrolled by uninstalling the Teams Rooms Pro management service. Microsoft also removes the device from backend monitoring during decommissioning and can delete collected data on request.
## Compliance

All engineers who work on the product are required to undergo security and privacy awareness training. Microsoft also ensures that all personnel certify acceptance of responsibilities for privacy requirements.

Teams Rooms Pro management provides regional data residency support through the data centers in Europe (EU), Asia Pacific (APAC), and the United States (US). The service customers will have data related to organization stored in the data center of their chosen region.

## More resources

[Microsoft Teams Rooms security](security.md)

[Microsoft Privacy Statement](https://aka.ms/privacy)

[Data management at Microsoft](https://www.microsoft.com/trust-center/privacy/data-management)

[Microsoft Teams Rooms Pro management](rooms-pro-management.md)
