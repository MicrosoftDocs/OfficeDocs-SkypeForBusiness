---
title: "Unassigned Phone Number"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.lscp.VoiceFeaVacantNumMain
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 24eca749-a9f3-40e7-839b-d21c3ef7d533
ROBOTS: NOINDEX, NOFOLLOW
description: "Unassigned numbers are phone numbers that are valid for your organization but are not assigned to a user or a phone. The unassigned number table identifies how you want calls to unassigned numbers to be treated."
---

# Unassigned Phone Number

> [!NOTE]
> Exchange UM remains available in Skype for Business Server 2019 when you integrate Skype for Business 2019 with Exchange 2013 or Exchange 2016. Due to changes in support in Exchange 2019, Exchange UM integration is being de-emphasised in favor of Cloud Voicemail and Cloud Auto Attendant features.

Unassigned numbers are phone numbers that are valid for your organization but are not assigned to a user or a phone. The unassigned number table identifies how you want calls to unassigned numbers to be treated.

How you configure the unassigned number table depends on how you want to use it. You can configure the table with all the valid extensions for your organization, with only unassigned extensions, or with a combination of both types of numbers. The unassigned number table can include both assigned and unassigned numbers, but it is invoked only when a caller dials a number that is not currently assigned. If you include all the valid extensions in the unassigned number table, you can specify the action that occurs whenever someone leaves your organization, without needing to reconfigure the table. If you include unassigned extensions in the table, you can tailor the action that occurs for specific numbers. For example, if you change the extension for your customer service desk, you can include the old customer service number in the table and assign it to an announcement that provides the new number.

> [!IMPORTANT]
> Before you configure the unassigned number table, you must have already either defined one or more announcements or set up an Exchange UM Auto Attendant.

The **Unassigned Number** page displays a list of the unassigned numbers ranges defined for your organization.

## Tasks you can perform

You can perform the following tasks from the **Unassigned Number** page:

- Create a new unassigned number range

- Change an existing unassigned number range

- Delete an unassigned number range

- Change the order of the unassigned number ranges to determine which action should be applied first to an incoming call that matches an unassigned number.

## UI Reference

The following list describes the commands on the page.

- **New** Starts a new unassigned number range.

- **Edit** Opens the selected unassigned number range for editing, selects all the unassigned number ranges in the list, or deletes the selected unassigned number range.

- **Move up** Moves the selected unassigned number range up in the list so that Skype for Business Server finds it sooner and applies the specified action before applying actions specified for other ranges in the list.

    > [!NOTE]
    > Skype for Business Server searches the unassigned number table from top to bottom and uses the first range that matches the unassigned number. For example, if you have a range that specifies a last resort action, make sure that range is at the bottom of the list.

- **Move down** Moves the selected unassigned number range down in the list.

- **Commit all** Saves all the changes you made to unassigned number ranges.

    > [!IMPORTANT]
    > This command saves all the changes that you made on the **New Unassigned Number** page and the **Edit Unassigned Number** page.

- **Refresh** Refreshes the list of unassigned number ranges.

The following list describes the fields on the page.

- **Name** The unique name that identifies the unassigned number range.

- **State** Shows which number ranges have been saved to the database and which have not.

- **Start range** The beginning number of the unassigned number range.

- **End range** The ending number of the unassigned number range.

- **Destination** The service ID of the Application service that hosts the Announcement application that will handle incoming calls to this range of unassigned numbers.

- **Announcement** The announcement that will be played for this range of unassigned numbers.

For details about Announcement features and capabilities, see [Plan for the Announcement application in Skype for Business](../../../plan-your-deployment/enterprise-voice-solution/announcement.md) in the Planning documentation. For details about working with unassigned number ranges, see [Configure Routing of Unassigned Phone Numbers](https://technet.microsoft.com/library/a0650659-dce7-455f-8977-02454bbfa400.aspx) in the Operations documentation.


