---
title: 'Lync Server 2013: View conferencing device information'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: View conferencing device information
ms:assetid: 838bdbf8-8b68-4eb6-8fa3-45bfd5b0b1cd
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ994043(v=OCS.15)
ms:contentKeyID: 51803954
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# View conferencing device information in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-20_

You can view information about the conferencing devices configured for use in your organization by using Windows PowerShell and the **Get-CsMeetingRoom** cmdlet. Run the **Get-CsMeetingRoom** cmdlet from either the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell.

<div>


> [!NOTE]  
> For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at <A href="http://go.microsoft.com/fwlink/p/?linkid=255876">http://go.microsoft.com/fwlink/p/?linkId=255876</A>.



</div>

If you use the **Get-CsMeetingRoom** cmdlet without any parameters, it returns information about all your conferencing devices. Optional parameters provide different ways for you to filter information. For details, see the Parameters section of [Get-CsMeetingRoom](https://docs.microsoft.com/powershell/module/skype/Get-CsMeetingRoom).

<div>


<div>

## Viewing Information about All Your Conferencing Devices

  - To view details about all your conferencing devices, type the following command in the Lync Server Management Shell, and then press Enter:
    
        Get-CsMeetingRoom
    
    This cmdlet returns information similar to the following for each conferencing device. Note that this example shows only some of the information that you’ll see when you run this cmdlet:
    
        ContactOptionFlags                : 64
        OwnerUrn                          : urn:device:roomsystem
        OriginatorSid                     :
        SamAccountName                    : room12129
        UserPrincipalName                 : room1219@litwareinc.com
        FirstName                         : 
        LastName                          :
        WindowsEmailAddress               :
        Sid                               : S-1-5-21-2831376166-2963252556-2165051629-1257
        LineServerURI                     :
        AudioVideoDisabled                : False
        IPPBXSoftPhoneRoutingEnabled      : False
        RemoteCallControlTelephonyEnabled : False
        PrivateLine                       :
        AcpInfo                           : {}
        HostedVoiceMail                   :
        DisplayName                       : Room 1219

</div>

<div>

## Viewing Information about a Specific Conferencing Device

  - To view information for a specific conferencing device, include the Identity parameter followed by the conferencing device identity (typically, the Active Directory display name). For example:
    
        Get-CsMeetingRoom -Identity "Room 1219"

</div>

For details, see the Help topic for the [Get-CsMeetingRoom](https://docs.microsoft.com/powershell/module/skype/Get-CsMeetingRoom) cmdlet.

</div>

</div>

<span> </span>

</div>

</div>

</div>

