---
title: "Adding commands to Lync menus in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 4/11/2016
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: a8443bc2-e234-4022-870a-00700f38b1ea

description: "You can add custom commands to Lync 2013 menus and pass the SIP Uniform Resource Identifier (URI) of the current user and selected contacts to the application that the custom command starts."
---

# Adding commands to Lync menus in Lync Server 2013
[]
You can add custom commands to Lync 2013 menus and pass the SIP Uniform Resource Identifier (URI) of the current user and selected contacts to the application that the custom command starts.
  
The custom commands that you add can appear on one or more of the following menus:
  
- The Tools menu, on the menu bar in the Lync main window
    
- The shortcut menu for contacts in the Contacts list
    
- The More Options menu, in the Conversation window
    
- The shortcut menu for people listed in the Conversation window participant list
    
- The options menu in a contact card 
    
You can define custom commands for two types of applications—applications that do either of the following:
  
- Apply only to the current user and are started on the local computer.
    
- Involve additional users, such as an online collaboration program, and must be started on each user's computer.
    
The custom command can be invoked in the following ways:
  
- Select one or more users, and then choose the custom command.
    
- Start a two-party or multiparty conversation, and then choose the custom command.
    
## To add a custom command

Use the registry settings in the following table to add a command to the menus. These entries are placed in the registry at one of the following locations:
  
- For 32bit OS: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\15.0\Lync\SessionManager\Apps
    
- For 64bit OS: HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Office\15.0\Lync\SessionManager\Apps
    
**Custom Command Registry Entries**

|**Name**|**Type**|**Data**|
|:-----|:-----|:-----|
|Name  <br/> |REG_SZ  <br/> |Name of the application as it appears on the menu.  <br/> |
|ApplicationType  <br/> |DWORD  <br/> |0 = Executable (default)  <br/> > [!NOTE]> Requires ApplicationInstallPath.           1 = Protocol  <br/> |
|ApplicationInstallPath  <br/> |REG_SZ  <br/> |Full path of the executable.  <br/> > [!NOTE]> Must be specified if ApplicationType is 0 (Executable).           |
|Path  <br/> |REG_SZ  <br/> |Full path to be started along with any parameters, including the default parameters  _%user-id%_ and  _%contact-id%_.  <br/> |
|SessionType  <br/> |DWORD  <br/> |0 = Local session. The application is started on the local computer.  <br/> 1 = Two-party session (default). Lync 2013 starts the application locally and then sends a desktop notification to the other user. The other user clicks the notification to start the application on their computer.  <br/> 2 = Multiparty session. Lync 2013 starts the application locally and then sends desktop notifications to the other users. The other user clicks the notification to start the specified application on their computer.  <br/> |
|ExtensibleMenu  <br/> |REG_SZ  <br/> |A list of the menus where this command will appear, separated by semicolons. Possible values are:  <br/> MainWindowActions  <br/> MainWindowRightClick  <br/> ConversationWindowActions  <br/> ConversationWindowRightClick  <br/> ContactCardMenu  <br/> If ExtensibleMenu is not defined, the default values of MainWindowRightClick and ConversationWindowActions are used.  <br/> |
   
For example, the following Registry Editor (.REG) file shows the results of adding a Contoso Sales Contact Manager menu item to Actions menu in the Conversation window:
  
```
Windows Registry Editor Version 5.00
[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Office\15.0\Lync\SessionManager\Apps\{1F9F07C6-7E0B-462B-AAD7-98C6DBEA8F69}]
"Name"="Contoso Sales Contact Manager"
"HelpMessage"="The Contoso Sales Contact Manager is not installed. Contact the Help Desk for more information."
"ApplicationType"=dword:00000000
"ApplicationInstallPath"="C:\\cscm.exe"
"Path"="C:\\cscm.exe %user-id% %contact-id%"
"SessionType"=dword:00000001
"ExtensibleMenu"="ConversationWindowActions;MainWindowRightClick"
```

## To access a custom command

To access a custom command after it is added, do one of the following, depending on the ExtensibleMenu values that you define:
  
- **MainWindowActions** In the Lync main window, click **Tools**, and then click your custom command.
    
- **MainWindowRightClick** In the Lync main window, right-click a contact, and then click your custom command. 
    
- **ConversationWindowActions** In the Conversation window, click the **More Options** icon, and then click your custom command. 
    
- **ConversationWindowRightClick** In the Conversation window, right-click a contact name, and then click your custom command. 
    

