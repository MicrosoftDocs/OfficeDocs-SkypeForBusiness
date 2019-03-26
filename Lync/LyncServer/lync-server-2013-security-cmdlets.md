---
title: 'Lync Server 2013: Security cmdlets'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Security cmdlets
ms:assetid: 9a6c654d-287d-434e-8d93-409f0d623f5a
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398799(v=OCS.15)
ms:contentKeyID: 48184968
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Security cmdlets in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-09_

The security cmdlets included in Microsoft Lync Server 2013 are primarily used to manage authentication, and user rights and permissions. A wide variety of cmdlets are available for managing authentication, including cmdlets for certificate and personal identification number (PIN) authentication. In addition, a number of cmdlets enable you to use the new role-based access control (RBAC) feature to delegate administrative control of Lync Server.

<div>

## Security Cmdlets

Many management tasks that apply to security settings can be performed from the Lync Server Control Panel. One major exception is the user permission cmdlets. However, all security management tasks can be performed using cmdlets from the Lync Server Management Shell or from within a script; using a script enables you to automate certain tasks. The following is a list of cmdlets that relate directly to managing security settings:

**[Certificate and authentication cmdlets in Lync Server 2013](lync-server-2013-certificate-and-authentication-cmdlets.md)**

  - <span></span>  
    [Get-CsCertificate](https://technet.microsoft.com/en-us/library/Gg398227(v=OCS.15))

  - <span></span>  
    [Import-CsCertificate](https://technet.microsoft.com/en-us/library/Gg398688(v=OCS.15))

  - <span></span>  
    [Remove-CsCertificate](https://technet.microsoft.com/en-us/library/Gg412895(v=OCS.15))

  - <span></span>  
    [Request-CsCertificate](https://technet.microsoft.com/en-us/library/Gg425723(v=OCS.15))

  - <span></span>  
    [Set-CsCertificate](https://technet.microsoft.com/en-us/library/Gg398518(v=OCS.15))

<!-- end list -->

  - <span></span>  
    [Test-CsCertificateConfiguration](https://technet.microsoft.com/en-us/library/Gg398647(v=OCS.15))

<!-- end list -->

  - <span></span>  
    [Get-CsClientCertificate](https://technet.microsoft.com/en-us/library/Gg398143(v=OCS.15))

  - <span></span>  
    [Revoke-CsClientCertificate](https://technet.microsoft.com/en-us/library/Gg425748(v=OCS.15))

<!-- end list -->

  - <span></span>  
    [Lock-CsClientPin](https://technet.microsoft.com/en-us/library/Gg398650(v=OCS.15))

  - <span></span>  
    [Set-CsClientPin](https://technet.microsoft.com/en-us/library/Gg398929(v=OCS.15))

  - <span></span>  
    [Unlock-CsClientPin](unhttps://technet.microsoft.com/en-us/library/Gg398650(v=OCS.15))

<!-- end list -->

  - <span></span>  
    [Get-CsClientPinInfo](https://technet.microsoft.com/en-us/library/Gg425947(v=OCS.15))

<!-- end list -->

  - <span></span>  
    [New-CsKerberosAccount](https://technet.microsoft.com/en-us/library/Gg398485(v=OCS.15))

<!-- end list -->

  - <span></span>  
    [Get-CsKerberosAccountAssignment](https://technet.microsoft.com/en-us/library/Gg398526(v=OCS.15))

  - <span></span>  
    [New-CsKerberosAccountAssignment](https://technet.microsoft.com/en-us/library/Gg398074(v=OCS.15))

  - <span></span>  
    [Remove-CsKerberosAccountAssignment](https://technet.microsoft.com/en-us/library/Gg413052(v=OCS.15))

  - <span></span>  
    [Set-CsKerberosAccountAssignment](https://technet.microsoft.com/en-us/library/Gg398232(v=OCS.15))

  - <span></span>  
    [Test-CsKerberosAccountAssignment](https://technet.microsoft.com/en-us/library/Gg425938(v=OCS.15))

<!-- end list -->

  - <span></span>  
    [Set-CsKerberosAccountPassword](https://technet.microsoft.com/en-us/library/Gg398659(v=OCS.15))

<!-- end list -->

  - <span></span>  
    [Get-CsPinPolicy](https://technet.microsoft.com/en-us/library/Gg398262(v=OCS.15))

  - <span></span>  
    [Grant-CsPinPolicy](https://technet.microsoft.com/en-us/library/Gg398871(v=OCS.15))

  - <span></span>  
    [New-CsPinPolicy](https://technet.microsoft.com/en-us/library/Gg398935(v=OCS.15))

  - <span></span>  
    [Remove-CsPinPolicy](https://technet.microsoft.com/en-us/library/Gg398431(v=OCS.15))

  - <span></span>  
    [Set-CsPinPolicy](https://technet.microsoft.com/en-us/library/Gg412997(v=OCS.15))

<!-- end list -->

  - <span></span>  
    [Get-CsProxyConfiguration](https://technet.microsoft.com/en-us/library/Gg399011(v=OCS.15))

  - <span></span>  
    [New-CsProxyConfiguration](https://technet.microsoft.com/en-us/library/Gg398335(v=OCS.15))

  - <span></span>  
    [Remove-CsProxyConfiguration](https://technet.microsoft.com/en-us/library/Gg398553(v=OCS.15))

  - <span></span>  
    [Set-CsProxyConfiguration](https://technet.microsoft.com/en-us/library/Gg425796(v=OCS.15))

<!-- end list -->

  - <span></span>  
    [Get-CsSipDomain](https://technet.microsoft.com/en-us/library/Gg398701(v=OCS.15))

  - <span></span>  
    [New-CsSipDomain](https://technet.microsoft.com/en-us/library/Gg425857(v=OCS.15))

  - <span></span>  
    [Remove-CsSipDomain](https://technet.microsoft.com/en-us/library/Gg398865(v=OCS.15))

  - <span></span>  
    [Set-CsSipDomain](https://technet.microsoft.com/en-us/library/Gg412949(v=OCS.15))

**[User rights and permissions cmdlets in Lync Server 2013](lync-server-2013-user-rights-and-permissions-cmdlets.md)**

  - <span></span>  
    [Get-CsAdminRole](https://technet.microsoft.com/en-us/library/Gg399050(v=OCS.15))

  - <span></span>  
    [New-CsAdminRole](https://technet.microsoft.com/en-us/library/Gg398271(v=OCS.15))

  - <span></span>  
    [Remove-CsAdminRole](https://technet.microsoft.com/en-us/library/Gg413036(v=OCS.15))

  - <span></span>  
    [Set-CsAdminRole](https://technet.microsoft.com/en-us/library/Gg399066(v=OCS.15))

  - <span></span>  
    [Update-CsAdminRole](https://technet.microsoft.com/en-us/library/JJ204851(v=OCS.15))

<!-- end list -->

  - <span></span>  
    [Get-CsAdminRoleAssignment](https://technet.microsoft.com/en-us/library/Gg398434(v=OCS.15))

<!-- end list -->

  - <span></span>  
    [Grant-CsOUPermission](https://technet.microsoft.com/en-us/library/Gg425739(v=OCS.15))

  - <span></span>  
    [Revoke-CsOUPermission](https://technet.microsoft.com/en-us/library/Gg398977(v=OCS.15))

  - <span></span>  
    [Test-CsOUPermission](https://technet.microsoft.com/en-us/library/Gg398787(v=OCS.15))

<!-- end list -->

  - <span></span>  
    [Grant-CsSetupPermission](https://technet.microsoft.com/en-us/library/Gg398569(v=OCS.15))

  - <span></span>  
    [Revoke-CsSetupPermission](https://technet.microsoft.com/en-us/library/Gg425834(v=OCS.15))

  - <span></span>  
    [Test-CsSetupPermission](https://technet.microsoft.com/en-us/library/Gg398428(v=OCS.15))

**[Interoperability cmdlets in Lync Server 2013](lync-server-2013-interoperability-cmdlets.md)**

  - [Get-CsOAuthConfiguration](https://technet.microsoft.com/en-us/library/JJ205155(v=OCS.15))

  - [Set-CsOAuthConfiguration](https://technet.microsoft.com/en-us/library/JJ204841(v=OCS.15))

<!-- end list -->

  - [Get-CsOAuthServer](https://technet.microsoft.com/en-us/library/JJ205238(v=OCS.15))

  - [New-CsOAuthServer](https://technet.microsoft.com/en-us/library/JJ205206(v=OCS.15))

  - [Remove-CsOAuthServer](https://technet.microsoft.com/en-us/library/JJ205408(v=OCS.15))

  - [Set-CsOAuthServer](https://technet.microsoft.com/en-us/library/JJ204896(v=OCS.15))

<!-- end list -->

  - [Get-CsPartnerApplication](https://technet.microsoft.com/en-us/library/JJ205128(v=OCS.15))

  - [New-CsPartnerApplication](https://technet.microsoft.com/en-us/library/JJ204628(v=OCS.15))

  - [Remove-CsPartnerApplication](https://technet.microsoft.com/en-us/library/JJ204820(v=OCS.15))

  - [Set-CsPartnerApplication](https://technet.microsoft.com/en-us/library/JJ204755(v=OCS.15))

</div>

<div>

## See Also


[Lync Server PowerShell Blog](http://go.microsoft.com/fwlink/p/?linkid=203150)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

