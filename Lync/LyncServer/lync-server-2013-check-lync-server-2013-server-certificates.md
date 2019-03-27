---
title: 'Lync Server 2013: Check Lync Server 2013 server certificates'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Check server certificates
ms:assetid: 7b0474e8-0efe-47f0-84eb-a1ba575dabfd
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn725210(v=OCS.15)
ms:contentKeyID: 63969620
ms.date: 01/27/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Check Lync Server 2013 server certificates

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-11-01_


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Verification schedule</p></td>
<td><p>Monthly</p></td>
</tr>
<tr class="even">
<td><p>Testing tool</p></td>
<td><p>Windows PowerShell</p></td>
</tr>
<tr class="odd">
<td><p>Permissions required</p></td>
<td><p>When run locally using the Lync Server Management Shell, users must be members of the RTCUniversalServerAdmins security group.</p>
<p>When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the Get-CsCertificate cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:</p>
<p><code>Get-CsAdminRole | Where-Object {$_.Cmdlets -match &quot;Get-CsCertificate&quot;}</code></p></td>
</tr>
</tbody>
</table>


<div>

## Description

The Get-CsCertificate cmdlet enables you to retrieve information about each of your Lync Server certificates. That’s especially important because certificates have a built-in expiration date. For example,, privately-issued certificates typically expire after 12 months. If any of your Lync Server certificates expire then you'll lose the accompanying functionality until that certificate is renewed or replaced.

</div>

<div>

## Running the test

To return information about each of your Lync Server certificates just run the following command:

`Get-CsCertificate`

Or, you can filter the return certificate information based on expiration date. For example, this command limits the returned data to certificates that expire (cannot be used after) June 1, 2014:

`Get-CsCertificate | Where-Object {$_.NotAfter -lt "6/1/2014"}`

For more information, see the Help documentation for the Get-CsCertificate cmdlet.

Note that, although the Test-CsCertificateConfiguration cmdlet exists, it is not very useful to administrators. (Instead, that cmdlet is primarily used by the Certificate wizard.) Although the cmdlet works, the information that it returns is of minimal value as shown in the following output example:

Thumbprint Use

\---------- ---

A9D51A2911C74FABFF7F2A8A994B20857D399107 Default

</div>

<div>

## Reviewing the output

The Get-CsCertificate cmdlet returns information similar to the following for each of your Lync Server certificates:

Issuer : CN=FabrikamCA

NotAfter : 12/28/2015 3:35:41 PM

NotBefore : 1/2/2014 12:49:37 PM

SerialNumber : 611BB01200000000000C

Subject : CN=LYNC-SE.fabrikam.com

AlternativeNames : {sip.fabrikam.com, LYNC-SE.fabrikam.com,

meet.fabrikam.com, admin.fabrikam.com...}

Thumbprint : A9D51A2911C74FABFF7F2A8A994B20857D399107

Use : Default

As a rule, the top issues involving Lync Server certificates involve dates and times, such as when certificates take effect (NotBefore) or when they expire (NotAfter). Because these dates and times are so important, you might want to limit the returned data to information such as the certificate use, the certificate serial number, and the certificate expiration date; then you can quickly review all the certificates and when they will expire. To return just that information, use the command together with the options as shown:

`Get-CsCertificate | Select-Object Use, SerialNumber, NotAfter | Sort-Object NotAfter`

That command returns data similar to the following, with the certificates sorted in order of their expiration date:

Use SerialNumber NotAfter

\--- ------------ --------

Default 611BB01200000000000C 12/28/2015 3:35:41 PM

WebServicesInteral 32980AA20BBB20000191 02/15/2016 2:16:12 PM

WebServicesExternal 0451B012003872651A0C 02/20/2016 7:11:58 AM

If you have certificate problems, you might want to review the AlternativeNames configured for a certificate. At first glance, that seems to be a problem. By default, and depending on the size of your console window, Get-CsCertificate might not be able to display all the names:

AlternativeNames : {sip.fabrikam.com, LYNC.fabrikam.com,

meet.fabrikam.com, admin.fabrika...}

To see all the alternative names assigned to a certificate use a command similar to this one:

`Get-CsCertificate | Where-Object {$_.SerialNumber -eq "611BB01200000000000C"} | Select-Object -ExpandProperty AlternativeNames`

That should show you all of the alternative names on the certificate:

sip.fabrikam.com

LYNC.fabrikam.com

meet.fabrikam.com

admin.fabrikam.com

LYNC-SE.fabrikam.com

Dialin.fabrikam.com

</div>

<div>

## See Also


[Get-CsCertificate](https://docs.microsoft.com/powershell/module/skype/Get-CsCertificate)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

