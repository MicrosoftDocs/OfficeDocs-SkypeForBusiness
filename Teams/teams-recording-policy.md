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
localization_priority: Normal
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
storing, and analyzing Teams communications. This includes communications platform APIs and events for recording, which provides:

- Seamless, high-quality media capture across devices and all
    supported endpoints for audio, video, screen share, and chat.

- Support for interaction capture between Teams users and supported
    calling endpoints (Teams, Teams Mobile, Skype for Business, PSTN)

- New administrative policies for compliance recording, including
    integration with existing Teams administrative calling and
    meeting tools and policies

Compliance Recording can be enabled on Microsoft 365 A3/A5/E3/E5/Business Premium and Office 365 A3/A5/E3/E5 users. 

The compliance recording solution integration capabilities were also
reviewed at Ignite 2019 in the [<span class="underline">Compliance
Recording and Microsoft Teams
session</span>](https://myignite.techcommunity.microsoft.com/sessions/83184?source=sessions).

## Teams interaction recording overview

Interaction recording use cases can effectively be separated into four
primary categories of recording functionality – Convenience, Functional,
Organizational, and Lawful Intercept, as shown in the image:

![Screenshot showing the interaction recording what and why.](media/recording-taxonomy.png "The image shows the recording categories.")

Each of the categories entails different requirements for how recordings
are initiated, what is recorded, where recordings are stored, who is
notified, who controls access, and how retention is handled.

| Type                   | Convenience        | Functional         | Org - General      | Org - Regulated | Lawful Intercept   |
| ---------------------- | ------------------ | ------------------ | ------------------ | --------------- | ------------------ |
| Initiator              | User               | App/Solution       | Admin (system)     | Admin (system)  | LEA                |
| Target                 | Per-call / meeting | Per-call / meeting | Per-call / meeting | Per-user        | Per-endpoint / DID |
| Storage owner          | User               | App                | Admin              | Compliance      | LEA                |
| Notification required? | Yes                | Yes                | Yes                | Yes             | No                 |
| Access Owner           | User               | App                | Admin              | Compliance      | LEA                |
| Retention Policy?      | Optional           | Yes                | Yes                | Yes             | Yes                |

Teams provides various capabilities for
[<span class="underline">convenient</span>](https://docs.microsoft.com/microsoftteams/cloud-recording)
and functional recording for meetings and live events. Organizational
recording means enabling organizations adopting Teams for calling and
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
<th><strong>Persona</strong></th>
<th><strong>Needs</strong></th>
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

![Screenshot showing the team custom app setting](media/hp-compliance-recording-for-teams-calling-and-meetings.jpg "The images shows the flow when a Teams meeting or call is sent and received.")

## Recorder

The core component of the compliance recording solution is the recorder.
Recorders are built as scalable Azure-based services (bots) that
[<span class="underline">leverage Microsoft’s communications
platform</span>](https://docs.microsoft.com/graph/cloud-communications-concept-overview)
and register as applications with Microsoft Graph. The recorder provides
the direct interaction with the Teams calls and meetings
[<span class="underline">communications platform
APIs</span>](https://docs.microsoft.com/graph/api/resources/communications-api-overview?view=graph-rest-1.0)
and provides the endpoint for media ingestion.

A [<span class="underline">sample compliance recorder application is
available</span>](https://github.com/microsoftgraph/microsoft-graph-comms-samples/tree/a3943bafd73ce0df780c0e1ac3428e3de13a101f/Samples/BetaSamples/LocalMediaSamples/ComplianceRecordingBot)
that shows how to configure the bot, create the app instance and assign
the compliance policies. The sample also has examples on API usage for
recording specific interactions such as handling
[<span class="underline">incoming
call</span>](https://github.com/microsoftgraph/microsoft-graph-comms-samples/blob/a3943bafd73ce0df780c0e1ac3428e3de13a101f/Samples/BetaSamples/LocalMediaSamples/ComplianceRecordingBot/FrontEnd/Http/Controllers/PlatformCallController.cs#L199-L244) routing,
[<span class="underline">changing recording
states</span>](https://github.com/microsoftgraph/microsoft-graph-comms-samples/blob/a3943bafd73ce0df780c0e1ac3428e3de13a101f/Samples/BetaSamples/LocalMediaSamples/ComplianceRecordingBot/FrontEnd/Bot/CallHandler.cs#L135-L138),
and [<span class="underline">removing the user who is being
recorded</span>](https://github.com/microsoftgraph/microsoft-graph-comms-samples/blob/a3943bafd73ce0df780c0e1ac3428e3de13a101f/Samples/BetaSamples/LocalMediaSamples/ComplianceRecordingBot/FrontEnd/Bot/CallHandler.cs#L121-L126).
Graph documentation on the specific APIs can be found here for
[<span class="underline">updateRecordingStatus</span>](https://docs.microsoft.com/graph/api/call-updaterecordingstatus?view=graph-rest-1.0&tabs=http)
and
[<span class="underline">incomingContext</span>](https://docs.microsoft.com/graph/api/resources/incomingcontext?view=graph-rest-1.0).

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
recording policies are managed using [<span class="underline">Microsoft
Powershell</span>](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
and can be applied at the tenant, per-user, and security group level for each
organization. You can find more information on Microsoft Docs for
[<span class="underline">Meeting
policies</span>](https://docs.microsoft.com/microsoftteams/meeting-policies-in-teams),
 [<span class="underline">calling
policies</span>](https://docs.microsoft.com/microsoftteams/teams-calling-policy) and  [<span class="underline">group
policies</span>](https://docs.microsoft.com/microsoftteams/assign-policies#assign-a-policy-to-a-group).

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

   [<span class="underline">Set-CsTeamsComplianceRecordingPolicy</span>](https://docs.microsoft.com/powershell/module/skype/set-csteamscompliancerecordingpolicy?view=skype-ps)

3. Assign the Compliance Recording policy to a user.

   ```powershell
   PS C:\> Grant-CsTeamsComplianceRecordingPolicy -Identity testuser@contoso.onmicrosoft.com -PolicyName TestComplianceRecordingPolicy
   ```

   [<span class="underline">Grant-CsTeamsComplianceRecordingPolicy</span>](https://docs.microsoft.com/powershell/module/skype/grant-csteamscompliancerecordingpolicy?view=skype-ps)

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
- Audio conferencing
- PSTN callers

## Compliance recording for Teams certification programs

In addition to publishing publicly-available APIs allowing partners to develop and integrate CCaaS solutions with Teams, we have developed the compliance recording for Microsoft Teams certification program to provide customers with the assurance that each participating partner’s solution has been tested and verified to provide the quality, compatibility and reliability they expect from Microsoft solutions.  

The following partners have certified their solution for Microsoft Teams.

|Partner|Solution website |
|:--|:--|
|NICE |[https://www.niceactimize.com/compliance/ms-teams-recording.html](https://www.niceactimize.com/compliance/ms-teams-recording.html) |


The following partners are in the process of certifying their solution for Microsoft Teams.

|Partner|Solution website |
|:--|:--|
|ASC Technologies |[https://www.asctechnologies.com/english/ASC_Recording_Insights_Compliance_Recording_for_Microsoft_Teams.html](https://www.asctechnologies.com/english/ASC_Recording_Insights_Compliance_Recording_for_Microsoft_Teams.html) |
|AudioCodes |[https://www.audiocodes.com/solutions-products/products/products-for-microsoft-365/smarttap-360-recording](https://www.audiocodes.com/solutions-products/products/products-for-microsoft-365/smarttap-360-recording) |
|CallCabinet |[https://www.callcabinet.com/compliance-microsoft-teams-call-recording](https://www.callcabinet.com/compliance-microsoft-teams-call-recording ) |
|Dubber |[https://www.dubber.net/call-recording/](https://www.dubber.net/call-recording/) |
|Landis Technologies |[https://landistechnologies.com/](https://landistechnologies.com/) |
|Luware |[https://luware.com/en/solution/microsoft-teams-recording/](https://luware.com/en/solution/microsoft-teams-recording/) |
|Numonix |[https://numonix.cloud](https://numonix.cloud)    |
|Oak Innovation |[https://www.oakinnovate.com/call-recording](https://www.oakinnovate.com/call-recording) |
|Red Box |[https://www.redboxvoice.com/compliance-recording-for-microsoft-teams](https://www.redboxvoice.com/compliance-recording-for-microsoft-teams)  |
|Verint |[https://www.verba.com/solutions/microsoft-teams-recording](https://www.verba.com/solutions/microsoft-teams-recording) |

This list will be updated as more partners join and meet the certification criteria.

## Next steps

If you are a vendor seeking to join the certification program, please mail  <a href= "mailto:Teamscategorypartner@microsoft.com">Teamscategorypartner@microsoft.com</a>.
