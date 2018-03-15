---
title: "View conferencing device information in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 838bdbf8-8b68-4eb6-8fa3-45bfd5b0b1cd
description: "You can view information about the conferencing devices configured for use in your organization by using Windows PowerShell and the Get-CsMeetingRoom cmdlet. Run the Get-CsMeetingRoom cmdlet from either the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell."
---

# View conferencing device information in Lync Server 2013
[]
You can view information about the conferencing devices configured for use in your organization by using Windows PowerShell and the **Get-CsMeetingRoom** cmdlet. Run the **Get-CsMeetingRoom** cmdlet from either the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. 
  
> [!NOTE]
> For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876). 
  
If you use the **Get-CsMeetingRoom** cmdlet without any parameters, it returns information about all your conferencing devices. Optional parameters provide different ways for you to filter information. For details, see the Parameters section of [Get-CsMeetingRoom](get-csmeetingroom.md).
  
## 

### Viewing Information about All Your Conferencing Devices

- To view details about all your conferencing devices, type the following command in the Lync Server Management Shell, and then press Enter:
    
  ```
  Get-CsMeetingRoom
  ```

    This cmdlet returns information similar to the following for each conferencing device. Note that this example shows only some of the information that you'll see when you run this cmdlet:
    
  ```
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
  ```

### Viewing Information about a Specific Conferencing Device

- To view information for a specific conferencing device, include the Identity parameter followed by the conferencing device identity (typically, the Active Directory display name). For example:
    
  ```
  Get-CsMeetingRoom -Identity "Room 1219"
  ```

For details, see the Help topic for the [Get-CsMeetingRoom](get-csmeetingroom.md) cmdlet. 
  

