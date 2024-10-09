---
title: Introduction to Microsoft Teams third party compliance recording
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.date: 06/27/2024
audience: Admin
ms.topic: conceptual
ms.service: msteams
ms.reviewer: ritikag,lisma
ms.localizationpriority: medium
search.appverid: MET150
description: Learn about Teams third party compliance recording for calling, meetings, town halls, webinars, and live events.
f1.keywords:
- CSH
ms.custom: 
 - Adopt
 - seo-marvel-mar2020
ms.collection: 
- Teams_ITAdmin_Adopt
- M365-collaboration
- tier3
- purview-compliance
appliesto: 
- Microsoft Teams
---

# Introduction to Microsoft Teams third party compliance recording

**APPLIES TO:** ✔️Meetings ✔️Webinars ✔️Town halls ✔️ Calls ✔️ Live events

## Overview

Third-party compliance recording allows orgs using Microsoft Teams for calls, meetings, and events to implement an admin policy for automatic recording. For your users to make calls, they must have an assigned Teams Phone license. As an admin, you can also choose when to capture calls, meetings, and events for subsequent processing and retention, in accordance with relevant corporate or regulatory policies.

Teams is enhanced to support the integration of partner recording solutions. These enhancements provide a complete solution for configuring, managing, recording, storing, and analyzing Teams communications. The enhancements include communications platform APIs and events for recording, which provide:

- Seamless, high-quality media capture across devices. Compliance recording captures the same screenshare activity as convenience recording. To learn which screenshare activities are captured, see [Record a meeting in Microsoft Teams](https://support.microsoft.com/office/record-a-meeting-in-microsoft-teams-34dfbe7f-b07d-4a27-b4c6-de62f1348c24).

- Support for interaction capture between Teams users and supported calling, meeting, and endpoints (Teams, Teams Mobile, Skype for Business, PSTN).

Compliance recording can be enabled on Microsoft 365 A3/A5/E3/E5/Business Premium, Office 365 A3/A5/E3/E5 users, Teams Rooms license, or Microsoft Teams Shared Devices license.

> [!NOTE]
> Compliance recording isn't currently supported for E911 emergency calling services.

The compliance recording solution integration capabilities were also
reviewed at Ignite 2019 in the [Compliance
Recording and Microsoft Teams
session](https://myignite.microsoft.com/archives/IG19-VCE40).

### Compliance vs convenience recording

In Microsoft Teams, there are two types of recordings:

- **Convenience recording-** an ad-hoc recording of a call or meeting that a user starts. To learn more about convenience recording, see [Teams meeting recording](meeting-recording.md).
- **Compliance recording-** using an admin policy to automatically record calls and meetings.

The following table details differences between convenience and compliance recording.

| Type                   | Convenience Recording | Compliance Recording |
| ---------------------- | ------------------ | --------------- |
| Initiator              | User               | Admin (system)  |
| Target                 | Per-call / meeting / event | Per-user        |
| Storage owner          | Organizer               | Admin or compliance officer    |
| Participant notification required? | Yes                | Yes             |
| Retention Policy      | Organizer's SharePoint Online policy enforced | Yes |

Users with an assigned compliance recording policy know that their digital
interactions with Teams are being recorded. They also know that they can't
disable the recording and don't have access to the recording once the interaction is complete. The recording becomes part of the organizational archive. This archive is available to compliance and legal personnel for eDiscovery, legal hold, and other corporate retention uses.

## Solution architecture overview

Compliance recording solutions are integrated with Teams as
shown in the following diagram:

:::image type="content" source="media/compliance-recording-diagram-small.png" alt-text="Diagram of the flow for when a Teams meeting or call is sent and received." lightbox="media/compliance-recording-diagram-expand.png":::

> [!NOTE]
> This solution is designed specifically to enable policy-based compliance recording with Teams. Any other use of this solution isn't supported.

## Example user needs

<table>
<thead>
<tr class="header">
<th>Persona</th>
<th>Needs</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Recorded users</td>
<td><ul>
<li><p>Be notified when recording is in progress.</p></li>
<li><p>Be informed when policy and/or recorder error is causing changes in calling behavior.</p></li>
</ul></td>
</tr>
<tr class="even">
<td>Communications admin</td>
<td><ul>
<li><p>Understand why and how to apply / enforce recording policies to Teams users / endpoints.</p></li>
<li><p>Configure and maintain Teams recording policies for the organization.</p></li>
<li><p>Monitor and troubleshoot recording-related issues with Teams calls and meetings.</p></li>
<li><p>Support internal compliance officer with operational analytics on usage, quality, and reliability.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td>Compliance officer</td>
<td><ul>
<li><p>Collect all Teams communications in the manner required to meet compliance obligations in appropriate regional boundaries.</p></li>
<li><p>Search for interactions based on communication-related metadata or interaction content. Common examples include:</p>
<ul>
<li><p><strong>Metadata</strong> - Participants, time, direction, dialed number, origin number, Custom business data.</p></li>
<li><p><strong>Content</strong> – Transcription, sentiment, phonetics, related interactions.</p></li>
</ul></li>
<li><p>Analyze and interact with collected communications, including the ability to monitor interactions as they're being collected.</p></li>
<li><p>Ensure security of collected communications and prevent tampering at all stages.</p></li>
</ul></td>
</tr>
</tbody>
</table>

## Recorders

The core component of the compliance recording solution is the recorder.
Recorders are built as scalable Azure-based services (bots) that
[use Microsoft's communications
platform](/graph/cloud-communications-concept-overview)
and register as applications with Microsoft Graph. The recorder provides
the direct interaction with the Teams calls and meetings
[communications platform
APIs](/graph/api/resources/communications-api-overview)
and provides the endpoint for media ingestion.

A [sample compliance recorder application is
available](https://github.com/microsoftgraph/microsoft-graph-comms-samples/tree/a3943bafd73ce0df780c0e1ac3428e3de13a101f/Samples/BetaSamples/LocalMediaSamples/ComplianceRecordingBot)
that shows how to configure the bot, create the app instance and assign
the compliance policies. The sample also has examples on API usage for
recording specific interactions such as handling
[incoming
call](https://github.com/microsoftgraph/microsoft-graph-comms-samples/blob/a3943bafd73ce0df780c0e1ac3428e3de13a101f/Samples/BetaSamples/LocalMediaSamples/ComplianceRecordingBot/FrontEnd/Http/Controllers/PlatformCallController.cs#L199-L244) routing,
[changing recording
states](https://github.com/microsoftgraph/microsoft-graph-comms-samples/blob/a3943bafd73ce0df780c0e1ac3428e3de13a101f/Samples/BetaSamples/LocalMediaSamples/ComplianceRecordingBot/FrontEnd/Bot/CallHandler.cs#L135-L138),
and [removing the user who is being
recorded](https://github.com/microsoftgraph/microsoft-graph-comms-samples/blob/a3943bafd73ce0df780c0e1ac3428e3de13a101f/Samples/BetaSamples/LocalMediaSamples/ComplianceRecordingBot/FrontEnd/Bot/CallHandler.cs#L121-L126).
Graph documentation on the specific APIs can be found here for
[updateRecordingStatus](/graph/api/call-updaterecordingstatus?tabs=http)
and
[incomingContext](/graph/api/resources/incomingcontext).

The exact implementation of the recorder service varies by partner, but must be designed to support multiple recorders. This requirement ensures high availability and geographical distribution, reducing latency between Teams and the recorder. Recorders should be designed with resiliency and redundancy in mind.

Partners must confirm the minimum required release version of the
Microsoft Graph communications APIs and SDKs with Microsoft before
submitting their solution for certification. This requirement ensures that all
requirements of compliance recording integration are supported.

Requirements that are fundamental for compliance recording
scenario:

- Recorder bot must be deployed in Azure.

- Recorder bot must run on a Windows VM in Azure.

- Recorder bot outbound firewall destination IP address must be open to the Azure public IP range.

- Recorder bot inbound firewall source IP address must be open to the [Teams IP range](/microsoft-365/enterprise/urls-and-ip-address-ranges#microsoft-teams).

The Azure and Windows VM requirements only apply to the Teams Bot
component, which means that a partner might implement the rest of the
platform of their choice provided they can meet the relevant performance
and functional requirements for compliance recording.

## Create and manage your compliance recording policy

Through creating and assigning compliance recording policies, as an admin, you can determine which users are to be recorded and which recorder is used for each user. Recorders are automatically invited to participate in conversations based on the configuration of these policies when a communication interaction takes place.
Compliance
recording policies are managed using [Microsoft
PowerShell](./teams-powershell-overview.md)
and can be applied at the tenant, per-user, and security group level for each
organization. You can find more information on Microsoft Learn for
[Meeting
policies](./meeting-policies-overview.md),
 [calling
policies](./teams-calling-policy.md) and  [group
policies](./assign-policies-users-and-groups.md#assign-a-policy-to-a-group).

1. Create an application instance in your tenant.

   ```powershell
   PS C:\> New-CsOnlineApplicationInstance -UserPrincipalName cr.instance@contoso.onmicrosoft.com -DisplayName ComplianceRecordingBotInstance -ApplicationId fcc88ff5-a42d-49cf-b3d8-f2e1f609d511

   RunspaceId        : 4c13efa6-77bc-42db-b5bf-bdd62cdfc5df
   ObjectId          : 5069aae5-c451-4983-9e57-9455ced220b7
   TenantId          : 5b943d7c-5e14-474b-8237-5022eb8e0dc9
   UserPrincipalName : cr.instance@contoso.onmicrosoft.com
   ApplicationId     : fcc88ff5-a42d-49cf-b3d8-f2e1f609d511
   DisplayName       : ComplianceRecordingBotInstance
   PhoneNumber       :
   ```

   ```powershell
   PS C:\> Sync-CsOnlineApplicationInstance -ObjectId 5069aae5-c451-4983-9e57-9455ced220b7
   ```

2. Create a Compliance Recording policy.

   ```powershell
   PS C:\> New-CsTeamsComplianceRecordingPolicy -Identity TestComplianceRecordingPolicy -Enabled $true -Description "Test policy created by tenant admin"

   Identity                        : Global
   ComplianceRecordingApplications : {}
   Enabled                         : True
   WarnUserOnRemoval               : True
   Description                     : Test policy created by tenant admin
   ```

   ```powershell
   PS C:\> Set-CsTeamsComplianceRecordingPolicy -Identity TestComplianceRecordingPolicy `
   -ComplianceRecordingApplications @(New-CsTeamsComplianceRecordingApplication -Id 5069aae5-c451-4983-9e57-9455ced220b7 -Parent TestComplianceRecordingPolicy)
   ```

   See [Set-CsTeamsComplianceRecordingPolicy](/powershell/module/teams/set-csteamscompliancerecordingpolicy).

3. Assign the Compliance Recording policy to a user.

   ```powershell
   PS C:\> Grant-CsTeamsComplianceRecordingPolicy -Identity testuser@contoso.onmicrosoft.com -PolicyName TestComplianceRecordingPolicy
   ```

   See [Grant-CsTeamsComplianceRecordingPolicy](/powershell/module/teams/grant-csteamscompliancerecordingpolicy).

   ```powershell
   PS C:\> Get-CsOnlineUser testuser@contoso.onmicrosoft.com | select SipAddress, TenantId, TeamsComplianceRecordingPolicy | fl

   UserPrincipalName              : testuser@contoso.onmicrosoft.com
   TenantId                       : 5b943d7c-5e14-474b-8237-5022eb8e0dc9
   TeamsComplianceRecordingPolicy : TestComplianceRecordingPolicy
   ```

## User experiences

### PSTN calls

Inbound call queue (CQ) calls are recorded for users who have an assigned compliance recording (CR) policy. Some routing methods might involve usability concerns with multiple announcements. We recommend appropriately configuring your call queues to align with your organization's intended user experience.

Compliance recording doesn't work if users have an Internet outage, and make or receive PSTN calls using an SBA.

### Notifications

Support for notifications is enabled using the Teams client experiences. The experiences can be either visual or audio.

#### Teams clients - visual notice

- Desktop/web
- Mobile (iOS/Android)
- Teams Phones
- Teams rooms

#### Other endpoints - audio notice

- SIP phones
- Skype for Business
- Audio conferencing (audio notice in dial-in number's default or user-selected language)
- PSTN callers (audio notice in Teams user's default language)

## Compliance recording for Teams certification programs

In addition to publishing publicly available APIs allowing partners to develop and integrate CCaaS solutions with Teams, we developed the compliance recording for Microsoft Teams certification program. This program provides customers with the assurance that each participating partner's solution is tested and verified. Customers can be assured that partners provide the quality, compatibility, and reliability they expect from Microsoft solutions.

The following partners certify their solution for Microsoft Teams.<br/><br/>

|Partner|Solution website |
|:--|:--|
|ASC Technologies |[https://www.asctechnologies.com/english/ASC_Recording_Insights_Compliance_Recording_for_Microsoft_Teams.html](https://www.asctechnologies.com/english/ASC_Recording_Insights_Compliance_Recording_for_Microsoft_Teams.html) |
|AudioCodes |[https://online.audiocodes.com/smarttap-360-live-for-microsoft-teams](https://online.audiocodes.com/smarttap-360-live-for-microsoft-teams) |
|CallCabinet |[https://www.callcabinet.com/compliance-microsoft-teams-call-recording](https://www.callcabinet.com/compliance-microsoft-teams-call-recording ) |
|Dubber |[https://www.dubber.net/call-recording/](https://www.dubber.net/call-recording/) |
|Touch Call Recording (GuardRec Compliance 2022.10.3) |[https://touchcallrecording.com/teams-policy-based-recording-for-callings-and-meetings](https://touchcallrecording.com/teams-policy-based-recording-for-callings-and-meetings) |
|Insightful Technology |[https://insightfultechnology.com/teams/](https://insightfultechnology.com/teams/) |
|Luware |[https://luware.com/en/solution/microsoft-teams-recording/](https://luware.com/en/solution/microsoft-teams-recording/) |
|Mida Solutions |[https://www.midasolutions.com/recorder-for-teams/](https://www.midasolutions.com/recorder-for-teams/) |
|NICE Engage |[https://www.nice.com/products/workforce-engagement/call-recording/air-and-engage](https://www.nice.com/products/workforce-engagement/call-recording/air-and-engage) |
|NICE NTR-X |[https://www.niceactimize.com/compliance/ms-teams-recording.html](https://www.niceactimize.com/compliance/ms-teams-recording.html) |
|Numonix |[https://numonix.cloud](https://numonix.cloud)    |
|Oak Innovation |[https://www.oakinnovate.com/clarify](https://www.oakinnovate.com/clarify) |
|Red Box |[https://www.redboxvoice.com/compliance-recording-for-microsoft-teams](https://www.redboxvoice.com/red-box-partners/microsoft-integration/compliance-recording-for-microsoft-teams)  |
|Theta Lake |[https://thetalake.com/integrations/microsoft/](https://thetalake.com/integrations/microsoft/) |
|Verint |[https://www.verba.com/solutions/microsoft-teams-recording](https://www.verba.com/solutions/microsoft-teams-recording) |

<br/>
The following partners are in the process of certifying their solution for Microsoft Teams.<br/><br/>

|Partner|Solution website |
|:--|:--|
|Cloud World Wide Services |[https://recordia.net/microsoft-teams-call-recording/](https://recordia.net/microsoft-teams-call-recording/) |
|CreaLog |[https://www.crealog.com/en/products-solutions/recording/](https://www.crealog.com/en/products-solutions/recording/) |
|Landis Technologies |[https://landistechnologies.com/](https://landistechnologies.com/) |
|Redwood Technologies |[https://www.contentguru.com/en-us/solutions/needs/compliance-recording-ms-teams/](https://www.contentguru.com/en-us/solutions/needs/compliance-recording-ms-teams/) |

This list gets updated as more partners join and meet the certification criteria.

## Support boundaries

Microsoft only supports compliance recording solutions from the listed certified partners. If there are issues, you must contact your compliance recording partner first. If needed, the partner can bring the issue to Microsoft through internal channels. Microsoft might reject support cases where a non-certified Compliance Recording solution is used, or if investigation shows the issue is one that the partner can address.

## Next steps

If you're a vendor seeking to join the certification program, fill out the calling platform intake as the next step.
> [!div class="nextstepaction"]
> [Calling Platform Intake](https://aka.ms/CallingPlatformIntake)
