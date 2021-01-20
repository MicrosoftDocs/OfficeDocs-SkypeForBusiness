---
title: "Create a call queue in Microsoft Teams - small business tutorial"
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.reviewer: colongma
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
audience: Admin
appliesto: 
  - Skype for Business
  - Microsoft Teams
localization_priority: Normal
f1.keywords: 
  - CSH
ms.custom: 
  - ms.teamsadmincenter.callqueues.overview"
  - Phone System
description: Learn how to set up call queues with Microsoft 365 Business Voice.
---
# Create a call queue - small business tutorial

Call queues provide a method of routing callers to people in your organization who can help with with a particular issue or question. Calls are distributed one at a time to the people in the queue (who are known as *agents*). 

Call queues provide:

- A greeting message.

- Music while people are waiting on hold in a queue.

- Call routing - in *First In, First Out* (FIFO) order - to agents.

- Handling options for queue overflow and timeout.

#### Before you begin

Get some [Phone System - Virtual User licenses](../teams-add-on-licensing/virtual-user.md) if you don't already have them. Get one for each call queue and auto attendant that you plan to set up. These licenses are free, so we suggest getting a few extra in case you decide to make changes to your setup in the future.

Since agents in a call queue may dial out to return a customer call, consider setting the caller ID for your call agents to your main phone number or the number of an appropriate auto attendant. See [Manage caller ID policies in Microsoft Teams](../caller-id-policies.md) for more information.

<a name="steps"></a>

#### Follow these steps to set up your call queue

# [Step 1<br>Create a team](#tab/create-team)

When creating a call queue, you can add individual users to the queue, or you can use an existing security group, Microsoft 365 group, or Microsoft Teams team. We recommend using a team. This allows members of the queue to chat with each other, share ideas, and create documents or other resources to help them help your customers. A team also provides a voice mailbox for callers to leave a message after hours or if the queue reaches its maximum capacity.

To create a team

1. First, click **Teams** on the left side of the app, then click **Join or create a team** at the bottom of your teams list.

2. Then click **Create team** (first card, top left corner).

3. Choose **Build a team from scratch**.

4. Next, choose whether you want a public or private team. We recommend **Private** for your call queue to avoid people unintentionally becoming part of the queue by joining the team.

5. Name your team and add an optional description.

6. When you're done, click **Create**.

8. Type the names of the people that you want to have in your call queue, and then click **Add**.

9. Click **Close**. People you add to a team will receive an email letting them know they are now a member of your team and the team will show up in their teams list.

> [!div class="nextstepaction"]
> [Step 2 - Resource accounts >](https://review.docs.microsoft.com/microsoftteams/business-voice/create-a-phone-system-call-queue-smb?branch=mikeplum-smb-voice&tabs=resource-account#steps)

# [Step 2<br>Resource accounts](#tab/resource-account)

Each call queue that you create requires a resource account. This is similar to a user account, except the account is associated with an auto attendant or call queue instead of a person. In this step, we'll create the account, assign it a *Microsoft 365 Phone System - Virtual User* license, and then use it to start creating the call queue.

### Create a resource account

You can create a resource account in the Teams admin center.

1. In the Teams admin center, expand **Org-wide settings**, and then click **Resource accounts**.

2. Click **Add**.

3. In the **Add resource account** pane, fill out **Display name**, **Username**, and choose **Call queue** for the **Resource account type**.

    ![Screenshot of add resource account user interface](../media/resource-account-add-cq.png)

4. Click **Save**.

The new account will appear in the list of accounts.

![Screenshot of a list of resource accounts](../media/resource-accounts-page.png)

### Assign a license

You must assign a *Microsoft 365 Phone System - Virtual User* license to the resource account.

1. In the Microsoft 365 admin center, click the resource account to which you want to assign a license.

2. On the **Licenses and Apps** tab, under **Licenses**, select **Microsoft 365 Phone System - Virtual User**.

3. Click **Save changes**.

    ![Screenshot of assign licenses user interface in the Microsoft 365 admin center](../media/resource-account-assign-virtual-user-license.png)

### Create a call queue

Next, we'll start creating a new call queue and assign the resource account.

1. In the Teams admin center, expand **Voice**, click **Call queues**, and then click **Add**.

1. Type a name for the call queue. Agents will see this name when they receive an incoming call from the queue.

2. Click **Add accounts**, search for the resource account that you want to use with this call queue, click **Add**, and then click **Add**.

3. Choose a language. This language will be used for system-generated voice prompts and voicemail transcription (if you enable them).

    ![Screenshot of resource account and language settings](../media/call-queue-name-language.png)

4. Specify if you want to play a greeting to callers when they arrive in the queue. You must upload an MP3, WAV, or WMA file containing the greeting that you want to play.

5. Teams provides default music to callers while they are on hold in a queue. If you want to play a specific audio file, choose **Play an audio file** and upload an MP3, WAV, or WMA file.

> [!NOTE]
> The uploaded recording can be no larger than 5 MB.
> The default music supplied in Teams call queues is free of any royalties payable by your organization. 

> [!div class="nextstepaction"]
> [Step 3 - Call agents >](https://review.docs.microsoft.com/microsoftteams/business-voice/create-a-phone-system-call-queue-smb?branch=mikeplum-smb-voice&tabs=call-agents#steps)

# [Step 3<br>Call agents](#tab/call-agents)

To add agents to the call queue, we'll add the team that we created earlier.

1. Click **Add groups**.
2. Type the name of the team that you created.
3. Click **Add**, and then click **Add**.

    ![Screenshot of users and groups settings for call queues](../media/call-queue-users-groups-smb.png)

You can add up to 20 agents individually and up to 200 agents via groups or teams.

> [!NOTE]
> When new users are added to the team, it can take up to eight hours for their first call to arrive.

> [!div class="nextstepaction"]
> [Step 4 - Resource accounts >](https://review.docs.microsoft.com/microsoftteams/business-voice/create-a-phone-system-call-queue-smb?branch=mikeplum-smb-voice&tabs=call-routing#steps)

# [Step 4<br>Call routing](#tab/call-routing)

Choose the call routing method that you want to use.

1. Set **Conference mode** to **Auto**.

2. Choose the **Routing method** you want to use. This determines the order in which agents receive calls from the queue. We recommend **Serial routing** or  **Round robin**. Choose from these options:

    - **Attendant routing** rings all agents in the queue at the same time. The first call agent to pick up the call gets the call.

    - **Serial routing** rings all call agents one by one. If an agent dismisses or does not pick up a call, the call will ring the next agent and will try all agents until it is picked up or times out.

    - **Round robin** balances the routing of incoming calls so that each call agent gets the same number of calls from the queue. This may be desirable in an inbound sales environment to assure equal opportunity among all the call agents.

    - **Longest idle** routes each call to the agent who has been idle the longest time. (Agents whose presence state has been Away for more than 10 minutes are not included.)

    ![Screenshot of conference mode and routing method settings](../media/call-queue-conference-mode-routing-method.png)

3. Turn **Presence-based routing** on. This routes calls to agents whose presence status is **Available**.

4. Choose if you want to allow agents to opt out of calls.

5. Set an **Agent alert time** to specify how long an agent's phone will ring before the queue redirects the call to the next agent.

    ![Screenshot of routing, opt out, and alert time settings](../media/call-queue-presence-agents-time.png)

> [!div class="nextstepaction"]
> [Step 5 - Call overflow >](https://review.docs.microsoft.com/microsoftteams/business-voice/create-a-phone-system-call-queue-smb?branch=mikeplum-smb-voice&tabs=call-overflow#steps)

# [Step 5<br>Call overflow](#tab/call-overflow)

Choose how you want to handle calls that exceed the maximum in the queue.

1. Set the **Maximum calls in the queue**.

2. Choose what you want to do when the maximum number of calls is reached. You can disconnect the call or redirect it. We recommend that you redirect the call to one of the following destinations:
    - **Person in the organization** - a person in your organization who is able to receive voice calls
    - **Voice app** - an auto attendant or another call queue. (Choose the resource account associated with the auto attendant or call queue when choosing this destination.)
    - **External phone number** - any phone number. Use this format: +[country code][area code][phone number]
    - **Voicemail** - you can use the voice mailbox of the team that you created.

    ![Screenshot of call overflow settings](../media/call-queue-overflow-handling.png)

> [!div class="nextstepaction"]
> [Step 6 - Call timeout >](https://review.docs.microsoft.com/microsoftteams/business-voice/create-a-phone-system-call-queue-smb?branch=mikeplum-smb-voice&tabs=call-timeout#steps)

# [Step 6<br>Call timeout](#tab/call-timeout)

Choose what you want to happen when calls have been waiting in the queue for too long.

1. Set the **Call Timeout: maximum wait time**.

2. Choose what you want to do when a call times out. You can disconnect the call or redirect it. We recommend that you redirect the call to one of the following destinations:
    - **Person in the organization** - a person in your organization who is able to receive voice calls
    - **Voice app** - an auto attendant or another call queue. (Choose the resource account associated with the auto attendant or call queue when choosing this destination.)
    - **External phone number** - any phone number. Use this format: +[country code][area code][phone number]
    - **Voicemail** - you can use the voice mailbox of the team that you created.

    ![Screenshot of call timeout settings](../media/call-queue-timeout-handling.png)

3. Click **Save**.

This completes the setup of your call queue. Next, you may want to [set up an auto attendant](create-a-phone-system-auto-attendant-smb.md).

---

