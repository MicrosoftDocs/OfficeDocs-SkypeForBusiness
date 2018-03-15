---
title: "Deployment process for Group Call Pickup in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 082daeac-e667-4e2d-b78d-8e0901f9f0e9

description: "This section provides an overview of the steps involved in deploying Group Call Pickup. You must deploy Enterprise Edition or Standard Edition with Enterprise Voice before you configure Group Call Pickup. The components required by Group Call Pickup are installed and enabled when you deploy Enterprise Voice."
---

# Deployment process for Group Call Pickup in Lync Server 2013
[]
This section provides an overview of the steps involved in deploying Group Call Pickup. You must deploy Enterprise Edition or Standard Edition with Enterprise Voice before you configure Group Call Pickup. The components required by Group Call Pickup are installed and enabled when you deploy Enterprise Voice.
  
**Group Call Pickup Deployment Process**

|**Phase**|**Steps**|**Required groups and roles**|**Deployment documentation**|
|:-----|:-----|:-----|:-----|
|Enable the SEFAUtil resource kit tool in the topology  <br/> | Use the **New-CsTrustedApplicationPool** cmdlet to create a new trusted application pool.  <br/>  Use the **New-CsTrustedApplication** cmdlet to specify the SEFAUtil tool as trusted application.  <br/>  Run the **Enable-CsTopology** cmdlet to enable the topology.  <br/>  Install the resource kit tools on a Front End Server that is in the trusted application pool created in step 1.  <br/>  Verify that SEFAUtil is running correctly by running it to display the call forwarding settings of a user in the deployment.  <br/> |RTCUniversalServerAdmins  <br/> |[Deploy the SEFAUtil tool in Lync Server 2013](deploy-the-sefautil-tool.md) <br/> |
|Configure call pickup number ranges in the call park orbit table  <br/> |Use the **New-CSCallParkOrbit** cmdlet to create call pickup number ranges in the call park orbit table and assign the call pickup ranges the type GroupPickup.  <br/> > [!NOTE]> You must use Lync Server Management Shell to create, modify, remove, and view Group Call Pickup number ranges in the call park orbit table. Group Call Pickup number ranges are not available in Lync Server Control Panel.           > [!NOTE]> For seamless integration with existing dial plans, number ranges are typically configured as a block of virtual extensions. Assigning Direct Inward Dialing (DID) numbers as range numbers in the call park orbit table is not supported.           |RTCUniversalServerAdmins  <br/> CsVoiceAdministrator  <br/> CsServerAdministrator  <br/> CsAdministrator  <br/> |[Configure call pickup group numbers in Lync Server 2013](configure-call-pickup-group-numbers.md) <br/> |
|Assign a call pickup number to users, and enable Group Call Pickup for the users  <br/> |Use the /enablegrouppickup parameter in the SEFAUtil resource kit tool to enable Group Call Pickup and assign a call pickup number for users.  <br/> |-  <br/> |[Enable Group Call Pickup for users in Lync Server 2013 and assign a group number](enable-group-call-pickup-for-users-and-assign-a-group-number.md) <br/> |
|Notify users of their assigned call pickup number and any other number of interest  <br/> |Because any user can retrieve a call made to a Group Call Pickup user, users may want to monitor more than one group.  <br/> |-  <br/> |[Communicate Group Call Pickup assignments to users in Lync Server 2013](communicate-group-call-pickup-assignment-to-users.md) <br/> |
|Verify your Group Call Pickup deployment  <br/> |Test placing and retrieving calls to make sure that your configuration works as expected.  <br/> |-  <br/> |[(Optional) Verify the Group Call Pickup deployment in Lync Server 2013](optional-verify-the-group-call-pickup-deployment.md) <br/> |
   

