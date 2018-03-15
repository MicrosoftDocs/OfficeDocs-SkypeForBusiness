---
title: "Integrating a third-party collaboration application with Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 00b9312c-b0c8-4f79-8b76-05b2d820e197
description: "You can integrate Lync 2013 with any third-party online collaboration application by adding information about the application to the registry. You can use Lync 2013 to start data conferencing sessions hosted on an in-house server, an Internet-based service, or both. The collaboration or data conferencing session can be started from the Contacts list or from an existing instant messaging, voice, or video session. Lync 2013 acts only as the vehicle for starting the application. Any existing Lync 2013 conversations remain active after the online collaboration session has begun."
---

# Integrating a third-party collaboration application with Lync Server 2013
[]
You can integrate Lync 2013 with any third-party online collaboration application by adding information about the application to the registry. You can use Lync 2013 to start data conferencing sessions hosted on an in-house server, an Internet-based service, or both. The collaboration or data conferencing session can be started from the Contacts list or from an existing instant messaging, voice, or video session. Lync 2013 acts only as the vehicle for starting the application. Any existing Lync 2013 conversations remain active after the online collaboration session has begun.
  
The following sections describe how to integrate Lync 2013 with Internet-based and server-based collaboration applications. 
  
## Integrating an Internet-Based Collaboration Application with Lync 2013

Generally, the steps involved in integrating a third-party collaboration application are as follows:
  
1. Information about the application is added to the registry.
    
2. The organizer signs in to Lync 2013 and selects contacts for data sharing and collaboration. Or, the organizer may already be in a conversation and decide to add data conferencing.
    
3. Lync 2013 reads the registry, starts the collaboration application, and then sends a custom SIP message—an appINVITE—to the selected participants.
    
4. Participants accept the invitation, and the collaboration application is started on each person's computer. Lync 2013 uses the registry to determine which collaboration application to use, and then starts that application by using the parameters included in the appINVITE message.
    
The following table describes the registry entries required to integrate an Internet-based collaboration application with Lync 2013. These entries are placed in the registry in the following location:
  
- HKEY_LOCAL_MACHINE\Software\Microsoft\Office\15.0\Lync\SessionManager\Apps\Parameters
    
**Registry Entries for an Internet-based Collaboration Application**

|**Name**|**Type**|**Data**|
|:-----|:-----|:-----|
|Name  <br/> |REG_SZ  <br/> |The application name for Lync 2013 menus.  <br/> |
|SmallIcon  <br/> |REG_SZ  <br/> |Path to 16-pixel x 16-pixel icon, BMP or PNG.  <br/> |
|Path  <br/> |REG_SZ  <br/> |Participant path for starting the online collaboration application.  <br/> |
|OriginatorPath  <br/> |REG_SZ  <br/> |Organizer path for starting the online collaboration application. This path can contain one or more custom parameters as defined in the Parameters subkey. For example,  `https://meetserv.adatum.com/cc/%param1%/join?id=%param2%&amp;role=present&amp;pw=%param3%` <br/> |
|SessionType  <br/> |DWORD  <br/> |0 = Local session. The application is started on the local computer.  <br/> 1 = Two-party session (default). Lync 2013 starts the application locally, and then sends a system notification to the other user. The other user clicks the notification and starts the specified application on their computer.  <br/> 2 = Multiparty session. Lync 2013 starts the application locally, and then sends system notifications to the other users, prompting them to start the specified application on their own computer.  <br/> |
|ExensibleMenu  <br/> |REG_SZ  <br/> | A list of the menus where this command will appear, separated by semi-colons. Possible values are:  <br/>  MainWindowActions  <br/>  MainWindowRightClick  <br/>  ConversationWindowActions  <br/>  ConversationWindowButton  <br/>  ConversationWindowRightClick  <br/>  If ExtensibleMenu is not defined, the default values of MainWindowRightClick and ConversationWindowActions are used.  <br/> |
   
The following table describes the registry entries for parameters. These entries are place at HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Lync\SessionManager\Apps\Parameters.
  
**Registry Entries for an Internet-based Collaboration Application**

|**Name**|**Type**|**Data**|
|:-----|:-----|:-----|
|Param1  <br/> |REG_SZ  <br/> |Used in tokenized format ( `%Parm1%`) to add user-specific values to the OriginatorPath registry key.  <br/> |
|Param2  <br/> |REG_SZ  <br/> |See Param1.  <br/> |
|Param3  <br/> |REG_SZ  <br/> |See Param1.  <br/> |
   
The following example registry settings integrate ADatum Collaboration Client with Lync 2013:
  
```
Windows Registry Editor Version 5.00
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\15.0\Lync\SessionManager]
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\15.0\Lync\SessionManager\Apps]
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\15.0\Lync\SessionManager\Apps\{C3F6E17A-855F-44a0-B90D-C0B92D38E5F1}]
"Path"="https://meetingservice.adatum.com/cc/%param1%/meet/%param2%"
"OriginatorPath"="https://meetserv.adatum.com/cc/%param1%/join?id=%param2%&amp;role=present&amp;pw=%param3%"
"SessionType"=dword:00000002
"ApplicationType"=dword:00000001
"LiveServerIntegration"=dword:00000000
"Name"="ADatum Online Collaboration Service"
"Extensiblemenu"="MainWindowActions;MainWindowRightClick;ConversationWindowActions;ConversationWindowRightClick"
[HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Lync\SessionManager]
[HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Lync\SessionManager\Apps]
[HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Lync\SessionManager\Apps\Parameters]
[HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Lync\SessionManager\Apps\Parameters\{C3F6E17A-855F-44a0-B90D-C0B92D38E5F1}]
"Param1"="meetserv"
"Param2"="admin"
"Param3"="abcdefg123"
```

## Integrating a Server-Based Collaboration Application with Lync 2013

The settings to add commands for starting a server-based collaboration application from within Lync 2013 are similar to those described in the previous section, Integrating an Internet-Based Collaboration Application with Lync 2013. However, the OriginatorPath is not required, and some values are changed. Registry entries are placed in the following location:
  
- HKEY_LOCAL_MACHINE\Software\Microsoft\Office\15.0\Lync\SessionManager\Apps\Parameters
    
**Registry Entries for a Server-based Collaboration Application**

|**Name**|**Type**|**Data**|
|:-----|:-----|:-----|
|Name  <br/> |REG_SZ  <br/> |Name of the application as it appears on the menu.  <br/> |
|ApplicationType  <br/> |DWORD  <br/> |Value = 1. Sets the application type to protocol. The other possible values do not apply in this case. If not present, ApplicationType is set to 0 (executable).  <br/> |
|Path  <br/> |REG_SZ  <br/> |Protocol used to start the collaboration application. For Live Meeting 2007, the value of Path is set to  `meet:%conf-uri%`.  <br/> |
|SessionType  <br/> |DWORD  <br/> |0 = Local session. The application is started on the local computer.  <br/> 1 = Two-party session (default). Lync 2013 starts the application locally, and then sends a system notification to the other user. The other user clicks the notification and starts the specified application on their computer.  <br/> 2 = Multiparty session. Lync 2013 starts the application locally, and then sends system notifications to the other users, prompting them to start the specified application on their computer.  <br/> |
|MCUType  <br/> |REG_SZ  <br/> |DATA = The type of server.  <br/> |
|ExtensibleMenu  <br/> |REG_SZ  <br/> | A list of the menus where this command will appear, separated by semicolons. Possible values are:  <br/>  MainWindowActions  <br/>  MainWindowRightClick  <br/>  ConversationWindowActions  <br/>  ConversationWindowButton  <br/>  ConversationWindowRightClick  <br/>  If ExtensibleMenu is not defined, the default values of MainWindowRightClick and ConversationWindowActions are used.  <br/> |
   
The following example adds commands to start ADatum Collaboration Client from within Lync 2013:
  
```
Windows Registry Editor Version 5.00
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\15.0\Lync\SessionManager]
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\15.0\Lync\SessionManager\Apps]
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\15.0\Lync\SessionManager\Apps\{27877e66-615c-4582-ab88-0cb2ca05d951}]
"Path"="meet:%conf-uri%"
"SessionType"=dword:00000002
"LiveServerIntegration"=dword:00000001
"ApplicationType"=dword:00000001
"Name"="ADatum Collaboration Client"
"MCUType"="Data"
"Extensiblemenu"="MainWindowActions;MainWindowRightClick;ConversationWindowActions;ConversationWindowRightClick"
```


