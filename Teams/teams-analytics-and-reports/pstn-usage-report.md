---
title: Microsoft Teams PSTN usage report
author: CarolynRowe
ms.author: crowe
manager: serdars
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: v-rifer
f1.keywords:
- NOCSH
ms.localizationpriority: medium
search.appverid: MET150
MS.collection: 
- M365-voice
description: Learn how to use the Teams PSTN usage report in the Microsoft Teams admin center to get an overview of calling and audio conferencing usage in your organization.
appliesto: 
- Microsoft Teams
ms.custom: seo-marvel-apr2020
---
# Microsoft Teams PSTN usage report

The Teams PSTN (Public Switched Telephone Network) usage report in the Microsoft Teams admin center gives you an overview of calling and audio conferencing activity in your organization. You can view detailed calling activity for Calling Plans if you use Microsoft as your telephony carrier and for Direct Routing if you use your own telephony carrier.

The **Calling Plans** tab shows information including the number of minutes that users spent in inbound and outbound PSTN calls and the cost of these calls. The **Direct Routing** tab shows you information including the SIP address and call start and end times. Use the information in this report to gain insight into PSTN usage in your organization and help you to investigate, plan, and make business decisions.

> [!NOTE]
> If you have a Telstra or Softbank calling plan, you will not see any call detail records in the PSTN usage report. Please contact Telstra or Softbank for your reporting needs. 

## View the PSTN usage report

1. In the left navigation of the Microsoft Teams admin center, click **Analytics & reports** > **Usage reports**. On the **View reports** tab, under **Report**, select **PSTN usage report**.
2. Under **Date range**, select a predefined range of 7 or 28 days, or set a custom range, and then select **Run report**.

## Interpret the report

### Calling Plans

   ![Screenshot of the Calling Plans PSTN usage report report in the admin center](../media/teams-reports-pstn-usage-calling-plans-with-callouts.png)![Screenshot of the PSTN    usage report in the Microsoft Teams admin center with numbered callouts](../media/teams-reports-pstn-usage-calling-plans-with-callouts.png#lightbox)

|Callout |Description  |
|--------|-------------|
|**1**   |The report can be viewed for trends over the last 7 days, 28 days, or a custom date range that you set. |
|**2**   |Each report has a date for when it was generated. The reports usually reflect a 24 to 48 hour latency from time of activity. |
|**3**   |The X axis is the selected date range for the specific report. The Y axis is the total number of calls over the selected time period. <br>Hover over the dot on a given date to see the total calls on that date.  |
|**4**   |The table gives you a breakdown of PSTN usage per call. <ul><li>**Time stamp (UTC)** is the time the call started.</li><li>**Display name** is the display name of the user. You can click the display name to go to the user's setting page in the Microsoft Teams admin center.</li><li>**Username** is the user's sign-in name.</li><li>**Phone number** is the number that received the call for inbound calls or the number dialed for outbound calls.</li><li>**Call type** is whether the call was a PSTN outbound or inbound call and the type of call such as a call placed by a user or an audio conference. The calls types you may see include:<br><br>**Teams user call types**<ul><li>**user_in** - the user received an inbound PSTN call</li><li>**user_out** - the user placed an outbound PSTN call</li><li>**user_out_conf** - the user added two or more PSTN participants to the call such as a three-way conference call</li><li>**user_out_transfer** - the user transferred the call to a PSTN number</li><li>**user_out_forwarding** - the user forwarded the call to a PSTN number</li><li>**conf_in** - an inbound call to the Audio Conferencing bridge</li><li>**conf_out** - an outbound call from the Audio Conferencing bridge usually to add a PSTN number to the conference</li><li>**unassigned_in** - an inbound PSTN call via Calling Plan to an unassigned number</li></ul><br>**Teams bots call types**<ul><li>**ucap_in** - an inbound PSTN call to Teams bot such as auto attendant or call queue</li><li>**ucap_out** - an outbound PSTN call from a Teams bot such as auto attendant or call queue</li></ul><br><li>**Called to** is the number dialed.</li><li>**To country or region** is the country or region dialed.</li><li>**Called from** is the number that placed the call.</li><li>**From country or region** is the country or region from where the call was placed.</li><li>**Charge** is the amount of money or cost of the call that's charged to your account. </li><li>**Currency** is the type of currency used to calculate the cost of the call. </li><li>**Duration** is how long the call was connected.</li><li>**Domestic/International** tells you whether the call was domestic (within a country or region) or international (outside a country or region) based on the user's location.</li><li>**Call ID** is the call ID for a call. It's an identifier for the call you can use when calling Microsoft Support.</li><li>**Number type** is the user's phone number type, such as a service of toll-free number. </li><li>**Country or region** is the usage location. </li> <li>**Conference ID** is the conference ID of the audio conference. </li><li>**Capability** is the license used for the call. The license types you may see include:<ul><li>**MCOEV or MCOEV_VIRTUALUSER or MCOEV_VIRTUALUSER_GOV** - Voice Applications such as Auto-Attendant or Call Queues</li><li>**FREECALL** - In the event of a technical issue that prevents us from pricing a call, the call is provided for free and will appear with this capability</li><li>**MCOPSTN1** - Domestic Calling Plan (3000 min US / 1200 min EU plans)</li><li>**MCOPSTN2** - International Calling Plan</li><li>**MCOPSTN5** - Domestic Calling Plan (120 min calling plan)</li><li>**MCOPSTN6** - Domestic Calling Plan (240 min calling plan)</li><li>**MCOPSTN8** - Domestic Calling Plan 120 min per user (not pooled across users like the other calling plans are)</li><li>**MCOPSTN9** - International Calling Plan</li><li>**MCOPSTNCAP** - Common Area Phone</li><li>**MCOPSTNPP** - Communications Credits</li><li>**MCOMEETADD** - Audio Conferencing</li><li>**MCOMEETADD_DIALOUT_US** - Audio Conferencing US and Canada dial-out plan</li><li>**MCOMEETADD_CN_GLOBAL** - Audio Conferencing for non-China users</li><li>**MCOMEETADD_TATA** - Tata Communications Connections</li><li>**MCOMEETACPEA** - Audio Conferencing Pay-Per-Minute </li><li>**MCOMEETACPEA_GOV** - Audio Conferencing Pay-Per-Minute for Government</li></ul></li></ul> To see the information that you want in the table, make sure to add the columns to the table.|
|**5**   |Select **Edit columns** to add or remove columns in the table. |
|**6**   |Select **Filter** to filter the report by username or call type. |
|**7**   |Select **Full screen** to view the report in full screen mode. |
|**8**   |You can export the report to a CSV file for offline analysis. Click **Export to Excel**, and then on the **Downloads** tab, click **Download** to download the report when it's ready.|

### Direct Routing

   ![Screenshot of the Direct Routing PSTN usage report report in the admin center](../media/teams-reports-pstn-usage-direct-routing-with-callouts.png)![Screenshot of the Direct Routing PSTN usage report in the Microsoft Teams admin center with numbered callouts](../media/teams-reports-pstn-usage-direct-routing-with-callouts.png#lightbox)

|Callout |Description  |
|--------|-------------|
|**1**   |The report can be viewed for trends over the last 7 days or 28 days. |
|**2**   |Each report has a date for when it was generated. The reports usually reflect a 24 to 48 hour latency from time of activity. |
|**3**   |The X axis is the selected date range for the specific report. The Y axis is the total number of calls over the selected time period.<br>Hover over the dot on a given date to see the total calls on that date.  |
|**4**   |The table gives you a breakdown of PSTN usage per call. <ul><li>**Time stamp (UTC)** is the time the call started.</li><li>**Display name** is the display name of the user. You can click the display name to go to the user's settings page in the Microsoft Teams admin center. The name can also be the name of a bot, for example the Call Queue or Cloud Auto Attendant. </li><li>**SIP address** is the SIP address of the user or a bot who received or made the call.</li><li>**Caller number** is the number of the user or the bot who made the call. </li><li>**Callee number** is the number of the user or the bot who received the call. On an inbound call to a Teams user it will be the Teams user, on an outbound call from a Teams user it will be the PSTN User. </li><li>**Call type** is whether the call was a PSTN outbound or inbound call and the type of call such as a call placed by a user or an audio conference. The call types you may see include:<br><br>**Teams user call types**<ul><li>**dr_in** - the user received an inbound PSTN call</li><li>**dr_out** - the user placed an outbound PSTN call</li><li>**dr_out_user_conf** - the user added a PSTN participant to the call</li><li>**user_out_transfer** - the user transferred the call to a PSTN number</li><li>**dr_out_user_forwarding** - the user forwarded the call to a PSTN number</li><li>**dr_out_user_transfer** - the user transferred the call to a PSTN number</li><li>**dr_emergency_out** - the user made an emergency call</li><li>**dr_unassigned_in** - an inbound PSTN call via Direct Routing to an unassigned number</li></ul><br>**Teams bots call types**<ul><li>**dr_in_bot** - an inbound PSTN call to a Teams bot such as auto attendant or call queue</li><li>**dr_out_bot** - an outbound PSTN call from a Teams bot such as auto attendant or call queue</li></ul><br><li>**Called to** is the number of the user who received the call.</li><li>**Start time (UTC)** is the time when the SIP proxy received the final answer (SIP Message  "200 OK") from the SBC on an outbound call (Teams/Bot to a PSTN User), or after the SIP Proxy send the Invite to the next hop within the Teams backend on an inbound call (PSTN User to a Teams/Bot). </li><li>**Invite time (UTC)** is the time when the initial Invite was sent on an outbound call from a Teams user or bot call to the SBC, or received on an inbound call to a Teams or bot call by the SIP Proxy component of Direct Routing from the SBC.</li><li>**Failure time (UTC)** is the time the call failed. For failed calls only. Final SIP Code, Final Microsoft Subcode, and Final SIP Phrase provide the reasons why the call failed and can help with troubleshooting. </li><li>**End time (UTC)** is the time the call ended (for successful calls only).</li><li>**Duration** is how long the call was connected, from invite to the call end or failure. For call forwarding, duration includes ringing in the Call Queue.</li><li>**Number type** is the user's phone number type, such as a service of toll-free number. </li><li>**Media bypass** indicates whether the trunk was enabled for media bypass. </li> <li>**SBC FQDN** is the fully qualified domain name (FQDN) of the Session Border Controller (SBC). </li><li>**Azure region for Media** is the data center that was used as media path in a non-bypass call. </li><li>**Azure region for Signaling** is the data center that was used for signaling for both bypass and non-bypass calls. </li><li>**Event type** is the event type of the call. You'll see Success for successful calls and Attempt for failed calls. </li><li>**Final SIP code** is the code with which the call ended.</li><li>**Final Microsoft subcode** is a code that indicates specific actions that occurred.</li><li>**Final SIP phrase** is the description of the SIP code and Microsoft subcode.</li><li>**Correlation ID** is a unique identifier for the call that you can use when calling Microsoft Support.</li><li>**Shared Correlation ID** is only visible in the downloadable CSV file and does not exist in the portal. The shared correlation ID exists in at least two calls which are related. Please see detailed description below.</li></ul> To see the information that you want in the table, make sure to add the columns to the table.|
|**5**   |Select **Edit columns** to add or remove columns in the table. |
|**6**   |Select **Full screen** to view the report in full screen mode. |
|**7**   |Select **Export to Excel** to download the data in a comma separated file (CSV) for offline analysis or to use it as input for your billing system. |

#### Caller/Callee fields considerations

Depending on the call direction, the Caller or Callee names can contain non-E164 numbers.

These fields can come from the customer SBC(s). There are three formats that the SBC can send to Direct Routing: E.164 numbers, non-E.164 numbers, and strings.

- E.164 phone number from a user who has an E.164 number to a user who also has an E.164 number. 
- Call from a non-E.164 number. A user from a third-party PBX interconnected with Direct Routing makes a call to a Teams user. In this case, the caller number might be any non-E.164 number, for example +1001. 
- A spammer calls and doesn't present a number, only a name, for example "Internal Revenue Service". This string will be shown in the reports.

#### Phone number obfuscation
Per-country privacy requirements include the obfuscation of the external (not owned by the customer) phone numbers. The three or four last digits of the phone number are replaced with asterisks (+123 456789***). 

For the incoming calls, the caller number is obfuscated, for outgoing calls, the callee number is obfuscated. This applies to the PSTN and Direct Routing reports in Tenant Admin Center, data export, and the call logs available via Microsoft Graph.

The obfuscation is based on the organization's location (country). Full phone numbers are shown for the countries that are not listed in the following table:

| Country | Number of obfuscation digits |
| :-: | :- |
|BE – Belgium | 3 |
|CH – Switzerland | 4 |
|DE - Germany | 3 |
|DK – Denmark | 3 |
|ES – Spain | 3 |
|FI – Finland | 3 |
|FR – France | 4 |
|IT – Italy | 3 |
|NL - Netherlands | 3 |
|NO - Norway | 3 |
|SE - Sweden | 3 |

#### About Shared Correlation ID

The Shared Correlation ID only exists in the exported Excel file that you download and indicates that two or more calls are related. 
The following explains the different scenarios, and when Shared Correlation ID is present.

1.    PSTN User 1 on a PSTN endpoint called Teams User 1 on Teams client, call type Dr_In, correlation ID    57f28917-42k5-4c0c-9433-79734873f2ac, no shared correlation ID.
2.    Teams User 1 on Teams client called PSTN User 1 on a PSTN endpoint, call type    Dr_Out    2c12b8ca-62eb-4c48-b68d-e451f518ff4, no shared correlation ID.
3.    PSTN User 1 on a PSTN endpoint called a Teams User 2 on Teams client, call type    Dr_In    f45e9a25-9f94-46e7-a457-84f5940efde9, shared correlation ID f45e9a25-9f94-46e7-a457-84f5940efde9.
4.    Existing call 3 with correlation ID "f45e9a25-9f94-46e7-a457-84f5940efde9". PSTN User 1 in a call with Teams User 2. Teams User 2 transferred (blind or consultative) a call to Teams or PSTN User, call type    Dr_Out_User_Transfer    45a1da7c-9e97-481a-8a05-3fe19a9a77e0, shared correlation ID    f45e9a25-9f94-46e7-a457-84f5940efde9.

## Exporting the reports
Click **Export to Excel**, and then on the **Downloads** tab, click **Download** to download the report when it's ready. Export process can take from a few seconds to several minutes to complete, depending on the quantity of the data.

This exports data of all users and enables you to do simple sorting and filtering for further analysis. Exported files contain additional fields that are not available in the online report. These can be used for troubleshooting and automated workflows.

 You will receive a zip file named "**Calls.Export.`[identifier]`.zip**", with the identifier being a unique ID for the export that can be used for troubleshooting.

If you have both Calling Plans and Direct Routing, the exported file may contain data for both products. PSTN usage report file will have filename "**PSTN.calls.`[UTC date]`.csv**" and Direct Routing "**DirectRouting.calls.`[UTC date]`.csv**".

 In addition to PSTN and Direct Routing files, the archive contains file "**parameters.json**", with the selected export time range and capabilities.

Exported files are in Comma Separated Values (CSV) format, compliant with [RFC 4180](https://tools.ietf.org/html/rfc4180) standard. The files can be opened in Excel or any other standards-compliant editor without requiring any transformations.

The first row of the CSV contains column names. All dates are UTC and in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format.

### Exported PSTN usage report

 You can export data up to one year from the current date unless country-specific regulations prohibit retention of the data for 12 months.

> [!div class="has-no-wrap"]  
> | # | Name | [Data type (SQL Server)](/sql/t-sql/data-types/data-types-transact-sql) | Description |
> | :-: | :-: | :-: |:------------------- |
> | 0 | UsageId | `uniqueidentifier` | Unique call identifier |
> | 1 | Call ID | `nvarchar(64)` | Call identifier. Not guaranteed to be unique |
> | 2 | Conference ID | `nvarchar(64)` | ID of the audio conference |
> | 3 | User Location | `nvarchar(2)` | Country code of the user, [ISO 3166-1 alpha-2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) |
> | 4 | AAD ObjectId | `uniqueidentifier` | Calling user's ID in Azure Active Directory.<br/> This and other user info will be null/empty for bot call types (ucap_in, ucap_out) |
> | 5 | UPN | `nvarchar(128)` | UserPrincipalName (sign-in name) in Azure Active Directory.<br/>This is usually the same as user's SIP Address, and can be same as user's e-mail address |
> | 6 | User Display Name | `nvarchar(128)` | Display name of the user |
> | 7 | Caller ID | `nvarchar(128)` | Number that received the call for inbound calls or the number dialed for outbound calls. [E.164](https://en.wikipedia.org/wiki/E.164) format |
> | 8 | Call Type | `nvarchar(32)` | Whether the call was a PSTN outbound or inbound call and the type of call such as a call placed by a user or an audio conference |
> | 9 | Number Type | `nvarchar(16)` | User's phone number type, such as a service of toll-free number |
> | 10 | Domestic/International | `nvarchar(16)` | Whether the call was domestic (within a country or region) or international (outside a country or region) based on the user's location |
> | 11 | Destination Dialed | `nvarchar(64)` | Country or region dialed |
> | 12 | Destination Number | `nvarchar(32)` | Number dialed in [E.164](https://en.wikipedia.org/wiki/E.164) format |
> | 13 | Start Time | `datetimeoffset` | Call start time |
> | 14 | End Time | `datetimeoffset` | Call end time |
> | 15 | Duration Seconds | `int` | How long the call was connected |
> | 16 | Connection Fee | `numeric(16, 2)` | Connection fee price |
> | 17 | Charge | `numeric(16, 2)` | Amount of money or cost of the call that is charged to your account |
> | 18 | Currency | `nvarchar(3)` | Type of currency used to calculate the cost of the call ([ISO 4217](https://en.wikipedia.org/wiki/ISO_4217)) |
> | 19 | Capability | `nvarchar(32)` | The license used for the call |

### Exported Direct Routing usage report

You can export data up to five months (150 days) from the current date unless country-specific regulations prohibit retention of the data for that period.

> [!div class="has-no-wrap"]  
> | # | Name | [Data type (SQL Server)](/sql/t-sql/data-types/data-types-transact-sql) | Description |
> | :-: | :-: | :-: |:------------------- |
> | 0 | CorrelationId | `uniqueidentifier` | Call identifier. Multiple legs of the same call can share the same CorrelationId |
> | 1 | AAD ObjectId | `uniqueidentifier` | Calling user's ID in Azure Active Directory.<br/> This and other user info can be null/empty for bot call types |
> | 2 | UPN | `nvarchar(128)` | UserPrincipalName (sign-in name, Azure Active Directory) of the user or bot that made or received the call.<br/>This is usually the same as user's SIP Address, and can be same as user's e-mail address |
> | 3 | Display Name | `nvarchar(128)` | The name of a user or a calling bot (for example, Call Queue or Auto Attendant) as set in Microsoft 365 admin center |
> | 4 | User country | `nvarchar(2)` | Country code of the user, [ISO 3166-1 alpha-2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) |
> | 5 | Invite time | `datetimeoffset` | When the initial Invite send on outbound from Teams user or bot call to the SBC, or received on inbound to Teams or bot call by the SIP Proxy component of Direct Routing from the SBC |
> | 6 | Start time | `datetimeoffset` | Time when the SIP proxy received the final answer (SIP Message  "200 OK") from the SBC on outbound (Teams/Bot to a PSTN User), or after the SIP Proxy send the Invite to the next hop within Teams backend on inbound call (PSTN User to a Teams/Bot).<br/>For failed and unanswered calls, this can be equal to invite or failure time |
> | 7 | Failure time | `datetimeoffset` | Only exists for failed (not fully established) calls |
> | 8 | End time | `datetimeoffset` | Only exists for successful (fully established) calls. Time when call ended |
> | 9 | Duration (seconds) | `int` | Duration of the call, from invite to the call end or failure. For call forwarding, duration includes ringing in the Call Queue. |
> | 10 | Success | `nvarchar(3)` | Yes/No. Success or attempt |
> | 11 | Caller Number | `nvarchar(32)` | Number of the user or bot who made the call. On inbound to a Team user call it will be a PSTN User, on outbound from Teams user call it will be the Teams user number |
> | 12 | Callee Number | `nvarchar(32)` | Number of the user or bot who received the call. On inbound to a Team user call it will be the Teams user, on outbound from Teams user call it will be the PSTN User |
> | 13 | Call type | `nvarchar(32)` | Call type and direction |
> | 14 | Azure region for Media | `nvarchar(8)` | The datacenter used for media path in non-bypass call |
> | 15 | Azure region for Signaling | `nvarchar(8)` | The datacenter used for signaling for both bypass and non-bypass calls |
> | 16 | Final SIP code | `int` | The code with which the call ended, [RFC 3261](https://tools.ietf.org/html/rfc3261) |
> | 17 | Final Microsoft subcode | `int` | In addition to the SIP codes, Microsoft has own subcodes that indicate the specific issue |
> | 18 | Final SIP Phrase | `nvarchar(256)` | Description of the SIP code and Microsoft subcode |
> | 19 | SBC FQDN | `nvarchar(64)` | Fully qualified domain name of the session border controller |
> | 20 | Media bypass | `nvarchar(3)` | Yes/No. Indicates if the trunk was enabled for media bypass or not |
> | 21 | Shared correlation ID | `uniqueidentifier` | Indicates that two or more calls are related |


## Related topics

- [Teams analytics and reporting](teams-reporting-reference.md)
- [PSTN call report in Microsoft Graph](/graph/api/callrecords-callrecord-getpstncalls?view=graph-rest-1.0&tabs=http)
- [Direct routing report in Microsoft Graph](/graph/api/callrecords-callrecord-getdirectroutingcalls?view=graph-rest-1.0&tabs=http)
