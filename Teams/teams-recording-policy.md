---
title: Introduction to Teams Policy-based Recording for Calling & Meetings
author: cabailey
ms.author: cabailey
manager: laurawi
ms.date: 05/11/2020
audience: Admin
ms.topic: conceptual
ms.service: msteams
ms.reviewer: abybee
ms.localizationpriority: medium
search.appverid: MET150
description: Learn about Teams Policy-based Recording for Calling & Meetings
f1.keywords:
- CSH
ms.custom: 
 - Adopt
 - seo-marvel-mar2020
ms.collection: 
- Teams_ITAdmin_Adopt
- M365-collaboration
- tier3
appliesto: 
- Microsoft Teams
---

# Introduction to Teams policy-based recording for callings & meetings

Policy-based recording enables organizations that adopt Microsoft Teams for calling
and meetings to stipulate, using an administrative policy, when calls and
online meetings should be automatically recorded and captured for
subsequent processing and retention as required by relevant corporate or
regulatory policy.

Teams has been enhanced to support integration of
third-party recording solutions, including the platform
functionality, user experiences, and administrative interfaces needed to
provide an end-to-end solution for configuring, managing, recording,
storing, and analyzing Teams communications. Enhancements include communications platform APIs and events for recording, which provides:

- Seamless, high-quality media capture across devices and all
    supported endpoints for audio, video, screen share, and chat.

- Support for interaction capture between Teams users and supported
    calling endpoints (Teams, Teams Mobile, Skype for Business, PSTN)

- New administrative policies for compliance recording, including
    integration with existing Teams administrative calling and
    meeting tools and policies

Compliance Recording can be enabled on Microsoft 365 A3/A5/E3/E5/Business Premium and Office 365 A3/A5/E3/E5 users. 

The compliance recording solution integration capabilities were also
reviewed at Ignite 2019 in the [Compliance
Recording and Microsoft Teams
session](https://myignite.microsoft.com/archives/IG19-VCE40).

## Teams interaction recording overview

Interaction recording use cases can effectively be separated into four
primary categories of recording functionality – Convenience, Functional,
Organizational, and Lawful Intercept, as shown in the image:

> [!div class="mx-imgBorder"]
> ![Screenshot showing the interaction recording what and why.](media/recording-taxonomy.png "The image shows the recording categories.")

Each of the categories entails different requirements for how recordings
are initiated, what is recorded, where recordings are stored, who is
notified, who controls access, and how retention is handled.

| Type                   | Convenience (Regular Teams Recording) | Org - Regulated (Compliance Recording) |
| ---------------------- | ------------------ | --------------- |
| Initiator              | User               | Admin (system)  |
| Target                 | Per-call / meeting | Per-user        |
| Storage owner          | User               | Compliance      |
| Notification required? | Yes                | Yes             |
| Access Owner           | User               | Compliance      |
| Retention Policy?      | Optional           | Yes             |

Teams provides various capabilities for
[convenient](./cloud-recording.md)
and functional recording of meetings and live events. Organizational
recording means enabling organizations that adopt Teams for calling and
meetings to stipulate, by way of an administrative policy, when calls and online
meetings should be automatically recorded and captured for subsequent
processing and retention as required by relevant corporate or regulatory
policy. Users under this policy will be aware that their digital
interactions with Teams are being recorded but will not be able to
disable the recording and will not have access to the recording once the
interaction is complete. The recording becomes part of the
organizational archive available to compliance and legal personnel for
eDiscovery, legal hold, and other corporate retention uses.

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
<li><p><strong>Metadata</strong> - Participants, time, direction, dialed number, origin number, Custom business data</p></li>
<li><p><strong>Content</strong> – Transcription, sentiment, phonetics, related interactions</p></li>
</ul></li>
<li><p>Analyze and interact with collected communications, including the ability to monitor interactions as they are being collected.</p></li>
<li><p>Ensure security of collected communications and prevent tampering at all stages.</p></li>
</ul></td>
</tr>
</tbody>
</table>

## Solution architecture overview

Compliance recording solutions are integrated with Teams as
shown in the following diagram:

> [!div class="mx-imgBorder"]
> ![Screenshot showing the team custom app setting.](media/hp-compliance-recording-for-teams-calling-and-meetings.jpg "The images shows the flow when a Teams meeting or call is sent and received.")

> [!NOTE]
> This solution is designed specifically to enable policy-based compliance recording with Teams. Any other use of this solution will not be supported.

## Recorder

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

The exact implementation of the recorder service will vary by partner
but must be designed to support multiple recorders in order to achieve
high availability and geographical distribution of deployment to reduce
latency from Teams to the recorder. In addition, it is expected that
Recorders themselves be designed with resiliency and redundancy in mind.

Partners must confirm the minimum required release version of the
Microsoft Graph communications APIs and SDKs with Microsoft before
submitting their solution for certification to ensure that all
requirements of compliance recording integration are supported.

Two specific requirements that are fundamental for compliance recording
scenario are:

- Recorder bot must be deployed in Azure

- Recorder bot must run on a Windows VM in Azure

The Azure and Windows VM requirements only apply to the Teams Bot
component, which means that a partner may implement the rest of the
platform of their choice provided they can meet the relevant performance
and functional requirements for compliance recording.

## Compliance recording policy assignment and provisioning

IT Administrators can determine which users are to be recorded and which
recorder will be used for each user, by creating and assigning
compliance recording policies. Recorders are automatically invited to
participate in conversations based on the configuration of these
policies when a communication interaction takes place. Compliance
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

   See [Set-CsTeamsComplianceRecordingPolicy](/powershell/module/skype/set-csteamscompliancerecordingpolicy).

3. Assign the Compliance Recording policy to a user.

   ```powershell
   PS C:\> Grant-CsTeamsComplianceRecordingPolicy -Identity testuser@contoso.onmicrosoft.com -PolicyName TestComplianceRecordingPolicy
   ```

   See [Grant-CsTeamsComplianceRecordingPolicy](/powershell/module/skype/grant-csteamscompliancerecordingpolicy).

   ```powershell
   PS C:\> Get-CsOnlineUser testuser@contoso.onmicrosoft.com | select SipAddress, TenantId, TeamsComplianceRecordingPolicy | fl

   UserPrincipalName              : testuser@contoso.onmicrosoft.com
   TenantId                       : 5b943d7c-5e14-474b-8237-5022eb8e0dc9
   TeamsComplianceRecordingPolicy : TestComplianceRecordingPolicy
   ```

## User experiences

Support for notifications is enabled using the Teams client experiences. The experiences can be either visual or audio.

**Teams clients - visual notice**
- Desktop/web
- Mobile (iOS/Android)
- Teams phones
- Teams rooms

**Other endpoints - audio notice**
- SIP phones
- Skype for Business
- Audio conferencing (audio notice in dial-in number's default or user-selected language)
- PSTN callers (audio notice in Teams user's default language)

> [!NOTE]
> Compliance Recording is not supported with Conference mode call queues. Please use Transfer mode call queues.
> Compliance Recording will not work if users have experienced an Internet outage, and are making and receiving PSTN calls using an SBA.

## Compliance recording for Teams certification programs

In addition to publishing publicly available APIs allowing partners to develop and integrate CCaaS solutions with Teams, we have developed the compliance recording for Microsoft Teams certification program to provide customers with the assurance that each participating partner's solution has been tested and verified to provide the quality, compatibility, and reliability they expect from Microsoft solutions.  

The following partners have certified their solution for Microsoft Teams.<br/><br/>

|Partner|Solution website |
|:--|:--|
|ASC Technologies |[https://www.asctechnologies.com/english/ASC_Recording_Insights_Compliance_Recording_for_Microsoft_Teams.html](https://www.asctechnologies.com/english/ASC_Recording_Insights_Compliance_Recording_for_Microsoft_Teams.html) |
|AudioCodes |[https://online.audiocodes.com/smarttap-360-live-for-microsoft-teams](https://online.audiocodes.com/smarttap-360-live-for-microsoft-teams) |
|CallCabinet |[https://www.callcabinet.com/compliance-microsoft-teams-call-recording](https://www.callcabinet.com/compliance-microsoft-teams-call-recording ) |
|Dubber |[https://www.dubber.net/call-recording/](https://www.dubber.net/call-recording/) |
|Insightful Technology |[https://insightfultechnology.com/teams/](https://insightfultechnology.com/teams/) |
|NICE Engage |[https://www.nice.com/products/workforce-engagement/call-recording/air-and-engage](https://www.nice.com/products/workforce-engagement/call-recording/air-and-engage) |
|NICE NTR |[https://www.niceactimize.com/compliance/ms-teams-recording.html](https://www.niceactimize.com/compliance/ms-teams-recording.html) |
|Numonix |[https://numonix.cloud](https://numonix.cloud)    |
|Oak Innovation |[https://www.oakinnovate.com/clarify](https://www.oakinnovate.com/clarify) |
|Red Box |[https://www.redboxvoice.com/compliance-recording-for-microsoft-teams](https://www.redboxvoice.com/red-box-partners/microsoft-integration/compliance-recording-for-microsoft-teams)  |
|Theta Lake |[https://thetalake.com/integrations/microsoft/](https://thetalake.com/integrations/microsoft/) |
|Verint |[https://www.verba.com/solutions/microsoft-teams-recording](https://www.verba.com/solutions/microsoft-teams-recording) |
|Oak Innovation |[https://www.oakinnovate.com/clarify](https://www.oakinnovate.com/clarify) |

<br/>
The following partners are in the process of certifying their solution for Microsoft Teams.<br/><br/>

|Partner|Solution website |
|:--|:--|
|GuardRec |[https://www.guardrec.com/en/teams-compliance-recording/](https://www.guardrec.com/en/teams-compliance-recording/) |
|Landis Technologies |[https://landistechnologies.com/](https://landistechnologies.com/) |
|Luware |[https://luware.com/en/solution/microsoft-teams-recording/](https://luware.com/en/solution/microsoft-teams-recording/) |
|Mida Solutions |[https://www.midasolutions.com/recorder-for-teams/](https://www.midasolutions.com/recorder-for-teams/) |
|Redwood Technologies |[https://www.contentguru.com/en-gb/solutions/needs/compliance-recording-MS-Teams/](https://www.contentguru.com/en-gb/solutions/needs/compliance-recording-MS-Teams/) |


This list will be updated as more partners join and meet the certification criteria.


## Next steps

If you are a vendor seeking to join the certification program, fill out [this form](https://aka.ms/CallingPlatformIntake) as the next step. If you need to provide additional context and details, send a mail to [Teamscategorypartner@microsoft.com](mailto:Teamscategorypartner@microsoft.com).
