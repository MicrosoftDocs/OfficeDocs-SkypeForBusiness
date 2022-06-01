---
title: Data and Privacy Information
author: donnah007 
ms.author: v-donnahill
manager: serdars
ms.date: 06/01/2022
ms.reviewer:  
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Data and Privacy Information
f1keywords: Microsoft Teams Rooms Managed Service Data and Privacy Information
---


# Approach

Customers using Microsoft Teams Rooms Managed Services entrust Microsoft with their most valuable asset — data. They trust that its privacy will be protected and that it will be used only in a way that is consistent with their expectations.

The technology follows privacy processes to make sure that it adheres to the customer promises in collecting and using data effectively running the service.
## Data collection and privacy

 Microsoft Teams Rooms Managed Services monitors devices, collects customer content data, and remotely accesses and manages the devices as an administrator. Data that is collected is limited to information required to monitor the health, root cause, and mitigating issues identified in the enrolled rooms. Certain data collected is specific to a room account, not to individual users.

> [!Note]
> Incidental references to an individual user may be present in the activity log during use of the device.

## Who can access data

Managed Services takes strong measures to help protect customer data from inappropriate access or use by unauthorized persons. These measures include restricting access by Microsoft personnel and subcontractors.

## Zero Standing Access data storage

Managed Services mitigates risks associated with accounts with privileged access from malicious actors--both inside and outside an organization--through the principle of Zero Standing Access. This principle enables Managed Services to operate without any privileges available to any user by default. Combined with the principles of Just-In-Time and Just-Enough-Access, it provides a robust framework to be secure and compliant by default. Diagnostic data is available to the Microsoft service operations team via an internal portal.

## Data handling

Microsoft is governed by strict standards for data transmission, storage, use, and retention. Microsoft has data handling standard policies that regulate how data should be handled based on data classification.

<!--Microsoft extends General Data Protection Regulation (GDPR) rights to customers worldwide.

## Data classification

The data classification can be used to adhere to security, compliance, and privacy requirements and processes for collecting, storing, and using user personal information.


|Classification|Description|Example|
| :- | :- | :- |
|Customer content|Content directly provided/created by admins and users. |Customer-generated BLOB or structured storage data</p><p>Customer-owned/provided secrets (passwords, certificates, encryption keys, storage keys) |
|End-user identifiable information (EUII)|Data that identifies or could be used to identify the user of a Microsoft service. EUII does not contain customer content. |User name or display name (DOMAIN\UserName)</p><p>User principal name (name@company.com)</p><p>User-specific IP address |
|Account Data|Customer billing information and payment instrument information, including administrator contact information, such as tenant administrator’s name, address, or phone number. |Tenant administrator contact information (for example, tenant administrator’s name, address, e-mail address, phone number)<p><p>Customer’s provisioning information |
|End User Pseudonymous Identifiers (EUPI) |An identifier created by Microsoft tied to the user of a Microsoft service. When EUPI is combined with other information, such as a mapping table, it identifies the end user. EUPI does not contain information uploaded or created by the customer</p><p>(Customer content or EUII)  | User GUIDs, PUIDs, or SIDsSession IDs |
|Organization Identifiable Information (OII)|Data that can be used to identify a tenant, generally config or usage data. This data is not linkable to a user and does not contain customer content. |Tenant ID (non-GUID)</p><p>Domain name in e-mail address (xxx@contoso.com) or other tenant-specific domain information |
|System metadata|Data generated while running the service or program that is not linkable to a user or tenant. |Event logs</p><p>Usage data</p><p>Configuration data |-->

## Technology description

Managed Services sends data to Microsoft for the purposes of monitoring, diagnosing, and mitigating any issues in the deployment. Examples include

1. Ensuring the device is up to date (including the app, OS, drivers, F/W)
1. Ensuring the device is ready to use (signed in, all peripherals reporting healthy state, etc.)
1. Ensuring the environment is ready (accounts provisioned, network speeds are fast enough, etc.)
1. Determining if there may be hardware issues or installation issues (such as loose cabling)
1. Heuristics to determine issues (excessive reboots, etc.)

Managed Services manages the device with the following actions:

1. Update software
1. Mitigate issues through reboots, resetting USB connections & states
1. Collect specific logs to help diagnose issues

Managed Services doesn't monitor or record audio, video, media, or meeting content from solution kits.

### Service-collected data categories
 
|Category|Details|Reason for Query|
| :- | :- | :- |
|Ongoing data collection and management|IP Address, identity of the room account (Exchange, Skype for Business and/or Teams), Location coordinates, emails and communication within portal with Microsoft or software|Identify and connect to the system under management; identify, diagnose, and mitigate failures; track usage, analytics, and insights; query and repair connectivity status|
|Ad hoc data collection and management|Event log information, user activity/Identity from the room user logged in log file along with diagnostics information\*, Windows system queries (Examples: List of USB devices, power state, etc.)|Identify, diagnose, and mitigate failures and for usage, analytics, and insights|
<!--|Trial enrollment and Setup |Windows System Queries</p><p>Examples: List of USB devices, power state, etc.|Required for enrollment, onboarding, order and delivery,and setup for the Trial.|-->

Certain sensitive data in the Device Activity log is redacted out locally (not collected by Managed Services):

1. Meeting subject and body
1. Contact card information for meeting attendees (such as title, phone number, etc.)
1. In Meeting IM message content

> [!NOTE]
> As Microsoft evolves Managed Services, the specific data is subject to change.

<!--### Agent Data Classification

The following table is a detailed description of all data MTRP agent collects during ongoing monitoring.

|Collected Data Description|Classification|
| :- | :- |
|Identity of a shared device|OII|
|Customer ID|OII|
|MMR agent directory location|System metadata|
|MTR app logs directory location|System metadata|
|Device serial number|System metadata|
|Device bios information|System metadata|
|version of the MMR agent|System metadata|
| :- | :- |
|Version of the MTR app|System metadata|
|Version of the teams app|System metadata|
|time of nightly maintenance job for MTR app|System metadata|
|MMR agent update url|System metadata|
|MMR agent ring|System metadata|
|windows os version|System metadata|
|currently logged in user|System metadata|
|MMR agent session guid|System metadata|
|domain name|System metadata|
|time since last os reboot|System metadata|
|time since last MMR agent start|System metadata|
|MTR device make and model|System metadata|
|device in use status|System metadata|
|device onboarding type|System metadata|
|number of connected monitors|System metadata|
|MTR speaker details|System metadata|
|MTR microphone details|System metadata|
|MTR default speaker details|System metadata|
|MTR app auto screen sharing setting|System metadata|
|MTR app bluetooth advertisement setting|System metadata|
|date of the last time the password was changed|System metadata|
|MTR password rotation setting|System metadata|
|MTR app teams/skype for business setting|System metadata|
|MTR app update ring|System metadata|
|MTR app content camera setting|System metadata|
|MTR app meetings names setting|System metadata|
|MTR app front of room displays setting|System metadata|
|MTR app guid|System metadata|
|Proxy address and port|System metadata|
|Health of the MTR device|System metadata|
|Details of MTR room account|oii|
|IPv4 address and ipv6 address|oii|
|Longitude and latitude|oii|
|MTR device hostname|oii|
|MTR device time zone|System metadata|
|status of the MTR app|System metadata|
|Crestron service details|System metadata|
|logitech firmware version and logitech sync version|System metadata|
|Total CPU percentage in use|System metadata|
|Total RAM in use|System metadata|
|CPU being used by MTR skype or teams apps|System metadata|
|MTR device temperature|System metadata|
|status of internal disk drives|System metadata|
|Details of any MTR app crashes|System metadata|
|Details of any detected memory leaks caused by apps on the device|System metadata|

|Details of any device blue screen errors that have taken place over the last 24 hours|System metadata|
| :- | :- |
 |details of any errors that the MTR app has detected during meetings on the device |System metadata|
|Installed software details|System metadata|
|Installed / pending / missing hot-fixes details|System metadata|
|recognized hardware details|System metadata|
|Details of all drivers on the device|System metadata|
|Details of any MMR device remediations|System metadata|
|Details of room usage during the last 24 hours, meetings time and counts|System metadata|
|Details of automatic windows store updates|System metadata|
|Details of windows os updates|System metadata|
|MMR agent crush details|System metadata|
|MMR agent connecting error details|System metadata|
|Details on if TPM security is enabled|System metadata|
|Details of the MTR device connection status|System metadata|

**Data MTRP agent collects for incident diagnostic and remediation**
|Collected Data Description|Classification|
| :- | :- |
|Event logs: System, Application, Skype Room System, Microsoft- Windows-AppXDeploymentServer%4Operational, Microsoft-Windows- PowerShell%4Operational, Microsoft-Windows- AppXDeployment%4Operational,Microsoft-Windows- AppXDeploymentServer%4Operational, Microsoft-Windows- TWinUI%4Operational, Microsoft Managed Rooms, Microsoft-Windows-TaskScheduler%4Operational, Security|System metadata|
|Redacted MTR app logs\*|System metadata|
|Microsoft teams logs|System metadata|
|MMR agent sqlLitedb|System metadata|
|Details of device power state information|System metadata|
|Device group policy information|System metadata|
|Audit trace of all MMR agent actions|System metadata|
\* Sensitive PII in the device activity log is redacted out locally.-->

### Enrollment


Managed Services is registered with the online portal for automated monitoring and support services, including diagnostics and reporting. Enrollment is done through network communications encrypted using the device’s Trusted Platform Module (TPM) based public key.

### Unenrollment

The device can be unenrolled by uninstalling Managed Services. Microsoft also removes the device from backend monitoring during decommissioning and can delete collected data on request.

<!--### Data flow

Managed Services adds a data flow from the agent to MTR Managed Services.

![data flow from agent to MTR Managed Services](../media/data-and-privacy-info-005.png)

Enabling the integration of Microsoft Defender for Endpoint will introduce an additional data flow from MDE Agent to the Microsoft Defender infrastructure.

![additional data flow from MDE Agent to Defender](../media/data-and-privacy-info-006.png)-->

## Compliance

All engineers who work on the product are required to undergo security and privacy awareness training. Microsoft also ensures that all personnel certify acceptance of responsibilities for privacy requirements.

Managed Services provides regional data residency support through the data centers in Europe (EU), Asia Pacific (APAC), and the United States (US). The service customers will have data related to organization stored in the data center of their chosen region.

## More resources

Microsoft Teams Rooms Security:/microsoftteams/rooms/security
Microsoft Privacy Statement: https://aka.ms/privacy
Data management at Microsoft: https://www.microsoft.com/trust-center/privacy/data-management
Managed Services service description: [Microsoft Teams Room managed service](microsoft-teams-rooms-premium.md)
