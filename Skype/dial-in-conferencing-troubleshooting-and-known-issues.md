---
title: Dial-in conferencing troubleshooting and known issues
ms.prod: OFFICE365
ms.assetid: 72979911-5319-4de2-a275-4dd9a0f44fe6
---



# Dial-in conferencing troubleshooting and known issues

 **This article is for customers who are using Microsoft as their dial-in conferencing provider. It does not apply to customers who are using a third-party audio conferencing provider (ACP).**
  
    
    

Dial-in conferencing using Microsoft as the dial-in conferencing provider is a new feature for Skype for Business Online. There are current issues that are being tracked, actively investigated and will be potentially resolved when the feature is updated in future builds in Office 365 and Skype for Business Online.
For now, use this as a reference when you are troubleshooting potential issues with getting dial-in conferencing set up and working for the people in your organization.
  
    
    


## Troubleshoot dial-in conferencing

The following table lists some of the common issues you might come across and their solutions.
  
    
    


|**Issue**|**Solution**|
|:-----|:-----|
|Entry and exit notifications are turned on when a meeting starts but they're turned off shortly after the meeting starts.  <br/> |By default, entry and exit notifications are disabled for meetings where participants join from both Skype for Business clients and when they dial in. You can enable the announcements in the **Skype Meeting Options** in the Skype for Business client. For a meeting where all participants dial in and join a meeting, entry and exit notifications are enabled by default as the participant roster isn't available to any participant. When a meeting has started with only participants calling in, the entry and exit notifications will be turned on, but when a participant joins using a Skype for Business client, the notifications will be turned off. When turned off, the notifications can be enabled back using **Skype Meeting Options** in the Skype for Business client. <br/> |
|If a user is provisioned the first time by being assigned an E5 license, it might be possible for the dial-in conferencing welcome email to not be delivered to the user's if the mailbox isn't enabled.  <br/> |If this happens, you can always resend the dial-in conferencing information of the user using **Dial-in conferencing** in the UNRESOLVED_TOKEN_VAL(Skype for Business admin center) or using PowerShell. See [Enable or disable sending emails when dial-in conferencing settings change](enable-or-disable-sending-emails-when-dial-in-conferencing-settings-change.md).  <br/> > [!NOTE]> In order to resend the dial-in conferencing PIN to the user, the PIN has to be reset. This can also be done by using the **Dial-in conferencing** in the UNRESOLVED_TOKEN_VAL(Skype for Business admin center) or using PowerShell.          |
   

## Dial-in conferencing known issues

The following is the list of known issues for dial-in conferencing.
  
    
    


|**Known issue**|**Comments**|
|:-----|:-----|
|Dial-in conferencing calls could take up to 24 hours to show in the usage reports.  <br/> |We're looking forward to make improvements on this area in future service updates.  <br/> |
|When a caller dials into a conference bridge after the meeting has been locked by a Skype for Business user, there isn't a notification in the Skype for Business client stating that the user is waiting in the lobby.  <br/> |This is currently by design, but we've taken the feedback in regard to supporting this capability in future service updates.  <br/> |
   

## See also


#### Other Resources


  
    
    
 [Set up dial-in or PSTN conferencing for Skype for Business](set-up-dial-in-or-pstn-conferencing-for-skype-for-business.md)
