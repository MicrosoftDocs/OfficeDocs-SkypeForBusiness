---
title: "Assign a Kerberos authentication account to a site in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 4/18/2017
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3d9c587c-c8b8-4f81-8ed9-1458a31fc292
description: "To successfully complete this procedure you should be logged on as a user who is a member of the RTCUniversalServerAdmins group."
---

# Assign a Kerberos authentication account to a site in Lync Server 2013
[]
To successfully complete this procedure you should be logged on as a user who is a member of the RTCUniversalServerAdmins group.
  
After creating the Kerberos account, you must assign it to a site. This is a Lync Server 2013 site, not an Active Directory site. You can create multiple Kerberos authentication accounts per deployment, but you can assign only one account to a site. Use the following procedure to assign a previously created Kerberos authentication account to a site. For details about creating the Kerberos account, see [Create a Kerberos authentication account in Lync Server 2013](create-a-kerberos-authentication-account.md).
  
### To assign a Kerberos authentication account to a site

1. As a member of the RTCUniversalServerAdmins group, log on to a computer in the domain running Lync Server 2013 or on to a computer where the administrative tools are installed.
    
2. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
3. From the command line, run the following two commands:
    
  ```
  New-CsKerberosAccountAssignment -UserAccount "Domain\UserAccount"
  		  -Identity "site:SiteName"
  ```

  ```
  Enable-CsTopology
  ```

    For example:
    
  ```
  New-CsKerberosAccountAssignment -UserAccount "contoso\kerbauth"
  		  -Identity "site:redmond"
  ```

  ```
  Enable-CsTopology
  ```

    > [!NOTE]
    > You must specify the UserAccount parameter by using the Domain\User format. The User@Domain.extension format is not supported for referring to the computer objects created for Kerberos authentication purposes. 
  
4. **OPTIONAL**: You may have configured an override FQDN (fully qualified domain name) for your WebServices, as per [Change the Web Services URL in Lync Server 2013](change-the-web-services-url.md). If that's the case, you'll need to add a SPN for this FQDN as well. For example, if the FQDN was webservices.contoso.local, you would run:
    
  ```
  setspn -S http/webservices.contoso.local kerbauth
  ```

5.     > [!IMPORTANT]
    > After making any changes to Kerberos authentication, such as adding an account or removing an account, you must run **Enable-CsTopology** from the Lync Server Management Shell command prompt. 
  

