---
title: Application-based authentication in Teams PowerShell Module
author: pbafna03
ms.author: pbafna
ms.reviewer: pbafna
manager: sshastri
ms.topic: conceptual
audience: admin
ms.service: msteams
ms.collection: 
  - M365-collaboration
description: Learn about application-based authentication in Teams PowerShell Module, used for administration of Microsoft Teams.
appliesto: 
  - Microsoft Teams
---

# Application-based authentication in Teams PowerShell Module

Application-based authentication is supported now in Teams PowerShell Module for a limited set of cmdlets in preview with versions 4.7.1-preview or later. Currently this mode of authentication is only supported in commercial environments.


## Cmdlets Supported

All Non \*-Cs cmdlets (for example, Get-Team), Get-CsTenant, Get-CsOnlineUser, Get-CsOnlineVoiceUser & \*-CsOnlineSipDomain cmdlets are already supported. Other cmdlets will be gradually rolled out. 


## Examples

The following examples show how to use Teams PowerShell Module with the Azure AD app-based authentication: 

- Connect using a certificate thumbprint:

  ```powershell
  Connect-MicrosoftTeams -CertificateThumbprint "XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX" -ApplicationId "00000000-0000-0000-0000-000000000000" -TenantId "YYYYYYYY-YYYY-YYYY-YYYY-YYYYYYYYYYYY"
  ```
  When you use the CertificateThumbprint parameter, the certificate needs to be installed on the computer where you're running the command. The certificate should be installed in the user certificate store.
  
- Connect using Access Tokens:
  
  Access Tokens can be retrieved via the login.microsoftonline.com endpoint. It requires two Access Tokens – “MS Graph” and “Skype and Teams Tenant Admin API” resources.

  ```powershell
  $ClientSecret   = "…"
  $ApplicationID = "00000000-0000-0000-0000-000000000000"
  $TenantID = "YYYYYYYY-YYYY-YYYY-YYYY-YYYYYYYYYYYY"

  $graphtokenBody = @{   
     Grant_Type    = "client_credentials"   
     Scope         = "https://graph.microsoft.com/.default"   
     Client_Id     = $ApplicationID   
     Client_Secret = $ClientSecret   
  }  

  $graphToken = Invoke-RestMethod -Uri "https://login.microsoftonline.com/$TenantID/oauth2/v2.0/token" -Method POST -Body $graphtokenBody | Select-Object -ExpandProperty Access_Token 

  $teamstokenBody = @{   
     Grant_Type    = "client_credentials"   
     Scope         = "48ac35b8-9aa8-4d74-927d-1f4a14a0b239/.default"   
     Client_Id     = $ApplicationID   
     Client_Secret = $ClientSecret 
  } 

  $teamsToken = Invoke-RestMethod -Uri "https://login.microsoftonline.com/$TenantID/oauth2/v2.0/token" -Method POST -Body $teamstokenBody | Select-Object -ExpandProperty Access_Token 

  Connect-MicrosoftTeams -AccessTokens @("$graphToken", "$teamsToken")
  ```
  
## How does it work?

Teams PowerShell Module fetches the app-based token using the application ID, tenant ID and certificate thumbprint. The application object provisioned inside Azure AD has a Directory Role assigned to it, which is returned in the access token. The session's role-based access control (RBAC) is configured using the directory role information that's available in the token.


## Setup Application-based authentication

An initial onboarding is required for authentication using application objects. Application and service principal are used interchangeably, but an application is like a class object while a service principal is like an instance of the class. You can learn more about these objects at [Application and service principal objects in Azure Active Directory](/azure/active-directory/develop/app-objects-and-service-principals).

High level steps for creating applications in Azure Ad are mentioned below, for detailed steps refer this [article](/azure/active-directory/develop/howto-create-service-principal-portal).

1. Register the application in Azure AD
2. Assign API permissions to the application
   - For \*-Cs cmdlets - no API permissions are needed.
   - For Non \*-Cs cmdlets - the Microsoft Graph API permissions needed are `User.Read.All`, `Group.ReadWrite.All`, `AppCatalog.ReadWrite.All`, `TeamSettings.ReadWrite.All`, `Channel.Delete.All`, `ChannelSettings.ReadWrite.All`, `ChannelMember.ReadWrite.All`.  
3. Generate a self-signed certificate
4. Attach the certificate to the Azure AD application
5. Assign Azure AD roles to the application

The application needs to have the appropriate RBAC roles assigned. Because the apps are provisioned in Azure AD, you can use any of the supported built-in roles.
 
