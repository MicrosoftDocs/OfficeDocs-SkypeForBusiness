---
title: 'Lync Server 2013: Planning for simple URLs'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Planning for simple URLs
ms:assetid: 20e4f4b6-b7ff-4297-b00d-d1211ee800ac
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398287(v=OCS.15)
ms:contentKeyID: 48183610
ms.date: 12/12/2015
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Planning for simple URLs in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2015-12-11_

Simple URLs make joining meetings easier for your users, and make getting to Lync Server administrative tools easier for your administrators.

Lync Server supports three simple URLs:

  - **Meet** is used as the base URL for all conferences in the site or organization. An example of a Meet simple URL is https://meet.contoso.com. A URL for a particular meeting might be https://meet.contoso.com/*username*/7322994.
    
    With the Meet simple URL, links to join meetings are easy to comprehend, and easy to communicate and distribute.

  - **Dial-in** enables access to the Dial-in Conferencing Settings webpage. This page displays conference dial-in numbers with their available languages, assigned conference information (that is, for meetings that do not need to be scheduled), and in-conference DTMF controls, and supports management of personal identification number (PIN) and assigned conferencing information. The Dial-in simple URL is included in all meeting invitations so that users who want to dial in to the meeting can access the necessary phone number and PIN information. An example of the Dial-in simple URL is https://dialin.contoso.com.

  - **Admin** enables quick access to the Lync Server Control Panel. From any computer within your organization’s firewalls, an admin can open the Lync Server Control Panel by typing the Admin simple URL into a browser. The Admin simple URL is internal to your organization. An example of the Admin simple URL is https://admin.contoso.com

<div>

## Simple URL Scope

You can configure your simple URLs to have global scope, or you can specify different simple URLs for each central site in your organization. If both a global scope simple URL and a site scope simple URL are specified, the site scope simple URL has precedence.

In most cases, we recommend that you set simple URLs only at the global level, so that a user’s Meet simple URL does not change if they move from one site to another. The exception would be organizations that need to use different telephone numbers for dial-in users at different sites. Note that if you set one simple URL (such as the Dial-in simple URL) at a site to be a site-level simple URL, you must also set the other simple URLs at that site to be site-level as well.

<div>


> [!NOTE]  
> If you choose to use site scoped simple URLs, your users won't be able to move between Front-End pools in different sites without those users rescheduling all of their scheduled meetings as the meeting simple URLs are different between sites. This includes fail-over scenarios where pools in backup relationships are in separate sites. When you need to fail-over between sites where site scoped simple URLs are deployed, users won't be able to join their meetings because of the scope for URL. For further information, check <A href="https://docs.microsoft.com/powershell/module/skype/Get-CsSimpleUrlConfiguration">Get-CsSimpleUrlConfiguration</A>.



</div>

You can set global simple URLs in Topology Builder. To set a simple URL at the site level, you must use the Set-CsSimpleURLConfiguration cmdlet.

</div>

<div>

## Naming Your Simple URLs

There are three recommended options for naming your simple URLs. Which option you choose has implications for how you set up your DNS A records and certificates which support simple URLs. In each option, you must configure one Meet simple URL for each SIP domain in your organization.

You always need just one simple URL in your whole organization for Dial-in, and one for Admin, no matter how many SIP domains you have.

For details about the necessary DNS A records and certificates, see [DNS requirements for simple URLs in Lync Server 2013](lync-server-2013-dns-requirements-for-simple-urls.md) and [Certificate requirements for internal servers in Lync Server 2013](lync-server-2013-certificate-requirements-for-internal-servers.md) in the Planning documentation.

In Option 1, you create a new SIP domain name for each simple URL.

If you use this option, you need a separate DNS A record for each simple URL, and each Meet simple URL must be named in your certificates.

### Simple URL Naming Option 1

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Simple URL</strong></p></td>
<td><p><strong>Example</strong></p></td>
</tr>
<tr class="even">
<td><p>Meet</p></td>
<td><p>https://meet.contoso.com, https://meet.fabrikam.com, and so on (one for each SIP domain in your organization)</p></td>
</tr>
<tr class="odd">
<td><p>Dial-in</p></td>
<td><p>https://dialin.contoso.com</p></td>
</tr>
<tr class="even">
<td><p>Admin</p></td>
<td><p>https://admin.contoso.com</p></td>
</tr>
</tbody>
</table>


With Option 2, simple URLs are based on the domain name lync.contoso.com. Therefore, you need only one DNS A record which enables all three types of simple URLs. This DNS A record references lync.contoso.com. Additionally, you still need separate DNS A records for other SIP domains in your organization.

### Simple URL Naming Option 2

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Simple URL</strong></p></td>
<td><p><strong>Example</strong></p></td>
</tr>
<tr class="even">
<td><p>Meet</p></td>
<td><p>https://lync.contoso.com/Meet, https://lync.fabrikam.com/Meet, and so on (one for each SIP domain in your organization)</p></td>
</tr>
<tr class="odd">
<td><p>Dial-in</p></td>
<td><p>https://lync.contoso.com/Dialin</p></td>
</tr>
<tr class="even">
<td><p>Admin</p></td>
<td><p>https://lync.contoso.com/Admin</p></td>
</tr>
</tbody>
</table>


Option 3 is most useful if you have many SIP domains, and you want them to have separate Meet simple URLs but want to minimize the DNS record and certificate requirements for these simple URLs.

### Simple URL Naming Option 3

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Simple URL</strong></p></td>
<td><p><strong>Example</strong></p></td>
</tr>
<tr class="even">
<td><p>Meet</p></td>
<td><p>https://lync.contoso.com/contosoSIPdomain/Meet</p>
<p>https://lync.contoso.com/fabrikamSIPdomain/Meet</p></td>
</tr>
<tr class="odd">
<td><p>Dial-in</p></td>
<td><p>https://lync.contoso.com/Dialin</p></td>
</tr>
<tr class="even">
<td><p>Admin</p></td>
<td><p>https://lync.contoso.com/Admin</p></td>
</tr>
</tbody>
</table>


<div>

## Simple URL Naming and Validation Rules

Topology Builder and the Lync Server Management Shell cmdlets enforce several validation rules for your simple URLs. You are required to set simple URLs for Meet and Dialin, but setting one for Admin is optional. Each SIP domain must have a separate Meet simple URL, but you need only one Dialin simple URL and one Admin simple URL for your whole organization.

Each simple URL in your organization must have a unique name, and cannot be a prefix of another simple URL (for example, you could not set lync.contoso.com/Meet as your Meet simple URL and lync.contoso.com/Meet/Dialin as your Dialin simple URL). Simple URL names cannot contain the FQDN of any of your pools, or any port information (for example, https://FQDN:88/meet is not allowed). All simple URLs must start with the https:// prefix.

Simple URLs can contain only alphanumeric characters (that is, a-z, A-Z, 0-9, and the period (.). If you use other characters, the simple URLs might not work as expected.

</div>

<div>

## Changing Simple URLs after Deployment

If you change a simple URL after initial deployment, you must be aware of how the change impacts your DNS records and certificates for simple URLs. If the base of a simple URL changes, then you must change the DNS records and certificates as well. For example, changing from https://lync.contoso.com/Meet to https://meet.contoso.com changes the base URL from lync.contoso.com to meet.contoso.com, so you would need to change the DNS records and certificates to refer to meet.contoso.com. If you changed the simple URL from https://lync.contoso.com/Meet to https://lync.contoso.com/Meetings, the base URL of lync.contoso.com stays the same, so no DNS or certificate changes are needed.

Whenever you change a simple URL name, however, you must run **Enable-CsComputer** on each Director and Front End Server to register the change.

</div>

</div>

<div>

## See Also


[DNS requirements for simple URLs in Lync Server 2013](lync-server-2013-dns-requirements-for-simple-urls.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

