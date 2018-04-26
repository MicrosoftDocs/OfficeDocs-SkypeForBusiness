---
title: "Plan call data connector"
ms.author: jambirk
author: jambirk
manager: serdars
ms.date: 1/31/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
description: "Overview of using SfBO telemetry tools to monitor an on-prem implementation in a hybrid scenario."
---
<!-- PM William Looney  -->

[!INCLUDE [disclaimer](../disclaimer.md)]
# Plan call data connector

The Skype for Business Server Call Data Connector enables SfB on-premise Server admins to leverage the SfB Online call quality management tools such as Call Analytics (CA) and Call Quality Dashboard (CQD) tools by connecting the call telemetry from their on-premise SfB deployment to the data pipelines used in SfB Online.

This feature allows an admin to unify on-premise and online users' call data and dashboards on the cloud, which provides better reporting and analytics experience, fast and easy access to information through a choice of device, and above all they benefit from the continuous investments and improvements in cloud. 

The Call Data Connector pushes call data (SIP messages and QoE messages) from the Skype for Business Server deployment into the data pipeline used to power the call quality management tools used in Skype for Business Online. To do this, your implementation must have an O365 tenant. To make the data actionable, the CMS topology information is also needed. 

## High Level Scenarios

###	Split Domain Organization 

Javier is the Skype for Business admin for Topsail Toys leading their journey to online services by piloting 500 users in Skype for Business Online. For any call quality issues, he had to check his on-premise Monitoring Server reports and then the online Call Analytics reports to get a complete picture of the users experience and issues. Javier is excited when he learns about the Call Data Connector. He opts in for Call Data connector in his company and is happy to see all his user’s data in one place and enjoys using the latest and greatest Call Quality management tools that are much easier to use and offer a richer feature set compared to the tools he has access for his on-premise deployment. With these tools in hand, he accelerates his plans for migrating the remaining on-premise users to SfB Online.

**Highlights:**
*	Split domain organizations see their on-premise and online data in the Call Quality management tools (currently CQD and Call Analytics).
*	Clear documentation describing what data is uploaded, how it used, and deployment/topology requirements.

###	On-premise organization
Maria is an SfB2019 admin who has installed the server in her company environment. Her company CTO told her that for better support for helpdesk team, they would like to use the Call Analytics feature of SfBO for all company users except for few Company Executives which they want to keep it onPrem. Maria creates a hybrid connection of the onPrem SfB server with Office 365 tenant with Skype Online with ADFS sync enabled to maintain synchronization for local and online users. She sets up a policy in the SfB 2019 to not send the Company Executives data to cloud. Once the environment is set the call data for all users except for Company Execs moves to cloud. Maria was not only able to empower the help desk team with Call Analytics reporting but also to keep the Companies Executive data within the company boundary which can be viewed with the onPrem CQD dashboard. She makes her CTO happy.

**Highlights:**
*	On Premises organizations creates a hybrid connection and see the on-premise and online data in the Call Quality management tools, also have the option to choose to keep data of customers in their environment by setting up policies.





