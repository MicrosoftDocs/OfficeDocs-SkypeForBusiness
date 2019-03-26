---
title: Cmdlets in Skype for Business Online that use the global scope and the tag scope
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Cmdlets that use the global scope and the tag scope
ms:assetid: 1e2bc055-8a72-425e-967b-e253add7018c
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362774(v=OCS.15)
ms:contentKeyID: 56558824
ms.date: 05/04/2015
mtps_version: v=OCS.15
---

# Cmdlets in Skype for Business Online that use the global scope and the tag scope

 


In Skype for Business Online, policies can be configured at either the *global scope* or at the *tag scope* (or *per-user scope*). When using the **Get-Cs** cmdlets, you do not have to specify a scope or identity. If you call one of these cmdlets without any parameters, then all the relevant items will be returned. For example, this command returns information about all your external access policies:

    Get-CsExternalAccessPolicy

You need to include only the Identity parameter or the Filter parameter if you want to limit the returned data. For example, to return only the global policy, use this command:

    Get-CsExternalAccessPolicy -Identity "global"

To return a per-user policy that has the Identity “RedmondAccessPolicy”, use this command:

    Get-CsExternalAccessPolicy -Identity "RedmondAccessPolicy"


> [!NOTE]  
> When referencing a per-user policy, the tag <STRONG>prefix</STRONG> is optional. This syntax, which includes the prefix, is also valid:<BR>Get-CsExternalAccessPolicy –Identity "tag:RedmondAccessPolicy"



To return all policies except the global policies (that is, all the per-user policies), use this command:

    Get-CsExternalAccessPolicy -Filter "tag:*"

The following cmdlets operate against both the global scope and the per-user (tag) scope:

  - [Get-CsClientPolicy](https://technet.microsoft.com/en-us/library/gg398830\(v=ocs.15\))

  - [Get-CsConferencingPolicy](https://technet.microsoft.com/en-us/library/gg398293\(v=ocs.15\))

  - [Get-CsDialPlan](https://technet.microsoft.com/en-us/library/gg413043\(v=ocs.15\))

  - [Get-CsExternalAccessPolicy](https://technet.microsoft.com/en-us/library/gg425805\(v=ocs.15\))

  - [Get-CsHostedVoicemailPolicy](https://technet.microsoft.com/en-us/library/gg398348\(v=ocs.15\))

  - [Get-CsPresencePolicy](https://technet.microsoft.com/en-us/library/gg398463\(v=ocs.15\))

  - [Get-CsVoicePolicy](https://technet.microsoft.com/en-us/library/gg398101\(v=ocs.15\))


> [!NOTE]  
> Despite the name, dial plans are, functionally speaking, policies. The term <EM>dial plan</EM> is used instead of, for example, dialing policy, in order to preserve the terminology used with previous versions of Lync Server.



## See Also


[Identities, scopes, and tenants in Skype for Business Online](identities-scopes-and-tenants-in-skype-for-business-online.md)  
[The Skype for Business Online cmdlets](https://technet.microsoft.com/en-us/library/dn362817\(v=ocs.15\))

