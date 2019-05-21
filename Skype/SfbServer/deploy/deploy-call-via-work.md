---
title: "Deploy Call Via Work in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- Strat_SB_Admin
ms.custom: 
ms.assetid: 4802d733-14ef-4509-92b9-07173614e45f
description: "Summary: Learn how to deploy Call Via Work in Skype for Business Server for some or all of your users."
---

# Deploy Call Via Work in Skype for Business Server
 
**Summary:** Learn how to deploy Call Via Work in Skype for Business Server for some or all of your users.
  
Use these steps to deploy Call Via Work for your users. Planning considerations are discussed in [Plan for Call Via Work in Skype for Business Server](../plan-your-deployment/enterprise-voice-solution/call-via-work.md). In previous versions of Lync Server remote call control was a feature which enabled users to control their PBX phones with Lync Server. In Skype for Business Server, this feature has been replaced with Call Via Work. 
  
## Prerequisites for Call Via Work

Call Via Work uses Unified Communications Web API (UCWA), which is automatically installed on all Skype for Business Server Front End Servers. To enable users for Call Via Work, you must also have the following prerequisites in place: 
  
- You must have a Mediation Server deployed, either as part of a Front End Server or as a standalone role. You must also deploy an IP-PBX gateway.
    
- All users who will be enabled for Call Via Work must have a Direct Inward Dialing (DID) on the PBX phone system. 
    
- You must enable all Call Via Work users for Enterprise Voice. When you do this, you must configure the Skype for Business DID number for each user to the corresponding DID number for the corresponding PBX phone system. 
    
- All users who will be using Call Via Work must have **Automatic Configuration** selected in their **Advanced Connections** option in their Skype for Business client. This enables the client to discover the UCWA URLs. **Automatic Configuration** is the default selection.
    
- For each Call Via Work user, enable call forwarding and simultaneous ringing. 
    
- For each Call Via Work user, ensure that dial-in conferencing and conferencing dial-out are enabled. This enables these users to get into and out of Skype for Business conferences.
    
- Ensure that delegation, team call, and response group are disabled for every Call Via Work user.
    
## Deploy Call Via Work

After the prerequisites are in place, do the following:
  
- Create a global phone number for your deployment which Skype for Business displays on the PBX caller ID of users who are making Call Via Work calls. 
    
- Create one or more Call Via Work policies
    
- Assign a Call Via Work policy to each user who will be enabled for Call Via Work
    
### Create the Call Via Work global phone number

- Type the following cmdlet
    
  ```
  Set-CsRoutingConfiguration -CallViaWorkCallerId +<PhoneNumber>
  ```

    For example, the following cmdlet sets the global phone number to 1-555-123-4567.
    
  ```
  Set-CsRoutingConfiguration -CallViaWorkCallerId +15551234567
  ```

### Create a Call Via Work policy

- Type the following cmdlet
    
  ```
  New-CsCallViaWorkPolicy [-Identity] <XdsIdentity> [-Tenant <guid>] [-Enabled <bool>] [-UseAdminCallbackNumber  <bool>] [-AdminCallbackNumber <string>] [-InMemory] [-Force] [-WhatIf] [-Confirm]  [<CommonParameters>]
  ```

    For example, the following cmdlet creates a Call Via Work policy called ContosoUser1CvWP, requires the user to use an admin callback number, and sets that callback number to 1-555-789-1234.
    
  ```
  New-CsCallViaWorkPolicy -Identity Tag:ContosoUser1CvWP -Enabled $true -UseAdminCallbackNumber $true -AdminCallbackNumber +15557891234
  ```

### Assign a Call Via Work policy to a user

- Type the following cmdlet
    
  ```
  Grant-CsCallViaWorkPolicy -Identity <UserName> -PolicyName Tag:<PolicyName>
  ```

    For example, the following cmdlet assigns the Call Via Work policy "ContosoUser1CvWP" to the user named **ContosoUser1**.
    
  ```
  Grant-CsCallViaWorkPolicy -Identity ContosoUser1 -PolicyName Tag:ContosoUser1CvWP
  ```

## See also

[Plan for Call Via Work in Skype for Business Server](../plan-your-deployment/enterprise-voice-solution/call-via-work.md)

