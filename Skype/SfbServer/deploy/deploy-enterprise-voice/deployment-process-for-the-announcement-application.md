---
title: "Deployment process for the Announcement application in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom: 
ms.assetid: 72c66249-c4ce-48ce-b1b9-90ebf77d7805
description: "Deployment process and steps for Announcement application in Skype for Business Server Enterprise Voice."
---

# Deployment process for the Announcement application in Skype for Business Server
 
Deployment process and steps for Announcement application in Skype for Business Server Enterprise Voice.
  
The Announcement application is an Enterprise Voice feature that enables you to configure what happens to calls to unassigned extensions (extensions that are valid for your organization, but are not assigned to a person or a phone). For example, you can configure calls to unassigned numbers to play a message, or to be transferred to a different destination, or both.
  
The Announcement application is installed as a feature of Response Group application on the Front End Server or Standard Edition server when you deploy Enterprise Voice. You need to configure Announcements by uploading your audio files or by configuring text-to-speech (TTS) and configuring the unassigned number table.
  
This section provides an overview of the steps involved in deploying the Announcement application. You must deploy Enterprise Voice before you configure announcements. The components required by the Announcement application are installed and enabled when you deploy Enterprise Voice.
  
**Announcement Deployment Process**

|**Phase**|**Steps**|**Roles**|**Deployment documentation**|
|:-----|:-----|:-----|:-----|
|Configure Announcement settings  <br/> | Create the announcement by recording and uploading audio files or by using text-to-speech (TTS). <br/>  Configure the unassigned number ranges in the unassigned number table and associate them with the appropriate announcement. <br/> |RTCUniversalServerAdmins  <br/> CsVoiceAdministrator  <br/> CsServerAdministrator  <br/> CsAdministrator  <br/> CsViewOnlyAdministrator  <br/> |[Create or delete an announcement in Skype for Business Server](create-an-announcement.md) <br/> [Create or modify an unassigned number range in Skype for Business Server](create-or-modify-an-unassigned-number-range.md) <br/> |
|Verify your Announcement deployment  <br/> |Test by listening to announcements to verify that your configuration works as expected.  <br/> |-  <br/> |[(Optional) Verify Announcement deployment in Skype for Business](optional-verify-announcement-deployment.md) <br/> |
   

