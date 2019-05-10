---
title: 'Lync Server 2013: Check voice normalization rules'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Check voice normalization rules
ms:assetid: bf71a218-71cd-4b64-b8e8-b3a98b6e87a2
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn725212(v=OCS.15)
ms:contentKeyID: 63969649
ms.date: 01/27/2015
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Check voice normalization rules in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-05-20_


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
<p>When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the Test-CsVoiceNormalizationRule cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:</p>
<p><code>Get-CsAdminRole | Where-Object {$_.Cmdlets -match &quot;Test-CsVoiceNormalizationRule&quot;}</code></p></td>
</tr>
</tbody>
</table>


<div>

## Description

Voice normalization rules are used to convert a phone number dialed by a user (for example, 2065551219) to the E.164 format that is used by Lync Server (+12065551219). For example, if users are in the habit of dialing a phone number without including the country code or the area code (e.g., 5551219) then you must have a voice normalization rule that can convert that number to the E.164 format: +12065551219. Without such a rule, the user won't be able to call 555-1219.

The Test-CsVoiceNormalizationRule cmdlet verifies that a specified voice normalization rule can successfully convert a specified phone number. For example, this command checks whether the global normalization rule NoAreaCode can normalize and convert the dial string 5551219.

`Get-CsVoiceNormalizationRule -Identity "global/NoAreaCode" | Test-CsVoiceNormalizationRule -DialedNumber "5551219"`

</div>

<div>

## Running the test

To run the Test-CsVoiceNormalizationRule cmdlet, you must first use the Get-CsVoiceNormalizationRule cmdlet to retrieve an instance of the rule being tested, and then pipe that instance to Test-CsVoiceNormalizationRule. Syntax similar to this won't work:

Test-CsVoiceNormalizationRule -DialedNumber "12065551219" –NormalizationRule "global/Prefix All"

Instead, use syntax such as the following, which combines both the Get-CsVoiceNormalizationRule and the Test-CsVoiceNormalizationRule cmdlets:

Get-CsVoiceNormalizationRule -Identity "global/Prefix All" | Test-CsVoiceNormalizationRule -DialedNumber "12065551219"

<div>


> [!NOTE]  
> . Or, you can also use this approach to retrieve an instance of a rule and then test that rule against a specified phone number:



</div>

`$x = Get-CsVoiceNormalizationRule -Identity "global/Prefix All"`

`Test-CsVoiceNormalizationRule -DialedNumber "12065551219" -NormalizationRule $x`

Enter the value for the DialedNumber parameter exactly as you expect that number to be dialed. For example, if the specified voice normalization rule is supposed to automatically add the country code (the initial 1 in the value 12065551219) then you should leave off the country code:

`-DialedNumber "2065551219"`

If the rule is configured correctly, it will automatically add the country code when translating the number to the E.164 format that is used by Lync Server.

For more information, see the Help documentation for the Test-CsVoiceNormalizationRule cmdlet.

</div>

<div>

## Determining success or failure

If the specified voice normalization rule can translate the supplied number then the translated number will be displayed on-screen:

TranslatedNumber

\----------------

\+12065551219

If the test fails then a blank translated number will be returned:

TranslatedNumber

\----------------

</div>

<div>

## Reasons why the test might have failed

If the Test-CsVoiceNormalizationRule does return a translated number that means that the specified voice normalization rule was unable to translate the supplied telephone number into the E.164 format that is used by Lync Server. To verify that, first make sure that you typed the telephone number in correctly. For example, you would expect your voice normalization rule to have problems translating a number similar to this:

`-DialedNumber "1"`

Assuming the number was entered correctly, your next step should be to verify that the specified normalization rule is designed to handle that phone number. For example, one normalization rule might be designed to handle the format 12065551219, but a second rule might be designed to handle the number 2065551219. (That’s the same phone number, minus the country code 1 at the very beginning.) To return detailed information about a voice normalization rule, run a command similar to this:

`Get-CsVoiceNormalizationRule -Identity "global/Prefix All" | Format-List`

To return detailed information about all the voice normalization rules, run this command instead:

`Get-CsVoiceNormalizationRule | Format-List`

</div>

<div>

## See Also


[Test-CsVoiceNormalizationRule](https://docs.microsoft.com/powershell/module/skype/Test-CsVoiceNormalizationRule)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

