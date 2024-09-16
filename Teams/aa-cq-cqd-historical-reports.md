---
title: Auto attendant and Call queue historical reports
author: mkbond007
ms.author: mabond
manager: pamgreen
ms.reviewer: colongma
ms.date: 09/16/2024
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - Tier1
  - ContentFreshnessFY24
search.appverid: MET150
audience: Admin
appliesto: 
  - Skype for Business
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords: 
  - CSH
ms.custom: 
  - Reporting
  - ms.teamsadmincenter.directrouting.cqd
  - ms.lync.lac.ToolsCallQualityDashboard
description: Learn about how to use the updated Teams Auto Attendant & Call Queue Historical Report Power BI report to view Auto Attendant and Call Queue historical data.
---



# Auto attendant and Call queue historical reports

> [!IMPORTANT]
> GCC High and DoD customers need to use [Auto attendant and call queue historical reports for GCC High and DoD](aa-cq-cqd-historical-reports-v164.md).

This Power BI template provides three reports that allow organizations to report on the number of calls processed by Auto attendants and Call queues. It also provides agent performance insights.

## V3.1.8 published on August 12, 2024

The Teams Auto Attendant & Call Queue Historical Report Power BI template provides the following three reports:

- The [Auto Attendant](media/aa-cq-historical-report-sample-aa-v316-new.png) report shows analytics for calls coming into your Auto attendants.
- The [Call Queue](media/aa-cq-historical-report-sample-cq-v316-new.png) report shows analytics for calls coming into your Call queues.
- The [Agent Timeline](media/aa-cq-historical-report-sample-at-v316-new.png) report shows a timeline view of agents being active in Call queue calls.

These reports use data from the Voice Applications Analytics Collector (VAAC) service.

## V3.x.x prerequisites

### Power BI Desktop

You need to have Power BI Desktop installed. You can install and use the free version from the [Microsoft Windows Store](https://aka.ms/pbidesktopstore).

> [!IMPORTANT]
> Power BI Desktop is updated and released on a monthly basis, incorporating customer feedback and new features. Only the most recent version of Power BI Desktop is supported; customers who contact support for Power BI Desktop will be asked to upgrade to the most recent version. You can get the most recent version of Power BI Desktop from the [Windows Store](https://aka.ms/pbidesktopstore), or as a single executable containing all supported languages that you [download](https://www.microsoft.com/download/details.aspx?id=58494) and install on your computer.

### Power BI Service

These reports can be [published to the Power BI service](/power-bi/create-reports/desktop-upload-desktop-files).

Once the report is published:

1. Go to the dataset **Settings**.
2. Expand the **Data source credentials** section.
3. Select **Edit credentials**.
4. Set the **Authentication method** to `OAuth2`.
5. Ensure **Skip test connection** is enabled.
6. Select **Sign in** and provide your credentials.

When completed, you're able to [configure a scheduled refresh](/power-bi/connect-data/refresh-scheduled-refresh) of the dataset.

### Access permissions

Use one of the following methods to control access to the historical reports:

- Voice applications policy

To control which Auto attendants, Call queues and Agents users can report on without providing them access to Teams admin center, create a voice applications policy that grants them access to historical reporting and assign them as an Authorized user to the appropriate Auto attendants and Call queues.

For more information, see [Plan for Auto attendant and Call queue authorized users](./aa-cq-authorized-users-plan.md).

> [!TIP]
> Using the voice applications policy to control access is the recommended approach.  With the voice applications policy and Authorized users it is possible to control which Auto attendants, Call queues, and Agents a user can report on. If necessary, the policy still allows a user to report on all Auto attendants, Call queues, and Agents without providing access to Teams admin Center.

Create, or modify, a voice applications policy that enables the historical reporting permissions. Assign the policy to the appropriate users. Assign the users as authorized users to the appropriate auto attendants and call queues. For more information, see [Manage voice applications policies in Microsoft Teams](./manage-voice-applications-policies.md)

The historical reporting permissions can only be set through PowerShell and will be available in Teams admin center later this year. 

For more information, see:

|New voice applications policy           |Existing voice applications policy |
|:---------------------------------------|:----------------------------------|
| [New-CsTeamsVoiceApplicationsPolicy/-HistoricalAutoAttendantMetricsPermission](/powershell/module/teams/new-csteamsvoiceapplicationspolicy#-HistoricalAutoAttendantMetricsPermission)  | [Set-CsTeamsVoiceApplicationsPolicy/-HistoricalAutoAttendantMetricsPermission](/powershell/module/teams/set-csteamsvoiceapplicationspolicy#-HistoricalAutoAttendantMetricsPermission) |
| [New-CsTeamsVoiceApplicationsPolicy/-HistoricalCallQueueMetricsPermission](/powershell/module/teams/new-csteamsvoiceapplicationspolicy#-HistoricalCallQueueMetricsPermission)  | [Set-CsTeamsVoiceApplicationsPolicy/-HistoricalCallQueueMetricsPermission](/powershell/module/teams/set-csteamsvoiceapplicationspolicy#-HistoricalCallQueueMetricsPermission) |
| [New-CsTeamsVoiceApplicationsPolicy/--HistoricalAgentMetricsPermission](/powershell/module/teams/new-csteamsvoiceapplicationspolicy#--HistoricalAgentMetricsPermission)  | [Set-CsTeamsVoiceApplicationsPolicy/-HistoricalCallQueueMetricsPermission](/powershell/module/teams/set-csteamsvoiceapplicationspolicy#--HistoricalAgentMetricsPermission) |

#### Known issues

If the voice applications policy assigned to a user only enables the historical reporting permissions, and optionally the real-time reporting permissions, then the user can't access the historical reports. Support is working to resolve this problem. In the interim, enable at least one Auto attendant and Call queue change permission in the policy. Enabling the Auto attendant **Business hours greeting** and Call queue **Welcome greeting** is suggested, but enabling any of the change permissions will work around this issue.

- Call Quality Dashboard (CQD) pipeline [legacy]

If you want the user to report on **all** the Auto attendants, Call queues, and Agents in the tenant and you want to grant the user access to Teams admin center to run other Usage reports, assign the user a CQD access role with both **View Reports** and **View EUII fields** set to **Yes**.

For more information, see [CQD access role](./turning-on-and-using-call-quality-dashboard.md#assign-admin-roles-for-access-to-cqd).

> [!NOTE]
> If a user is assigned a CQD access role and a voice applications policy, the CQD role will take precendence and the user will see all the Auto attendants, Call queues and Agents in the tenant.

## V3.x.x desktop installation

The following steps assume the Power BI Desktop client is installed on your computer and that your account has the necessary permissions to access the CQD data pipeline.

Perform the following steps:

1. Download and save the [Teams Auto Attendant & Call Queue Historical Reports V3.1.8.zip](https://www.microsoft.com/download/details.aspx?id=104623) file on your computer.

2. Open the zip file.

3. Open the `Teams Auto Attendant & Call Queue Historical Reports V3.1.8.pbit` template file. Power BI Desktop should launch.

4. Select the **DataSource**, **Report Level**, and **UTC Offset**.  

   :::image type="content" source="media/aa-cq-historical-report-01-v318.png" alt-text="Screenshot showing the DataSource, Report Level, and UTC Offset selections.":::

    - **DataSource**: Select the `api.interfaces.records.teams.microsoft.com` entry.
    - **Report Level**:
        - Select `Per Call` (default) to retrieve all the individual call records.
        - Select `Per Day` to retrieve an aggregated total for each day. 
    - **UTC Offset**: Select the UTC offset that represents the time zone the reports are presented in. Only valid when the **Report Level** is set to `Per Call`

    #### Per Day vs Per Call 

   - Per Call reporting retrieves the individual call records for each Auto attendant, Call queue, and Agent, the user is authorized for and makes them available in the Power BI client. Per Call reporting also allows call records to be displayed in the local time zone selected by the user. For some customers, especially those using the CQD access role to control access, this may result in hitting the 90,000 default or 200,000 per query record limit. In this case, the Per Day reporting option should be selected.

    - Per Day reporting retrieves one daily summary record for each Auto attendant, Call queue, and Agent. This results in fewer records being returned to the client, reducing the possibility of hitting the 90,000 default or 200,000 per query record limit. Per Day reporting is based on a UTC-00:00 day (00:00:00-23:59:59 UTC) only and any UTC offset supplied by the user is ignored.

5. Sign in with your Teams account.
   - Select **File**, then **Options and settings**, and then **Data source settings**.
   - Select **Edit Permissions**, and then **Edit**.
   - Select **Organizational account**, and then **Sign in**.
   - Select **Save**, then **OK**, and then **Close**.

     :::image type="content" source="media/aa-cq-historical-report-03-v301.png" alt-text="Screenshot showing sign-in for V3.x.x.":::

6. Select **Refresh**, in the ribbon bar and the data refreshes.

## Data latency for Auto attendant and Call queue analytics

The data is typically available within 30 minutes of the call being completed, but there are cases where it can take several hours for the data to appear.

You have to refresh the report to see any new data.

## Auto attendant and Call queue historical reports

### Cloud Auto Attendant Analytics report

#### Interpret the report

:::image type="content" source="media/aa-cq-historical-report-sample-aa-v316-new-explain.png" alt-text="Screenshot showing sample cloud auto attendant analytics report." lightbox="media/aa-cq-historical-report-sample-aa-v316-new-explain.png":::

| Callout | Title | Description |
|:-|:-|:-|
| 1 | Date | The start and end date of the report.<br>Use this slider to select the date range to report on.<br><br>[**See Known Issues**](#known-issues) |
| 2 | Time Range | The start and end hour of the report. The report spans all dates/times from start date/start hour to the end date/end hour.<br>Use this slider to select the time range to report on. |
| 3 | Auto Attendant Resource Accounts | The Resource Accounts to be reported on. To see the calls for a specific Auto attendant, select all the resource accounts assigned to that Auto attendant. If the full Resource Account name is **aa_test@microsoft.com**, then this value is: **aa_test**<br>Default: All |
| 4 | Quick Stats -> Incoming Calls | The breakdown shows the total number of calls received between the start date/start hour and end date/end hour.<br><br>*TIP: Hover over any metric in this section to display a tooltip with the individual calls that make up the total.* |
| 5a | Quick Stats -> Usage Statistics | The breakdown shows the average call duration in the Auto Attendant and the average number of caller actions. |
| 5b | Caller Action Count | The breakdown on the number of caller actions (key presses, voice commands) |
| 6 | Quick Stats -> Directory Search Method | The breakdown shows how the Directory Search option was used by callers.<br>This section of the report is blank if the Auto Attendant isn't configured for this service or if callers don't use it.<br><br>Directory Search Method Legend Definitions:<br><ul><li>**DTMF** - Caller used the telephone dial pad to search for the user's name</li><li>**Voice** - Caller used voice input to search for the user's name</ul> |
| 7 | Call Results | The breakdown shows the call treatment received by callers.<br><br>Call Results Legend Definitions:<br><ul><li>**Terminated (No Caller Action)** - Call was disconnected - the caller didn't make any selections</li><li>**Terminated (With Caller Action)** - Call was disconnected - the caller made selections</li><li>**Terminated (Disconnected)** - Call was disconnected per the auto attendant configuration</li><li>**Terminated (No Operator)** - Call was disconnected as there was no operator to transfer the call to</li><li>**Terminated (Transfer Failed)** - Call was disconnected as the configured transfer failed</li><li>**Transferred (AA)** - Call was transferred to another Auto Attendant</li><li>**Transferred (CQ)** - Call was transferred to a Call Queue</li><li>**Transferred (Operator)** - Call was transferred to the Operator</li><li>**Transferred (Voicemail)** - Call was transferred to Shared Voicemail</li><li>**Transferred (External)** - Call was transferred to an External Number</li><li>**Transferred (User)** - Call was transferred to a Person in the organization</li><li>**Other** - Some other condition occurred</li></ul><br>*TIP: Hover over any metric in this section to display a tooltip with the individual calls that make up the total.* |
| 8 |  | The breakdown shows the caller paths through the auto attendant and the final call result.<br><br>Column definitions:<br><ul><li>**MM-DD** - The month and day the call</li><li>**Start Hour** - The hour the call started</li><li>**Name** - The Resource Account name</li><li>**Call flow** - The call flow the call followed. See [Auto Attendant dimensions -> AutoAttendantCallFlow](#auto-attendant-dimensions)</li><li>**Call Type** - The connectivity method for the call.  CalllingPlan or DirectRouting</li><li>**Call Result** - The end result of the call (see #7 Call Results)</li><li>**Call Count** - The number of calls that followed this same path</li><li>**Average Call Duration (seconds)** - The average number of seconds the call spent in the Auto Attendant</li></ul><br>*TIP: Hover over any metric in this section to display a tooltip with the individual calls that make up the total.* |

#### Known issues

1. Only the calls and caller actions in the first Auto attendant that answers the call are reported on.  Calls and caller actions in chained Auto attendants (when one Auto attendant transfers to another Auto attendant) aren't reported on.
1. The Auto attendant resource account ID's name instead of Auto attendant name is shown.  To show all the traffic for an Auto attendant, you must select all the resource accounts assigned to the Auto attendant.
1. Only 28 days of call history are available. Auto attendant data is considered personal data and is subject to data privacy retention policies.
1. The Date selector sometimes shows dates outside the range of available data resulting in a blank report. Change the dates to be within the last 28 days to resolve the issue.

### Cloud Call Queue Analytics report

#### Interpret the report

:::image type="content" source="media/aa-cq-historical-report-sample-cq-v316-new-explain.png" alt-text="Screenshot showing sample cloud call queue analytics report." lightbox="media/aa-cq-historical-report-sample-cq-v316-new-explain.png":::

|Callout  |Title                                  |Description               |
|:--------|:--------------------------------------|:-------------------------|
|1        |Date                                   |The start and end date of the report.<br>Use this slider to select the date range to report on.<br><br>[**See Known Issues**](#known-issues-1) |
|2        |Time Range                             |The start and end hour of the report. The report spans all dates/times from start date/start hour to the end date/end hour.<br>Use this slider to select the time range to report on.    |
|3        |Call Queue Resource Accounts           |The Resource Accounts to be reported on. To see the calls for a specific Call queue, select all the resource accounts assigned to that Call queue. If the full Resource Account name is **cq_test@microsoft.com**, then this value is: **cq_test**<br>Default: All       |
|4        |Quick Stats -> Incoming Calls          |The breakdown shows the total number of calls received between the start date/start hour and end date/end hour.<br><br>*TIP: Hover over any metric in this section to display a tooltip with the individual calls that make up the total.* |
|5        |Quick Stats -> Average Wait Time (seconds)      |The breakdown shows the average call duration in the Call Queue before a caller is answered or they abandon. |
|6        |Call Results                           |The breakdown shows the call treatment received by callers.<br><br>Call Results Legend Definitions:<br><ul><li>**Abandoned** - Caller disconnected before an agent answered or before Call Timeout occurred</li><li>**Agent Answered** - Caller was answered by an agent</li><li>**Overflowed** - The Call Overflow exception handling condition occurred</li><li>**Timed Out** - The Call Timeout exception handling occurred</li><li>**No Agents** - The No Agent exception handling condition occurred</li><li>**Other** - Some other condition occurred</li></ul><br>*TIP: Hover over any metric in this section to display a tooltip with the individual calls that make up the total.*   |
|7        |Call Volume, Abandoned Calls, Agent Opt-in Count     |The breakdown shows the number of calls received and abandoned per hour and the maximum number of agents that were opted into the call queue at that time  |
|8        |Average Session Length (seconds)       |The breakdown shows how long calls waited before each call result.<br><br><ul><li>**Agent Answered (Call)** - for calls answered by an agent</li><li>**Agent Answered (Callback)** - for callbacks answered by an agent</li><li>**Abandoned** - for calls abandoned before an agent answered or before Call Timeout occurred</li><li>**Overflowed (Disconnect)** - for calls where the Call Overflow exception handling occurred and the treatment was to disconnect</li><li>**Overflowed (Xferred)** - for calls where the Call Overflow exception handling occurred and the treatment was to transfer the caller to a Person in the organization or externally</li><li>**Overflowed (Voicemail)** - for calls where the Call Overflow exception handling occurred and the treatment was to send the call to shared voicemail</li><li>**Timed Out (Disconnect)** - for calls where the Call Timeout exception handling occurred and the treatment was to disconnect</li><li>**Timed Out (Xferred)** - for calls where the Call Timeout exception handling occurred and the treatment was to transfer the caller to a Person in the organization or externally</li><li>**Timed Out (Voicemail)** - for calls where the Call Timeout exception handling occurred and the treatment was to send the call to shared voicemail</li><li>**No Agents (Disconnect)** - for calls where the No Agents exception handling occurred and the treatment was to disconnect</li><li>**No Agents (Xferred)** - for calls where the No Agents exception handling occurred and the treatment was to transfer the caller to a Person in the organization or externally</li><li>**No Agents (Voicemail)** - for calls where the No Agents exception handling occurred and the treatment was to send the call to shared voicemail</li><li>**Other** - for calls where some other condition occurred</li></ul> |
|9        |Call Overflow/Timeout/No Agents Destinations |The breakdown shows where the calls that received the Call Overflow, Call Timeout or No Agents exception handling treatment were sent.<br><br><ul><li>**ApplicationEndpoint** - call was transferred to another Auto Attendant or Call Queue</li><li>**Mailbox** - call was transferred to shared voicemail</li><li>**Other** - some other condition occurred</li><li>**Phone** - call was transferred externally</li><li>**User** - call was transferred to a Person in the organization</li></ul> |

#### Known issues

1. Only the calls and caller actions in the first Call queue that answers the call are reported on.  Calls in chained Call queues (when one Call queue transfers to another Call queue) aren't reported on.
1. The Call queues resource account ID's name instead of Call queue name is shown.  To show all the traffic for a Call queue, you must select all the resource accounts assigned to the Call queue.
1. Only 28 days of call history are available. Call queue data is considered personal data and is subject to data privacy retention policies.
1. The Date selector sometimes shows dates outside the range of available data resulting in a blank report. Change the dates to be within the last 28 days to resolve the issue.

### Cloud Call Queue Agent Timeline report

#### Interpret the report

:::image type="content" source="media/aa-cq-historical-report-sample-at-v316-new-explain.png" alt-text="Screenshot showing sample cloud call queue agent timeline report." lightbox="media/aa-cq-historical-report-sample-at-v316-new-explain.png":::

|Callout  |Title                                  |Description               |
|:--------|:--------------------------------------|:-------------------------|
|1        |Date                                   |The start and end date of the report.<br>Use this slider to select the date range to report on.<br><br>[**See Known Issues**](#known-issues-2) |
|2        |Agent Username                         |The agents to report on. If the full username is **user@microsoft.com**, then this value is: **user** <br>Default: All    |
|3        |Call Queue Resource Accounts           |The Resource Accounts to be reported on. To see the calls for a specific Call queue, select all the resource accounts assigned to that Call queue.<br>Default: All       |
|4        |Quick Stats -> Incoming Calls          |The breakdown shows the total number of calls answered, the average number of calls answered per agent and the average call length of answered calls handled.<br><br>*TIP: Hover over any metric in this section to display a tooltip with the individual calls that make up the total.* |
|5        |Calls Answered (by date)               |The breakdown shows the number of agent-answered calls by date |
|6        |                                       |The breakdown shows how many calls each agent in the queue answered and the average call duration for those calls. |
|7        |Calls Answered (by hour)               |The breakdown shows the number of agent-answered calls by hour  |
|8        |                                       |The breakdown shows the number of calls answered by agent, by Call Queue.<br><br>Column definitions:<br><ul><li>**MM-DD** - The month and day the call</li><li>**Hour** - The hour the call was answered</li><li>**CQ Name** - The Resource Account name</li><li>**Agent Name** - The URI name of the agent who answered the call</li><li>**Calls Answered** - The number of calls answered by this agent from this Call Queue</li><li>**Average Call Duration (Seconds)** - The average call duration of each call in seconds</li><li>**Total Call Duration (Minutes)** - The total call duration for all calls</li><li>**Total Call Duration (HH:MM:SS)** - The total call duration for all calls</li></ul> |

#### Known issues

1. Only 28 days of call history are available. Call queue and Agent data is considered personal data and is subject to data privacy retention policies.
1. The Call queues resource account ID's name instead of Call queue name is shown.  To show all the traffic for a Call queue, you must select all the resource accounts assigned to the Call queue.
1. The Agent's UPN name instead of their name is shown.
1. The Date selector sometimes shows dates outside the range of available data resulting in a blank report. Change the dates to be within the last 28 days to resolve the issue.
1. In some scenarios, the agent answered call count might be different than the number of calls shown in the Teams client call history. The Teams client call history is correct. Support is investigating, but there's no estimated time to repair available at this time.
1. When an agent answers a call in a different call queue due to redirection through Call Overflow exception handling, they are displayed in the original call queue where the exception occurred instead of the one they answered the call in.

## Auto attendant and Call queue historical reports field definitions

#### fAutoAttendant table field description

|Name                                    |Data Type                |Description                                                                              |
|:---------------------------------------|:------------------------|:----------------------------------------------------------------------------------------|
|AA Name                                 |Text                     |Name of the resource account attached to the Auto Attendant<br><br>If the full Resource Account name is **aa_test@microsoft.com**, then this value is: **aa_test** |
|AA Start Date Local                     |Date                     |Auto Attendant call start date - Local (based on selected UTC Offset)                    |
|AA Start Hour                           |Whole Number             |Auto Attendant call start hour - Local (based on selected UTC Offset)                    |
|AA Start Time Local                     |Date/time                |Auto Attendant call start time - Local (based on selected UTC Offset)                    |
|AA Start Time UTC                       |Date/time                |Auto Attendant call start time - UTC                                                     |
|AACallerActionCount                     |Whole number             |Summarize: Sum<br>Count of actions selected by caller in Auto Attendant during the call  |
|AACallerActionCountAverage (Measure)    |Whole number             |Average of AACallerActionCount - zero instead of blank                                   |
|AACallFlow                              |Text                     |See [Auto Attendant dimensions -> AutoAttendantCallFlow](#auto-attendant-dimensions)     |
|AACallResult                            |Text                     |See [Auto Attendant dimensions -> AutoAttendantCallResult](#auto-attendant-dimensions)   |
|AACallResultLegend                      |Text                     |Legend items for on AACallResult. Possible values are:<br><ul><li>**Terminated (No Caller Action)** - Call was disconnected - the caller didn't make any selections</li><li>**Terminated (With Caller Action)** - Call was disconnected - the caller made selections</li><li>**Terminated (Disconnected)** - Call was disconnected per the auto attendant configuration</li><li>**Terminated (No Operator)** - Call was disconnected as there was no operator to transfer the call to</li><li>**Terminated (Transfer Failed)** - Call was disconnected as the configured transfer failed</li><li>**Transferred (AA)** - Call was transferred to another Auto Attendant</li><li>**Transferred (CQ)** - Call was transferred to a Call Queue</li><li>**Transferred (Operator)** - Call was transferred to the Operator</li><li>**Transferred (Voicemail)** - Call was transferred to Shared Voicemail</li><li>**Transferred (External)** - Call was transferred to an External Number</li><li>**Transferred (User)** - Call was transferred to a Person in the organization</li><li>**Other** - Some other condition occurred</li></ul>                |
|AAChainDuration                         |Decimal number           |Summarize: Sum<br>Duration of call in Auto Attendant                                     |
|AAChainDurationAverage (Measure)        |Decimal number           |Average of AAChainDuration - zero instead of blank                                       |
|AAChainIndex                            |Whole Number             |                                                                                         |
|AAConnectivityType                      |Text                     |See [Common dimensions -> PSTNConnectivityType](#common-dimensions)                      |
|AACount                                 |Whole Number             |Summarized: Sum<br>Number of Auto Attendants involved in call                            |
|AADirectorySearchMethod                 |Text                     |See Auto [Attendant dimensions -> AutoAttendantDirectorySearchMethod](#auto-attendant-dimensions)  |
|AADirectorySearchMethodCountDTMF (Measure)  |Whole number         |Count of calls that used DTMF to search the directory - zero instead of blank            |
|AADirectorySearchMethodCountVoice (Measure) |Whole number         |Count of calls that used Voice to search the directory - zero instead of blank           |
|AADirectorySearchMethodLegend           |Text                     |Legend items for AADirectorySearchMethod. Possible values are:<br><ul><li>**DTMF** - Caller used the telephone dial pad to search for the user's name</li><li>**Voice** - Caller used voice input to search for the user's name</li></ul>                             |
|AATransferAction                        |Text                     |See [Auto Attendant Dimensions -> AutoAttendantTransferAction](#auto-attendant-dimensions)   |
|Call Duration Seconds                   |Whole number             |Call duration                                                                            |
|Call End Time Local                     |Date/time                |Call end time - Local (based on selected UTC Offset)                                     |
|Call End Time UTC                       |Date/time                |Call end time - UTC                                                                      |
|Call Start Time Local                   |Date/time                |Call start time - Local (based on selected UTC Offset)                                   |
|Call Start Time UTC                     |Date/time                |Call start time - UTC                                                                    |
|ConferenceID (Per Day only)             |Text                     |Used for troubleshooting purposes - provide this information when opening a ticket       |
|DialogID (Per Day only)                 |Text                     |Used for troubleshooting purposes - provide this information when opening a ticket       |
|DocumentID (Per Day only)               |Text                     |Used for troubleshooting purposes - provide this information when opening a ticket       |
|MM-DD                                   |Text                     |Auto Attendant call month-day                                                            |
|PSTNMinutes                             |Whole number             |Summarize: Sum<br>Total minute usage                                                     |
|TotalCallCount                          |Whole number             |Summarize: Sum<br>Always 1 - used to provide sum of all calls                            |
|TotalCallCountSum (Measure)             |Whole number             |Sum of TotalCallCount                                                                    |

### Cloud Call Queue Analytics report

#### fCallQueueAnalytics table field description

|Name                                    |Data Type                |Description                                                                              |
|:---------------------------------------|:------------------------|:----------------------------------------------------------------------------------------|
|Call Count                              |Whole number             |Summarize: Sum<br>Number of calls                                                        |
|Call Count Abandoned                    |Whole number             |Summarize: Sum<br>Number of abandoned calls                                              |
|Call Count Sum (Measure)                |Whole number             |Call Count Sum - zero instead of blank                                                   |
|Call Count Sum Abandoned (Measure)      |Whole number             |Call Count Abandoned - zero instead of blank                                             |
|Call Duration Seconds                   |Whole number             |Summarize: Sum<br>Call duration                                                          |
|Call Duration Seconds AVG (Measure)     |While number             |Average Call Duration Seconds                                                            |
|Call End Time Local                     |Date/time                |Call end time - Local (based on selected UTC Offset)                                     |
|Call End Time UTC                       |Date/time                |Call end time - UTC                                                                      |
|Call Queue Agent Count                  |Whole number             |Summarize: Sum<br>Number of agents configured in the Call queue                          |
|Call Queue Agent Opt In Count           |Whole number             |Summarize: Sum<br>Number of agents opted-in to the Call queue                            |
|Call Queue Call Result                  |Text                     |See [Call Queue Dimensions -> CallQueueCallResult](#call-queue-dimensions)               |
|Call Queue Call Result Legend           |Text                     |Legend items for Call Queue Result. Possible values:<br><ul><li>**Abandoned** - the caller hung up before an agent could answer or before timeout occurred</li><li>**Agent Answered** - the caller was answered by an agent</li><li>**Overflowed** - the call overflow exception occurred</li><li>**Timed Out** - the call timeout exception occurred</li><li>**No Agents** - the no agents exception occurred</li><li>**Other** - some other condition occurred</li></ul>                                      |
|Call Queue Target Type                  |Text                     |See [Call Queue Dimensions -> CallQueueTargetType](#call-queue-dimensions)               |
|Call Queue Target Type Legend           |Text                     |Legend items for Call Queue Target Type. Possible values:<br><ul><li>**Abandoned** - the caller hung up before an agent could answer or before timeout occurred</li><li>**Agent Answered (Call)** - the caller was answered by an agent</li><li>**Agent Answered (Callback)** - the callback was answered by an agent</li><li>**Overflowed (Application)** - the call overflow exception occurred - call routed to another application</li><li>**Overflowed (Disconnect)** - the call overflow exception occurred - call disconnected</li><li>**Overflowed (External)** - the call overflow exception occurred - call was transferred externally</li><li>**Overflowed (User)** - the call overflow exception occurred - call was transferred to a Person in the organization</li><li>**Overflowed (Voicemail)** - the call overflow exception occurred - call was transferred to shared voicemail</li><li>**Timed Out (Application)** - the call timeout exception occurred - call routed to another application</li><li>**Timed Out (Disconnect)** - the call timeout exception occurred - call was disconnected</li><li>**Timed Out (External)** - the call timeout exception occurred - call was transferred externally</li><li>**Timed Out (User)** - the call timeout exception occurred - call was transferred to a Person in the organization</li><li>**Timed Out (Voicemail)** - the call timeout exception occurred - call was transferred to shared voicemail</li><li>**No Agents (Application)** - the no agents exception occurred - call was routed to another application</li><li>**No Agents (Disconnect)** - the no agents exception occurred - call was disconnected</li><li>**No Agents (External)** - the no agents exception occurred - call was transferred externally</li><li>**No Agents (User)** - the no agents exception occurred - call was transferred to a Person in the organization</li><li>**No Agents (Voicemail)** - the no agents exception occurred - call was transferred to shared voicemail</li></ul> |
|Call Start Time Local                   |Date/time                |Call start time - Local (based on selected UTC Offset)                                   |
|Call Start Time UTC                     |Date/time                |Call start time - UTC                                                                    |
|ConferenceID (Per Call only)            |Text                     |Used for troubleshooting purposes - provide this information when opening a ticket       |
|CQ Name                                 |Text                     |Name of resource account attached to Call Queue<br><br>If the full Resource Account name is **cq_test@microsoft.com**, then this value is: **cq_test** |
|CQHour                                  |Whole Number             |Call queue call start hour                                                               |
|Date                                    |Date/time                |Call queue call start date and time (hour)                                               |
|DateTimeCQName                          |Text                     |Unique key for filtering on fCallQueueFinalStateAction                                   |
|DialogID (Per Call only)                |Text                     |Used for troubleshooting purposes - provide this information when opening a ticket       |
|DocumentID (Per Call only)              |Text                     |Used for troubleshooting purposes - provide this information when opening a ticket       |
|PSTN Connectivity Type                  |Text                     |See [Common Dimensions -> PSTNConnectivityType](#common-dimensions)                      |
|PSTN Total Minutes                      |Whole number             |Summarize: Sum<br>Total minutes usage for PSTN calls                                     |

#### fCallQueueFinalStateAction table field description

|Name                                    |Data Type                |Description                                                                              |
|:---------------------------------------|:------------------------|:----------------------------------------------------------------------------------------|
|Average Call Duration (Seconds)         |Decimal number           |Summarize: Sum<br>Average call duration in seconds for abandoned calls                   |
|Average Call Duration (Seconds) Average (Measure)  |Whole number  |Average of Average Call Duration (Seconds) - zero instead of blank                       |
|Average Call Queue Duration (Sec)       |Decimal number           |Summarize: Sum<br>Average waiting time in seconds for answered calls                     |
|Average Call Queue Duration (Sec) (Measure)        |Whole number  |Average of Average Call Queue Duration (Sec) - zero instead of blank                     |
|Call Count                              |Whole number             |Summarize: Sum<br>Number of calls                                                        |
|Call Queue Call Result                  |Text                     |See [Call Queue Dimensions -> CallQueueCallResult](#call-queue-dimensions)               |
|Call Queue Call Result Legend           |Text                     |Legend items for Call Queue Call Result. Possible values:<br><ul><li>**Abandoned** - the caller hung up before an agent could answer or before timeout occurred</li><li>**Agent Answered (Call)** - the caller was answered by an agent</li><li>**Agent Answered (Callback)** - the callback was answered by an agent</li><li>**Overflowed (Disconnect)** - the call overflow exception occurred - call disconnected</li><li>**Overflowed (Xferred)** - the call overflow exception occurred - call was transferred externally</li><li>**Overflowed (Voicemail)** - the call overflow exception occurred - call was transferred to shared voicemail</li><li>**Timed Out (Callback)** - the callback timed out - callback didn't occur</li><li>**Timed Out (Disconnect)** - the call timeout exception occurred - call was disconnected</li><li>**Timed Out (Xferred)** - the call timeout exception occurred - call was transferred externally</li><li>**Timed Out (Voicemail)** - the call timeout exception occurred - call was transferred to shared voicemail</li><li>**No Agents (Disconnect)** - the no agents exception occurred - call was disconnected</li><li>**No Agents (Xferred)** - the no agents exception occurred - call was transferred externally</li><li>**No Agents (Voicemail)** - the no agents exception occurred - call was transferred to shared voicemail</li></ul> |
|Call Queue Final State Action           |Text                     |See [Call Queue Dimensions -> CallQueueFinalStateAction](#call-queue-dimensions)         |
|CQ Name                                 |Text                     |Name of resource account attached to Call Queue<br><br>If the full Resource Account name is **cq_test@microsoft.com**, then this value is: **cq_test** |
|CQHour                                  |Number                   |Hour that the call took place in                                                         |
|Date                                    |Date/time                |Call Queue call start date and time (hour)                                               |
|DateTimeCQName                          |Text                     |Unique key for filtering on fCallQueueFinalStateAction                                   |
|IsAbandoned                             |True/false               |True if the caller hangs up before the agent answers                                     |
|Local Date                              |Date/time                |Local date/time (based on selected UTC Offset)                                           |
|UTC Date                                |Date/time                |UTC  date/time                                                                           |

### Cloud Call Queue Agent Timeline report

#### fAgentTimelineAnalytics table field description

|Name                                    |Data Type                |Description                                                                              |
|:---------------------------------------|:------------------------|:----------------------------------------------------------------------------------------|
|Agent Name                              |Text                     |User UPN<br>If the full username is **user@microsoft.com**, then this value is: **user** |
|AgentTimelineAnalyticsSummaryLink       |Text                     |Used to link with fAgentTimelineAnalyticsSummary for the pop-up tooltip                  |
|Call Duration (HH:MM:SS)                |Text                     |Call Duration (Minutes) converted to HH:MM:SS                                            |
|Call Duration (Minutes)                 |Whole number             |Summarize: Sum<br>Total call duration of answered Call queue calls in minutes            |
|Call Duration (Second)                  |Whole number             |Summarize: Sum<br>Total call duration of answered Call queue calls in seconds            |
|Call End Time Local                     |Date/time                |Call end time - Local (based on selected UTC Offset)                                     |
|Call End Time UTC                       |Date/time                |Call end time - UTC                                                                      |
|Call Start Time Local                   |Date/time                |Call start time - Local (based on selected UTC Offset)                                   |
|Call Start Time UTC                     |Date/time                |Call start time - UTC                                                                    |
|ConferenceID                            |Text                     |Used for troubleshooting purposes - provide this information when opening a ticket       |
|CQ Name                                 |Text                     |Name of resource account attached to Call Queue<br><br>If the full Resource Account name is **cq_test@microsoft.com**, then this value is: **cq_test** |
|DateTime                                |DateTime                 |Date of call                                                                             |
|DialogID                                |Text                     |Used for troubleshooting purposes - provide this information when opening a ticket       |
|DocumentID                              |Text                     |Used for troubleshooting purposes - provide this information when opening a ticket       |
|Hour (Measure)                          |Whole number             |Hour of call                                                                             |
|Total Call Count                        |Whole number             |Summarize: Sum<br>Number of calls presented to agent                                     |

#### fAgentTimelineAnalyticsSummary table field description

|Name                                    |Data Type                |Description                                                                              |
|:---------------------------------------|:------------------------|:----------------------------------------------------------------------------------------|
|Agent Name                              |Text                     |User UPN<br>If the full username is **user@microsoft.com**, then this value is: **user** |
|AgentTimelineAnalyticsLink              |Text                     |Used to link with fAgentTimelineAnalytics for the pop-up tooltip                         |
|Average Call Duration (Seconds)         |Decimal number           |Summarize: Sum<br>The average duration of answered Call queue calls in seconds           |
|Average Call Duration (Seconds) - zero instead of blank (Measure) | Whole number | Average Call Duration (Seconds) - zero instead of blank                  |
|CQ Name                                 |Text                     |Name of resource account attached to Call Queue<br><br>If the full Resource Account name is **cq_test@microsoft.com**, then this value is: **cq_test** |
|Date                                    |Date                     |Date of call                                                                             |
|Hour                                    |Whole number             |Hour of call                                                                             |
|MM-DD                                   |Text                     |Month and day of call                                                                    |
|Total Call Count                        |Whole number             |Summarize: Sum<br>Number of calls presented to agent                                     |
|Total Call Count divided by Count of Agent Name (Measure |Whole number| Average call count per agent                                                        |
|Total Call Count Sum (Measure)          |Whole number             |Sum of Total Call Count - zero instead of blank                                          |
|Total Call Duration (HH:MM:SS)          |Text                     |Call Duration (Minutes) converted to HH:MM:SS                                            |
|Total Call Duration (Minutes)           |Whole number             |Summarize: Sum<br>Total call duration of answered Call queue calls in minutes            |

## Data Limits

Each report tab retrieves data for all Auto attendants, Call queues, or agents the user is authorized for in the tenant for the selected date range. This data retrieval occurs regardless of the specific Resource Accounts or Agent selected on the report. Filtering to show only the requested information occurs locally. 

**Each report tab is restricted to retrieving 90,000 rows.**

If there's a large number of calls being processed each day, it's possible that the report won't show all calls for all days within the selected date range. There's no notification when this exclusion occurs. Try shortening the date range to avoid this issue.

If shortening the date range isn't sufficient, it's possible to increase the number of rows that can be retrieved by modifying the report as follows:

1. Select **Transform data** in the ribbon bar to open the Power Query Editor.
1. Select **LimitResultRowsCount** on the left-hand side.
1. Change the value in the field to the right to a larger number.
1. Close the Power Query Editor window.
1. Select **Yes** when prompted to apply the changes now. The report should automatically refresh.
1. Save your report.

**The maximum number of rows that can be returned is 200,000.**

Setting the value to a number higher than 200,000 has no effect as this value is a hard-coded limit on the server.

Increasing the limit results in longer execution and response times.

## Report Execution Time Limits

Increasing the maximum number of rows that can be returned results in longer execution and response times meaning the report might time out before the data can be returned.  The report execution time can be increased by modifying the report as follows:

1. Select on the **Transform data** in the ribbon bar to open the Power Query Editor.
1. Select on **ReportExecutionMinutes** on the left-hand side.
1. Change the value in the field to the right to a larger number.
1. Close the Power Query Editor window.
1. Select **Yes** when prompted to apply the changes now. The report should automatically refresh.
1. Save your report.

## Customization

You can customize certain visualization aspects of the reports, such as adding or removing fields to be shown in the various visualizations, changing chart type, and more.

### Change color schema

The following steps assume you already completed the installation steps.

Perform the following steps:

1. Select **View tab** on the ribbon.

   :::image type="content" source="media/aa-cq-historical-report-04.png" alt-text="Screenshot selecting view tab to change color scheme.":::

2. Select the color schema from the drop-down list.

   :::image type="content" source="media/aa-cq-historical-report-05.png" alt-text="Screenshot showing various color schemes.":::
  
## Dimensions and measurements

The following dimensions and measurements are available to be used.

### Common dimensions

These dimensions are common to both Auto attendants and Call queues:

|Name (Type)                                            |Possible Values                |Description                                                       |
|:------------------------------------------------------|:------------------------------|:-----------------------------------------------------------------|
|ConferenceId<br>(Text)                                 |GUID                           |Call identifier                                                   |
|Date<br>(DateTime)                                     |                               |Date of call (UTC)                                                |
|DialogId<br>(Text)                                     |GUID                           |Call identifier                                                   |
|DocumentId<br>(Text)                                   |GUID                           |Call identifier                                                   |
|Duration<br>(Whole Number)                             |                               |Duration of call, in seconds                                      |
|EndTime<br>(DateTime)                                  |                               |Time call ended (UTC)                                             |
|FirstIsCaller<br>(Boolean)                             |                               |[First and Second endpoint classification](dimensions-and-measures-available-in-call-quality-dashboard.md)     |
|FirstUPN<br>(Text)                                     |                               |The user principal name (UPN) of the first endpoint's user        |
|Hour<br>(Text)                                         |                               |Hour call started (UTC)                                           |
|Minute<br>(Text)                                       |                               |Minute call started (UTC)                                         |
|PSTNCallDuration<br>(Whole Number)                     |                               |Duration of the call                                              |
|PSTNCallType<br>(Text)                                 |                               |                                                                  |
|                                                       |External                       |Call is coming from outside the tenant                            |
|                                                       |Internal                       |Call is coming from within the tenant                             |
|PSTNConnectivityType<br>(Text)                         |                               |                                                                  |
|                                                       |CallingPlan                    |The call arrived on a Calling Plan number                         |
|                                                       |DirectRouting                  |The call arrived on a Direct Routing number                       |
|                                                       |ACS Call                       |The call arrived from the web (click2call)                        |
|Second<br>(Text)                                       |                               |Second call started (UTC)                                         |
|SecondUPN<br>(Text)                                    |                               |The user principal name (UPN) of the second endpoint's user       |
|TenantId<br>(Text)                                     |                               |Tenant ID                                                         |
|Timestamp<br>(DateTime)                                |                               |Time record was written (UTC)                                     |
|UserStartTimeUTC<br>(DateTime)                         |                               |Time call started (UTC)                                           |

### Auto attendant dimensions

|Name (Type)                                            |Possible Values                |Description                                                       |
|:------------------------------------------------------|:------------------------------|:-----------------------------------------------------------------|
|AutoAttendantCallFlow<br>(Text)                        |                               |Encapsulates the different states of Auto Attendant call          |
|                                                       |abs_search                     |A dial-by-name search occurred                                    |
|                                                       |announcement                   |An announcement was played                                        |
|                                                       |automatic_menu                 |Default call routing                                              |
|                                                       |call_termination               |Call was ended, see AutoAttendantCallResult                       |
|                                                       |call_transfer                  |Call was transferred, see AutoAttendantCallResult                 |
|                                                       |first_level_menu               |Transition state - can be ignored                                 |
|                                                       |main_menu                      |Greeting message was played                                       |
|                                                       |speech_input_confirmation      |Caller used voice input                                           |
|                                                       |user_selection                 |Caller used touch tone key entry                                  |
|AutoAttendantCallResult<br>(Text)                      |                               |Final call result                                                 |
|                                                       |failed_to_establish_media      |The media portion of the call couldn't be established             |
|                                                       |failover_to_operator           |Call transferred to operator typically due to a system error      |
|                                                       |oaa_chain_too_long             |Too many legs in the AA                                           |
|                                                       |oaa_session_too_long           |AA session lasted too long                                        |
|                                                       |service_declined               |AA didn't accept the call                                         |
|                                                       |service_terminated             |AA configuration disconnects the call or call hung up             |
|                                                       |terminated_automatic_selection |AA configuration disconnects the calls                            |
|                                                       |terminated_no_operator         |All terminated due to error no operator defined                   |
|                                                       |terminated_transfer_failed     |Call terminated as transfer failed - typically to external number |
|                                                       |transfer_in_progress           |AA->AA transfer                                                   |
|                                                       |transferred_to_operator        |Call was transferred to operator                                  |
|                                                       |transferred_to_cq              |Call was transferred to Call queue                                |
|                                                       |transferred_to_receptionist    |Same as transferred_to_operator                                   |
|                                                       |transferred_to_self            |Call was returned to the start of the AA                          |
|                                                       |transferred_to_shared_voicemail |Call was transferred to shared voicemail                         |
|                                                       |transferred_to_user            |Call was transferred to a user                                    |
|                                                       |unknown                        |An unknown condition occurred                                     |
|                                                       |user_terminated                |Caller hung up                                                    |
|AutoAttendantCallerActionCounts<br>(Whole Number)      |                               |The number of actions (touch tone key or voice entries) the caller performed |
|AutoAttendantChainDurationInSecs<br>(Real Number)      |                               |The number of seconds the call remained in this portion of the call flow     |
|AutoAttendantChainIndex<br>(Whole Number)              |                               |                                                                  |
|AutoAttendantChainStartTime<br>(DateTime)              |                               |The start time of this portion of the call flow                   |
|AutoAttendantCount<br>(Whole Number)                   |                               |How many auto attendants the call transitioned through            |
|AutoAttendantDirectorySearchMethod<br>(Text)           |                               |Directory search method                                           |
|                                                       |abs_search_dtmf                |Touch tone                                                        |
|                                                       |abs_search_voice               |Voice                                                             |
|AutoAttendantId<br>(Text)                              |                               |Auto Attendant GUID                                               |
|AutoAttendantIdentity<br>(Text)                        |                               |Resource account URI the call arrived on                          |
|AutoAttendantTransferAction<br>(Text)                  |                               |Call transfer target type                                         |
|                                                       |AA                             |Transferred to an AA                                              |
|                                                       |CQ                             |Transferred to a CQ                                               |
|                                                       |external_pstn                  |Transferred to an external number                                 |
|                                                       |shared voicemail               |Transferred to shared voicemail                                   |
|                                                       |Unknown                        |Unknown action                                                    |
|HasAA<br>(Boolean)                                     |                               |Is AA involved in call                                            |

### Call queue dimensions

| Name (Type)                                | Possible Values         | Description                                |
|:-------------------------------------------|:------------------------|:-------------------------------------------|
| CallQueueAgentCount<br>(Whole Number)      |                         | Number of agents in Call queue             |
| CallQueueAgentOptInCount<br>(Whole Number) |                         | Number of agents opted-in to Call queue    |
| CallQueueCallResult<br>(Text)              |                         | Call queue call final state                |
|                                            | agent_joined_conference | Call answered - conference mode CQ         |
|                                            | callback_call_timed_out | Call back call timed out                   |
|                                            | declined                |                                            |
|                                            | disconnected            |                                            |
|                                            | error                   |                                            |
|                                            | failed                  |                                            |
|                                            | invalid                 |                                            |
|                                            | overflown               | Overflow condition met                     |
|                                            | timed_out               | Timeout condition met                      |
|                                            | no_agent                | No Agent condition met                     |
|                                            | transferred_to_agent    | Call answered - transfer mode CQ           |
|                                            | transferred_to_callback_caller | Callback call answered by agent     |
| CallQueueDurationSeconds<br>(Real Number)  |                         | Call duration in the Call queue            |
| CallQueueFinalStateAction<br>(Text)        |                         | Call queue final action                    |
|                                            | disconnect              | time_out calls                             |
|                                            | disconnect_with_busy    | overflown calls                            |
|                                            | failed_to_accept_call   | Call queue couldn't accept the call       |
|                                            | forward                 | Call was forwarded to a Person in the organization or externally |
|                                            | shared_voicemail        | Call was sent to shared voicemail          |
|                                            | other                   | Some other condition occurred              |
|                                            | voicemail               | Call was sent to personal voicemail        |
| CallQueueId<br>(Text)                      |                         | Call queue GUID                            |
| CallQueueIdentity<br>(Text)                |                         | Resource account URI the call arrived on   |
| CallQueueTargetType<br>(Text)              |                         | Call redirection target                    |
|                                            | ApplicationEndpoint     | Another voice applications                 |
|                                            | Mailbox                 | Shared voicemail                           |
|                                            | Other                   | Some other condition occurred              |
|                                            | Phone                   | External transfer                          |
|                                            | User                    | User in the tenant                         |
| HasCQ<br>(Boolean)                         |                         | Is CQ involved in call                     |
| TransferredFromCQId<br>(Text)              |                         | Call queue GUID call was transferred from  |
| TransferredFromCallQueueIdentity<br>(Text) |                         | Resource account URI the call was transferred from |

### Measurements

|Name (Type)                                            |Possible Values                |Description                                                       |
|:------------------------------------------------------|:------------------------------|:-----------------------------------------------------------------|
|AvgAutoAttendantChainDurationSeconds<br>(Real Number)  |                               |The average call duration within each portion of the auto attendant call flow |
|AvgCallDuration<br>(Real Number)                       |                               |The average call duration in seconds                              |
|AvgCallQueueDurationSeconds<br>(Real Number)           |                               |The average call queue duration in seconds                        |
|PSTNTotalMinutes<br>(Real Number)                      |                               |Total call duration in minutes                                    |
|TotalAudioStreamDuration<br>(Real Number)              |                               |                                                                  |
|TotalCallCount<br>(Whole Number)                       |                               |Total number of calls                                             |

### Constructing a valid query

A valid query consists of several attributes in a JSON object:

```json
{
   "Filters":[
      {
         "DataModelName":"Date",
         "Value":"2022-04-01",
         "Operand":4
      },
      {
         "DataModelName":"Date",
         "Value":"2022-04-30",
         "Operand":6
      }
   ],
   "Dimensions":[
      {
         "DataModelName":"AutoAttendantIdentity"
      },
      {
         "DataModelName":"AutoAttendantDirectorySearchMethod"
      }
   ],
   "Measurements":[
      {
         "DataModelName":"PSTNTotalMinutes"
      },
      {
         "DataModelName":"TotalCallCount"
      }
   ],
   "Parameters":{
      "UserAgent":"Power BI Desktop"
   },
   "LimitResultRowsCount":100000
}
```

#### Required fields

- **Filters**: used to filter data returned by VAAC
  - DataModelName should be one of the supported dimensions
  - Value should be in the correct format (datetime, string, number etc.)
  - *Operands*:
    - 0 - Equals
    - 1 - Not Equals
    - 2 - Contains
    - 3 - Begins With
    - 4 - Greater Than
    - 5 - Greater Than or Equal To
    - 6 - Less Than
    - 7 - Less Than or Equal To
    - 8 - Does Not Contain
    - 9 - Does Not Begin With

- **Dimensions**:
  - DataModelName should be one of the supported dimensions

- **Measurements**:
  - DataModelName should be one of the supported measurements

- **Parameters**: Currently only UserAgent is supported.

- **LimitResultRowsCount**: the max count of rows returned by VAAC

## Accessing VAAC outside of Power BI

Any application that can access RESTful web services can use the VAAC API to retrieve historical data. In the following example, [Postman](https://www.postman.com/) is used.
  
### Preparation

1. Download [Postman](https://www.postman.com/).
1. Import the folder `postman` in the [downloaded zip file](#v3xx-desktop-installation) instructions into Postman.

:::image type="content" source="media/aa-cq-historical-report-postman-01.png" alt-text="Screenshot showing import completed" lightbox="media/aa-cq-historical-report-postman-01.png":::

### Accessing VAAC using Postman

1. Select **VAAC - msit** on the top right ***No Environment*** drop-down.
2. Select **Environments** on the left hand rail menu.
3. Select **VAAC - msit** under **Globals**.
4. Replace **userName**, **password**, and **tenantId** with the applicable credentials.
5. Select **Reset All** in the top right corner.
6. Select **Save**.

   :::image type="content" source="media/aa-cq-historical-report-postman-02.png" alt-text="Screenshot showing username, password and tenant ID fields configured" lightbox="media/aa-cq-historical-report-postman-02.png":::

7. Select **Collections** on the left hand rail menu.
8. Select **Config API Access Token - Prod** and navigate to the **Body** tab.
9. Select **Send**.

   An access token is returned.

   :::image type="content" source="media/aa-cq-historical-report-postman-03.png" alt-text="Screenshot showing result with access token returned." lightbox="media/aa-cq-historical-report-postman-03.png":::

   If an access token isn't returned, check your credentials to make they have [sufficient permissions](#access-permissions).

10. Select **VAAC ConfigAPI Prod** and navigate to the **Params** tab.

    - [Compress](#compress-the-json-query) the query as outlined
    - [URL encode](#url-encode-the-compressed-json-query) the compressed result as outlined

11. Fill in your [query](#constructing-a-valid-query) string.
12. Select **Send**.

### Reading the result

After you submit your input, there are a couple of possible results:

- If the input is invalid, an error message with the actual reason is returned
- If the input is valid, the result looks like this:

   :::image type="content" source="media/aa-cq-historical-report-postman-04.png" alt-text="Screenshot showing query result with dataResult field" lightbox="media/aa-cq-historical-report-postman-04.png":::

   In this case, the data is in the "dataResult" field in the same order requested in the query dimension and measurements attributes.

### Compress the JSON query

The VAAC API only accepts GZip-compressed or Base64-encoded strings as input.

Find any website to compress the JSON blob using GZIP or Base64.

- [GZIP](https://www.multiutil.com/text-to-gzip-compress/)
- [Base64](https://www.multiutil.com/text-to-base64-converter/)

GZIP output should look like this:

```console
H4sIAAAAAAAACq2SQWsCMRCF7/6KkLNC3EoPe9u6FISuFbW9lB4GM9TQbEaSCSLif+9mV4uCBwXnMkze5L0vkH1PCCFfjWX0QeZfaWxqf+xJLIGhIo12CjXKPM0o+2cLn2BjEjKVZQM1Gqjhhfy+QQ9Oy3x0PDz0H5HypK6nPJ9SUv9uV2RpanTBkLvxiUVkKpjRaXA80ejY8E7eg3/hUBqPKya/WyD41bpCXpP+tzvjrBBC9NjA8o2ks8VyuiQGWxkXGcNdkO3FMVg7puj4GtAMfLPa/Y2Tk/wI6IufhjHl0xa9eJmIEsMv06Y16cLlm6kNzzFEy3Pahi4kH6pUvcMfrAhUU3oCAAA=
```

Base64 output should look like this:

```console
ew==
IkZpbHRlcnMiOls=
ew==
IkRhdGFNb2RlbE5hbWUiOiJEYXRlIiw=
IlZhbHVlIjoiMjAyMi0wNC0wMSIs
Ik9wZXJhbmQiOjQ=
fSw=
ew==
IkRhdGFNb2RlbE5hbWUiOiJEYXRlIiw=
IlZhbHVlIjoiMjAyMi0wNC0zMCIs
Ik9wZXJhbmQiOjY=
fQ==
XSw=
IkRpbWVuc2lvbnMiOls=
ew==
IkRhdGFNb2RlbE5hbWUiOiJBdXRvQXR0ZW5kYW50SWRlbnRpdHki
fSw=
ew==
IkRhdGFNb2RlbE5hbWUiOiJBdXRvQXR0ZW5kYW50RGlyZWN0b3J5U2VhcmNoTWV0aG9kIg==
fQ==
XSw=
Ik1lYXN1cmVtZW50cyI6Ww==
ew==
IkRhdGFNb2RlbE5hbWUiOiJQU1ROVG90YWxNaW51dGVzIg==
fSw=
ew==
IkRhdGFNb2RlbE5hbWUiOiJUb3RhbENhbGxDb3VudCI=
fQ==
XSw=
IlBhcmFtZXRlcnMiOns=
IlVzZXJBZ2VudCI6IlBvd2VyIEJJIERlc2t0b3Ai
fSw=
IkxpbWl0UmVzdWx0Um93c0NvdW50IjoxMDAwMDA=
fQ==
```

### URL-Encode the compressed JSON query

The GZIP or Base64 compressed JSON query must be [URL encoded](https://meyerweb.com/eric/tools/dencoder/).

GZIP URL encoded output looks like this:

```console
H4sIAAAAAAAACq2SQWsCMRCF7%2F6KkLNC3EoPe9u6FISuFbW9lB4GM9TQbEaSCSLif%2B9mV4uCBwXnMkze5L0vkH1PCCFfjWX0QeZfaWxqf%2BxJLIGhIo12CjXKPM0o%2B2cLn2BjEjKVZQM1Gqjhhfy%2BQQ9Oy3x0PDz0H5HypK6nPJ9SUv9uV2RpanTBkLvxiUVkKpjRaXA80ejY8E7eg3%2FhUBqPKya%2FWyD41bpCXpP%2BtzvjrBBC9NjA8o2ks8VyuiQGWxkXGcNdkO3FMVg7puj4GtAMfLPa%2FY2Tk%2FwI6IufhjHl0xa9eJmIEsMv06Y16cLlm6kNzzFEy3Pahi4kH6pUvcMfrAhUU3oCAAA%3D
```

Base64 URL encoded output looks like this:

```console
%0Aew%3D%3D%0AIkZpbHRlcnMiOls%3D%0Aew%3D%3D%0AIkRhdGFNb2RlbE5hbWUiOiJEYXRlIiw%3D%0AIlZhbHVlIjoiMjAyMi0wNC0wMSIs%0AIk9wZXJhbmQiOjQ%3D%0AfSw%3D%0Aew%3D%3D%0AIkRhdGFNb2RlbE5hbWUiOiJEYXRlIiw%3D%0AIlZhbHVlIjoiMjAyMi0wNC0zMCIs%0AIk9wZXJhbmQiOjY%3D%0AfQ%3D%3D%0AXSw%3D%0AIkRpbWVuc2lvbnMiOls%3D%0Aew%3D%3D%0AIkRhdGFNb2RlbE5hbWUiOiJBdXRvQXR0ZW5kYW50SWRlbnRpdHki%0AfSw%3D%0Aew%3D%3D%0AIkRhdGFNb2RlbE5hbWUiOiJBdXRvQXR0ZW5kYW50RGlyZWN0b3J5U2VhcmNoTWV0aG9kIg%3D%3D%0AfQ%3D%3D%0AXSw%3D%0AIk1lYXN1cmVtZW50cyI6Ww%3D%3D%0Aew%3D%3D%0AIkRhdGFNb2RlbE5hbWUiOiJQU1ROVG90YWxNaW51dGVzIg%3D%3D%0AfSw%3D%0Aew%3D%3D%0AIkRhdGFNb2RlbE5hbWUiOiJUb3RhbENhbGxDb3VudCI%3D%0AfQ%3D%3D%0AXSw%3D%0AIlBhcmFtZXRlcnMiOns%3D%0AIlVzZXJBZ2VudCI6IlBvd2VyIEJJIERlc2t0b3Ai%0AfSw%3D%0AIkxpbWl0UmVzdWx0Um93c0NvdW50IjoxMDAwMDA%3D%0AfQ%3D%3D
```

> [!IMPORTANT]
> The VAAC API is limited to returning a maximum of 200,000 rows per query.
>
> Requests into the system are throttled based on the IP address making the call, the recognized tenant identity in the auth header, as well as the calling service in order to prevent a single client, tenant, or service from monopolizing the resources.

## Version 3.x.x history and support status

Refer to: Teams Auto Attendant & Call Queue Historical Reports - Change Log.docx in the downloaded zip file for a detailed list of changes.

|Version  |Date Published     |Supported |Filename                                                    |Description                                                             |
|:--------|:------------------|:---------|:-----------------------------------------------------------|:-----------------------------------------------------------------------|
|3.1.8    |August 12, 2024    |Yes       |Teams Auto Attendant & Call Queue Historical Reports V3.1.7 |Bug fix for Date slicer on Call Queue tab                               |
|3.1.7    |July 15, 2024      |No        |Teams Auto Attendant & Call Queue Historical Reports V3.1.7 |Improved support for authorized users, removed original reporting templates |
|3.1.6    |April 15, 2024     |No        |Teams Auto Attendant & Call Queue Historical Reports V3.1.6 |Support click2call, callback, authorized users, and some visuals changed due to deprecation |
|3.1.5    |January 29, 2024   |No        |Teams Auto Attendant & Call Queue Historical Reports V3.1.5 |Corrected an error with the Per Day query logic for fAgentTimelineAnalytics and fAgentTimelineAnalyticsSummary  |
|3.1.4    |January 24, 2024   |No        |Teams Auto Attendant & Call Queue Historical Reports V3.1.4 |Per day reporting for large volume customers, accessibility improvements for screen readers   |

## Related articles
- [Auto attendant and Call queue real-time metrics](aa-cq-real-time-reports.md)
- [Plan for authorized users](aa-cq-authorized-users-plan.md)
- [Manage the Queues app](manage-queues-app.md)

