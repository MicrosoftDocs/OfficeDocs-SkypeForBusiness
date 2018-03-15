---
title: "Security cmdlets in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 9a6c654d-287d-434e-8d93-409f0d623f5a
description: "The security cmdlets included in Microsoft Lync Server 2013 are primarily used to manage authentication, and user rights and permissions. A wide variety of cmdlets are available for managing authentication, including cmdlets for certificate and personal identification number (PIN) authentication. In addition, a number of cmdlets enable you to use the new role-based access control (RBAC) feature to delegate administrative control of Lync Server."
---

# Security cmdlets in Lync Server 2013
[]
The security cmdlets included in Microsoft Lync Server 2013 are primarily used to manage authentication, and user rights and permissions. A wide variety of cmdlets are available for managing authentication, including cmdlets for certificate and personal identification number (PIN) authentication. In addition, a number of cmdlets enable you to use the new role-based access control (RBAC) feature to delegate administrative control of Lync Server.
  
## Security Cmdlets

Many management tasks that apply to security settings can be performed from the Lync Server Control Panel. One major exception is the user permission cmdlets. However, all security management tasks can be performed using cmdlets from the Lync Server Management Shell or from within a script; using a script enables you to automate certain tasks. The following is a list of cmdlets that relate directly to managing security settings:
  
 **[Certificate and authentication cmdlets in Lync Server 2013](certificate-and-authentication-cmdlets.md)**
  
> [Get-CsCertificate](get-cscertificate.md)
    
> [Import-CsCertificate](import-cscertificate.md)
    
> [Remove-CsCertificate](remove-cscertificate.md)
    
> [Request-CsCertificate](request-cscertificate.md)
    
> [Set-CsCertificate](set-cscertificate.md)
    
> [Test-CsCertificateConfiguration](test-cscertificateconfiguration.md)
    
> [Get-CsClientCertificate](get-csclientcertificate.md)
    
> [Revoke-CsClientCertificate](revoke-csclientcertificate.md)
    
> [Lock-CsClientPin](lock-csclientpin.md)
    
> [Set-CsClientPin](set-csclientpin.md)
    
> [Unlock-CsClientPin](unlock-csclientpin.md)
    
> [Get-CsClientPinInfo](get-csclientpininfo.md)
    
> [New-CsKerberosAccount](new-cskerberosaccount.md)
    
> [Get-CsKerberosAccountAssignment](get-cskerberosaccountassignment.md)
    
> [New-CsKerberosAccountAssignment](new-cskerberosaccountassignment.md)
    
> [Remove-CsKerberosAccountAssignment](remove-cskerberosaccountassignment.md)
    
> [Set-CsKerberosAccountAssignment](set-cskerberosaccountassignment.md)
    
> [Test-CsKerberosAccountAssignment](test-cskerberosaccountassignment.md)
    
> [Set-CsKerberosAccountPassword](set-cskerberosaccountpassword.md)
    
> [Get-CsPinPolicy](get-cspinpolicy.md)
    
> [Grant-CsPinPolicy](grant-cspinpolicy.md)
    
> [New-CsPinPolicy](new-cspinpolicy.md)
    
> [Remove-CsPinPolicy](remove-cspinpolicy.md)
    
> [Set-CsPinPolicy](set-cspinpolicy.md)
    
> [Get-CsProxyConfiguration](get-csproxyconfiguration.md)
    
> [New-CsProxyConfiguration](new-csproxyconfiguration.md)
    
> [Remove-CsProxyConfiguration](remove-csproxyconfiguration.md)
    
> [Set-CsProxyConfiguration](set-csproxyconfiguration.md)
    
> [Get-CsSipDomain](get-cssipdomain.md)
    
> [New-CsSipDomain](new-cssipdomain.md)
    
> [Remove-CsSipDomain](remove-cssipdomain.md)
    
> [Set-CsSipDomain](set-cssipdomain.md)
    
 **[User rights and permissions cmdlets in Lync Server 2013](user-rights-and-permissions-cmdlets.md)**
  
> [Get-CsAdminRole](get-csadminrole.md)
    
> [New-CsAdminRole](new-csadminrole.md)
    
> [Remove-CsAdminRole](remove-csadminrole.md)
    
> [Set-CsAdminRole](set-csadminrole.md)
    
> [Update-CsAdminRole](update-csadminrole.md)
    
> [Get-CsAdminRoleAssignment](get-csadminroleassignment.md)
    
> [Grant-CsOUPermission](grant-csoupermission.md)
    
> [Revoke-CsOUPermission](revoke-csoupermission.md)
    
> [Test-CsOUPermission](test-csoupermission.md)
    
> [Grant-CsSetupPermission](grant-cssetuppermission.md)
    
> [Revoke-CsSetupPermission](revoke-cssetuppermission.md)
    
> [Test-CsSetupPermission](test-cssetuppermission.md)
    
 **[Interoperability cmdlets in Lync Server 2013](interoperability-cmdlets.md)**
  
- [Get-CsOAuthConfiguration](get-csoauthconfiguration.md)
    
- [Set-CsOAuthConfiguration](set-csoauthconfiguration.md)
    
- [Get-CsOAuthServer](get-csoauthserver.md)
    
- [New-CsOAuthServer](new-csoauthserver.md)
    
- [Remove-CsOAuthServer](remove-csoauthserver.md)
    
- [Set-CsOAuthServer](set-csoauthserver.md)
    
- [Get-CsPartnerApplication](get-cspartnerapplication.md)
    
- [New-CsPartnerApplication](new-cspartnerapplication.md)
    
- [Remove-CsPartnerApplication](remove-cspartnerapplication.md)
    
- [Set-CsPartnerApplication](set-cspartnerapplication.md)
    
## See also

#### 

[Lync Server PowerShell Blog](https://go.microsoft.com/fwlink/p/?LinkId=203150)

