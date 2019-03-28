---
title: "Configure dial-in conferencing in Skype for Business Server"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 38d9f168-80b8-46f2-a1c0-becd84e58e73
description: "Summary: Read this topic to learn how to configure dial-in conferencing in Skype for Business Server."
---

# Configure dial-in conferencing in Skype for Business Server
 
**Summary:** Read this topic to learn how to configure dial-in conferencing in Skype for Business Server.
  
After you have created a topology that includes the conferencing workload and selected dial-in conferencing, you must perform additional steps to configure dial-in conferencing. Before you read this topic, be sure you have read [Plan for dial-in conferencing in Skype for Business Server](../../plan-your-deployment/conferencing/dial-in-conferencing.md), [Hardware and software requirements for conferencing in Skype for Business Server](../../plan-your-deployment/conferencing/hardware-and-software-requirements.md), and the [Deployment flowchart and checklist for dial-in conferencing](deploy-conferencing.md#deployment-flowchart-and-checklist-for-dial-in-conferencing). 
  
To configure dial-in conferencing, you must perform the following tasks:
  
- [Configure dial plans](dial-in-conferencing.md#BKMK_ConfigureDialPlans)
    
- [Configure dial-in conferencing regions](dial-in-conferencing.md#BKMK_ConfigureDialInRegions)
    
- [Configure dial-in access numbers](dial-in-conferencing.md#BKMK_ConfigureDialInAccessNumbers)
    
- [Configure conferencing policies](dial-in-conferencing.md#BKMK_ConfigureConferencingPolicies)
    
- [Assign a Line URI to a user account](dial-in-conferencing.md#BKMK_AssignaLineURI)
    
In addition, you may perform the following optional tasks. For more information about these optional tasks, see [Manage dial-in conferencing in Skype for Business Server](../../manage/conferencing/dial-in-conferencing.md).
  
- Manage PIN policies for dial-in conferencing
    
- Manage key mapping for DTMF commands
    
- Create conference directories
    
- Manage conference join and leave announcements
    
- Test dial-in conferencing settings
    
- Send welcome mail to dial-in users
    
## Configure dial plans
<a name="BKMK_ConfigureDialPlans"> </a>

When you deploy dial-in conferencing, you need to create or modify one or more dial plans for routing dial-in access phone numbers. You must also make sure that each dial plan contains at least one normalization rule--a rule that converts telephone extensions into complete phone numbers in E.164 format. 
  
Users of dial-in conferencing join conferences as authenticated enterprise users by entering their personal identification number (PIN) and their phone number. You need a normalization rule to convert extensions into complete phone numbers so that users can be authenticated when they enter just a telephone extension.
  
To set up dial plans for dial-in conferencing:
  
- Whether or not you deploy Enterprise Voice, modify the global dial plan to add a dial-in conferencing region and to make sure that a normalization rule accurately converts your dial-in access numbers. For detailed instructions, see [Create or modify a dial plan in Skype for Business Server](../../deploy/deploy-enterprise-voice/dial-plans.md).
    
- If you did not deploy Enterprise Voice, create dial plans for your dial-in conferencing access numbers. Be sure to include a dial-in conferencing region. For detailed instructions, see [Create or modify a dial plan in Skype for Business Server](../../deploy/deploy-enterprise-voice/dial-plans.md).
    
- If you deployed Enterprise Voice, modify Enterprise Voice dial plans as necessary to include regions and use appropriate normalization rules for dial-in access numbers. You can also create dedicated dial plans that are used only for dial-in access numbers. For detailed instructions, see [Create or modify a dial plan in Skype for Business Server](../../deploy/deploy-enterprise-voice/dial-plans.md).
    
For details about creating normalization rules, see [Create or modify a normalization rule in Skype for Business](../../deploy/deploy-enterprise-voice/normalization-rules.md).
  
## Configure dial-in conferencing regions
<a name="BKMK_ConfigureDialInRegions"> </a>

When you set up a dial plan, you specify the dial-in conferencing region that applies to that dial plan. The dial-in conferencing region associates dial-in conferencing access numbers with the appropriate dial plan. When you create the dial-in access number, you select the regions that associate the access number with the appropriate dial plans. 
  
Because it important to specify a region for all dial plans, we recommend that you verify that all dial plans have conferencing regions. 
  
To verify whether the region is set for all dial-in conferencing dial plans, use the **Get-CsDialPlan** cmdlet. If the region is missing from dial plans, you can use the **Set-CsDialPlan** cmdlet to set the region. You can also use Skype for Business Server Control Panel to update the region in existing dial plans. For details about using Skype for Business Server Control Panel, see [Create or modify a dial plan in Skype for Business Server](../../deploy/deploy-enterprise-voice/dial-plans.md).
  
### To verify whether dial plans have the region property set

1. Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the **Cs-VoiceAdministrator**, **Cs-ServerAdministrator**, or **CsAdministrator** role.
    
2. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.
    
3. Run the following at the command prompt:
    
   ```
   Get-CsDialPlan [-Identity <Identifier of the dial plans to be retrieved>]
   ```

   For example:
    
   ```
   Get-CsDialPlan
   ```

   In this example, all the dial plans configured for your organization are returned.
    
4. Review the returned dial plans to identify any that are missing the dial-in conferencing region. 
    
For more information, see [Get-CsDialPlan](https://docs.microsoft.com/powershell/module/skype/get-csdialplan?view=skype-ps).
  
### To set the region property for a dial plan

1. Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the **Cs-VoiceAdministrator**, **Cs-ServerAdministrator**, or **CsAdministrator** role.
    
2. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.
    
3. For any dial plans that are missing the dial-in conferencing region, run:
    
   ```
   Set-CsDialPlan [-Identity <Identity of the dial plan to be modified>] -DialinConferencingRegion "<new region>"
   ```

   For example:
    
   ```
   Set-CsDialPlan -Identity Redmond -DialinConferencingRegion "US West Coast"
   ```

   In this example, the dial plan with the Identity of Redmond is modified to set the DialinConferencingRegion property to "US West Coast". 
    
For more information, see [Set-CsDialPlan](https://docs.microsoft.com/powershell/module/skype/set-csdialplan?view=skype-ps).
  
## Configure dial-in access numbers
<a name="BKMK_ConfigureDialInAccessNumbers"> </a>

When you deploy dial-in conferencing, you need to set up phone numbers that users can dial from the public switched telephone network (PSTN) to join the audio portion of conferences. These dial-in access numbers appear in meeting invitations and on the Dial-in Conferencing Settings webpage.
  
Before you can create dial-in access numbers, you must first plan your dial-in conferencing regions and then configure dial plans with the regions. For details about regions, see [Plan for dial-in conferencing in Skype for Business Server](../../plan-your-deployment/conferencing/dial-in-conferencing.md). For details about configuring dial plans for dial-in conferencing, see [Create or modify a dial plan in Skype for Business Server](../../deploy/deploy-enterprise-voice/dial-plans.md).
  
> [!NOTE]
> You cannot use a new dial-in access number until Active Directory Domain Services (AD DS) replication of that access number is complete. Replication can take several hours to complete. 
  
> [!NOTE]
> After you create dial-in access numbers, you can modify the display name for the Active Directory contact objects so that users can more easily identify the correct access number. To modify the display name, use the [Set-CsDialInConferencingAccessNumber](https://docs.microsoft.com/powershell/module/skype/set-csdialinconferencingaccessnumber?view=skype-ps) cmdlet. You should not modify Active Directory objects manually.
  
### To create a dial-in access number

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open Skype for Business Server Control Panel.
    
3. In the left navigation bar, click **Conferencing** and then click **Dial-in Access Number**.
    
4. On the **Dial-in Access Number** page, do one of the following:
    
   - Click **New** to open **New Dial-in Access Number**.
    
   - Click one of the dial-in access numbers in the list, click **Edit**, and then click **Show details**.
    
     > [!NOTE]
     > Using the search field to search for the contents of a column in the list of dial-in access numbers may not yield the results you expect. Instead, sort the list by the column of interest to identify the dial-in access number you want to view or change. 
  
5. In **Display number**, type the phone number that public switched telephone network (PSTN) phone users dial to join a conference. This number is displayed in meeting invitations and on the Dial-in Conferencing Settings webpage.
    
6. In **Display name**, type a description for the dial-in access number. This is the name that is associated with the dial-in access number in Skype for Business search results. This name is displayed in the client when a user calls the access number. 
    
7. In **Line URI**, type the E.164 number of the dial-in access number in TEL URI format, including the + symbol before the number and excluding spaces. For example, tel:+14255550200.
    
    > [!NOTE]
    > The same Line URI cannot be reused by another dial-in conferencing access number. 
  
8. In **SIP URI**, do the following:
    
   - In the text box, type a unique SIP URI for this dial-in conferencing access number. This SIP URI is displayed in various locations including, but not limited to, call notification messages and previous versions of Lync clients.
    
     > [!NOTE]
     > The same SIP URI cannot be reused by another dial-in conferencing access number. The SIP URI cannot be modified after the access number is created. The only way to change the SIP URI is to delete and recreate the access number. 
  
   - In the drop-down list box, click the domain of the Conferencing Attendant application that supports this dial-in access number.
    
9. In **Pool**, click the pool that is running the instance of Conferencing Attendant that supports this dial-in access number.
    
    > [!NOTE]
    > If you need to change the pool after you create the access number, you must use the [Move-CsApplicationEndpoint](https://docs.microsoft.com/powershell/module/skype/move-csapplicationendpoint?view=skype-ps) cmdlet or delete and recreate the access number.
  
10. In **Primary language**, click the language in which prompts are played for this dial-in access number. 
    
    The primary language is the language that the Conferencing Attendant uses to answer the call. Supported languages are displayed alongside each access phone number on the Dial-in Conferencing Settings webpage.
    
11. (Optional) In **Secondary languages (maximum of four)**, click **Add**, select one or more additional languages that you want to support for callers to this dial-in access number, and then click **OK**. 
    
    You can choose up to four secondary languages for each dial-in access number. Users can select a secondary language before entering the conference ID when they dial in to a conference.
    
12. To add a region for the dial-in access number, under **Associated regions**, click **Add**, click one or more regions that are associated with the dial plans for this dial-in access number, and then click **OK**.
    
13. To delete a region from the dial-in access number, under **Associated regions**, click the region you want to delete, and then click **Remove**.
    
14. Click **Commit**.
    
## Configure conferencing policies
<a name="BKMK_ConfigureConferencingPolicies"> </a>

Conferencing policy is a user account setting that specifies the conferencing experience for participants. You can create conferencing policies with a site scope or a user scope. Conferencing policy settings encompass many aspects of conference scheduling and participation. Several conferencing policy settings support dial-in conferencing for participants. When you configure dial-in conferencing, you should verify that these fields are set appropriately for your organization, and modify them as necessary. 
  
For more information about configuring conferencing policies, see [Manage conferencing policies in Skype for Business Server](../../manage/conferencing/conferencing-policies.md).
  
## Assign a Line URI to a user account
<a name="BKMK_AssignaLineURI"> </a>

Dial-in users enter their phone number or extension and a PIN to join conferences as authenticated users. The telephony **Line URI** specified on Skype for Business Server user accounts is required for authentication.
  
The procedure in this topic describes how to assign a **Line URI** for a single user account. If you need to assign a **Line URI** for multiple user accounts, you can create a script that uses the **Set-CsUser** cmdlet. For details about using a sample script to assign **Line URI** to multiple user accounts, see [Assign Line URIs to Multiple Users](https://go.microsoft.com/fwlink/p/?linkId=196945).
  
1. Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the **Cs-UserAdministrator** or **CsAdministrator** role.
    
2.  Open Skype for Business Server Control Panel.
    
3. In the left navigation bar, click **Users**.
    
4. In the search field, type the name of the user you want to configure for dial-in conferencing or click **Add filter** to specify search fields, and then click **Find**.
    
5. Double-click the user name to open the **Edit Skype for Business Server User** dialog box.
    
6. Under **Telephony**, in the **Line URI** field, type a unique, normalized phone number (for example, tel:+14255550200).
    
    > [!NOTE]
    > You can specify **Line URI** only if **Telephony** is set to **PC-to-PC only**, **Enterprise Voice**, **Remote call control** or **Remote call control only**. 
  
7. Click **Commit**.
    

