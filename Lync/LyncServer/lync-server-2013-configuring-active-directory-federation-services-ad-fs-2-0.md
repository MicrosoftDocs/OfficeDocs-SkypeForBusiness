---
title: 'Lync Server 2013: Configuring Active Directory Federation Services (AD FS 2.0)'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Configuring Active Directory Federation Services (AD FS 2.0)
ms:assetid: 0ba8657f-55b8-41b3-960c-fdc5eeee6978
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn308561(v=OCS.15)
ms:contentKeyID: 54973682
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuring Active Directory Federation Services (AD FS 2.0) for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-07-03_

The following section describes how to configure Active Directory Federation Services (AD FS 2.0) to support multi-factor authentication. For information on how to install AD FS 2.0, see AD FS 2.0 Step-by-Step and How To Guides at [http://go.microsoft.com/fwlink/p/?LinkId=313374](http://go.microsoft.com/fwlink/p/?linkid=313374).

<div class="">


> [!NOTE]  
> When installing AD FS 2.0, do not use the Windows Server Manager to add the Active Directory Federation Services role. Instead, download and install the Active Directory Federation Services 2.0 RTW package at <A href="http://go.microsoft.com/fwlink/p/?linkid=313375">http://go.microsoft.com/fwlink/p/?LinkId=313375</A>.



</div>

<div>


**To configure AD FS for two-factor Authentication**

1.  Log in to the AD FS 2.0 computer using a Domain Admin account.

2.  Start Windows PowerShell.

3.  From the Windows PowerShell command-line, run the following command:
    
        add-pssnapin Microsoft.Adfs.PowerShell

4.  Establish a partnership with each Lync Server 2013 with Cumulative Updates for Lync Server 2013: July 2013 Director, Enterprise Pool, and Standard Edition server that will be enabled for passive authentication by running the following command, replacing the server name specific to your deployment:
    
        Add-ADFSRelyingPartyTrust -Name LyncPool01-PassiveAuth -MetadataURL https://lyncpool01.contoso.com/passiveauth/federationmetadata/2007-06/federationmetadata.xml

5.  From the Administrative Tools menu, launch the AD FS 2.0 Management console.

6.  Expand **Trust Relationships** \> **Relying Party Trusts**.

7.  Verify that a new trust has been created for your Lync Server 2013 with Cumulative Updates for Lync Server 2013: July 2013 Enterprise Pool or Standard Edition server.

8.  Create and assign an Issuance Authorization Rule for your relying party trust using Windows PowerShell by running the following commands:
    
       ```
        $IssuanceAuthorizationRules = '@RuleTemplate = "AllowAllAuthzRule" => issue(Type = "http://schemas.microsoft.com/authorization/claims/permit", Value = "true");'
       ```
    
       ```
        Set-ADFSRelyingPartyTrust -TargetName LyncPool01-PassiveAuth 
        -IssuanceAuthorizationRules $IssuanceAuthorizationRules
       ```

9.  Create and assign an Issuance Transform Rule for your relying party trust using Windows PowerShell by running the following commands:
    
       ```
        $IssuanceTransformRules = '@RuleTemplate = "PassThroughClaims" @RuleName = "Sid" c:[Type == "http://schemas.microsoft.com/ws/2008/06/identity/claims/primarysid"]=> issue(claim = c);'
       ```
    
       ```
        Set-ADFSRelyingPartyTrust -TargetName LyncPool01-PassiveAuth -IssuanceTransformRules $IssuanceTransformRules
       ```

10. From the AD FS 2.0 Management console, right click on your relying party trust and select **Edit Claim Rules**.

11. Select the **Issuance Authorization Rules** tab and verify that the new authorization rule was created successfully.

12. Select the **Issuance Transform Rules** tab and verify that the new transform rule was created successfully.

</div>

</div>

<span> </span>

</div>

</div>

</div>

