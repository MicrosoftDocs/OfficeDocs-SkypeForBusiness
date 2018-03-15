---
title: "Synchronize a Kerberos authentication account password to IIS in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 05925a66-2684-4c1b-adfa-69bd0da1bf38
description: "To successfully complete this procedure you should be logged on as a user who is a member of the RTCUniversalServerAdmins group."
---

# Synchronize a Kerberos authentication account password to IIS in Lync Server 2013
[]
To successfully complete this procedure you should be logged on as a user who is a member of the RTCUniversalServerAdmins group.
  
In a site, Front End Servers, Standard Edition servers, and Directors can use a Kerberos authentication account for purposes of authenticating requests to the Web Services service. This procedure locates each server running Web Services in a site that has been assigned a Kerberos account and updates the Internet Information Services (IIS) configuration settings to use the Kerberos account. For details, see [Set a Kerberos authentication account password on a server in Lync Server 2013](set-a-kerberos-authentication-account-password-on-a-server.md).
  
### To set and configure a Kerberos authentication account password

1. Log on to a source computer (such as fe01.contoso.com) as a member of RTCUniversalServerAdmins group.
    
2. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
3. From the Lync Server Management Shell command line, run the following two commands:
    
  ```
  Set-CsKerberosAccountPassword -FromComputer SourceComputer -ToComputer DestinationComputer
  ```

    For example:
    
  ```
  Set-CsKerberosAccountPassword -FromComputer fe01.contoso.com -ToComputer dir01.contoso.com
  ```

    > [!IMPORTANT]
    > The name of the source computer and destination computer must be a fully qualified domain (FQDN) name of the server. You cannot use the pool FQDN unless the pool name is the same as the name of the computer that you are using as a source computer or destination computer. 
  
    > [!IMPORTANT]
    > After making any changes to Kerberos authentication, such as adding an account or removing an account, you must run **Enable-CsTopology** from the Lync Server Management Shell command prompt. 
  

