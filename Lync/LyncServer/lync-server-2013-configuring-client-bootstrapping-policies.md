---
title: 'Lync Server 2013: Configuring client bootstrapping policies'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Configuring client bootstrapping policies
ms:assetid: 45042eca-b845-4207-b12f-b8b7f5d44bdf
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425941(v=OCS.15)
ms:contentKeyID: 48184031
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuring client bootstrapping policies in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

The Group Policy Management Console (GPMC) and the Group Policy Object Editor are tools that you use to manage Group Policy. Included with the Office Group Policy Administrative Template are Lync 2013.admx (ADMX) and .adml (ADML) Administrative Templates, which contain the registry-based policy settings that you configure for Group Policy objects in the domain. ADML files are language-specific complements to ADMX files. Each ADMX and ADML file contains the policy settings for a single Office application. For more information, see “Office 2013 Administrative Template files (ADMX, ADML)” in the Office 2013 documentation at <http://go.microsoft.com/fwlink/p/?linkid=267516>.

For Lync 2013, there are several client bootstrapping policies that you should consider configuring before users sign in to the server for the first time. For example, the default servers and security mode that the client should use until sign-in is complete. You can use Group Policy to establish these settings in users’ computer registries before they sign in and begin receiving in-band provisioning settings from the server. The following table lists the Group Policy settings that are available for Lync 2013.

### Group Policy Settings for Lync 2013

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Group Policy setting</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Specify Server<br />
(ConfigurationMode)</p></td>
<td><p>Specifies how Lync 2013 identifies the transport and server to use during sign-in. Within this setting, you specify the following:</p>
<ul>
<li><p>ServerAddressExternal: Specifies the server name or IP address used by clients and federated contacts when connecting from outside the external firewall.</p></li>
<li><p>ServerAddressInternal: Specifies the server name or IP address used when clients connect from inside the organization’s firewall.</p></li>
<li><p>Transport: Specifies either Transmission Control Protocol (TCP) or Transport Layer Security (TLS).</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Additional server versions supported<br />
(ConfiguredServerCheckValues)</p></td>
<td><p>Specifies a list of server version names separated by semi-colons that Lync Server 2013 will log on to, in addition to the server versions that are supported by default.</p></td>
</tr>
<tr class="odd">
<td><p>Disable automatic upload of sign-in failure logs (DisableAutomaticSendTracing)</p></td>
<td><p>Automatically uploads sign-in failure logs to Lync Server for analysis. No logs are automatically uploaded if sign-in is successful. If this policy is not configured, the following happens:</p>
<dl>
<dt><span></span></dt>
<dd><p>For Lync Online users: Sign-in failure logs are automatically uploaded.</p>
</dd>
<dt><span></span></dt>
<dd><p>For Lync on-premises users: A confirmation dialog box is shown to the user before upload.</p>
</dd>
</dl>
<p>When this setting is disabled, sign-in logs are automatically uploaded to the Lync Server for both Lync on-premises and Lync Online users. When this setting is enabled, sign-in logs are never uploaded automatically.</p></td>
</tr>
<tr class="even">
<td><p>Disable HTTP fallback for SIP connection<br />
(DisableHttpConnect)</p></td>
<td><p>Prevents Lync Server from trying to connect to the server by using HTTP, if TLS or TCP are unavailable. By default, Lync first attempts to connect to the server by using TLS or TCP and, if neither of these transport methods is successful, Lync tries to connect by using HTTP. Use this policy to disable the fallback HTTP connection attempt.</p></td>
</tr>
<tr class="odd">
<td><p>Require logon credentials<br />
(DisableNTCredentials)</p></td>
<td><p>Requires the user to provide logon credentials for Lync rather than automatically using Windows credentials during sign-in to a SIP server.</p></td>
</tr>
<tr class="even">
<td><p>Disable server version check<br />
(DisableServerCheck)</p></td>
<td><p>If you set this policy to 1, prevents Lync from checking the server name and version before signing in. By default, Lync makes these checks before signing in.</p></td>
</tr>
<tr class="odd">
<td><p>Enable using BITS to download Address Book Service files<br />
(EnableBitsForGalDownload)</p></td>
<td><p>Enables Lync to use Background Intelligent Transfer Service (BITS) to download the Address Book Services files.</p></td>
</tr>
<tr class="even">
<td><p>Configure SIP security mode<br />
(EnableSIPHighSecurityMode)</p></td>
<td><p>Enables Lync to send and receive instant messages more securely. This policy has no effect on Windows .NET or Microsoft Exchange Server services.</p>
<p>If you do not configure this policy setting, Lync can use any transport. But if it does not use TLS and if the server authenticates users, Lync must use either NTLM or Kerberos authentication.</p></td>
</tr>
<tr class="odd">
<td><p>Global Address Book Download Initial Delay<br />
(GalDownloadInitialDelay)</p></td>
<td><p>Specifies the time period before a download of the global address list (GAL) occurs. The default value is 60 minutes, which means the server delays the download of GAL file for a random period of between 0 and 60 minutes.</p></td>
</tr>
<tr class="even">
<td><p>Prevent users from running Microsoft Lync<br />
(PreventRun)</p></td>
<td><p>Prevents users from running Lync. You can configure this policy setting under both Computer Configuration and User Configuration, but the policy setting under Computer Configuration takes precedence.</p></td>
</tr>
<tr class="odd">
<td><p>Allow storage of user passwords<br />
(SavePassword)</p></td>
<td><p>Enables Lync to store passwords.</p></td>
</tr>
<tr class="even">
<td><p>Configure SIP compression mode<br />
(SipCompression)</p></td>
<td><p>Specifies when to turn on SIP compression. By default, SIP compression is enabled based on the adapter speed. Note that setting this policy might cause an increase in sign-in time.</p></td>
</tr>
<tr class="odd">
<td><p>Trusted Domain List<br />
(TrustModelData)</p></td>
<td><p>Lists the trusted domains that do not match the prefix of the customer SIP domain.</p></td>
</tr>
</tbody>
</table>


Policies configured on the server take precedence over Group Policy settings and client options configured by the user. The following table summarizes the order in which settings take precedence when a conflict occurs.

### Group Policy Precedence

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Precedence</th>
<th>Location or Method of Setting</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>1</p></td>
<td><p>Lync Server 2013 in-band provisioning</p></td>
</tr>
<tr class="even">
<td><p>2</p></td>
<td><p>HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Office\15.0\Lync</p></td>
</tr>
<tr class="odd">
<td><p>3</p></td>
<td><p>HKEY_CURRENT_USER\SOFTWARE\Policies\Microsoft\Office\15.0\Lync</p></td>
</tr>
<tr class="even">
<td><p>4</p></td>
<td><p>The Lync - Options dialog box in Lync 2013</p></td>
</tr>
</tbody>
</table>


<div>

## To define Group Policy settings by using the Lync 2013 administrative template files

1.  Create a root-level folder to contain all language-neutral ADMX files. For example, create the root folder for the central store on your domain controller at this location:
    
    `%systemroot%\sysvol\domain\policies\PolicyDefinitions`
    
    <div>
    

    > [!NOTE]  
    > This procedure assumes that you want to manage multiple computers in your domain. In this case, you store the templates in a central store in the Sysvol folder on the primary domain controller. This provides a replicated central storage location for domain Administrative Templates.

    
    </div>

2.  Create a subfolder for each language that you’ll use. These subfolders will contain the language-specific ADML resource files. For example, create a subfolder for United States English (EN-US) at this location:
    
    `%systemroot%\sysvol\domain\policies\PolicyDefinitions\EN-US`

</div>

</div>

<span> </span>

</div>

</div>

</div>

