---
title: "Response Groups Queue Create New or Edit Existing"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.date: 3/24/2015
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.lscp.RgsQueueEdit
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: cbdde536-8668-4a08-9862-8615e8691fd7
description: "Response Group queues hold calls to a response group until an agent answers the call."
---

# Response Groups Queue: Create New or Edit Existing

Response Group queues hold calls to a response group until an agent answers the call.

## UI Reference

The following list describes the fields on the page.

- **Name** Each queue must have a name. Type a descriptive name for the queue.

- **Description** This field is optional. Use it to provide additional details about the queue.

- **Groups** Select the agent groups that you want to assign to the queue. Click **Select** to add agent groups to the list. Click **Remove** to delete the selected agent group from the list.

    The up and down arrows move a selected agent group up and down in the list. The order of agent groups affects the order in which Skype for Business Server searches for an available agent. That is, the first group in the list is searched first for an available agent, followed by the second group, and so on.

- **Enable queue time-out** Select this check box to specify a maximum period of time for a caller to wait on hold before an agent answers the call. If you select this option, you also need to specify the following:

  - **Time-out period (seconds)** Select or type the maximum number of seconds a caller can wait before an agent answers the call.

  - **Call action** Select the action that occurs when a call times out. Your choices are:

  - **Disconnect**

  - **Forward to voice mail** If you select this option, in **SIP address**, type a voice mail address in the format sip:<username>@<domainname> (for example, sip:bob@contoso.com).

  - **Forward to telephone number** If you select this option, in **SIP address** type the telephone number in the format sip:<number>@<domainname> (for example, sip:+14255550121@contoso.com).

  - **Forward to SIP address** Select this option to forward the call to another user. In **SIP address**, type the URI for the user in the format sip:<username>@<domainname>.

  - **Forward to another queue** If you select this option, browse to the queue that is to receive calls when the calls time out.

- **Enable queue overflow** Select this check box to specify a maximum number of calls that the queue can hold. If you select this option, you also need to specify the following:

  - **Maximum number of calls** Select or type the maximum number of calls the queue can hold.

  - **Forward the call** Select which call is to take action when the queue overflow threshold is met.

  - **Call action** Select the action that occurs when the queue overflow threshold is met. Your choices are:

  - **Disconnect**

  - **Forward to voice mail** If you select this option, in **SIP address**, type a voice mail address in the format sip:<username>@<domainname> (for example, sip:bob@contoso.com).

  - **Forward to telephone number** If you select this option, in **SIP address** type the telephone number in the format sip:<number>@<domainname> (for example, sip:+14255550121@contoso.com).

  - **Forward to SIP address** Select this option to forward the call to another user. In **SIP address**, type the URI for the user in the format sip:<username>@<domainname>.

  - **Forward to another queue** If you select this option, browse to the queue that is to receive calls when the queue overflow threshold is met.

For details about Response Group features and capabilities, see [Plan for the Response Group application in Skype for Business Server 2015](../../plan-your-deployment/enterprise-voice-solution/response-group.md) in the Planning documentation. For details about working with queues, see [Managing Response Group Queues](https://technet.microsoft.com/library/1e91720c-ab67-4dfb-b30c-0ef2a8012310.aspx) in the Operations documentation.


