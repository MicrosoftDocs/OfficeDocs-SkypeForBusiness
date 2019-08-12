---
title: "Deployment process for Group Call Pickup in Skype for Business"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: quickstart
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom: 
ms.assetid: 082daeac-e667-4e2d-b78d-8e0901f9f0e9
description: "Deployment process and steps for Group Call Pickup in Skype for Business Server Enterprise Voice."
---

# Deployment process for Group Call Pickup in Skype for Business
 
Deployment process and steps for Group Call Pickup in Skype for Business Server Enterprise Voice.
  
Group Call Pickup enables users to answer incoming calls to their colleagues from their own phones. 
  
 The components that Group Call Pickup uses are automatically installed and enabled on the Front End Server or Standard Edition server when you deploy Enterprise Voice. However, you must use the following steps to configure Group Call Pickup before it is available to users.
  
**Group Call Pickup Deployment Process**

|**Phase**|**Steps**|**Required groups and roles**|**Deployment documentation**|
|:-----|:-----|:-----|:-----|
|Enable the SEFAUtil tool in your topology|Use the New-CsTrustedApplicationPool  cmdlet to create a new trusted application pool. Use the New-CsTrustedApplication  cmdlet to specify the SEFAUtil tool as trusted application. Run the Enable-CsTopology  cmdlet to enable the topology. If you don't already have it, download the Skype for Business Server version of the SEFAUtil tool from this location, and install it on the trusted application pool you created in step 1. Verify that SEFAUtil is running correctly by running it to display the call forwarding settings of a user in the deployment. |RTCUniversalServerAdmins  <br/> |[Deploy the SEFAUtil tool in Skype for Business](deploy-the-sefautil-tool.md) <br/> [New-CsTrustedApplicationPool](https://docs.microsoft.com/powershell/module/skype/new-cstrustedapplicationpool?view=skype-ps) </br>[New-CsTrustedApplication](https://docs.microsoft.com/powershell/module/skype/new-cstrustedapplication?view=skype-ps)</br>[Enable-CsTopology](https://docs.microsoft.com/powershell/module/skype/enable-cstopology?view=skype-ps) <br/> [Skype for Business Server 2015 Resource Kit Tools Documentation](../../management-tools/resource-kit-tools.md). (For Skype for Business Server you must use the current version of the tool, but this documentation from Lync Server 2013 still applies.)  <br/> |
|Configure call pickup number ranges in the call park orbit table  <br/> |Use the **New-CSCallParkOrbit** cmdlet to create call pickup number ranges in the call park orbit table and assign the call pickup ranges the type **GroupPickup**.  <br/> For seamless integration with existing dial plans, number ranges are typically configured as a block of virtual extensions. Assigning Direct Inward Dialing (DID) numbers as range numbers in the call park orbit table is not supported.  <br/> |RTCUniversalServerAdmins  <br/> CsVoiceAdministrator  <br/> CsServerAdministrator  <br/> CsAdministrator  <br/> |[Create or modify a Group Call Pickup number range in Skype for Business](create-or-modify-a-group-call-pickup-number-range.md) <br/> |
|Assign a call pickup number to users, and enable Group Call Pickup for the users  <br/> |Use the /enablegrouppickup parameter in the SEFAUtil resource kit tool to enable Group Call Pickup and assign a call pickup number for users.  <br/> |-  <br/> |[Enable Group Call Pickup for users and assign a group number in Skype for Business](enable-group-call-pickup-for-users-and-assign-a-group-number.md) <br/> |
|Notify users of their assigned call pickup number and any other number of interest  <br/> |After you enable Group Call Pickup for users, use email or some other mechanism to notify users of their call pickup group number. Notify users of the call pickup group number for any group that they might want to monitor. Because users can retrieve calls for other users even if they are not in the same group, users might need the call pickup group number for multiple groups.  <br/> |-  <br/> ||
|Verify your Group Call Pickup deployment  <br/> | Test placing and retrieving calls to make sure that your configuration works as expected. At a minimum, verify the following: <br/>  Call a user who is enabled for Group Call Pickup and have another user retrieve the call. The other user can be in the same group, in a different group, or not have Group Call Pickup enabled. <br/>  Call a user who is enabled for Group Call Pickup and do not answer the call. <br/> |-  <br/> ||
   

