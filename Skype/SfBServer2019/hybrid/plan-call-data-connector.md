---
title: "Plan call data connector"
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 1/31/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
description: "Overview of using Skype for Business Online telemetry tools to monitor an on-premises implementation in a hybrid scenario."
---
<!-- PM William Looney  -->



# Plan Call Data Connector

[!INCLUDE [disclaimer](../disclaimer.md)]

## Overview
This topic describes benefits, planning considerations, and requirements for implementing Skype for Business Server Call Data Connector.  For more information on configuring Call Data Connector, see INSERT LINK HERE.

Call Data Connector greatly simplifies call monitoring in a hybrid environment because you no longer need to use different sets of on-premises and online tools to monitor all of your users call quality.  Whether your users are homed on premises or online, you can view call quality for your entire organization online.

With Call Data Connector, the Skype for Business Server pushes call data to the cloud service so that you can leverage the Skype for Business Online Call Analytics (CA) and Call Quality Dashboard (CQD) tools. These tools enable you to monitor the quality of calls and troubleshoot connection problems with Microsoft Teams and Skype for Business services as follows:

- Call Analytics focuses on quality problems with specific calls. It shows detailed information about calls and meetings for each user in a Skype for Business acouunt.  With Call Analytics, you can assign permissions to a Helpdesk operator who can then monitor calls without having access to the rest of the Skype for Business Admin center.

- Call Quality Dashboard focuses on network performance and issues across an organization. Skype for Business administrators and network engineers use this tool to troubleshoot and optimize network performance.


For more information on Call Quality Dashboard and Call Analytics, see INSERT LINK(S) HERE.

## Requirements
To set up Call Data Connector, the following are required:

- 

The Call Data Connector pushes call data (SIP messages and QoE messages) from the Skype for Business Server deployment into the data pipeline used to power the call quality management tools used in Skype for Business Online. To do this, your implementation must have an O365 tenant. To make the data actionable, the CMS topology information is also needed. 









**Highlights:**
*	On Premises organizations creates a hybrid connection and see the on-premise and online data in the Call Quality management tools, also have the option to choose to keep data of customers in their environment by setting up policies.





