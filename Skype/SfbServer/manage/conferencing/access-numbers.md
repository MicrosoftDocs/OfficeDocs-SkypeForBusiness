---
title: "Manage dial-in conferencing access numbers in Skype for Business Server "
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: a0d64779-93de-4d82-ae35-e4454ef8b8f6
description: "Summary: Learn how to manage dial-in conferencing access numbers in Skype for Business Server."
---

# Manage dial-in conferencing access numbers in Skype for Business Server
 
**Summary:** Learn how to manage dial-in conferencing access numbers in Skype for Business Server.
  
When you deploy dial-in conferencing, you need to set up phone numbers that users can dial from the public switched telephone network (PSTN) to join the audio portion of conferences. These dial-in access numbers appear in meeting invitations and on the Dial-in Conferencing Settings webpage. 
  
This topic describes how to view, modify, or delete existing dial-in conferencing access numbers. For more information about how to create initial dial-in access numbers, see [Configure dial-in conferencing in Skype for Business Server](../../deploy/deploy-conferencing/dial-in-conferencing.md).
  
## View dial-in conferencing access numbers

You can view dial-in conferencing access numbers by using Skype for Business Server Control Panel or by using Skype for Business Server Management Shell.
  
### View dial-in access numbers by using Skype for Business Server Control Panel

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2.  Open Skype for Business Server Control Panel.
    
3. In the left navigation bar, click **Conferencing**, and then click **Dial-in Access Number**.
    
4. On the **Dial-in Access Number** page, click the access number that you would like to view.
    
5. In **Edit**, select the **Show Details** check box.
    
### View dial-in access numbers by using Skype for Business Server Management Shell

To view information about dial-in access numbers, use the **Get-CsDialInConferencingAccessNumber** cmdlet.
  
The following command returns a collection of all the dial-in conferencing access numbers configured for use in the organization: 
  
```
Get-CsDialInConferencingAccessNumber
```

The following is an example of the type of information returned:
  
<pre>
Identity           : CN={20ca8dc8-5ff8-41f4-b5bb-22ba9972ae2e},
                     CN=Application Contacts,CN=RTCService=Services,
                     CN=Configuration,DC=litwareinc,DC=com
PrimaryUri         : sip:testnumber@litwareinc.com
DisplayName        : Test
DisplayNumber      : 1-425-555-1019
LineUri            : tel:+14255551019
PrimaryLanguage    : en-US
SecondaryLanguages : {}
Pool               : atl-cs-001.litwareinc.com
HostingProvider    :
Regions            : {US}
</pre>

For more information, see [Get-CsDialInConferencingAccessNumber](https://docs.microsoft.com/powershell/module/skype/get-csdialinconferencingaccessnumber?view=skype-ps).
  
## Modify dial-in conferencing access numbers

You can modify dial-in access numbers by using Skype for Business Server Control Panel or by using Skype for Business Server Management Shell.
  
### Modify dial-in access numbers by using Skype for Business Server Control Panel

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2.  Open Skype for Business Server Control Panel.
    
3. In the left navigation bar, click **Conferencing**, and then click **Dial-in Access Number**.
    
4. On the **Dial-in Access Number** page, click one of the dial-in access numbers in the list, click **Edit**, and then click **Show details**.
    
    > [!NOTE]
    > Using the search field to search for the contents of a column in the list of dial-in access numbers may not yield the results you expect. Instead, sort the list by the column of interest to identify the dial-in access number you want to view or change. 
  
5. In **Display number**, type the phone number that public switched telephone network (PSTN) phone users dial to join a conference. 
    
    This number is displayed in meeting invitations and on the Dial-in Conferencing Settings webpage.
    
6. In **Display name**, type a description for the dial-in access number. This is the name that is associated with the dial-in access number in Skype for Business search results.
    
    This name is displayed in the client when a user calls the access number. 
    
7. In **Line URI**, type the E.164 number of the dial-in access number in TEL URI format, including the + symbol before the number and excluding spaces. For example, tel:+14255550200.
    
    > [!NOTE]
    > The same Line URI cannot be reused by another dial-in conferencing access number. 
  
8. In **SIP URI**, do the following:
    
   In the text box, type a unique SIP URI for this dial-in conferencing access number. This SIP URI is displayed in various locations including, but not limited to, call notification messages and previous versions of Lync clients.
    
    > [!NOTE]
    > The same SIP URI cannot be reused by another dial-in conferencing access number. The SIP URI cannot be modified after the access number is created. The only way to change the SIP URI is to delete and recreate the access number. 
  
   In the drop-down list box, click the domain of the Conferencing Attendant application that supports this dial-in access number.
    
9. In **Pool**, click the pool that is running the instance of Conferencing Attendant that supports this dial-in access number.
    
    > [!NOTE]
    > If you need to change the pool after you create the access number, you must use the **Move-CsApplicationEndpoint** cmdlet or delete and recreate the access number.
  
10. In **Primary language**, click the language in which prompts are played for this dial-in access number. 
    
    The primary language is the language that the Conferencing Attendant uses to answer the call. Supported languages are displayed alongside each access phone number on the Dial-in Conferencing Settings webpage.
    
11. (Optional) In **Secondary languages (maximum of four)**, click **Add**, select one or more additional languages that you want to support for callers to this dial-in access number, and then click **OK**. 
    
    You can choose up to four secondary languages for each dial-in access number. Users can select a secondary language before entering the conference ID when they dial in to a conference.
    
12. To add a region for the dial-in access number, under **Associated regions**, click **Add**, click one or more regions that are associated with the dial plans for this dial-in access number, and then click **OK**.
    
13. To delete a region from the dial-in access number, under **Associated regions**, click the region you want to delete, and then click **Remove**.
    
14. Click **Commit**.
    
### Modify dial-in access numbers by using Skype for Business Server Management Shell

To modify dial-in access numbers, use the **Set-CsDialInConferencingAccessNumber** cmdlet.
  
The following command modifies the DisplayName property for the dial-in conferencing access number with the Identity sip:RedmondDialIn@litwareinc.com. In this example, the display name is set to "Redmond Dial-In Access Number":
  
```
Set-CsDialInConferencingAccessNumber -Identity "sip:RedmondDialIn@litwareinc.com" -DisplayName "Redmond Dial-In Access Number"
```

In the next example, the dial-in conferencing access number with the Identity sip:RedmondDialIn@litwareinc.com is modified to include two regions: Redmond and Seattle. To do this, the Regions parameter is called, followed by the two regions (two string values separated by commas). Note that this command will fail unless both the Redmond and Seattle regions have already been defined in dial plans.
  
```
Set-CsDialInConferencingAccessNumber -Identity "sip:RedmondDialIn@litwareinc.com" -Regions "Redmond", "Seattle"
```

For more information, see [Set-CsDialInConferencingAccessNumber](https://docs.microsoft.com/powershell/module/skype/set-csdialinconferencingaccessnumber?view=skype-ps).
  
## Delete a dial-in conferencing access number

You can delete a dial-in conferencing access number by using Skype for Business Server Control Panel or by using Skype for Business Server Management Shell.
  
### Delete a dial-in conferencing access number by using Skype for Business Server Control Panel

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or assigned to the CsServerAdministrator or CsAdministrator role, log on to any computer that is in the network in which you deployed Skype for Business Server.
    
2.  Open Skype for Business Server Control Panel.
    
3. In the left navigation bar, click **Conferencing**, and then click **Dial-in Access Number**.
    
4. On the page, click the dial-in number you want to delete in the list, click **Edit**, and then click **Delete**.
    
5. Click **OK**.
    
### Delete a dial-in conferencing access number by using Skype for Business Server Management Shell

To delete a dial-in conferencing access number, use the **Remove-CsDialInConferencingAccessNumber**.
  
The following command deletes the dial-in conferencing access number with Identity sip:RedmondDialInAccess@litwareinc.com:
  
```
Remove-CsDialInConferencingAccessNumber -Identity "sip:RedmondDialInAccess@litwareinc.com"
```

The next command deletes all the dial-in conferencing access numbers associated with the Northwest region:
  
```
Get-CsDialInConferencingAccessNumber -Region "Northwest" | Remove-CsDialInConferencingAccessNumber
```

The next command deletes all the dial-in conferencing access numbers where Italian is the primary language:
  
```
Get-CsDialInConferencingAccessNumber | Where-Object {$_.PrimaryLanguage -eq "it-IT"} | Remove-CsDialInConferencingAccessNumber
```

For more information, see [Remove-CsDialInConferencingAccessNumber](https://docs.microsoft.com/powershell/module/skype/remove-csdialinconferencingaccessnumber?view=skype-ps).
  

