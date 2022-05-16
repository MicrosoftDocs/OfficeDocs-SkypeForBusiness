---
title: Create a call queue in Microsoft Teams Phone System - small business tutorial
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: dobro
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
ms.localizationpriority: medium
f1.keywords: 
  - CSH
ms.custom: 
  - ms.teamsadmincenter.callqueues.overview"
  - Phone System
description: Learn how to set up call queues for small and medium businesses in Microsoft Teams Phone System.
---
# Create a call queue - small and medium business tutorial

Call queues provide a method of routing callers to people in your organization who can help with a particular issue or question. Calls are distributed one at a time to the people in the queue (who are known as *agents*).

Call queues provide:

- A greeting message.

- Music while people are waiting on hold in a queue.

- Call routing - in *First In, First Out* (FIFO) order - to agents.

- Handling options for queue overflow and timeout.

## Video demonstration

This video demonstrates how to create a call queue in Microsoft Teams.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWCF23?autoplay=false]

## Before you begin

Get some [Microsoft Teams Phone Standard - Virtual User licenses](../teams-add-on-licensing/virtual-user.md) if you don't already have them. Get one for each call queue and auto attendant that you plan to set up. These licenses are free, so we suggest getting a few extra in case you decide to make changes to your setup in the future.

Since agents in a call queue may dial out to return a customer call, consider setting the caller ID for your call agents to your main phone number or the number of an appropriate auto attendant. See [Manage caller ID policies in Microsoft Teams](../caller-id-policies.md) for more information.

<a name="steps"></a>

## Follow these steps to set up your call queue

### [Step 1 - Create a team](#tab/create-team)

When creating a call queue, you can add individual users to the queue, or you can use an existing security group, Microsoft 365 group, or Microsoft Teams team. We recommend [using a team channel](https://support.microsoft.com/office/9f07dabe-91c6-4a9b-a545-8ffdddd2504e). This allows members of the queue to chat with each other, share ideas, and create documents or other resources to help them help your customers. A team also provides a voice mailbox for callers to leave a message after hours or if the queue reaches its maximum capacity.

To create a team

1. First, click **Teams** on the left side of the app, then click **Join or create a team** at the bottom of your teams list.

2. Then click **Create team** (first card, top left corner).

3. Choose **Build a team from scratch**.

4. Next, choose whether you want a public or private team. We recommend **Private** for your call queue to avoid people unintentionally becoming part of the queue by joining the team.

5. Name your team and add an optional description.

6. When you're done, click **Create**.

7. Type the names of the people that you want to have in your call queue, and then click **Add**.

8. Click **Close**. People you add to a team will receive an email letting them know they are now a member of your team and the team will show up in their teams list.

Next, we'll add a channel to use with the call queue.

To add a channel

1. In Teams, find the team you just created, click **More options** (...), and then click **Add channel**.

2. Type a name and description for the channel.

3. Under **Privacy**, choose **Standard - Accessible to everyone on the team** and then click **Add**.

> [!div class="nextstepaction"]
> [Step 2 - Resource accounts >](/microsoftteams/business-voice/create-a-phone-system-call-queue-smb?tabs=resource-account#steps)

### [Step 2 - Resource accounts](#tab/resource-account)

Each call queue that you create requires a resource account. This is similar to a user account, except the account is associated with an auto attendant or call queue instead of a person. In this step, we'll create the account, assign it a *Microsoft Teams Phone Standard - Virtual User* license, and then use it to start creating the call queue.

#### Create a resource account

You can create a resource account in the Teams admin center.

1. In the Teams admin center, expand **Voice**, and then click **Resource accounts**.

2. Click **Add**.

3. In the **Add resource account** pane, fill out **Display name**, **Username**, and choose **Call queue** for the **Resource account type**. Agents will see the display name when they receive an incoming call from the queue.

4. Click **Save**.

   The new account will appear in the list of accounts.

#### Assign a license

You must assign a *Microsoft Teams Phone Standard - Virtual User* license to the resource account.

1. In the Microsoft 365 admin center, in the **Active users** list, click the resource account to which you want to assign a license.

2. On the **Licenses and Apps** tab, under **Licenses**, select **Microsoft Teams Phone Standard - Virtual User**.

3. Click **Save changes**.

#### Create a call queue

Next, we'll start creating a new call queue and assign the resource account.

1. In the Teams admin center, expand **Voice**, click **Call queues**, and then click **Add**.

2. Type a name for the call queue.

3. Click **Add accounts**, search for the resource account that you want to use with this call queue, click **Add**, and then click **Add**.

4. (Optional) Under **Assign calling ID**, click **Add**, search for the resource accounts that you created for your auto attendant, click **Add**, and then click **Add**. This will give your call agents the caller ID of your main line when they call out.

5. Choose a language. This language will be used for system-generated voice prompts and voicemail transcription (if you enable them).

6. Specify if you want to play a greeting to callers when they arrive in the queue. You must upload an MP3, WAV, or WMA file containing the greeting that you want to play.

7. Teams provides default music to callers while they are on hold in a queue. If you want to play a specific audio file, choose **Play an audio file** and upload an MP3, WAV, or WMA file.

   > [!NOTE]
   > The uploaded recording can be no larger than 5 MB.
   > The default music supplied in Teams call queues is free of any royalties payable by your organization.

> [!div class="nextstepaction"]
> [Step 3 - Call agents >](/microsoftteams/business-voice/create-a-phone-system-call-queue-smb?tabs=call-agents#steps)

### [Step 3 - Call agents](#tab/call-agents)

To add agents to the call queue, we'll add them to the team and channel that we created earlier. You need to be a member of the team to do this.

1. Select the **Choose a team** option and click **Add a channel**.
2. Type the name of the team that you created, select it, and click **Add**.
3. Select the channel that you created for the queue.
4. Click **Apply**.

> [!NOTE]
> When new users are added to the team, it can take up to eight hours for their first call to arrive.

> [!div class="nextstepaction"]
> [Step 4 - Resource accounts >](/microsoftteams/business-voice/create-a-phone-system-call-queue-smb?tabs=call-routing#steps)

### [Step 4 - Call routing](#tab/call-routing)

Choose the call routing method that you want to use.

1. Set **Conference mode** to **Auto**.

2. Choose the **Routing method** you want to use. This determines the order in which agents receive calls from the queue. We recommend **Serial routing** or  **Round robin**. Choose from these options:

    - **Attendant routing** rings all agents in the queue at the same time. The first call agent to pick up the call gets the call.

    - **Serial routing** rings all call agents one by one. If an agent dismisses or does not pick up a call, the call will ring the next agent and will try all agents until it is picked up or times out.

    - **Round robin** balances the routing of incoming calls so that each call agent gets the same number of calls from the queue. This may be desirable in an inbound sales environment to assure equal opportunity among all the call agents.

    - **Longest idle** routes each call to the agent who has been idle the longest time. (Agents whose presence state has been **Away** for more than 10 minutes are not included.)

3. Turn **Presence-based routing** on. This routes calls to agents whose presence status is **Available**.

4. Choose if you want to allow agents to opt out of calls.

5. Set an **Agent alert time** to specify how long an agent's phone will ring before the queue redirects the call to the next agent.

> [!div class="nextstepaction"]
> [Step 5 - Call overflow >](/microsoftteams/business-voice/create-a-phone-system-call-queue-smb?tabs=call-overflow#steps)

### [Step 5 - Call overflow](#tab/call-overflow)

Choose how you want to handle calls that exceed the maximum in the queue.

1. Set the **Maximum calls in the queue**.

2. Choose what you want to do when the maximum number of calls is reached. You can disconnect the call or redirect it. We recommend that you redirect the call to one of the following destinations:
    - **Person in the organization** - a person in your organization who is able to receive voice calls
    - **Voice app** - an auto attendant or another call queue. (Choose the resource account associated with the auto attendant or call queue when choosing this destination.)
    - **External phone number** - any phone number. Use this format: +[country code][area code][phone number]
    - **Voicemail** - you can use the voice mailbox of the team that you created.

> [!div class="nextstepaction"]
> [Step 6 - Call timeout >](/microsoftteams/business-voice/create-a-phone-system-call-queue-smb?tabs=call-timeout#steps)

### [Step 6 - Call timeout](#tab/call-timeout)

Choose what you want to happen when calls have been waiting in the queue for too long.

1. Set the **Maximum wait time**.

2. Choose what you want to do when a call times out. You can disconnect the call or redirect it. We recommend that you redirect the call to one of the following destinations:
    - **Person in the organization** - a person in your organization who is able to receive voice calls
    - **Voice app** - an auto attendant or another call queue. (Choose the resource account associated with the auto attendant or call queue when choosing this destination.)
    - **External phone number** - any phone number. Use this format: +[country code][area code][phone number]
    - **Voicemail** - you can use the voice mailbox of the team that you created.

3. Click **Save**.

This completes the setup of your call queue. Next, you may want to [set up an auto attendant](set-up-auto-attendant.md).

---
