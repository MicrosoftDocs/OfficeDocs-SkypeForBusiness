---
title: "Configure unassigned phone numbers in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: a0650659-dce7-455f-8977-02454bbfa400
description: "Lync Server lets you configure what happens to incoming calls to phone numbers that are valid for your organization, but are not assigned to a user or a phone. To configure the handling of such calls, you set up an unassigned number table. You can use the table to route the calls to an Announcement application or to an Exchange UM server."
---

# Configure unassigned phone numbers in Lync Server 2013
[]
Lync Server lets you configure what happens to incoming calls to phone numbers that are valid for your organization, but are not assigned to a user or a phone. To configure the handling of such calls, you set up an unassigned number table. You can use the table to route the calls to an Announcement application or to an Exchange UM server.
  
How you configure the unassigned number table depends on how you want to use it. You can configure the table with all the valid extensions for your organization, with only unassigned extensions, or with a combination of both types of numbers. The unassigned number table can include both assigned and unassigned numbers, but it is invoked only when a caller dials a number that is not currently assigned. If you include all the valid extensions in the unassigned number table, you can specify the action that occurs whenever someone leaves your organization, without needing to reconfigure the table. If you include unassigned extensions in the table, you can tailor the action that occurs for specific numbers. For example, if you change the extension for your customer service desk, you can include the old customer service number in the table and assign it to an announcement that provides the new number.
  
> [!IMPORTANT]
> Before you configure the unassigned number table, you must already have either one or more announcements defined or an Exchange UM Auto Attendant set up. For details about creating announcements, see [Create an announcement in Lync Server 2013](create-an-announcement.md). To see if you have configured Exchange UM settings, run the **Get-CsExUmContact** cmdlet. For details, see [Get-CsExUmContact](get-csexumcontact.md). 
  
## In this section

- [Create or modify an unassigned number range in Lync Server 2013](create-or-modify-an-unassigned-number-range.md)
    
- [Delete an unassigned number range in Lync Server 2013](delete-an-unassigned-number-range.md)
    

