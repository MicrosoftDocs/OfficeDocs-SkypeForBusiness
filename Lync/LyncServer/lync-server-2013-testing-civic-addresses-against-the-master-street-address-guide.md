---
title: 'Testing civic addresses against the master street address guide'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Testing civic addresses against the master street address guide
ms:assetid: dc680de9-2a0f-4fd3-a99e-9bab0bc30ae5
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn690132(v=OCS.15)
ms:contentKeyID: 63969657
ms.date: 01/27/2015
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Testing civic addresses against the master street address guide in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-06-05_


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Verification schedule</p></td>
<td><p>Daily</p></td>
</tr>
<tr class="even">
<td><p>Testing tool</p></td>
<td><p>Windows PowerShell</p></td>
</tr>
<tr class="odd">
<td><p>Permissions required</p></td>
<td><p>When run locally using the Lync Server Management Shell, users must be members of the RTCUniversalServerAdmins security group.</p>
<p>When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the Test-CsRegistration cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:</p>
<pre><code>Get-CsAdminRole | Where-Object {$_.Cmdlets -match &quot;Test-CsLisCivicAddress &quot;}</code></pre></td>
</tr>
</tbody>
</table>


<div>

## Description

The Test-CsLisCivicAddress cmdlet is used to verify locations that were added to your Location Information service (LIS) database. The cmdlet works by comparing locations against the locations found in the Master Street Address Guide (MSAG) that belongs to your E9-1-1 Network Routing Provider. If you do not have a network routing provider or if the provider cannot be reached, then your tests will fail.

If you add the optional switch parameter UpdateValidationStatus to your command, then the corresponding MSAGValid database property will be set to True for each address passing the test.

</div>

<div>

## Running the test

The Test-CsLisCivicAddress cmdlet can be used to test individual addresses or to test multiple addresses. For example, this command tests a single address located in Redmond, WA:

    Test-CsLisCivicAddress -HouseNumber 1234 -HouseNumberSuffix "" -PreDirectional "" -StreetName Main -StreetSuffix St -PostDirectional "" -City Redmond -State WA -PostalCode 98052 -Country US -UpdateValidationStatus

By comparison, this command tests all the addresses currently in your LIS database:

    Get-CsLisCivicAddress | Test-CsLisCivicAddress -UpdateValidationStatus

For more information, see the Help documentation for the [Test-CsRegistration](https://technet.microsoft.com/en-us/library/Gg412737(v=OCS.15)) cmdlet.

</div>

<div>

## Determining success or failure

Test-CsLisCivicAddress will report back Success or Failure for the supplied addresses. An address test will fail if the address cannot be found or if the service provider cannot be contacted.

</div>

<div>

## Reasons why the test might have failed

Here are some common reasons why Test-CsLisCivicAddress might fail:

  - The LIS service provider might not be available. You can retrieve the URL of your LIS service provider by running the Get-CsLisConfiguration cmdlet:
    
        Get-CsLisConfiguration 
    
    You can then ping that URL to verify that the service provider is available.

</div>

</div>

<span> </span>

</div>

</div>

</div>

