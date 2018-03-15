---
title: "Set a Kerberos authentication account password on a server in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 902d3292-678d-4512-9248-586053cb638b
description: "To successfully complete this procedure you should be logged on as a user who is a member of the RTCUniversalServerAdmins group."
---

# Set a Kerberos authentication account password on a server in Lync Server 2013
[]
To successfully complete this procedure you should be logged on as a user who is a member of the RTCUniversalServerAdmins group.
  
You must set up a password on the Kerberos account for each site that has Front End Servers, Standard Edition servers, and Directors. You can set up the password by running the **Set-CsKerberosAccountPassword** Windows PowerShell cmdlet on one server in the site (for example, one Front End Server). For each site, you must run the **Set-CsKerberosAccountPassword** cmdlet. The cmdlet configures Internet Information Services (IIS) for the Web Services service, and then sets the password on the computer account in Active Directory Domain Services. An alternate method, based on which parameter is used with the cmdlet, configures IIS on one server while using another server that has been configured as the source of the Kerberos account password. 
  
When you use the **Set-CsKerberosAccountPassword** cmdlet to set a password, Kerberos sets the password to a randomly generated string. This cmdlet contacts all IIS instances in all Lync Server 2013 central sites to which this account is assigned. 
  
### To set a password for a Kerberos authentication account

1. Log on to any domain computer with Lync Server Management Shell installed as a member of the RTCUniversalServerAdmins group.
    
2. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
3. From the command line, run the following two commands:
    
  ```
  Set-CsKerberosAccountPassword -UserAccount "Domain\UserAccount"
  ```

    For example:
    
  ```
  Set-CsKerberosAccountPassword -UserAccount "contoso\KerbAuth"
  ```

    > [!NOTE]
    > You must specify the UserAccount parameter by using the Domain\User format. The User@Domain.extension format is not supported for referencing the computer objects created for Kerberos authentication purposes. 
  
    > [!IMPORTANT]
    > After making any changes to Kerberos authentication, such as adding an account or removing an account, you must run **Enable-CsTopology** from the Lync Server Management Shell command prompt. 
  

