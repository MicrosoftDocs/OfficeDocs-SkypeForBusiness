---
title: 'Lync Server 2013: Steps to prepare and deploy Lync Server hybrid environment'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Steps to prepare and deploy Lync Server 2013 hybrid environment
ms:assetid: a50d4f7b-63f4-4663-af63-56ca87e4e3e7
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205157(v=OCS.15)
ms:contentKeyID: 48185060
ms.date: 12/29/2016
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Steps to prepare and deploy Lync Server 2013 hybrid environment

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2016-12-08_

The following table lists the steps required to prepare your environment for a hybrid deployment with Skype for Business Online and Microsoft Office 365.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Completed?</th>
<th>Step</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td></td>
<td><p>Create a tenant account for Office 365 and enable Lync Online</p></td>
<td><p>Learn about Office 365 and Lync Online at <a href="https://go.microsoft.com/fwlink/p/?linkid=254980">Office 365</a>.</p>
<p>To make sure that your environment is ready for Office 365, see the <a href="https://go.microsoft.com/fwlink/p/?linkid=401408">System Requirements</a>.</p>
<p>For details about setting up Office 365, see <a href="https://go.microsoft.com/fwlink/p/?linkid=254982">Getting Started with Office 365</a> and <a href="http://go.microsoft.com/fwlink/p/?linkid=254979">Set Up Office 365</a>.</p></td>
</tr>
<tr class="even">
<td></td>
<td><p>Add your domain and verify ownership</p></td>
<td><p>Your domain is sometimes also referred to as your <em>vanity domain</em>. You must add your domain to your Office 365 tenant, and then follow the steps to validate the domain with Office 365. This is to confirm that you are the owner of the domain.</p>
<p>To add your domain to your Office 365 tenant, follow the steps described at <a href="https://go.microsoft.com/fwlink/p/?linkid=254983">Add your domain to Office 365</a>.</p>
<p>Complete all of the steps in each section in the topic, including &quot;Edit DNS records for your Office 365 services.&quot;</p></td>
</tr>
<tr class="odd">
<td></td>
<td><p>Verify environment readiness</p></td>
<td><p>You can use the Office 365 Setup Assistant to help you deploy Office 365. For more information, see <a href="https://go.microsoft.com/fwlink/p/?linkid=254985">Use Setup Assistant to determine Office 365 readiness</a>.</p>
<p>For details about using the tool and deploying Office 365, see <a href="https://go.microsoft.com/fwlink/p/?linkid=257337">Office 365 deployment guide</a>.</p></td>
</tr>
<tr class="even">
<td></td>
<td><p>Prepare for Active Directory synchronization</p></td>
<td><p>Active Directory synchronization keeps your on-premises Active Directory continuously synchronized with Office 365. This lets you create synchronized versions of each user account and group, and also enables global address list (GAL) synchronization from your local Microsoft Exchange Server environment to Microsoft Exchange Online.</p>
<div>

> [!IMPORTANT]  
> You need to synchronize the AD accounts for all Lync users in your organization between your on-premises and online Lync deployments, even if users are not moved to Lync Online. If you do not synchronize all users, communication between on-premises and online users in your organization may not work as expected.


</div>
<p>To prepare your environment for Active Directory synchronization, follow the steps described in <a href="https://go.microsoft.com/fwlink/p/?linkid=254988">Directory synchronization Roadmap</a>, including setting up single sign-on.</p></td>
</tr>
<tr class="odd">
<td></td>
<td><p>Create certificates for Active Directory Federation Services (AD FS)</p></td>
<td><p>You will need to create the certificates that are used for identity federation with Office 365. For more information, see the “Federation server certificates” section of the Plan for and deploy AD FS for use with single sign-on topic at <a href="https://go.microsoft.com/fwlink/p/?linkid=285376">Checklist: Use AD FS to implement and manage single sign-on</a>.</p></td>
</tr>
<tr class="even">
<td></td>
<td><p>Assign certificates for AD FS</p></td>
<td><p>After you create the certificates that are used for identity federation with Office 365, you must install and assign them.</p></td>
</tr>
<tr class="odd">
<td></td>
<td><p>Move pilot users to Skype for Business Online</p></td>
<td><p>After you have completed the steps to prepare and configure your environment for Skype for Business Online, you can start moving pilot users to Lync Online.</p>
<p>See <a href="lync-server-2013-move-users-to-lync-online.md">Move users to Lync Online in Lync Server 2013</a>.</p></td>
</tr>
<tr class="even">
<td></td>
<td><p>Administering users in a hybrid deployment</p></td>
<td><p>For details about how to administer users in a hybrid deployment, see <a href="lync-server-2013-administering-users-in-a-hybrid-deployment.md">Administering users in a hybrid Lync Server 2013 deployment</a>.</p></td>
</tr>
</tbody>
</table>


</div>

<span> </span>

</div>

</div>

</div>

