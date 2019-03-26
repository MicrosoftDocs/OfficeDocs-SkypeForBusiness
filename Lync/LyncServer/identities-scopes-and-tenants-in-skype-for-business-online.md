---
title: Identities, scopes, and tenants in Skype for Business Online
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Identities, scopes, and tenants
ms:assetid: 7cfa194a-2d01-4370-9b48-ee13ff597fa5
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362819(v=OCS.15)
ms:contentKeyID: 56558817
ms.date: 05/04/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Identities, scopes, and tenants in Skype for Business Online

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2015-03-09_

Many of the Windows PowerShell cmdlets used to manage Skype for Business Online require you to be very specific about the item that you are trying to manage. For example, when you run the [Set-CsUserAcp](https://docs.microsoft.com/powershell/module/skype/Set-CsUserAcp) cmdlet, you must indicate which user you are trying to manage. This makes sense. Unless you specifically tell the cmdlet which user account to manage, the **Set-CsUserAcp** cmdlet has no idea which user’s audio conferencing information should be modified. For this reason, each time you run the **Set-CsUserAcp** cmdlet, you’ll need to include the Identity parameter, followed by the Identity of the user account to be modified:

    Set-CsUserAcp -Identity "Ken Myer" -TollNumber "14255551298" -ParticipantPassCode 13761 -Domain "fabrikam.com" -Name "Fabrikam ACP"

If the term *Identity* always referred to the Identity of a user account, there would be little cause for confusion. When you are dealing with people (users, contacts, and so on), Identities refer to the individual users themselves. However, items other than user accounts also have Identities. When you are dealing with components of the Skype for Business Online service—policies, configuration settings, and so on—the term Identity means something slightly different. For example, consider this command:

    Get-CsMeetingConfiguration -Identity "global"

In this case, the Identity "global" refers to the scope of the meeting configuration settings. *Scope* is a term used in Skype for Business Online (and in Lync Server) to designate spheres of management. By default, policies and settings always have a global scope. When you first set up your Skype for Business Online account you'll have, by default, a collection of global policies and settings—global meeting configuration settings, a global external access policy, a global dial plan, and so on.

These global policies and settings were introduced in Microsoft Lync Server 2010 to help ensure that all users and all components would always, in some way, be managed. This was not necessarily true in Microsoft Office Communicator 2007 R2. Depending on how you accessed the system, you could potentially end up in a largely unmanaged state (typically, because Group Policy could not be applied to your user account). In contrast, in Lync Server and in Skype for Business Online, nothing is ever left unmanaged. This is because, in lieu of anything else, global policies and settings will always be enforced.

What do we mean by "in lieu of anything else"? Well, in the case of Skype for Business Online, it’s possible to create policies at the *tag scope*, or sphere of management. Policies created at the tag scope (also known as *the per-user scope*) take priority over policies created at the global scope. In other words, a per-user policy will always take precedence over a global policy. For example, you might have two external user access policies. The global policy prohibits users from communicating with people who have accounts on public instant messaging (IM) providers, such as Windows Live. The per-user policy, AllowPublicIMCommunication, allows communication with public IM providers.

You might also have two users: Ken Myer and Pilar Ackerman. Ken Myer has been assigned the per-user policy. Pilar Ackerman has not been assigned a per-user policy; that is, she is managed by the global external access policy. The following table shows which user (if any) can communicate with public IM providers:


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Policy Settings</th>
<th>Ken Myer</th>
<th>Pilar Ackerman</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Global policy setting for public IM providers</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
</tr>
<tr class="even">
<td><p>Per-user policy setting for public IM providers</p></td>
<td><p>Yes</p></td>
<td><p>No</p></td>
</tr>
<tr class="odd">
<td><p>User can communicate with public IM providers</p></td>
<td><p>Yes</p></td>
<td><p>No</p></td>
</tr>
</tbody>
</table>


As you can see, Ken Myer is allowed to communicate with public IM providers. This is because the settings in the per-user policy assigned to him override the settings in the global policy. Pilar Ackerman cannot communicate with public IM providers. This is because she is managed by the global policy, and the global policy prohibits such communications.

Per-user policies must be created for you by Office 365 Support. After the policies are created, you can then assign them to users by using the appropriate **Grant-Cs** cmdlet (for example, [Grant-CsExternalAccessPolicy](https://docs.microsoft.com/powershell/module/skype/Grant-CsExternalAccessPolicy)). Per-user policies are easy to identify because the policy Identity always begins with the tag **prefix**. For example:

    Identity : tag:AllowPublicIMCommunication

<div>


> [!NOTE]  
> The tag <STRONG>prefix</STRONG> dates back to the early development days of Lync Server 2010. In those days, per-user policies were referred to as <EM>tag policies</EM> and were identified by the tag <STRONG>prefix</STRONG>. These policies are now more accurately referred to as <EM>per-user policies</EM>, and the tag scope is more accurately referred to as the <EM>per-user scope</EM>. However, for technical reasons, the tag <STRONG>prefix</STRONG> was never changed.



</div>

Another key term used when working with Skype for Business Online and Windows PowerShell is *tenant*. When you set up a Skype for Business Online account, your new deployment is assigned a tenant ID number, which is a globally unique identifier (GUID) similar to this:

    bf19b7db-6960-41e5-a139-2aa373474354

A few of the Skype for Business Online cmdlets require you to enter the tenant ID whenever you run the cmdlet. You must enter the tenant ID even if you have logged on to, and only have, one tenant. Fortunately, you do not have to memorize the tenant ID. You can retrieve your tenant ID at any time by running the following Windows PowerShell command:

    Get-CsTenant | Select-Object TenantId

Of course, knowing things such as the difference between the global scope and the per-user scope (or the tag scope) is only half the battle. It’s also important to know when (or even if) you can use these scopes. The same is true for Identities and the tenant parameter. The following topics describe how the different Skype for Business Online cmdlets use Identities, scopes, and the tenant parameter:

  - [Cmdlets in Skype for Business Online that use only the global scope](cmdlets-in-skype-for-business-online-that-use-only-the-global-scope.md)

  - [Cmdlets in Skype for Business Online that use the global scope and the tag scope](cmdlets-in-skype-for-business-online-that-use-the-global-scope-and-the-tag-scope.md)

  - [Cmdlets in Skype for Business Online that use a user identity](cmdlets-in-skype-for-business-online-that-use-a-user-identity.md)

  - [Cmdlets in Skype for Business Online that use a user identity and the tag scope](cmdlets-in-skype-for-business-online-that-use-a-user-identity-and-the-tag-scope.md)

  - [Cmdlets in Skype for Business Online that use the Tenant parameter](cmdlets-in-skype-for-business-online-that-use-the-tenant-parameter.md)

  - [Cmdlets in Skype for Business Online that use a conferencing provider identity](cmdlets-in-skype-for-business-online-that-use-a-conferencing-provider-identity.md)

  - [Cmdlets in Skype for Business Online that do not use a scope or an identity](cmdlets-in-skype-for-business-online-that-do-not-use-a-scope-or-an-identity.md)

</div>

<span> </span>

</div>

</div>

</div>

