---
title: "View meeting configuration settings in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d03a4684-9d8b-4728-917d-5b5c91511e2c
description: "In Lync Server 2013 Control Panel, you use meeting configuration setting to control how meetings are implemented in your deployment. This includes the following meeting configurations:"
---

# View meeting configuration settings in Lync Server 2013
[]
In Lync Server 2013 Control Panel, you use meeting configuration setting to control how meetings are implemented in your deployment. This includes the following meeting configurations:
  
- A global configuration that is created by default when you deploy Lync Server 2013.
    
- Optional site-level and user-level configurations that you can create and use to specify how meetings are implemented for specific sites or users.
    
### To view meeting configuration settings

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Conferencing** and then click **Meeting Configuration**.
    
4. On the **Meeting Configuration** page, click the meeting configuration that you would like to view. 
    
5. In **Edit File Filter**, select the **Show Details…** check box. 
    
    **Edit Meeting Configuration - \<policy\>** opens displaying the settings for the selected policy. For details about configuring the settings, see [Create or modify a collection of meeting configuration settings in Lync Server 2013](create-or-modify-a-collection-of-meeting-configuration-settings.md).
    
## Viewing Meeting Configuration Information by Using Windows PowerShell Cmdlets

Meeting configuration settings can be viewed by using Windows PowerShell and the Get-CsMeetingConfiguration cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876).
  
### To view meeting configuration information

- To view information about all your meeting configuration settings, type the following command in the Lync Server Management Shell and then press ENTER:
    
  ```
  Get-CsMeetingConfiguration
  ```

    That will return information similar to this:
    
  ```
  Identity                        : Global
  PstnCallersBypassLobby          : True
  EnableAssignedConferenceType    : True
  DesignateAsPresenter            : Company
  AssignedConferenceTypeByDefault : True
  AdmitAnonymousUsersByDefault    : True
  RequireRoomSystemsAuthorization : False
  LogoURL                         :
  LegalURL                        :
  HelpURL                         :
  CustomFooterText                :
  AllowConferenceRecording        : True
  
  ```

For more information, see the help topic for the [Get-CsMeetingConfiguration](get-csmeetingconfiguration.md) cmdlet. 
  

