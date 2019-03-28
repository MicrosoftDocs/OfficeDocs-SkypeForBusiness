---
title: "Response Groups Create New or Edit Existing Agent Group"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.lscp.RgsGroupEdit
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 79eaaf6c-6928-4925-8220-c7ada6b37205
ROBOTS: NOINDEX, NOFOLLOW
description: "Agent groups define who can answer calls to a response group (known as agents) and the settings that apply to all the agents in the group."
---

# Response Groups: Create New or Edit Existing Agent Group

Agent groups define who can answer calls to a response group (known as agents) and the settings that apply to all the agents in the group.

## UI Reference

The following list describes the fields on the page.

- **Name** Each agent group requires a unique name. Use a descriptive name that identifies the group's function. For example, Help Desk.

- **Description** This field is optional. Use it to provide additional details about the group.

- **Participation policy** Specify the way that agents are to sign into the response group:

  - Select **Informal** to specify that the agents in the group do not need to sign in and out. Informal agents are automatically signed in when they sign in. The default is **Informal**.

  - Select **Formal** to specify that the agents in the group must sign in and out. When you select this option, agents click a menu item in the client to open a browser and display a web page console for signing in and out.

- **Alert time (seconds)** Specify the number of seconds to ring an agent before offering the call to the next available agent. The value must be at least 10 seconds and less than 180 seconds. The default is 20 seconds.

- **Routing method** Select the method for determining the order in which agents receive calls:

  - Select **Longest idle** to offer a new call first to the agent who has been idle (has had a presence of **Available** or **Inactive**) the longest.

  - Select **Parallel** to offer a new call to all available agents at the same time. The call is sent to the first agent who accepts it.

  - Select **Round robin** to offer a new call to each agent in turn.

  - Select **Serial** to always offer a new call to agents in the order in which they are listed in the **Agent** list.

  - Select **Attendant** to offer a new call to all agents who are signed in and the Response Group application at the same time, regardless of their current presence. Attendants and client users who are configured as agents can see all the calls that are waiting and can answer waiting calls in any order. The call is sent to the first agent who accepts it, and the other attendants and users no longer see the call.

- **Agents** Select the users who are to be agents for the response group in one of the following ways:

  - Select **Use an existing email distribution list** to use an Exchange distribution list. Type the email address of the distribution list in **Distribution list address**.

    > [!NOTE]
    > You can select only one distribution list for an agent group. If the distribution list includes nested distribution lists, the nested distribution lists are not included in the agent group.

    > [!NOTE]
    > The order in which agents are listed in the distribution list affects the order in which agents receive calls for round robin and serial routing.

    > [!NOTE]
    > Hidden memberships or hidden lists might become visible to Response Group administrators or users. For details, see [Create or modify an agent group in Skype for Business](../../../deploy/deploy-enterprise-voice/create-or-modify-an-agent-group.md).

  - Select **Define a custom group of agents** to select the users you want to assign as agents for the response group. Click **Select** to add an agent to the list. Click **Remove** to delete a selected agent from the list.

    The up and down arrows move a selected agent up and down in the agent list. The order of agents in the list affects the order in which agents receive calls for round robin and serial routing.

For details about Response Group features and capabilities, see [Plan for the Response Group application in Skype for Business Server](../../../plan-your-deployment/enterprise-voice-solution/response-group.md) in the Planning documentation. For details about working with agent groups, see [Managing Agent Groups](https://technet.microsoft.com/library/36084cdc-38f1-4c45-922f-f81c7e86210c.aspx) in the Operations documentation.


