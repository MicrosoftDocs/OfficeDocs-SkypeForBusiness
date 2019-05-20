---
title: "Configure the client experience with Skype for Business 2015"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 66867a96-ff00-497d-889c-2e908cc384ce
description: "Summary: Read this topic to learn how to configure the client experience for Skype for Business users."
---

# Configure the client experience with Skype for Business 2015
 
**Summary:** Read this topic to learn how to configure the client experience for Skype for Business 2015 users.
  
Skype for Business 2015 provides a new user experience that is based on the Skype consumer product experience. In addition to all the features of Lync, Skype for Business provides new features with simplified controls and familiar icons. For detailed information about the new client experience, see [Explore Skype for Business](https://go.microsoft.com/fwlink/?LinkId=529022).
  
Skype for Business Server supports the new Skype for Business client experience as well as the Lync client experience. As an administrator, you can choose the preferred client experience for your users. For example, you might want to deploy the Lync client experience until users in your organization are fully trained in the new Skype for Business experience. Or, if you have not yet upgraded all users to Skype for Business Server, you might want all users to have the same client experience until all are upgraded to the new server.
  
> [!IMPORTANT]
> If your organization has both Skype for Business Server and Lync Server deployed, the default client experience will differ depending on server versions and UI settings. When users launch Skype for Business for the first time, they will always see the Skype for Business user interface--even if you have selected the Lync client experience. After several minutes, users are asked to switch to Lync mode. For more information, see **First launch client behavior** later in this topic.
  
> [!NOTE]
> The Lync 2013 client experience is not an option for Skype for Business 2016 client versions or later. Before you attempt to configure your client environment to use the Lync 2013 client, please check the client version to ensure it does not start with the number 16; for example: 16.x.x.x. 
  
## Configure the client experience

You can specify the client experience the users in your organization will see by using the **Set-CSClientPolicy** cmdlet with the EnableSkypeUI parameter:
  
```
Set-CsClientPolicy  [-Identity <XdsIdentity] [-EnableSkypeUI <$true | $false>]
```

where XdsIdentity refers to the Global policy or a named site policy.
  
The following command selects the Skype for Business client experience for all users in your organization affected by the Global policy (remember, site or user-specific policies override the Global policy): 
  
```
Set-CsClientPolicy -Identity Global -EnableSkypeUI $true
```

The next command selects the Lync client experience for all users in your organization affected by the Global policy:
  
```
Set-CsClientPolicy -Identity Global -EnableSkypeUI $false
```

The next command selects the Skype for Business client experience for all users within the Redmond site:
  
```
Set-CsClientPolicy -Identity site:Redmond -EnableSkypeUI $true
```

If you want to configure the client experience for specific users within your organization, you can create a new user policy by using the **New-CsClientPolicy** cmdlet, and then assign the policy to specific users by using the **Grant-CsClientPolicy** cmdlet.
  
For example, the following command creates a new client policy, SalesClientUI, that selects the Skype for Business client experience:
  
```
New-CsClientPolicy -Identity SalesClientUI -EnableSkypeUI $true
```

The next command assigns the policy, SalesClientUI, to all members of the Sales department:
  
```
Get-CsUser -LDAPFilter "Department=Sales" | Grant-CsClientPolicy -PolicyName SalesClientUI
```

## First launch client behaviors

By default, when users launch Skype for Business 2015 for the first time, they will always see the Skype for Business user interface--even if you have selected the Lync client experience by setting the value of the EnableSkypeUI parameter to $False as described previously. After several minutes, users will then be asked to switch to Lync mode.
  
If you want to display the Lync user interface when users launch the Skype for Business client for the first time, follow these steps before the client is started for the first time after being updated:
  
1. Confirm that the value of  `EnableSkypeUI` is set to $False in the policy you are using as described previously.
    
2. Update the system registry on the user's computer. You should do this before the first time users launch the Skype for Business client, and you should do this only once. For information about how to create a Group Policy Object to update the registry on a domain joined computer, see the section later in the topic.
    
    In the **[HKEY_CURRENT_USER\Software\Microsoft\Office\Lync]** key, create a new **Binary** value.
    
    The **Value name** must be **EnableSkypeUI**, and the **Value data** must be set to **00 00 00 00**.
    
    The key should look like the following:
    
   <pre>
   [HKEY_CURRENT_USER\Software\Microsoft\Office\Lync]
   "CanSharePptInCollab"=dword:00000001
   "CanShareOneNoteInCollab"=dword:00000001
   "CanAppShareInCollab"=dword:00000001
   "EnableSkypeUI"=hex:00,00,00,00
   </pre>

The Lync user interface will now be displayed when users launch the Skype for Business client for the first time.
  
### Control the display of the Welcome screen tutorial

When users open the Skype for Business client, the default behavior is to display a Welcome screen that includes  *7 Quick tips most people ask for*. You can turn off the display of the Welcome screen but still allow users to access the tutorial by adding the following Registry value on the client computer:
  
In the **[HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Lync]** key, create a new **DWORD (32-bit) Value**. The **Value name** must be **IsBasicTutorialSeenByUser**, and the **Value data** must be set to **1**.
  
The key should look like the following:
  
`"IsBasicTutorialSeenByUser"=dword:00000001`

### Turn off the client tutorial

If you do not want your users to be able to access the tutorial, you can turn off the client tutorial with the following Registry value:
  
In the **[HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Lync]** key, create a new **DWORD (32-bit) Value**. The **Value name** must be **TutorialFeatureEnabled**, and the **Value data** must be set to **0**.
  
Lync
  
```
"TutorialFeatureEnabled"=dword:00000000
```

You can turn the tutorial back on by setting the **Value data** to **1**.
  
## Default client behaviors

If your organization has both Skype for Business Server and Lync Server deployed, the client experience will differ depending on server versions and the Skype UI setting. The following table shows the initial client experience based on server version and the UI setting:
  

|**Server version**|**EnableSkypeUI setting**|**Client experience**|
|:-----|:-----|:-----|
|Skype for Business Server |Default  <br/> |Skype for Business  <br/> |
|Skype for Business Server  |True  <br/> |Skype for Business  <br/> |
|Skype for Business Server  |False  <br/> |User asked to switch to Lync mode (user can switch to Skype for Business later if you change the UI setting to $true)  <br/> |
|Lync Server 2010 or Lync Server 2013 (with correct patches)  <br/> |Default  <br/> |User asked to switch to Lync mode (user can switch to Skype for Business later if you change the UI setting to $true)  <br/> |
|Lync Server 2010 or Lync Server 2013 (with correct patches)  <br/> |True  <br/> |Skype for Business  <br/> |
|Lync Server 2010 or Lync Server 2013 (with correct patches)  <br/> |False  <br/> |User asked to switch to Lync mode (user can switch to Skype for Business later if you change the UI setting to $true)  <br/> |
|Lync Server 2010 or Lync Server 2013 (without patches)  <br/> |Default  <br/> |User asked to switch to Lync mode (user cannot switch to Skype for Business later)  <br/> |
   
The next table shows the client experience when the administrator changes the initial setting for the Skype UI experience:
  

|**Server version**|**EnableSkypeUI setting**|**Client UI = Lync**|**Client UI = Skype for Business**|
|:-----|:-----|:-----|:-----|
|Skype for Business Server |True  <br/> |User asked to switch to Skype for Business  <br/> |Skype for Business  <br/> |
|Skype for Business Server |False  <br/> |Lync mode  <br/> |User asked to switch to Lync mode  <br/> |
|Lync Server 2010 or Lync Server 2013 (with correct patches)  <br/> |True  <br/> |User asked to switch to Skype for Business  <br/> |Skype for Business  <br/> |
|Lync Server 2010 or Lync Server 2013 (with correct patches)  <br/> |False  <br/> |Lync mode  <br/> |User asked to switch to Lync mode  <br/> |
|Lync Server 2010 or Lync Server 2013 (without patches)  <br/> |Default  <br/> |Lync mode (cannot switch to Skype for Business)  <br/> |Lync mode (cannot switch to Skype for Business)  <br/> |
   
The patch versions required to manage the configuration of the Skype for Business client are:
  
- Lync Server 2010 - February 2015 Cumulative Update (4.0.7577.710) for Lync Server 2010. For information, see [Updates for Lync Server 2010](https://go.microsoft.com/fwlink/p/?LinkId=532771)
    
- Lync Server 2013 - December 2014 Cumulative Update (5.0.8308.857) for Lync Server 2013. For information, see [Updates for Lync Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=532772).
    
## Create a Group Policy Object to modify the registry on a domain joined computer

The registry update to display the Lync client experience the first time a user launches the Skype for Business 2015 client should be done only once. If you use a Group Policy Object (GPO) to update the registry, you need to define the object to create a new value rather than update the Value data. When the GPO is applied, if the new value does not exist, the GPO will create it and set the Value data to 0. 
  
The following procedure describes how to modify the registry so that the Lync client experience is displayed the first time a user launches the Skype for Business 2015 client. You can also use this procedure to update the registry to disable the Welcome screen tutorial as described earlier.
  
### To create the GPO

1. Start the **Group Policy Management console**.
    
    For information about how to use the Group Policy Management Console, see [Group Policy Management Console](https://go.microsoft.com/fwlink/?LinkId=532759).
    
2. Right-click the **Group Policy Objects** node and select **New** on the menu.
    
3. In the **New GPO** dialog, enter a name for the GPO, for example,MakeLyncDefaultUI, and then click **OK**.
    
4. Right-click on the new GPO you just created and then select **Edit** from the menu.
    
5. In the **Group Policy Management Editor**, expand **User Configuration**, expand **Preferences**, expand **Windows Settings**, and then select the **Registry** node.
    
6. Right-click on the **Registry** node, and then select **New** > **Registry Item**.
    
7. On the **New Registry Properties** dialog, update the following:
    
   |**Field**|**Value to select or enter**|
   |:-----|:-----|
   |**Action** <br/> |**Create** <br/> |
   |**Hive** <br/> | HKEY_CURRENT_USER <br/> |
   |**Key Path** <br/> |Software\Microsoft\Office\Lync  <br/> |
   |**Value name** <br/> |EnableSkypeUI  <br/> |
   |**Value type** <br/> |REG_BINARY  <br/> |
   |**Value data** <br/> |00000000  <br/> |
   
8. Click **OK** to save your changes, and then close the GPO.
    
Next, you'll need to link the GPO you created to the group of users that you want to assign the policy to, such as an OU.
  
### To use the GPO to assign the policy

1. In the Group Policy Management Console, right-click on the OU you want to assign the policy to, and then select **Link to an existing GPO**.
    
2. On the **Select GPO** dialog, select the GPO you created, and then select **OK**.
    
3. On the target user's computer, open a command prompt and type the following command:
       
```
gpupdate /target:user
```

    
    The message "Updating policy..." is displayed while the GPO is applied. When it is completed, the message "User Policy update has completed successfully" is displayed.
    
4. At the command prompt, type the following command:
    
    **gpresult /r**
    
    You should see "Assigned Group Policy Objects" with the name of the GPO you created displayed below.
    
You can also verify that the GPO has successfully updated the registry on a user's computer by examining the registry. Open Registry Editor and navigate to the **[HKEY_CURRENT_USER\Software\Microsoft\Office\Lync]** key. If the GPO successfully updated the registry you will see a value named EnableSkypeUI with a value of 0.
  

