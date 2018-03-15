---
title: "Managing policies in Skype for Business Online"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 6/22/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection:
- Ent_O365_Hybrid
- Ent_O365_Hybrid_Top
ms.assetid: 91372888-a96e-44db-a0dc-d08facbfce87

description: "The following cmdlets manage Skype for Business Online policies. Policies help determine the Skype for Business Online capabilities that are available to users and to the organization as a whole."
---

# Managing policies in Skype for Business Online
[]
The following cmdlets manage Skype for Business Online policies. Policies help determine the Skype for Business Online capabilities that are available to users and to the organization as a whole.
  
|**Cmdlet**|**Description**|
|:-----|:-----|
|[Get-CsClientPolicy](get-csclientpolicy.md)          [Grant-CsClientPolicy](grant-csclientpolicy.md) <br/> |Client policies are used to determine the Lync client features that are available to users. For example, you might give the capability to transfer files to some users, but not to others.  <br/> |
|[Get-CsConferencingPolicy](get-csconferencingpolicy.md)          [Grant-CsConferencingPolicy](grant-csconferencingpolicy.md) <br/> |Conferencing policies determine the features and capabilities that can be used in a conference. This includes everything from whether the conference can include IP audio and video to the maximum number of people who can attend a meeting.  <br/> |
|[Get-CsExternalAccessPolicy](get-csexternalaccesspolicy.md)          [Grant-CsExternalAccessPolicy](grant-csexternalaccesspolicy.md) <br/> |External access policies are used to determine whether your users are allowed to communicate with users from federated domains, and/or whether your users are allowed to communicate with users who have accounts on public IM providers, such as Windows Live or AOL.  <br/> |
|[Get-CsVoicePolicy](get-csvoicepolicy.md)          [Grant-CsVoicePolicy](grant-csvoicepolicy.md)          [Remove-CsVoicePolicy](remove-csvoicepolicy.md) <br/> |Voice policies are used to manage Enterprise Voice features, as simultaneous ringing (the ability to have a second phone ring each time someone calls your office phone) and call forwarding.  <br/> |
   
You can also manage selected conferencing policy settings by using the Skype for Business Online admin center:
  
![Lync admin center general options properties](media/LyncOnlinePowerShell_Meeting_Properties.png)
  
You can also manage external access policy settings by using the Skype for Business Online admin center:
  
![Admin center external communication options](media/LyncOnlinePowerShell_External_Access.png)
  
## See also

#### 

[The Skype for Business Online cmdlets](the-skype-for-business-online-cmdlets.md)
  
[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online.md)

