---
title: 'Lync Server 2013: Planning for two-factor authentication'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Planning for two-factor authentication
ms:assetid: 16f08710-8961-4659-acbf-ebb95a198fb4
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn308562(v=OCS.15)
ms:contentKeyID: 54973683
ms.date: 04/06/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Planning for two-factor authentication in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2015-04-06_

The following is a list of deployment considerations when configuring a Microsoft Lync Server 2013 environment to support two-factor authentication.

<div>

## Client Support

The Lync 2013 Cumulative Updates for Lync Server 2013: July 2013 desktop client and all mobile clients currently support two-factor authentication.

</div>

<div>

## Topology Requirements

Customers are strongly encouraged to deploy two-factor authentication using dedicated Lync Server 2013 with Cumulative Updates for Lync Server 2013: July 2013 Edge, Director, and User Pools. To enable passive authentication for Lync users, other authentication methods must be disabled for other roles and services, including the following:


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Configuration Type</th>
<th>Service Type</th>
<th>Server Role</th>
<th>Authentication Type to Disable</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Web Service</p></td>
<td><p>WebServer</p></td>
<td><p>Director</p></td>
<td><p>Kerberos, NTLM, and Certificate</p></td>
</tr>
<tr class="even">
<td><p>Web Service</p></td>
<td><p>WebServer</p></td>
<td><p>Front End</p></td>
<td><p>Kerberos, NTLM, and Certificate</p></td>
</tr>
<tr class="odd">
<td><p>Proxy</p></td>
<td><p>EdgeServer</p></td>
<td><p>Edge</p></td>
<td><p>Kerberos and NTLM</p></td>
</tr>
<tr class="even">
<td><p>Proxy</p></td>
<td><p>Registrar</p></td>
<td><p>Front End</p></td>
<td><p>Kerberos and NTLM</p></td>
</tr>
</tbody>
</table>


Unless these authentication types are disabled at the service level, all other versions of the Lync client will be unable to sign in successfully once two-factor authentication is enabled within in your deployment.

</div>

<div>

## Lync Service Discovery

DNS records used by internal and/or external clients to discover Lync services should be configured to resolve to a Lync server that is not enabled for two-factor authentication. With this configuration, users from Lync Pools that are not enabled for two-factor authentication will not be required to enter a PIN to authenticate, while users from Lync Pools that are enabled for two-factor authentication will be required to enter their PIN to authenticate.

</div>

<div>

## Exchange Authentication

Customers who have deployed two-factor authentication for Microsoft Exchange may find that certain features in the Lync client are unavailable. This is currently by design, as the Lync client does not support two-factor authentication for features that are dependent on Exchange integration.

</div>

<div>

## Lync Contacts

Lync users who are configured to leverage the Unified Contact Store feature will find that their contacts are no longer available after signing in with two-factor authentication.

You should use the **Invoke-CsUcsRollback** cmdlet to remove existing user contacts from the Unified Contact Store and store them in Lync Server 2013 before enabling two-factor authentication.

</div>

<div>

## Skill Search

Customers who have configured the Skill Search feature in their Lync environment will find that this feature does not work when Lync is enabled for two-factor authentication. This is by design, as Microsoft SharePoint does not currently support two-factor authentication.

</div>

<div>

## Lync Credentials

There are a number of deployment considerations involving saved Lync credentials which may impact users who are configured to use two-factor authentication.

<div>

## Deleting Saved Credentials

Desktop client users should use the **Delete my sign-in info** option in the Lync client and delete their SIP profile folder from %localappdata%\\Microsoft\\Office\\15.0\\Lync before attempting to sign for the first time using two-factor authentication.

</div>

<div>

## DisableNTCredentials

With the Kerberos or NTLM authentication method, the user’s Windows credentials are used automatically for authentication. In a typical Lync Server 2013 deployment where Kerberos and/or NTLM is enabled for authentication, users should not have to enter their credentials every time that they sign in.

If users are unintentionally prompted for credentials before they are prompted to enter their PIN, the **DisableNTCredentials** registry key may be unintentionally configured on client computers, possibly through Group Policy.

To prevent the additional prompt for credentials, create the following registry entry on the local workstation or use the Lync administrative template to apply to all users for a given pool using Group Policy:

HKEY\_LOCAL\_MACHINE\\Software\\Policies\\Microsoft\\Office\\15.0\\Lync

REG\_DWORD: DisableNTCredentials

Value: 0x0

</div>

<div>

## SavePassword

When a user signs in to Lync for the first time, the user is prompted to save his or her password. If selected, this option allows the user’s client certificate to be stored in the personal certificate store and the user’s Windows credentials to be stored in the Credential Manager of the local computer.

The **SavePassword** registry setting should be disabled when Lync is configured to support two-factor authentication. To prevent users from saving their passwords, change the following registry entry on the local workstation or use the Lync administrative template to apply to all users for a given pool using Group Policy:

HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\15.0\\Lync

REG\_DWORD: SavePassword

Value: 0x0

</div>

</div>

<div>

## AD FS 2.0 Token Replay

AD FS 2.0 provides a feature referred to as token replay detection, by which multiple token requests using the same token can be detected and then discarded. When this feature is enabled, token replay detection protects the integrity of authentication requests in both the WS-Federation passive profile and the SAML WebSSO profile by making sure that the same token is never used more than once.

This feature should be enabled in situations where security is a very high concern such as when using kiosks. For more information about token replay detection, see Best Practices for Secure Planning and Deployment of AD FS 2.0 at [http://go.microsoft.com/fwlink/p/?LinkId=309215](http://go.microsoft.com/fwlink/p/?linkid=309215).

</div>

<div>

## External User Access

Configuring an AD FS Proxy or Reverse Proxy to support Lync two-factor authentication from external networks is not covered in these topics.

</div>

</div>

<span> </span>

</div>

</div>

</div>

