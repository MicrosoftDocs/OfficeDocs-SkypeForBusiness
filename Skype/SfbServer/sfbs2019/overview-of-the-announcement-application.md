---
title: "Overview of the Announcement application in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 2abee804-2599-48bb-90b2-15df0bae5e20
description: "When you deploy the Announcement application, you need to configure an unassigned number table that determines the action to be taken when someone dials an unassigned number. The unassigned number table contains ranges of phone numbers that are valid for the organization and specifies which Announcement application handles each range. When a caller dials a telephone number that is valid for your organization but is not assigned to anyone, Lync Server looks up the number in the unassigned number routing table, identifies which range the number falls in, and routes the call to the Announcement application specified for that range. The Announcement application answers the call and plays an audio message (if you configured it to do so) and then either disconnects the call or transfers it to a predetermined destination, such as to an operator. You can use Lync Server Management Shell cmdlets to configure multiple audio messages or to transfer destinations."
---

# Overview of the Announcement application in Lync Server 2013
[]
When you deploy the Announcement application, you need to configure an unassigned number table that determines the action to be taken when someone dials an unassigned number. The unassigned number table contains ranges of phone numbers that are valid for the organization and specifies which Announcement application handles each range. When a caller dials a telephone number that is valid for your organization but is not assigned to anyone, Lync Server looks up the number in the unassigned number routing table, identifies which range the number falls in, and routes the call to the Announcement application specified for that range. The Announcement application answers the call and plays an audio message (if you configured it to do so) and then either disconnects the call or transfers it to a predetermined destination, such as to an operator. You can use Lync Server Management Shell cmdlets to configure multiple audio messages or to transfer destinations.
  
How you configure the unassigned number table depends on how you want to use it. If you have specific numbers that are no longer in use and you want to play messages that are tailored for each number, you can enter those specific numbers in the unassigned number table. For example, if you changed the number for your customer service desk, you can enter the old customer service number and associate it with an announcement that gives the new number. If you want to play a general message to anyone who calls a number that is not assigned, such as for employees who have left your organization, you can enter ranges for all the valid extensions in your organization. The unassigned number table is invoked whenever the caller dials a number that is not currently assigned.
  
In Lync Server 2013, the Announcement application is automatically installed with the Response Group application. The Announcement and Response Group applications are standard components of an Enterprise Voice deployment: When you deploy Enterprise Voice, both of these applications are automatically deployed. 
  

