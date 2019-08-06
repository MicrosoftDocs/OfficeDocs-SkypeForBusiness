---
title: "Enable users for Enterprise Voice in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: quickstart
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom: 
ms.assetid: f252b23b-9641-4160-aa81-bf06dc2eced3
description: "Summary: Learn how to enable users to make and receive calls by using Enterprise Voice in Skype for Business Server."
---

# Enable users for Enterprise Voice in Skype for Business Server
 
**Summary:** Learn how to enable users to make and receive calls by using Enterprise Voice in Skype for Business Server.
  
After you deploy Enterprise Voice or Call Via Work, you can use the following procedures to enable a user to make calls by using Enterprise Voice:
  
> [!NOTE]
> Of the following procedures, only the first can be performed by using Skype for Business Server Control Panel. For the remaining procedures, you can use only Skype for Business Server Management Shell. 
  
- Enable the user account for Enterprise Voice.
    
- (Optional) Assign the user account a user-specific voice policy.
    
- (Optional) Assign the user account a user-specific dial plan.
    
### To enable a user account for Enterprise Voice

1. Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the **CsVoiceAdministrator**, **CsServerAdministrator**, or **CsAdministrator** administrative role.
    
2. Open Skype for Business Server Control Panel.
    
3. In the left navigation bar, click **Users**.
    
4. In the **Search users** box, type all or the first portion of the display name, first name, last name, Security Accounts Manager (SAM) account name, SIP address, or line Uniform Resource Identifier (URI) of the user account that you want to enable, and then click **Find**.
    
5. In the table, click the user account that you want to enable for Enterprise Voice.
    
6. On the **Edit** menu, click **Show details**.
    
7. On the **Edit Skype for Business Server User** page, under **Telephony**, click **Enterprise Voice**.
    
8. Click **Line URI**, and then type a unique, normalized phone number (for example, tel:+14255550200).
    
9. Click **Commit**.
    
To finish enabling a user for Enterprise Voice, be sure that the user is assigned a voice policy and a dial plan, whether global (assigned by default) or user-specific.By default, all users are assigned a global voice policy and dial plan. If a voice policy or dial plan exists at the site level for the site on which the user account is homed, those site policies will automatically apply to the user. To apply a per-user voice policy or dial plan to a user, you must run the **Grant-CsVoicePolicy** and **Grant-CsDialPlan** cmdlets. For details, see the following procedures in this topic.
## Voice Policy Assignment

Global and site-level voice policies are automatically assigned to all user accounts that are enabled for Enterprise Voice. You can also create voice policies that apply to specific users or groups. These per-user policies must be explicitly assigned to the users or groups. If you want to use the global or site voice policy for all users who are enabled for Enterprise Voice, you can skip this section and continue to [Dial Plan Assignment](enable-users-for-enterprise-voice.md#BKMK_DialPlanAssignment) section later in this topic.
  
### To assign a user-specific voice policy

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.
    
3. To assign an existing user voice policy to a user, run the following at the command prompt:
    
   ```
   Grant-CsVoicePolicy -Identity <UserIdParameter> -PolicyName <String>
   ```

    For example:
    
   ```
   Grant-CsVoicePolicy -Identity "Bob Kelly" -PolicyName VoicePolicyJapan
   ```

    In this example, the user with the display name Bob Kelly is assigned the voice policy with the name **VoicePolicyJapan**.
    
## Dial Plan Assignment
<a name="BKMK_DialPlanAssignment"> </a>

To complete user account configuration for either users of Enterprise Voice or users of dial-in conferencing, the user must be assigned a dial plan. User accounts will automatically use the global dial plan or, if one exists, the site-level dial plan, when you do not explicitly assign an existing per-user dial plan. If you want to use the global or site dial plan for all users who are enabled for Enterprise Voice, you can skip this section.
  
### To assign a user-specific dial plan

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.
    
3. To assign a user-specific dial plan, run the following at the command prompt:
    
   ```
   Grant-CsDialPlan -Identity <UserIdParameter> -PolicyName <String>
   ```

    For example:
    
   ```
   Grant-CsDialPlan -Identity "Bob Kelly" -PolicyName DialPlanJapan
   ```

    In this example, the user with the display name Bob Kelly is assigned the user dial plan with the name **DialPlanJapan**.
    

