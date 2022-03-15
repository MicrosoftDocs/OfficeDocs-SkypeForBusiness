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

To create a team:

1. First, select **Teams** on the left side of the app, then select **Join or create a team** at the bottom of your teams list.

2. Then select **Create team** (first card, top left corner).

3. Choose **From scratch**.

4. Next, choose whether you want a public or private team. We recommend **Private** for your call queue to avoid people unintentionally becoming part of the queue by joining the team.

5. Name your team and add an optional description.

6. When you're done, select **Create**.

7. Type the names of the people that you want to have in your call queue, and then select **Add**.

8. Select **Close**. People you add to a team will receive an email letting them know they are now a member of your team and the team will show up in their teams list.

Next, we'll add a channel to use with the call queue.

To add a channel

1. In Teams, find the team you just created, select **More options** (...), and then select **Add channel**.

2. Type a name and description for the channel.

3. Under **Privacy**, choose **Standard - Accessible to everyone on the team** and then select **Add**.

> [!div class="nextstepaction"]
> [Step 2 - Resource accounts >](?tabs=resource-account#steps)

### [Step 2 - Resource accounts](#tab/resource-account)

Each call queue that you create requires a resource account. This is similar to a user account, except the account is associated with an auto attendant or call queue instead of a person. In this step, we'll create the account, assign it a *Microsoft Teams Phone Standard - Virtual User* license, and then use it to start creating the call queue.

#### Create a resource account

You can create a resource account in the Teams admin center.

1. In the Teams admin center, expand **Voice**, and then select **Resource accounts**.

2. Select **Add**.

3. In the **Add resource account** pane, fill out **Display name**, **Username**, and choose **Call queue** for the **Resource account type**. Agents will see the display name when they receive an incoming call from the queue.

4. Select **Save**.

   The new account will appear in the list of accounts.

#### Assign a license

You must assign a *Microsoft Teams Phone Standard - Virtual User* license to the resource account.

1. In the Microsoft 365 admin center, in the **Active users** list, select the resource account to which you want to assign a license.

2. On the **Licenses and Apps** tab, under **Licenses**, select **Microsoft Teams Phone Standard - Virtual User**.

3. Select **Save changes**.

#### Create a call queue

Next, we'll start creating a new call queue and assign the resource account.

1. In the Teams admin center, expand **Voice**, select **Call queues**, and then select **Add**.

2. Type a name for the call queue.

3. Select **Add accounts**, search for the resource account that you want to use with this call queue, select **Add**, and then select **Add**.

4. (Optional) Under **Assign calling ID**, select **Add**, search for the resource accounts that you created for your auto attendant, select **Add**, and then select **Add**. This will give your call agents the caller ID of your main line when they call out.

    > [!NOTE]
    > The resource account used for calling ID purposes must have a **Microsoft Teams Phone Standard - Virtual User** license and one of the following assigned:
    >
    > - A Calling Plan license and a phone number assigned
    > - An Operator Connect phone number assigned
    > - An online voice routing policy (phone number assignment is optional when using Direct Routing)

5. Choose a [supported language](../create-a-phone-system-call-queue-languages.md). This language will be used for system-generated voice prompts and voicemail transcription (if you use them).

6. Specify if you want to play a greeting to callers when they arrive in the queue. You must upload an MP3, WAV, or WMA file containing the greeting that you want to play.

    Teams provides default music to callers while they are on hold in a queue. If you want to play a specific audio file, choose **Play an audio file** and upload an MP3, WAV, or WMA file.

   > [!NOTE]
   > The uploaded recording can be no larger than 5 MB.
   > The default music supplied in Teams call queues is free of any royalties payable by your organization.

> [!div class="nextstepaction"]
> [Step 3 - Call agents >](?tabs=call-agents#steps)

### [Step 3 - Call agents](#tab/call-agents)

To add agents to the call queue, you can add them to the team and channel that we created earlier, add agents individually, or add groups. You need to be a member of the team to do this.

#### Via Teams channel

1. Select the **Choose a team** option and select **Add a channel**.
2. Type the name of the team that you created, select it, and select **Add**.
3. Select the channel that you created for the queue.
4. Select **Apply**.

The following clients are supported when using a Teams channel for call queues:

- Microsoft Teams Windows client
- Microsoft Teams Mac client

> [!NOTE]
> If you use this option, it can take up to 24 hours for the call queue to be fully operational.

#### Via users and groups

You can add up to 20 agents individually and up to 200 agents via groups.

If you want to add individual users or groups to the queue, select the **Choose users and groups** option.

To add a user to the queue, select **Add users**, search for the user, select **Add**, and then select **Add**.

To add a group to the queue, select **Add groups**, search for the group, select **Add**, and then select **Add**. You can use distribution lists, security groups, and Microsoft 365 groups or Microsoft Teams teams.

> [!NOTE]
> New users added to a group can take up to eight hours for their first call to arrive.

> [!div class="nextstepaction"]
> [Step 4 - Call routing >](?tabs=call-routing#steps)

### [Step 4 - Call routing](#tab/call-routing)

**Conference mode** significantly reduces the amount of time it takes for a caller to be connected to an agent, after the agent accepts the call. For conference mode to work, agents in the call queue must use one of the following clients:

- The latest version of the Microsoft Teams desktop client, Android app, or iOS app
- Microsoft Teams Phone version 1449/1.0.94.2020051601 or later
  
Agents' Teams accounts must be set to Teams-only mode. Agents who don't meet the requirements aren't included in the call routing list. We recommend enabling conference mode for your call queues if your agents are all using compatible clients.

> [!NOTE]
> Conference mode is not supported if phone calls are routed to the queue from a Direct Routing gateway that is enabled for Location Based Routing.

Choose the call routing method that you want to use.

1. Set **Conference mode** to **On**.

2. Choose the **Routing method** you want to use. This determines the order in which agents receive calls from the queue. We recommend **Serial routing** or  **Round robin**. Choose from these options:

    - **Attendant routing** rings all agents in the queue at the same time. The first call agent to pick up the call gets the call.

    - **Serial routing** rings all call agents one by one. If an agent dismisses or does not pick up a call, the call will ring the next agent and will try all agents until it is picked up or times out.

    - **Round robin** balances the routing of incoming calls so that each call agent gets the same number of calls from the queue. This may be desirable in an inbound sales environment to assure equal opportunity among all the call agents.

    - **Longest idle** routes each call to the agent who has been idle the longest time. (Agents whose presence state has been **Away** for more than 10 minutes are not included.)

3. Turn **Presence-based routing** on. This routes calls to agents whose presence status is **Available**.

    **Presence-based routing** uses the availability status of call agents to determine whether an agent should be included in the call routing list for the selected routing method.

    Call agents whose availability status is set to **Available** are included in the call routing list and can receive calls. Agents whose availability status is set to any other status are excluded from the call routing list and won't receive calls until their availability status changes back to **Available**.

    You can use presence-based call routing with any of the routing methods.

    If an agent opts out of getting calls, they won't be included in the call routing list regardless of what their availability status is set to.

    > [!NOTE]
    > If [Compliance recording](../teams-recording-policy.md) is turned on, the combination of **Conference mode** and **Attendant routing** is not supported. If you need to use **Conference mode**, select **Serial Routing**, **Round robin**, or **Longest idle** as the **Routing method**. If you need to use **Attendant routing**, set **Conference mode** to **Off**.
    >
    > When using **Longest idle** and when there are less calls in queue than available agents, only the first two longest idle agents will be presented with calls from the queue.
    >
    > When using **Longest idle** there may be times when an agent receives a call from the queue shortly after becoming unavailable or if there is a short delay in receiving a call from the queue after becoming available.

4. Choose if you want to allow agents to opt out of calls.

5. Set an **Agent alert time** to specify how long an agent's phone will ring before the queue redirects the call to the next agent. We recommend to set the **Agent alert time** to 20 seconds.

> [!div class="nextstepaction"]
> [Step 5 - Call overflow >](?tabs=call-overflow#steps)

### [Step 5 - Call overflow](#tab/call-overflow)

**Maximum calls in the queue** specifies the maximum number of calls that can wait in the queue at any given time. The default is 50, but it can range from 0 to 200. When this limit is reached, the call is handled as specified by the **When the maximum number of calls is reached** setting.

Choose how you want to handle calls that exceed the maximum in the queue.

1. Set the **Maximum calls in the queue**.

2. Choose what you want to do when the maximum number of calls is reached. You can disconnect the call or redirect it. We recommend that you redirect the call to one of the following destinations:
    - **Person in the organization** - a person in your organization who is able to receive voice calls
    - **Voice app** - an auto attendant or another call queue. (Choose the resource account associated with the auto attendant or call queue when choosing this destination.)
    - **External phone number** - any phone number. Use this format: +[country code][area code][phone number]
    - **Voicemail** - you can use the voice mailbox of the team that you created.

    For external transfers, see [Prerequisites](../plan-auto-attendant-call-queue.md#prerequisites) and the [external phone number transfers - technical details](../create-a-phone-system-auto-attendant.md#external-phone-number-transfers---technical-details) for number formatting.

> [!NOTE]
> If the maximum number of calls is set to 0, then the greeting message will not play.

> [!div class="nextstepaction"]
> [Step 6 - Call timeout >](?tabs=call-timeout#steps)

### [Step 6 - Call timeout](#tab/call-timeout)

**Call Timeout: maximum wait time** specifies the maximum time a call can be on hold in the queue before it is redirected or disconnected. You can specify a value from 0 seconds to 45 minutes.

Choose what you want to happen when calls have been waiting in the queue for too long.

1. Set the **Maximum wait time**.

2. Choose what you want to do when a call times out. You can disconnect the call or redirect it. We recommend that you redirect the call to one of the following destinations:
    - **Person in the organization** - a person in your organization who is able to receive voice calls
    - **Voice app** - an auto attendant or another call queue. (Choose the resource account associated with the auto attendant or call queue when choosing this destination.)
    - **External phone number** - any phone number. Use this format: +[country code][area code][phone number]
    - **Voicemail** - you can use the voice mailbox of the team that you created.

    For external transfers, see [Prerequisites](../plan-auto-attendant-call-queue.md#prerequisites) and the [external phone number transfers - technical details](../create-a-phone-system-auto-attendant.md#external-phone-number-transfers---technical-details) for number formatting.

3. When you have selected your call timeout options, select **Save**.

This completes the setup of your call queue.

---
