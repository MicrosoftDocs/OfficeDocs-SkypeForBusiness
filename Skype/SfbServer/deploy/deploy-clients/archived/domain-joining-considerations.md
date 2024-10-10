---
ms.date: 03/17/2018
title: "Skype Room System domain joining considerations"
ms.author: serdars
author: SerdarSoysal
manager: serdars
audience: ITPro
ms.reviewer: sohailta
ms.topic: quickstart
ms.service: skype-for-business-server
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.assetid: 3034fdcb-7c89-42c4-9c5e-13400e82d88f
description: "Read this article to learn how to join a Skype Room System appliance PC to your domain."
---

# Skype Room System domain joining considerations
 
Read this article to learn how to join a Skype Room System appliance PC to your domain.
  
## Domain joining considerations

You can join the Skype Room System appliance PC to the Active Directory domain or leave it in a Workgroup. Consider the following points before making this decision:
  
- Domain-joining the Skype Room System appliance PC helps in importing your organization's private root certificate chain automatically.
    
- Domain-joining the Skype Room System appliance PC enables you to grant domain users and groups administrative rights. By doing so, you won't have to remember the local machine level administrator account password.
    
- When you join a Skype Room System appliance PC to the domain, it's required that you create a separate Organizational Unit (OU), so that you can provide Group Policy Object (GPO) exclusions to the OU where all the Skype Room System machine objects reside. When you do this, create machine objects in the OU before joining the Skype Room System appliance PC to the domain.
    
- Many organizations have the following GPOs, which affect Skype Room System appliance PC functions. Ensure that you override or block the inheritance of these GPOs in the Skype Room System OU: 
    
  - Timeout of sign in sessions (auto lockout)
    
  - Power management related policies
    
  - Requiring other authentication steps
    
  - Denying access to local drives
    
  - Prompting users for slow network connections
    
  - Start a certain program at sign in
    
  - Create another domain user account on all domain-joined machines.
    
  - Push Windows Update to Skype Room System
    
- Alternatively, you might decide to leave the appliance PC in the workgroup. As with the desktop Skype for Business client, this requires you to manually import the root certificate chain on the Skype Room System appliance PC. You're not required to import the root certificate chain if your Skype for Business deployment is using a public certificate (for example, Entrust, VeriSign, and so on). 
    
If you plan to join Skype Room System machines to the domain, to avoid joining Skype Room System machine inadvertently to an unintended OU, which might not be free from GPOs, ensure you join the correct OU. You can use the following cmdlet from the Skype Room System machine to join in the correct OU and doesn't receive GPOs that might block LRS functionality. Contact your system administrator or OEM partner to run these cmdlets:
  
```powershell
$username = "contso.local\LRS01"
$password = ConvertTo-SecureString "password123" -AsPlainText -Force
$myCred = New-Object System.Management.Automation.PSCredential $username, $password
Add-Computer -DomainName contoso.local -Credential $mycred -OUPath "OU=LyncRoomSystem,OU=Resources,DC=CONTOSO,DC=LOCAL"
```

Even if you create a separate OU and block inheritance, there are some policies, which could cause issues at a higher level. A Group Policy with No Override setting beats an OU with a Block Policy Inheritance setting. For more information, see the article [No Override as Compared to Block Policy Inheritance](/previous-versions/windows/it-pro/windows-2000-server/cc978255(v=technet.10)) in the Group Policy documentation.
  
You might have multiple approaches to solving these problems. We advise you to consult with your Active Directory experts to ensure you're provided with an OU that has appropriate GPO settings, or at least an OU in which the previously described policies don't exist. It's advisable to enable Quality of Service (QoS) for Skype Room System devices.

## See also
  
[Device Configuration: Create New or Edit Existing](../../../help-topics/help-lscp/device-configuration-create-new-or-edit-existing.md#device-configuration-create-new-or-edit-existing)

[Managing Quality of Service](../../../plan-your-deployment/network-requirements/network-requirements.md#managing-quality-of-service)
