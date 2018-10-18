﻿---
title: 'Lync Server 2013: Configuring Lync Server to use the unified contact store'
TOCTitle: Configuring Lync Server 2013 to use the unified contact store
ms:assetid: 6aa17ae3-764e-4986-a900-85a3cdb8c1fc
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ688083(v=OCS.15)
ms:contentKeyID: 49733680
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuring Microsoft Lync Server 2013 to use the unified contact store

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-02-07_

The unified contact store enables users to maintain a single contacts list and then have those contacts available in multiple applications, including Microsoft Lync 2013, Microsoft Outlook 2013, and Microsoft Outlook Web App 2013. When you enable the unified contact store for a user that user's contacts are not stored in Microsoft Lync Server 2013 and then retrieved using the SIP protocol. Instead, his or her contacts are stored in Microsoft Exchange Server 2013 and are retrieved by using Exchange Web Services.

<div>


> [!NOTE]  
> Technically, contact information is stored in a pair of folders found in the user's Exchange 2013 mailbox. The contacts themselves are stored in a folder named Lync Contacts which is visible to end users; metadata about the contacts are stored in a subfolder that is not visible to end users.



</div>

<div>

## Enabling the Unified Contact Store for a User

If you have already configured server-to-server authentication between Lync Server 2013 and Exchange 2013 then you have also enabled the use of the unified contact store; no additional server configuration is required. However, additional user account configuration is required in order to move a user's contacts into the unified contact store. By default, user contacts are kept in Lync Server and not in the unified contact store.

Access to the unified contact store is managed by using Lync Server user services policies. User server policies have only a single property (UcsAllowed); this property is used to determine the location where a user's contacts are stored. If a user is managed by a user services policy where UcsAllowed has been set to True ($True) then the user's contacts will be stored in in the unified contact store. If the user is managed by a user services policy where UcsAllowed has been set to False ($False) then his or her contacts will be stored in Lync Server.

When you install Lync Server 2013 a single user services policy (configured at the global scope) is installed as well. The UcsAllowed value in this policy is set to True, meaning that, by default, user contacts will be stored in the unified contact store (assuming this has been deployed and configured). If you want to migrate all of your user contacts to the unified contact store you do not have to do anything at all.

If you would prefer not to migrate all your contacts to the unified contact store you can disable the unified contact store for all users by setting the UcsAllowed property in the global policy to False:

    Set-CsUserServicesPolicy -Identity global -UcsAllowed $False

After you have disabled the unified contact store in the global policy you can then create a per-user policy that enables the use of the unified contact store; this allows you to have some users keep their contacts in the unified contact store while other users continue to keep their contacts in Lync Server. You can create a per-user user services policy by using a command similar to this:

    New-CsUserServicesPolicy -Identity "AllowUnifiedContactStore" -UcsAllowed $True

After you have created the new policy you must then assign that policy to any user who should have access to the unified contact store. Per-user policies can be assigned to users by using commands similar to this:

    Grant-CsUserServicesPolicy -Identity "Ken Myer" -PolicyName "AllowUnifiedContactStore"

After the policy has been assigned Lync Server will begin to migrate the user's contacts to the unified contact store. After migration is complete, the user will then have his or her contacts stored in Exchange rather than Lync Server. If the user happens to be logged on to Lync 2013 at the time migration completes, a message box will appear and he or she will be asked to log off of Lync and then log back on in order to finalize the process. Users who have not been assigned this per-user policy will not have their contacts migrated to the unified contact store. That’s because those users are being managed by the global policy, and use of the unified contact store has been disabled in the global policy.

You can verify that a user's contacts have successfully been migrated to the unified contact store by running the [Test-CsUnifiedContactStore](https://docs.microsoft.com/en-us/powershell/module/skype/Test-CsUnifiedContactStore) cmdlet from within the Lync Server Management Shell:

    Test-CsUnifiedContactStore -UserSipAddress "sip:kenmyer@litwareinc.com" -TargetFqdn "atl-cs-001.litwareinc.com"

If Test-CsUnifiedContactStore succeeds that means that the contacts for the user sip:kenmyer@litwareinc.com have been migrated to the unified contact store.

</div>

<div>

## Rolling Back the Unified Contact Store

If you need to remove a user's contacts from the unified contact store (for example, if the user needs to be rehomed on Microsoft Lync Server 2010 and thus can no longer use the unified contact store) you must do two things. First, you must assign the user a new user services policy, one that prohibits storing contacts in the unified contact store. (That is, a policy where the UcsAllowed property has been set to $False.) If you do not have such a policy you can create one using a command similar to this:

    New-CsUserServicesPolicy -Identity NoUnifiedContactStore -UcsAllowed $False

You can then assign this new per-user policy (NoUnifiedContactStore) by using a command like this:

    Grant-CsUserServicesPolicy -Identity "Ken Myer" -PolicyName NoUnifiedContactStore

The preceding command assigns the new policy to the user Ken Myer, and also prevents Ken's contacts from being migrated to the unified contact store.

<div>


> [!NOTE]  
> In some cases you can achieve the same net effect by simply unassigning the user's current user services policy. For example, suppose Ken Myer has a per-user user services policy the enables the unified contact store, but your global policy prohibits the use of the unified contact store. In that case, you could unassign Ken's per-user services policy. When you do that, Ken will automatically be managed by the global policy, and thus will no longer have access to the unified contact store.<BR>To unassign a previously-assigned per-user policy, use the same command as shown before, but this time set the PolicyName parameter to a null value:<BR>Grant-CsUserServicesPolicy –Identity "Ken Myer" –PolicyName $Null



</div>

The terminology "prevents Ken's contacts from being migrated to the unified contact store" is important to keep in mind when working with the unified contact store. Simply assigning Ken a new user services policy will not move his contacts out of the unified contact store. When a user logs on to Lync Server 2013, the system checks the user's user services policy to see whether his or her contacts should be kept in the unified contact store. If the answer is yes (that is, if the UcsAllowed property is set to $True) then those contacts will be migrated to the unified contact store (assuming that those contacts are not already in the unified contact store). If the answer is no, then Lync Server simply ignores the user's contacts and moves on to its next task. That means that Lync Server will not automatically move a user's contacts from out of the unified contact store, regardless of the value of the UcsAllowed property.

That also means that, after assigning the user a new user services policy, you must then run the [Invoke-CsUcsRollback](https://docs.microsoft.com/en-us/powershell/module/skype/Invoke-CsUcsRollback) cmdlet in order to move the user's contacts out of Exchange 2013 and back to Lync Server 2013. For example, after assigning Ken Myer a new user services policy you can then move his contacts out of the unified contact store by using the following command:

    Invoke-CsUcsRollback -Identity "Ken Myer"

If you change the user services policy but do not run the Invoke-CsUcsRollback cmdlet Ken's contacts will not be removed from the unified contact store. What if you run Invoke-CsUcsRollback but do not change Ken Myer's user services policy? In that case, Ken's contacts will be temporarily removed from the unified contact store. The fact that this removal is temporary is important to keep in mind. After Ken's contacts have been removed from the unified contact store, Lync Server 2013 will wait 7 days and then check to see which user services policy has been assigned to Ken. If Ken is still assigned a policy that enables the user of the unified contact store, then his contacts will automatically be moved back to into the contact store. To permanently remove contacts from the unified contact store you must change the user services policy in addition to running the Invoke-CsUcsRollback cmdlet.

Due to the large number of variables that can affect migration, it is difficult to estimate how long it will take before accounts are fully migrated to the unified contact store. As a general rule, however, migration does not take effect immediately: even when migrating a small number of contacts it might take 10 minutes or more before the move is complete.

</div>

</div>

<span> </span>

</div>

</div>

</div>

