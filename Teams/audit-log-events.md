---
title: Search the audit log for events in Microsoft Teams
author: markjjo
ms.author: markjjo
manager: laurawi
ms.topic: article
audience: admin
ms.service: msteams
ms.collection: 
  - M365-collaboration
f1.keywords:
- NOCSH
ms.reviewer: anwara
search.appverid: MET150
description: "Learn how to retrieve Microsoft Teams data from the audit log in the Microsoft 365 compliance center."
appliesto: 
  - Microsoft Teams
---

# Search the audit log for events in Microsoft Teams

> [!IMPORTANT]
> [!INCLUDE [new-teams-sfb-admin-center-notice](includes/new-teams-sfb-admin-center-notice.md)]

The audit log can help you investigate specific activities across Microsoft 365 services. For Microsoft Teams, here are some of the activities that are audited:

- Team creation
- Team deletion
- Added channel
- Changed setting

For a complete list of Teams activities that are audited, see [Teams activities](#teams-activities) and [Shifts in Teams activities (in preview)](#shifts-in-teams-activities).

> [!NOTE]
> Audit events from private channels are also logged as they are for teams and standard channels.

## Turn on auditing in Teams

Before you can look at audit data, you have to first turn on auditing in the [Security & Compliance Center](https://protection.office.com). For help with turning on auditing, read [Turn audit log search on or off](https://support.office.com/article/Turn-Office-365-audit-log-search-on-or-off-e893b19a-660c-41f2-9074-d3631c95a014).

> [!IMPORTANT]
> Audit data is only available from the point at which you turned on auditing.

## Retrieve Teams data from the audit log

1. To retrieve audit logs, go to the [Security & Compliance Center](https://go.microsoft.com/fwlink/?linkid=855775). Under **Search**, select **Audit log search**.

2. Use **Search** to filter by the activities, dates, and users you want to audit.

3. Export your results to Excel for further analysis.

> [!IMPORTANT]
> Audit data is only visible in the audit log if auditing is turned on.

The length of time that an audit record is retained and searchable in the audit log depends on your Microsoft 365 or Office 365 subscription, and specifically the type of license that's assigned to users. To learn more, see the [Security & Compliance Center service description](/office365/servicedescriptions/office-365-platform-service-description/office-365-securitycompliance-center).

## Tips for searching the audit log

Here are tips for searching for Teams activities in the audit log.

![Screenshot of audit log search page](media/audit-log-search-page.png)

- You can select specific activities to search for by clicking the activity name. Or you can search for all activities in a group (such as **File and folder activities**) by clicking the group name. If an activity is selected, you can click it to cancel the selection. You can also use the search box to display the activities that contain the keyword that you type.

  ![Screenshot of audit log search](media/audit-log-search.png)

- To display events for activities run using cmdlets, select **Show results for all activities** in the **Activities** list. If you know the name of the operation for these activities, search for all activities, and then filter the results by typing the name of the operation in the box in the **Activity** column. To learn more, see [Step 3: Filter the search results](/microsoft-365/compliance/search-the-audit-log-in-security-and-compliance?view=o365-worldwide#step-3-filter-the-search-results).

- To clear the current search criteria, click **Clear**. The date range returns to the default of the last seven days. You can also click **Clear all to show results for all activities** to cancel all selected activities.

- If 5,000 results are found, you can probably assume that there are more than 5,000 events that met the search criteria. You can refine the search criteria and rerun the search to return fewer results, or you can export all the search results by selecting **Export results** > **Download all results**.

Check out [this video](https://www.youtube.com/embed/UBxaRySAxyE) for using audio log search. Join Ansuman Acharya, a program manager for Teams, as he demonstrates how to do an audit log search for Teams.

## Use Cloud App Security to set activity policies

Using [Microsoft Cloud App Security](/cloud-app-security/what-is-cloud-app-security) integration, you can set [activity policies](/cloud-app-security/user-activity-policies) to enforce a wide range of automated processes using the app provider's APIs. These policies enable you to monitor specific activities carried out by various users, or follow unexpectedly high rates of one certain type of activity.

After you set an activity detection policy, it starts to generate alerts. Alerts are only generated on activities that occur after you create the policy. Here's some example scenarios for how you can use activity policies in Cloud App Security to monitor Teams activities.

### External user scenario

One scenario you might want to keep an eye on, from a business perspective, is the addition of external users to your Teams environment. If external users are enabled, monitoring their presence is a good idea.  You can use [Cloud App Security](/cloud-app-security/what-is-cloud-app-security) to identify potential threats.

![Screenshot of a list of events triggered by mass deletions](media/TeamsExternalUserAddPolicy.png)

The screenshot of this policy to monitor adding external users allows you to name the policy, set the severity according to your business needs, set it as (in this case) a single activity, and then establish the parameters that will specifically monitor only the addition of non-internal users, and limit this activity to Teams.

The results from this policy can be viewed in the activity log:

![Screenshot of a list of events triggered by mass deletions](media/TeamsExternalUserList.png)

Here you can review matches to the policy you've set, and make any adjustments as needed, or export the results to use elsewhere.

### Mass delete scenario

As mentioned earlier, you can monitor deletion scenarios. It's possible to create a policy that would monitor mass deletion of Teams sites. In this example, an alert-based policy is set up to detect mass deletion of teams in a span of 30 minutes.

![Screenshot of the policy create page showing the setting up of a policy for mass team deletion detection](media/TeamsMassDeletePolicy.png)

As the screenshot shows, you can set many different parameters for this policy to monitor Teams deletions, including severity, single or repeated action, and parameters limiting this to Teams and site deletion. This can be done independently of a template, or you may have a template created to base this policy on, depending on your organizational needs.

After you establish a policy that works for your business, you can review the results in the activity log as events are triggered:

![Screenshot of a list of events triggered by mass deletions](media/TeamsMassDeleteList.png)

You can filter down to the policy you've set to see the results of that policy. If the results you're getting in the activity log are not satisfactory (maybe you're seeing lots of results, or nothing at all), this may help you to fine-tune the query to make it more relevant to what you need it to do.

### Alert and governance scenario

You can set alerts and send emails to admins and other users when an activity policy is triggered. You can set automated governance actions such as suspending a user or making a user to sign in again in an automated way. This example shows how a user account can be suspended when an activity policy is triggered and determines a user deleted two or more teams in 30 minutes.

![Screenshot of alerts and governance actions for an activity policy](media/audit-log-governance.png)

## Use Cloud App Security to set anomaly detection policies

[Anomaly detection policies](/cloud-app-security/anomaly-detection-policy) in Cloud App Security provide out-of-the-box user and entity behavioral analytics (UEBA) and machine learning (ML) so that you can immediately run advanced threat detection across your cloud environment. Because they're automatically enabled, the new anomaly detection policies provide immediate results by providing immediate detections, targeting numerous behavioral anomalies across your users and the machines and devices connected to your network. Additionally, the new policies expose more data from the Cloud App Security detection engine, to help you speed up the investigation process and contain ongoing threats.

We're working to integrate Teams events into anomaly detection policies. For now, you can set up anomaly detection policies for other Office products and take action items on users who match those policies.

## Teams activities

Here's a list of all events that are logged for user and admin activities in Teams in the Microsoft 365 audit log. The table includes the friendly name that's displayed in the **Activities** column and the name of the corresponding operation that appears in the detailed information of an audit record and in the CSV file when you export the search results.

|Friendly name  |Operation|Description |
|---------|---------|---------|
|Added bot to team   |BotAddedToTeam        |A user adds a bot to a team.        |
|Added channel   |ChannelAdded         |A user adds a channel to a team.         |
|Added connector  |ConnectorAdded          |A user adds a connector to a channel.        |
|Added members    |MemberAdded         |A team owner adds members to a team, channel, or group chat.         |
|Added tab    |TabAdded         |A user adds a tab to a channel.        |
|Changed channel setting    |ChannelSettingChanged         |The ChannelSettingChanged operation is logged when the following activities are performed by a team member. For each of these activities, a description of the setting that was changed (shown in parentheses is displayed in the **Item** column in the audit log search results. <ul><li>Changes name of a team channel (**Channel name**)</li><li>Changes description of a team channel (**Channel description**)</li> </ul>      |
|Changed organization setting   |TeamsTenantSettingChanged         |The TeamsTenantSettingChanged operation is logged when the following activities are performed by a global admin in the Microsoft 365 admin center. These activities affect org-wide Teams settings. To learn more, see [Manage Teams settings for your organization](enable-features-office-365.md). <br>For each of these activities, a description of the setting that was changed (shown in parentheses) is displayed in the **Item** column in the audit log search results.<ul><li>Enables or disables Teams for the organization (**Microsoft Teams**).</li><li>Enables or disables interoperability between Microsoft Teams and Skype for Business for the organization (**Skype for Business interoperability**).</li><li>Enables or disables the organizational chart view in Microsoft Teams clients (**Org chart view**).</li><li>Enables or disables the ability for team members to schedule private meetings (**Private meeting scheduling**).</li><li>Enables or disables the ability for team members to schedule channel meetings (**Channel meeting scheduling**).</li><li>Enables or disables video calling in Teams meetings (**Video for Skype meetings**).</li><li>Enables or disables screen sharing in Microsoft Teams meetups for the organization (**Screen sharing for Skype meetings**).</li><li>Enables or disables that ability to add animated images (called Giphys) to Teams conversations (**Animated images**).</li><li>Changes the content rating setting for the organization (**Content rating**). The content rating restricts the type of animated image that can be displayed in conversations.</li><li>Enables or disables the ability for team members to add customizable images (called custom memes) from the internet to team conversations (**Customizable images from the Internet**).</li><li>Enables or disables the ability for team members to add editable images (called stickers) to team conversations (**Editable images**).</li><li>Enables or disables that ability for team members to use bots in Microsoft Teams chats and channels (**Org-wide bots)**.</li><li>Enables specific bots for Microsoft Teams. This doesn't include the T-Bot, which is Teams help bot that's available when bots are enabled for the organization (**Individual bots**).</li><li>Enables or disables the ability for team members to add extensions or tabs (**Extensions or tabs**).</li><li>Enables or disables the side-loading of proprietary bots for Microsoft Teams (**Side loading of Bots**).</li><li>Enables or disables the ability for users to send email messages to a Microsoft Teams channel (**Channel email**).</li></ul>|
|Changed role of members in team    |MemberRoleChanged         |A team owner changes the role of members in a team. The following values indicate the role type assigned to the user. <br><br>**1** - Indicates the Member role.<br>**2** -  Indicates the Owner role.<br>**3** -  Indicates the Guest role.<br><br>The Members property also includes the name of your organization and the member's email address.        |
|Changed team setting    |TeamSettingChanged        |The TeamSettingChanged operation is logged when the following activities are performed by a team owner. For each of these activities, a description of the setting that was changed (shown in parentheses) is displayed in the **Item** column in the audit log search results.<ul><li>Changes the access type for a team. Teams can be set as private or public (**Team access type**). When a team is private (the default setting), users can access the team only by invitation. When a team is public, it's discoverable by anyone.</li><li>Changes the information classification of a team (**Team classification**). For example, team data can be classified as high business impact, medium business impact, or low business impact.</li><li>Changes the name of a team (**Team name**).</li><li>Changes the team description (**Team description**).</li><li>Changes made to team settings. To access these settings,  a team owner can right-click a team, select **Manage team**, and then click the **Settings** tab. For these activities, the name of the setting that was changed is displayed in the **Item** column in the audit log search results.</li></ul>         |
|Created team    |TeamCreated         |A user creates a team.         |
|Deleted all organization apps|DeletedAllOrganizationApps           |Deleted all organization apps from the catalog.     |
|Deleted app |AppDeletedFromCatalog           |An app has been deleted from the catalog.     |
|Deleted channel     |ChannelDeleted         |A user deletes a channel from a team.         |
|Deleted team  |TeamDeleted            |A team owner deletes a team.      |
|Installed app |AppInstalled         |An app was installed.   |
|Performed action on card|PerformedCardAction|A user took action on an adaptive card within a chat. Adaptive cards are typically used by bots to allow the rich display of information and interaction in chats. <br/><br/>**Note:** Only inline input actions on an adaptive card inside a chat will be available in the audit log. For example, when a user submits a poll response in a channel conversation on an adaptive card generated by a Poll bot. User actions such as "View result", which will open a dialog, or user actions inside dialogs won't be available in the audit log.|
|Published app |AppPublishedToCatalog           |An app was added to the catalog.     |
|Removed bot from team   |BotRemovedFromTeam         |A user removes a bot from a team.       |
|Removed connector     |ConnectorRemoved         |A user removes a connector from a channel.         |
|Removed members    |MemberRemoved        |A team owner removes members from a team, channel, or group chat.         |
|Removed tab    |TabRemoved         |A user removes a tab from a channel.         |
|Uninstalled app |AppUninstalled           |An app was uninstalled.     |
|Updated app |AppUpdatedInCatalog           |An app was updated in the catalog.     |
|Updated connector    |ConnectorUpdated         |A user modified a connector in a channel.         |
|Updated tab   |TabUpdated         |A user modified a tab in a channel.         |
|Upgraded app |AppUpgraded           |An app was upgraded to its latest version in the catalog.     |
|User signed in to Teams     |TeamsSessionStarted         |A user signs in to a Microsoft Teams client. This event doesn't capture token refresh activities.         |
|Sent a message with a URL link in Teams     |MessageCreatedHasLink         |A user sends a message containing a URL link in Teams.         |
|Edited a message with a URL link in Teams     |MessageEditedHasLink         |A user edits a message and adds a URL link to it in Teams.         |


## Shifts in Teams activities

**(in preview)**

If your organization is using the Shifts app in Teams, you can search the audit log for activities related to the Shifts app. Here's a list of all events that are logged for Shifts activities in Teams in the Microsoft 365 audit log.

|Friendly name  |Operation  |Description  |
|---------|---------|---------|
|Added scheduling group |ScheduleGroupAdded          |A user successfully adds a new scheduling group to the schedule.|
|Edited scheduling group     |ScheduleGroupEdited         |A user successfully edits a scheduling group.          |
|Deleted scheduling group         |ScheduleGroupDeleted              |A user successfully deletes a scheduling group from the schedule.|
|Withdrew schedule |ScheduleWithdrawn              |A user successfully withdraws a published schedule.|
|Added shift      |ShiftAdded          |A user successfully adds a shift.           |
|Edited shift       |ShiftEdited       |A user successfully edits a shift.        |
|Deleted shift          |ShiftDeleted          | A user successfully deletes a shift.               |
|Added time off      |TimeOffAdded          |A user successfully adds time off on the schedule.          |
|Edited time off         |TimeOffEdited           |A user successfully edits time off.          |
|Deleted time off     |TimeOffDeleted              |A user successfully deletes time off.           |
|Added open shift     |OpenShiftAdded          |A user successfully adds an open shift to a scheduling group.          |
|Edited open shift    |OpenShiftEdited          |A user successfully edits an open shift in a scheduling group.          |
|Deleted open shift      |OpenShiftDeleted          |A user successfully deletes an open shift from a scheduling group.         |
|Shared schedule     |ScheduleShared                  |A user successfully shared a team schedule for a date range.          |
|Clocked in using Time clock         |ClockedIn          |A user successfully clocks in using Time clock.          |
|Clocked out using Time clock      |ClockedOut          |A user successfully clocks out using Time clock.          |
|Started break using Time clock      |BreakStarted          |A user successfully starts a break during an active Time clock session.          |
|Ended break using Time clock    |BreakEnded          |A user successfully ends a break during an active Time clock session.          |
|Added Time clock entry     |TimeClockEntryAdded          |A user successfully adds a new manual Time clock entry on Time Sheet.          |
|Edited Time clock entry     | TimeClockEntryEdited             |A user successfully edits a Time clock entry on Time Sheet.          |
|Deleted Time clock entry    |TimeClockEntryDeleted              |A user successfully deletes a Time clock entry on Time Sheet.          |
|Added shift request         |RequestAdded              |A user added a shift request.          |
|Responded to shift request     |RequestRespondedTo                  |A user responded to a shift request.          |
|Canceled shift request         |RequestCancelled               |A user canceled a shift request.          |
|Changed schedule setting      |ScheduleSettingChanged          |A user changes a setting in Shifts settings.         |
|Added workforce integration      |WorkforceIntegrationAdded                  | The Shifts app is integrated with a third-party system.         |
|Accepted off shift message         |OffShiftDialogAccepted          |A user acknowledges the off-shift message to access Teams after shift hours.           |

## Office 365 Management Activity API

You can use the Office 365 Management Activity API to retrieve information about Teams events. To learn more about the  Management Activity API schema for Teams, see [Teams schema](/office/office-365-management-api/office-365-management-activity-api-schema#microsoft-teams-schema).

## Attribution in Teams audit logs

Membership changes to Teams (such as users added or deleted) made through Azure Active Directory (Azure AD), Microsoft 365 admin portal, or Microsoft 365 Groups Graph API will appear in Teams audit messages and in the General channel with an attribution to an existing owner of the team, and not to the actual initiator of the action. In these scenarios, consult Azure AD or [Microsoft 365 Group audit logs](/microsoft-365/compliance/search-the-audit-log-in-security-and-compliance) to see the relevant information.

## Related topics

- [Search the audit log in the Microsoft 365 compliance center](/microsoft-365/compliance/search-the-audit-log-in-security-and-compliance)
