---
title: "Plan for the Announcement application in Skype for Business"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection:
- IT_Skype16
- Strat_SB_Admin
ms.custom:
ms.assetid: 2abee804-2599-48bb-90b2-15df0bae5e20
description: "Planning for the announcement application in Skype for Business Server Enterprise Voice, which configures what to do with phone calls to unassigned phone numbers in your organizations. Includes audio file requirements."
---

# Plan for the Announcement application in Skype for Business

Planning for the announcement application in Skype for Business Server Enterprise Voice, which configures what to do with phone calls to unassigned phone numbers in your organizations. Includes audio file requirements.

The Skype for Business Server Announcement application enables you to configure the handling of incoming phone calls when the dialed number is valid for your organization, but is not assigned to a user or a phone. You can transfer these calls to a predetermined destination (phone number, SIP URI, or voice mail), or play an audio announcement, or both. The Announcement application helps you avoid the situations in which a caller misdials and hears a busy tone or the SIP client receives an error message. This section includes planning information that is specific to the Announcement application

When you deploy the Announcement application, you need to configure an unassigned number table that determines the action to be taken when someone dials an unassigned number. The unassigned number table contains ranges of phone numbers that are valid for the organization and specifies which Announcement application handles each range. When a caller dials a telephone number that is valid for your organization but is not assigned to anyone, Skype for Business Server looks up the number in the unassigned number routing table, identifies which range the number falls in, and routes the call to the Announcement application specified for that range. The Announcement application answers the call and plays an audio message (if you configured it to do so) and then either disconnects the call or transfers it to a predetermined destination, such as to an operator. You can use Skype for Business Server Management Shell cmdlets to configure multiple audio messages or to transfer destinations.

How you configure the unassigned number table depends on how you want to use it. If you have specific numbers that are no longer in use and you want to play messages that are tailored for each number, you can enter those specific numbers in the unassigned number table. For example, if you changed the number for your customer service desk, you can enter the old customer service number and associate it with an announcement that gives the new number. If you want to play a general message to anyone who calls a number that is not assigned, such as for employees who have left your organization, you can enter ranges for all the valid extensions in your organization. The unassigned number table is invoked whenever the caller dials a number that is not currently assigned.

## Deployment and requirements

Tthe Announcement application is automatically installed with the Response Group application. The Announcement and Response Group applications are standard components of an Enterprise Voice deployment: When you deploy Enterprise Voice, both of these applications are automatically deployed.

### Software requirements

All Front End Servers or Standard Edition servers that run the Announcement application must have the Windows Media Format Runtime installed for servers running Windows Server 2008 R2, or Microsoft Media Foundation for servers running Windows Server 2012 or Windows Server 2012 R2. For Windows Server 2008 R2, the Windows Media Format Runtime is installed as part of Windows Desktop Experience. Windows Media Format Runtime or Microsoft Media Foundation is required for Windows Media Audio (.wma) files that the Announcement application plays for announcements and music.

### Port Requirements

The Announcement application uses **Port 5071** for SIP listening requests.

> [!NOTE]
> This port is the default setting, which you can change by using the **Set-CsApplicationServer** cmdlet. For details about this cmdlet, see the Skype for Business Server Management Shell documentation.

### Audio File Requirements

The Announcement application supports Wave (.wav) file format and Windows Media audio (.wma) file format for music and announcements. Audio file requirements for the Announcement application are the same as for the Response Group application. For details, see [Technical Requirements for Response Groups](https://technet.microsoft.com/library/477488bd-124f-437b-9327-732a0d7271ca.aspx).


