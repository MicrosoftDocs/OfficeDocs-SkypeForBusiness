---
title: Data and Privacy Information
author: donnah007 
ms.author: v-donnahill
manager: serdars
ms.date: 04/07/2022
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

Customers using managed services entrust Microsoft with their most valuable asset — data. They trust that its privacy will be protected and that it will be used only in a way that is consistent with their expectations.

The technology follows privacy processes to make sure that it adheres to the customer promises in collecting and using dataeffectively running the service.

## Data Collection

Data collected by the Technology is limited to information required to monitor the health, root cause, and mitigate issues identified in the enrolled rooms.

The Technology will monitor devices, collect telemetry data, and allow Microsoft to remotely access and manage the devices as an administrator.

Telemetry data collected is specific to a Room account, not an individual user. Incidental references to an individual user may be present in the activity log during use of the device.

### Who can access your data

The Technology service take strong measures to help protect customer data from inappropriate access or use by unauthorized persons. This includes restricting access by Microsoft personnel and subcontractors.

### Zero Standing Access Data Storage

The Technology mitigates risks associated with accounts with privileged access – from malicious actors both inside and outside an organization – through the principle of Zero Standing Access. This enables the service to operate without any privileges available to any user by default. Combined with the principles of Just-In-Time and Just-Enough-Access, it provides a robust framework to be secure and compliant by default. Diagnostic data is available to our service operations team via an internal portal.

## Data Handling

Microsoft is governed by strict standards for data transmission, storage, use and retention. Microsoft has Data Handling Standard policies that how data should be handled based on data classification.

Microsoft extends General Data Protection Regulation (GDPR) data protection rights to all customers worldwide, not just in Europe.

## Data Classification

The data classification can be used to adhere to security, compliance, and privacy requirements and processes for collecting, storing, and using user personal information.


|Classification|Description|Example|
| :- | :- | :- |
|Customer Content|Content directly provided/created by admins and users.|<p>- Customer generated BLOB or structured storage data</p><p>- Customer-owned/provided secrets (passwords, certificates, encryption keys, storage keys)</p>|
|End User Identifiable Information (EUII)|Data that identifies or could be used to identify the user of a Microsoft service. EUII does not contain Customer content.|<p>- User name or display name (DOMAIN\UserName)</p><p>- User principal name (name@company.com)</p><p>- User-specific IP address</p>|
|Account Data|<p>Customer billing information and payment instrument information, including administrator contact information, such as tenant</p><p>administrator’s name, address, or</p><p>phone number.</p>|<p>- Tenant administrator contact information (for example,</p><p>tenant administrator’s name, address, e-mail address, phone number)</p><p>- Customer’s provisioning</p><p>information</p>|
|End User Pseudonymous Identifiers (EUPI)|<p>An identifier created by Microsoft tied to the user of a Microsoft service. When EUPI is combined with other information, such as a mapping table, it identifies the end user. EUPI does not contain information uploaded or created by the customer</p><p>(Customer content or EUII)</p>|<p>- User GUIDs, PUIDs, or SIDs</p><p>- Session IDs</p>|
|Organization Identifiable Information (OII)|Data that can be used to identify a tenant, generally config or usage data. This data is not linkable to a user and does not contain Customer content.|<p>- Tenant ID (non-GUID)</p><p>- Domain name in e-mail address (xxx@contoso.com) or other tenant-specific domain</p><p>information</p>|
|System Metadata|Data generated while running the service or program that is not linkable to a user or tenant.|<p>- Event logs</p><p>- Usage data</p><p>- Configuration data</p>|

Technology Description

The Technology will send data to Microsoft for the purposes of monitoring, diagnosing, and mitigating any issues in the deployment. Examples include

1. Ensuring the Device is up to date (including the App, OS, Drivers, F/W)
1. Ensuring the Device is ready to use (signed in, all peripherals reporting healthy state, etc.)
1. Ensuring the Environment is ready (accounts provisioned, Network speeds are fast enough, etc.)
1. Determining if there may be hardware issues or installation issues (such as loose cabling)
1. Heuristics to determine issues (excessive reboots, etc.) 

The Technology will manage the device with actions such as

1. Update software
1. Mitigate issues through reboots, resetting USB connections & states
1. Collect specific logs to help diagnose issues

The Technology does not monitor or record audio, video, media, or meeting content from Solution Kits. 

### Service-collected data categories
 
|Category|Details|Reason for Query|
| :- | :- | :- |
|Ongoing Data Collection & Management|IP Address, Identity of the Room Account (Exchange, Skype for Business and/or Teams), Location Coordinates, Emails and communication within Portal with Microsoft or software|Identify and Connect to the System Under Management; Identify, Diagnose, and Mitigate failures; Track Usage, Analytics, and Insights; Query & Repair Connectivity Status|
|Ad hoc Data Collection & Management|<p>Event log information, User Activity/Identity from the Room user logged in log file along with Diagnostics information\*, Windows System Queries (Examples: List of USB devices,</p><p>power state, etc.)</p>|Identify, Diagnose, and Mitigate failures and for Usage, Analytics, and Insights|
|<p>Trial Enrollment and</p><p>Setup</p>|<p>Windows System Queries</p><p>Examples: List of USB devices, power state, etc.</p>|<p>Required for enrollment, onboarding, order and delivery,</p><p>and setup for the Trial.</p>|

\* Sensitive PII in the Device Activity log is redacted out locally (not collected by the Technology):

1. Meeting Subject & Body
1. Contact Card information for Meeting Attendees (such as Title, Phone Number, etc.)
1. In Meeting IM Message Content

>> [!NOTE]
>As Microsoft evolves the Technology, the specific data is subject to change. 

### Agent Data Classification

**Detailed description of all data MTRP agent collects during ongoing monitoring**
|Collected Data Description|Classification|
| :- | :- |
|Identity of a shared device|OII|
|Customer ID|OII|
|MMR Agent directory location|System Metadata|
|MTR app logs directory location|System Metadata|
|Device Serial Number|System Metadata|
|Device Bios Information|System Metadata|

|Version of the MMR Agent|System Metadata|
| :- | :- |
|Version of the MTR app|System Metadata|
|Version of the Teams app|System Metadata|
|Time of nightly maintenance job for MTR app|System Metadata|
|MMR agent update URL|System Metadata|
|MMR agent ring|System Metadata|
|Windows OS version|System Metadata|
|Currently logged in user|System Metadata|
|MMR Agent session GUID|System Metadata|
|Domain name|System Metadata|
|Time since last OS reboot|System Metadata|
|Time since last MMR agent start|System Metadata|
|MTR device make and model|System Metadata|
|Device in use status|System Metadata|
|Device onboarding type|System Metadata|
|Number of connected monitors|System Metadata|
|MTR speaker details|System Metadata|
|MTR microphone details|System Metadata|
|MTR default speaker details|System Metadata|
|MTR app auto screen sharing setting|System Metadata|
|MTR app Bluetooth advertisement setting|System Metadata|
|Date of the last time the password was changed|System Metadata|
|MTR password rotation setting|System Metadata|
|MTR app Teams/Skype for Business setting|System Metadata|
|MTR app update ring|System Metadata|
|MTR app content camera setting|System Metadata|
|MTR app meetings names setting|System Metadata|
|MTR app front of room displays setting|System Metadata|
|MTR app GUID|System Metadata|
|Proxy address and port|System Metadata|
|Health of the MTR device|System Metadata|
|Details of MTR room account|OII|
|IPV4 Address and IPV6 address|OII|
|Longitude and latitude|OII|
|MTR device hostname|OII|
|MTR device time zone|System Metadata|
|Status of the MTR app|System Metadata|
|Crestron service details|System Metadata|
|Logitech firmware version and Logitech sync version|System Metadata|
|Total CPU percentage in use|System Metadata|
|Total RAM in use|System Metadata|
|CPU being used by MTR Skype or Teams Apps|System Metadata|
|MTR device temperature|System Metadata|
|Status of internal disk drives|System Metadata|
|Details of any MTR app crashes|System Metadata|
|Details of any detected memory leaks caused by apps on the device|System Metadata|

|<p>Details of any device blue screen errors that have taken place over the</p><p>last 24 hours</p>|System Metadata|
| :- | :- |
|<p>Details of any errors that the MTR App has detected during meetings on</p><p>the device</p>|System Metadata|
|Installed software details|System Metadata|
|Installed / pending / missing hot-fixes details|System Metadata|
|Recognized hardware details|System Metadata|
|Details of all drivers on the device|System Metadata|
|Details of any MMR device remediations|System Metadata|
|Details of room usage during the last 24 hours, meetings time and counts|System Metadata|
|Details of automatic Windows store updates|System Metadata|
|Details of Windows OS updates|System Metadata|
|MMR agent crush details|System Metadata|
|MMR agent connecting error details|System Metadata|
|Details on if TPM security is enabled|System Metadata|
|Details of the MTR device connection status|System Metadata|

**Data MTRP agent collects for incident diagnostic and remediation**
|Collected Data Description|Classification|
| :- | :- |
|<p>Event logs: System, Application, Skype Room System, Microsoft- Windows-AppXDeploymentServer%4Operational, Microsoft-Windows- PowerShell%4Operational, Microsoft-Windows- AppXDeployment%4Operational,Microsoft-Windows- AppXDeploymentServer%4Operational, Microsoft-Windows- TWinUI%4Operational, Microsoft Managed Rooms, Microsoft-Windows-</p><p>TaskScheduler%4Operational, Security</p>|System Metadata|
|Redacted MTR app logs\*|System Metadata|
|Microsoft teams logs|System Metadata|
|MMR agent sqlLitedb|System Metadata|
|Details of device power state information|System Metadata|
|Device group policy information|System Metadata|
|Audit trace of all MMR agent actions|System Metadata|
\* Sensitive PII in the Device Activity log is redacted out locally.

### Enrollment


This Technology will be registered with the online portal for automated monitoring and support services, including diagnostics and reporting. Enrollment is done through network communications encrypted using the device’s Trusted Platform Module (TPM) based public key.

### Un-enrollment

The device can be un-enrolled by uninstalling the Technology. Microsoft will also remove the device from backend monitoring during decommissioning and can delete collected data on request.

### Data flow

The technology will add a data flow from the agent to MTR Managed Services.

![data flow from agent to MTR Managed Services](../media/data-and-privacy-info-005.png)

Enabling the integration of Microsoft Defender for Endpoint will introduce an additional data flow from MDE Agent to the Microsoft Defender infrastructure.

![additional data flow from MDE Agent to Defender](../media/data-and-privacy-info-006.png)

## Compliance

All the engineers who work on the product are required to undergo security and privacy awareness training. Microsoft also ensures that all personnel certify acceptance of responsibilities for privacy requirements.

The technology provides regional data residency support through the datacenters in Europe (EU), Asia Pacific (APAC), and the United States (US). This means the service customers will have data related to organization stored in the datacenter of their chosen region.

## Additional resources

Microsoft Teams Rooms Security:/microsoftteams/rooms/security
Microsoft Privacy Statement: https://aka.ms/privacy
Data management at Microsoft: https://www.microsoft.com/trust-center/privacy/data-management
The technology service description: [Microsoft Teams Room managed service](microsoft-teams-rooms-premium.md)
