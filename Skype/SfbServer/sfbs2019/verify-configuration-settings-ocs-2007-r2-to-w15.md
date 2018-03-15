---
title: "Verify configuration settings [OCS 2007 R2 to W15]"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 41dbf91c-f2e1-4b9a-88cf-959575558cf2
description: "In this articlePolicies and Settings to Verify after MigrationTo verify policies and settingsTo verify policies and settings by using cmdlets"
---

# Verify configuration settings [OCS 2007 R2 to W15]
[]
 **In this article**
  
[Policies and Settings to Verify after Migration](#sectionSection0)
  
[To verify policies and settings](#sectionSection1)
  
[To verify policies and settings by using cmdlets](#sectionSection2)
  
After you merge the topology and run the **Import-CsLegacyConfiguration** cmdlet, verify that your Office Communications Server 2007 R2 policies and settings were imported to Lync Server 2013. The following table lists the policies and settings that you should verify. 
  
## Policies and Settings to Verify after Migration
<a name="sectionSection0"> </a>

|**If you use this workload:**|**Verify these policies and settings:**|
|:-----|:-----|
|Instant messaging (IM) and conferencing  <br/> |Presence policy  <br/> Conferencing policy  <br/> |
|Dial-in conferencing  <br/> |Dial-in access numbers  <br/> Dial plans  <br/> |
|Enterprise Voice  <br/> |Voice policy  <br/> Voice routes  <br/> Dial plans  <br/> PSTN usage settings  <br/> |
|Communicator Web Access  <br/> |Simple URLs  <br/> |
|External users  <br/> |External access policies  <br/> |
|Archiving  <br/> |Archiving policy  <br/> |
   
## To verify policies and settings
<a name="sectionSection1"> </a>

1. In your Office Communications Server 2007 R2 environment, make note of the names of dial plans (formerly known as location profiles), dial-in access numbers (Conferencing Attendant access phone numbers and regions), voice routes, and the policies listed in the preceding table, in addition to the URLs used for Communicator Web Access. 
    
2. On the Lync Server 2013 Front End server, open Lync Server Control Panel.
    
3. To verify imported conferencing policies, in the left pane, click **Conferencing**, click **Conferencing Policy**, and then verify that all the conferencing policies in your Office Communications Server 2007 R2 environment are included in the list.
    
    > [!NOTE]
    > The **Meeting** policy from previous versions of Office Communications Server is now known as the conferencing policy in Lync Server 2013. Additionally, the **Anonymous Particpants** setting from previous versions of Office Communications Server is now a setting in the Lync Server 2013 conferencing policy. 
  
    > [!NOTE]
    > In Office Communications Server 2007 R2, if the conferencing policy is not set to **use per user**, only global policy settings are imported. No other conference policies are imported in this situation. 
  
    > [!NOTE]
    > If **Anonymous Participants** is set to **Enforce per user** in your Office Communications Server 2007 R2 conferencing policy, two conferencing policies are created during migration: one with **AllowAnonymousParticipantsInMeetings** set to **True** and one with **AllowAnonymousParticipantsInMeetings** set to **False**. 
  
4. To verify imported dial plans, click **Voice Routing**, click **Dial Plan**, and then verify that all the dial plans in your Office Communicator 2007 R2 environment are included in the list.
    
    > [!NOTE]
    > In Lync Server 2013, **location profiles** are now referred to as **dial-plans**. 
  
5. To verify imported voice policies, click **Voice Routing**, click **Voice Policy**, and then verify that all the voice policies in your Office Communicator 2007 R2 environment are included in the list.
    
    > [!NOTE]
    > If voice policy is not set to **use per user** in your Office Communications Server 2007 R2 environment, only global policy settings are imported. No other voice policies are imported in this situation. 
  
6. To verify imported voice routes, click **Voice Routing**, click **Route**, and then verify that all the voice routes in your Office Communicator 2007 R2 environment are included in the list.
    
7. To verify imported PSTN usage settings, click **Voice Routing**, click **PSTN Usage**, and then verify that the PSTN Usage settings from your Office Communicator 2007 R2 environment are included in the list.
    
8. To verify imported external access policies, click **Federation and External Access**, click **External Access Policy**, and then verify that all the external access policies in your Office Communicator 2007 R2 environment are included in the list.
    
9. To verify archiving policies, click **Monitoring and Archiving**, click **Archiving Policy**, and then verify that all the archiving policies in your Office Communications Server 2007 R2 environment are included in the list.
    
10. Open the Lync Server Management Shell.
    
11. To verify presence policies, at the command line, type the following:
    
  ```
  Get-CsPresencePolicy
  ```

    By looking at the name in the **Identity** parameter, verify that all the presence policies in your Office Communications Server 2007 R2 environment were imported. 
    
## To verify policies and settings by using cmdlets
<a name="sectionSection2"> </a>

1. Open the Lync Server Management Shell.
    
2. Run the cmdlets in the following table to verify policies and settings.
    
    The syntax of these cmdlets is like the following example:
    
  ```
  Get-CsConferencingPolicy
  ```

    For details about these cmdlets, run:
    
  ```
  Get-Help <cmdlet name> -Detailed
  ```

|**For this policy or setting:**|**Use this cmdlet:**|
|:-----|:-----|
|Presence policy  <br/> |**Get-CsPresencePolicy** <br/> |
|Conferencing policy  <br/> |**Get-CsConferencingPolicy** <br/> |
|Dial-in access numbers  <br/> |**Get-CsDialInConferencingAccessNumber** <br/> |
|Dial plans  <br/> |**Get-CsDialPlan** <br/> |
|Voice policy  <br/> |**Get-CsVoicePolicy** <br/> |
|Voice routes  <br/> |**Get-CsVoiceRoute** <br/> |
|PSTN Usage  <br/> |**Get-CsPstnUsage** <br/> |
|URLs  <br/> |**Get-CsSimpleUrlConfiguration** <br/> |
|External access policies  <br/> |**Get-CsExternalAccessPolicy** <br/> |
|Archiving policy  <br/> |**Get-CsArchivingPolicy** <br/> |
   

