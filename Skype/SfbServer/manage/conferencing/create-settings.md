---
title: "Create meeting configuration settings in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 6d8f9ff8-2a04-4175-9bf0-1ec5d78fd015
description: "Summary: Learn how to create meeting configuration settings in Skype for Business Server."
---

# Create meeting configuration settings in Skype for Business Server
 
**Summary:** Learn how to create meeting configuration settings in Skype for Business Server.
  
You can create meeting configuration settings by using Skype for Business Server Control Panel or by using Skype for Business Server Management Shell.
  
## Create meeting configuration settings by using Skype for Business Server Control Panel

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2.  Open Skype for Business Server Control Panel.
    
3. In the left navigation bar, click **Conferencing**, and then click **Meeting Configuration**.
    
4. On the **Meeting Configuration** page, click **New**, and then do one of the following:
    
    - To create a site-level policy, click **Site configuration**. In the **Select a Site** search field, type all or part of the name of the site for which you want to define meeting join settings. In the resulting list of sites, click the site you want, and then click **OK**.
    
    - To create a pool-level policy, click **Pool configuration**. In the **Select a Service** search field, type all or part of the name of the pool service for which you want to define meeting join settings. In the resulting list of services, click the pool you want, and then click **OK**.
    
5. To route participants who dial in from the public switched telephone network (PSTN) through the lobby, clear the **PSTN callers bypass lobby** check box. By default, participants dialing in from the PSTN go directly to the meeting.
    
6. To configure who can be a presenter in the meeting, in **Designate as presenter**, do one of the following:
    
   - To not allow anyone other than the organizer to be a presenter, click **None**.
    
   - To allow only participants who are members of your organization to be a presenter, click **Company**. This is the default setting.
    
   - To allow any participants to be a presenter, click **Everyone**.
    
7. To have the organizer select a conference type when scheduling a meeting, clear the **Assigned conference type by default** check box. By default, the conference type is automatically assigned.
    
8. To prevent anonymous (unauthenticated) users from being automatically admitted, clear the **Admit anonymous users by default** check box. By default, anonymous users are automatically admitted to meetings.
    
9. To customize the meeting invite that is sent out to participants, do the following. Note that the maximum length for URLs and custom footer text is 1KB. Except for **Help URL**, if you do not specify a value for the customizations, they will not be included in the meeting. If you do not include a custom help URL, the default help URL for Skype for Business will be displayed in the invite. 
    
   - To customize the logo that appears in the meeting invite, in **Logo URL**, enter the location of the logo. The logo must be a GIF or JPG image with a size of 188 by 30 pixels. 
    
   - To customize the help text that appears in the meeting invite, in **Help URL**, enter the location of the help text.
    
   - To customize the legal text that appears in the meeting invite, in **Legal text URL**, enter the location of the legal text.
    
   - To customize the footer text that appears in the meeting invite, in **Custom footer text**, enter text.
    
10. Click **Commit**.
    
## Create meeting configuration settings by using Skype for Business Server Management Shell

To create meeting configuration settings, use the **New-CsMeetingConfiguration** cmdlet.
  
The following command creates a new set of meeting configuration settings for the Redmond site:
  
```
New-CsMeetingConfiguration -Identity "site:Redmond"
```

Because no parameters (other than the mandatory Identity parameter) were specified in the preceding command, the new meeting configuration settings will use the default values for all its properties.
  
To create settings that use different property values, simply include the appropriate parameter and parameter value. For example, to create a collection of meeting configuration settings that, by default, admit everyone to a meeting as a presenter use a command like this:
  
```
New-CsMeetingConfiguration -Identity "site:Redmond" -DesignateAsPresenter "Everyone"
```

Multiple property values can be set by including multiple parameters. For example, the following command admits everyone to a meeting as a presenter and also forces PSTN users to wait in the lobby until they are formally admitted to the meeting:
  
```
New-CsMeetingConfiguration -Identity "site:Redmond" -DesignateAsPresenter "Everyone" -PSTNUCallersBypassLobby $True
```

For more information, including a complete list of parameters, see [New-CsMeetingConfiguration](https://docs.microsoft.com/powershell/module/skype/new-csmeetingconfiguration?view=skype-ps).
  

