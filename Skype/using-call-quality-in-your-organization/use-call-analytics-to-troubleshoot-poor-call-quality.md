---
title: "Use Call Analytics to troubleshoot poor Skype for Business call quality"
ms.author: lolaj
author: LolaJacobsen
manager: serdars
ms.date: 12/15/2017
ms.topic: article
ms.assetid: 66945036-ae87-4c08-a0bb-984e50d6b009
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
ms.collection: Adm_Skype4B_Online
ms.audience: Admin
ms.appliesto: Microsoft Teams
localization_priority: Normal
ROBOTS: None
f1keywords: None
ms.custom:
- Setup
description: "Use Call Analytics details about devices, networks, and connectivity to troubleshoot user problems with Skype for Business calls and meetings."
---

# Use Call Analytics to troubleshoot poor Skype for Business call quality

Call Analytics helps you to troubleshoot call or connection problems with Skype for Business. Call Analytics shows detailed information about the devices, networks, and connectivity for the calls and meetings of each user in your Skype for Business account. If building, site, and tenant information has been added to Call Analytics, it will also be shown for each call and session. Information available via Call Analytics can help you figure out why a user had a poor call or meeting experience. 
  
> [!NOTE]
> Call Analytics is currently in preview. Text and images described here may not match your experience. 
  
## Troubleshoot call quality problems using Call Analytics

The permissions level assigned to you determines what type of information you have access to in Call Analytics:
  
- **Skype for Business admin**: You have access to all the information in Call Analytics and in the Skype for Business Admin center.
    
- **Helpdesk agent with Tier 1 permissions**: You see a limited set of data in Call Analytics. You can troubleshoot calls, but you'll hand off problems with meetings to a Tier 2 agent. You don't have access to the rest of the Skype for Business Admin center.
    
- **Helpdesk agent with Tier 2 permissions**: You see all available data in Call Analytics and can help troubleshoot problems with both calls and meetings. You don't have access to the rest of the Skype for Business Admin center.
    
See your Skype for Business admin if you need help with permissions.
  
 **Open Call Analytics as a Tier 1 or Tier 2 helpdesk agent**
  
1. Go to [https://adminportal.services.skypeforbusiness.com](https://adminportal.services.skypeforbusiness.com), and then sign in with your user name and password.
    
2. In **User Search**, start typing either the name or sip address of the user whose calls you want to troubleshoot and then select the user from the list.
    
    ![Screenshot of the User Search box of Call Analytics in the Skype for Business Admin Center.](../images/db52efc5-dac1-4623-ba72-41e42f0a0fb4.png)
  
3. In **Call history**, select the call or meeting that you want to troubleshoot.
    
    ![Screenshot shows the call history page for a user with information such as the user's contact details, a summary of the 7-day quality and activity for meetings and calls, and an overview of dates and times, recipients, and audio quality,](../images/aef80e09-3b37-46db-8e7b-8cf71712349b.png)
  
4. Select the **Advanced** tab, and then look for yellow and red items which indicate poor call quality or connection problems.
    
    In the session details for each call or meeting, minor issues appear in yellow. (For example, in the following screenshot, the values are in yellow for Average jitter, Max jitter, and Average packet loss rate.) If something is yellow, it's outside of normal range, and it may be contributing to the problem, but it's unlikely to be the main cause of the problem. If something is red, it's a significant problem, and it's likely the main cause of the poor call quality for this session. 
    
    ![Screenshot shows the Advanced tab of a user's Call history with the Inbound network section expanded to reveal that the data for average jitter, max jitter, and average packet loss rate are shown in a yellow color, meaning they are minor issues.](../images/13f314ce-97cf-4bd0-a147-14b177d07040.png)
  
In rare cases, quality of experience data isn't received for audio sessions. Often this is caused by the call dropping and connection with the client terminating. When this occurs, the session rating is "unavailable".
  
For audio sessions that do have quality of experience (QoE) data, the following table describes major issues that qualify a session as "poor."
  
|**Issue**|**Area**|**Description**|
|:-----|:-----|:-----|
|Call setup  <br/> |Session  <br/> |The error code Ms-diag 20-29 indicates the call setup failed. The user couldn't join the call or meeting.  <br/> |
|Audio network classified poor call  <br/> |Session  <br/> |Network quality issues were encountered in areas such as packet loss, jitter, NMOS degradation, RTT, or concealed ratio. For more information about the conditions used to classify poor calls, see this [Microsoft blog post](https://go.microsoft.com/fwlink/p/?linkid=852133).  <br/> |
|Device not functioning  <br/> |Device  <br/> | A device isn't functioning correctly. Device not functioning ratios are : <br/>  DeviceRenderNotFunctioningEventRatio >= 0.005 <br/>  DeviceCaptureNotFunctioningEventRatio >= 0.005 <br/> |
   
## Related topics
[Set up Skype for Business Call Analytics](set-up-call-analytics.md)

[What's the difference between Call Analytics and Call Quality Dashboard?](difference-between-call-analytics-and-call-quality-dashboard.md)

