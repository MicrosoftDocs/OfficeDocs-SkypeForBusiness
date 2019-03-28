---
title: "View meeting configuration settings in Skype for Business Server"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 932c7e2d-6de3-4176-ac6e-ec230f8230f2
description: "Summary: Learn how to view meeting configuration settings in Skype for Business Server."
---

# View meeting configuration settings in Skype for Business Server
 
**Summary:** Learn how to view meeting configuration settings in Skype for Business Server.
  
You can view meeting configuration settings by using Skype for Business Server Control Panel or by using Skype for Business Server Management Shell.
  
## View meeting configuration settings by using Skype for Business Server Control Panel
<a name="BKMK_ViewJoinSettings"> </a>

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2.  Open Skype for Business Server Control Panel.
    
3. In the left navigation bar, click **Conferencing**, and then click **Meeting Configuration**.
    
4. On the **Meeting Configuration** page, click the meeting configuration that you would like to view.
    
5. In **Edit File Filter**, select the **Show Details** check box.
    
    **Edit Meeting Configuration - \<policy\>** opens displaying the settings for the selected policy.
    
    For details about configuring the settings, see [Create meeting configuration settings in Skype for Business Server](create-settings.md).
    
## View meeting configuration settings by using Skype for Business Server Management Shell
<a name="BKMK_ViewJoinSettings"> </a>

To view information about all your meeting configuration settings, use the **Get-CsMeetingConfiguration** cmdlet:
  
```
Get-CsMeetingConfiguration
```

This command will return information similar to the following:
  
<pre>
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
</pre>

For more information, including a complete list of parameters, see [Get-CsMeetingConfiguration](https://docs.microsoft.com/powershell/module/skype/get-csmeetingconfiguration?view=skype-ps).
  

