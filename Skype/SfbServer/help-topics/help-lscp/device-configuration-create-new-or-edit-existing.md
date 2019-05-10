---
title: "Device Configuration Create New or Edit Existing"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/23/2015
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.lscp.ClientPhoneCfgEdit
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: aac152bf-80e9-408a-9dbb-60d0843484ab
description: "On the New Device Configuration or Edit Device Configuration page, you can create or modify a collection of settings used to manage Skype for Business Phone Edition. These settings enable you to configure such things as the required security mode, device logging level, Voice Quality of Service (QoS) settings, and whether or not phones should automatically lock after a specified period of inactivity."
---

# Device Configuration: Create New or Edit Existing
 
On the **New Device Configuration** or **Edit Device Configuration** page, you can create or modify a collection of settings used to manage Skype for Business Phone Edition. These settings enable you to configure such things as the required security mode, device logging level, Voice Quality of Service (QoS) settings, and whether or not phones should automatically lock after a specified period of inactivity.
  
## Tasks you can perform

You can perform the following tasks on the **New Device Configuration** or **Edit Device Configuration** page:
  
- Add a new device configuration.
    
- Modify the properties of an existing device configuration.
    
## UI Reference

The following lists describe the menus, commands, fields, and properties on the page.
  
- **Scope** Identifies the scope (Global or Site) of the device configuration.
    
- **Name** You can add or modify the name of the device configuration.
    
- **SIP security** You can configure transport and authentication requirements for Skype for Business Phone Edition devices. You can select from the following options:
    
  - **Low** Allow any type of authorization or transport.
    
  - **Medium** NTLM or Kerberos is required for user authentication.
    
  - **High** NTLM or Kerberos is required for user authentication and TLS is required for SIP connections.
    
- **Logging level** You can enable logging on the UC device. Valid values are: Off; Low; Medium; and High. The default value is Off.
    
- **Voice Quality of Service (QoS)** You can specify the DSCP value assigned to voice traffic emanating from a Skype for Business Phone Edition device. The default is 40. However, 40 is not the value typically used for audio traffic; instead, audio traffic is almost always marked with the DSCP code 46. In order to maintain consistency throughout your network, you might want to change this value to 46.
    
- **Phone lock** You can specify whether or not UC phones will automatically lock themselves after a specified period of inactivity. The following are the settings you can configure:
    
  - **Enforce device locking** You can enforce device locking by selecting this check box.
    
  - **Minimum PIN length** You can specify the minimum length for the personal identification number (PIN) that is used to unlock the phone. The range for the PIN length is four to 15 digits. The default length is six digits.
    
  - **Phone lock time-out** You can specify the minimum length of time before the phone locks itself. The range for the time-out is 0 to 60 minutes; the default value is 10 minutes. Enter the value in the format HH:MM:SS.
    
## See also

[Device Configuration](device-configuration.md)

[Set-CsUCPhoneConfiguration](https://docs.microsoft.com/powershell/module/skype/set-csucphoneconfiguration?view=skype-ps)
