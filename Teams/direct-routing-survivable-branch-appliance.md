---
title: Direct Routing SBA
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.date: 12/08/2020
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-voice
ms.reviewer: crowe
search.appverid: MET150
f1.keywords: 
  - NOCSH
  - ms.teamsadmincenter.directrouting.overview
description: Learn more about Direct Routing, such as configuration, necessary core deployment decisions, and voice routing considerations.
ms.custom: 
  - seo-marvel-apr2020
  - seo-marvel-jun2020
appliesto: 
  - Microsoft Teams
---

# Survivable Branch Appliance (SBA) for Direct Routing


Occasionally, a customer site using Direct Routing to connect to Microsoft Phone System may experience an internet outage.

Assume that the customer site--called a branch--temporarily cannot connect to the Microsoft cloud through Direct Routing. However, the intranet inside the branch is still fully functional and users can connect to the Session Border Controller (SBC) that is providing PSTN connectivity.

This article describes how to use a Survivable Branch Appliance (SBA) to enable Microsoft Phone System to continue to make and receive Public Switched Telephone Network (PSTN) calls in the case of an outage.

## Prerequisites

The SBA is distributable code provided by Microsoft to SBC vendors who then embed code into their firmware or distribute it separately to have SBA run on a separate VM or hardware. 

To get the latest Session Border Controller firmware with the embedded Survivable Branch Appliance,  contact your SBC vendor. In addition, the following is required:

- The SBC needs to be configured for Media Bypass to ensure that the Microsoft Teams client in the branch site can have media flowing directly with the SBC. 

- TLS1.2 should be enabled on the SBA VM OS.
- Ports 3443, 4444 and 8443 are used by Microsoft SBA Server to communicate with the Teams client and should be allowed on the firewall. 
- Port 5061 (or the one configured on the SBC) is used by Microsoft SBA Server to communicate with the SBC and should be allowed on the firewall. 
- UDP Port 123 is used by Microsoft SBA Server to communicate with NTP server and should be allowed on the firewall.
- Port 443 is used by Microsoft SBA Server to communicate with Microsoft 365 and should be allowed on the firewall.
- Azure IP Ranges and Service Tags for the Public Cloud should be defined according to the guidelines described at: https://www.microsoft.com/download/details.aspx?id=56519

## Supported Teams clients

The SBA feature is supported on the following Microsoft Teams clients: 

- Microsoft Teams Windows desktop 

- Microsoft Teams macOS desktop
- Teams for Mobile 
- Teams Phones

## How it works

During an internet outage, the Teams client should switch to the SBA automatically, and ongoing calls should continue with no interruptions. No action is required from the user. As soon as the Teams client detects that the internet is up and any outgoing calls are finished, the client will fall back to normal operation mode and connect to other Teams services. The SBA will upload collected Call Data Records to the cloud and call history will be updated so that this information is available for review by the tenant administrator. 

When the Microsoft Teams client is in offline mode, the following calling-related functionality is available: 

- Making PSTN calls via local SBA/SBC with media flowing through the SBC.

- Receiving PSTN calls via local SBA/SBC with media flowing through the SBC. 

- Hold and Resume of PSTN calls.

## Configuration

For the SBA feature to work, the Teams client needs to know which SBAs are available in each branch site, and which SBAs are assigned to the users in that site. The configuration steps are as follows:

1. Create the SBAs.
2. Create the Teams branch survivability policy.
3. Assign the policy to users.
4. Register an application for the SBA with Azure Active Directory.

All configuration is done by using Skype for Business Online PowerShell cmdlets. (The Teams admin center does not yet support the Direct Routing SBA feature.) 

(For information on configuring the SBC, with links to SBC vendor documentation, see Session Border Controller configuration at the end of this article.)

### Create the SBAs

To create the SBAs, you will use the New-CsTeamsSurvivableBranchAppliance cmdlet. This cmdlet has the following parameters:

| Parameter| Description |
| :------------|:-------|
| Identity  | The identity of the SBA  |
| Fqdn | The FQDN of the SBA |
| Site | The TenantNetworkSite where the SBA is located |
| Description | Free format text |
|||

For example:

``` powershell
C:\> New-CsTeamsSurvivableBranchAppliance  -Fqdn sba1.contoso.com -Description "SBA 1" 
Identity    : sba1.contoso.com 
Fqdn        : sba1.contoso.com 
Site        : 
Description : SBA 1 
```

### Create the Teams Branch Survivability Policy 

To create a policy, you use the New-CsTeamsSurvivableBranchAppliancePolicy cmdlet. This cmdlet has the following parameters. Note that the policy can contain one or more SBAs.

| Parameter| Description |
| :------------|:-------|
| Identity | The identity of the policy |
| BranchApplianceFqdns  | The FQDN of the SBA(s) in the site |
||

For example:

``` powershell
C:\> new-CsTeamsSurvivableBranchAppliancePolicy -Identity CPH -BranchApplianceFqdns "sba1.contoso.com","sba2.contoso.com" 
Identity             : Tag:CPH 
BranchApplianceFqdns : {sba1.contoso.com, sba2.contoso.com} 
```

You can add or remove SBAs from a policy by using the Set-CsTeamsSurvivableBranchAppliancePolicy cmdlet. For example: 

``` powershell
Set-CsTeamsSurvivableBranchAppliancePolicy -Identity CPH -BranchApplianceFqdns @{remove="sba1.contoso.com"} 
Set-CsTeamsSurvivableBranchAppliancePolicy -Identity CPH -BranchApplianceFqdns @{add="sba1.contoso.com"} 
```

### Assign a policy to a user

To assign the policy to individual users, you will use the Grant-CsTeamsSurvivableBranchAppliancePolicy cmdlet. This cmdlet has the following parameters:

| Parameter| Description |
| :------------|:-------|
| Identity | The identity of the user |
| PolicyName | The identity of the policy |
||

For example:

``` powershell
C:\> Grant-CsTeamsSurvivableBranchAppliancePolicy -PolicyName CPH -Identity user@contoso.com 
```

You can remove a policy from a user by granting the $Null policy as shown in the next example:

``` powershell
C:\> Grant-CsTeamsSurvivableBranchAppliancePolicy -PolicyName $Null -Identity user@contoso.com 
```

### Register an application for the SBA with Azure Active Directory

To allow different SBAs used within your tenant to read required data from Microsoft 365, you need to register an application for the SBA with Azure Active Directory. 

For more information about application registration, see the following:

- [Develop line-of-business apps for Azure Active Directory](/azure/active-directory/manage-apps/developer-guidance-for-integrating-applications)

- [Register an application with the Microsoft identity platform](/azure/active-directory/develop/quickstart-register-app).  

You only need to register one application for use by all the SBAs in your tenant. 

For the SBA registration, you need the following values created by the registration: 

- Application (client) ID 
- Client secret 

For the SBA application, keep the following in mind: 

- The name can be whatever you decide.  
- Supported account types = Account in this organizational directory only. 
- The Web Redirect Uri = https://login.microsoftonline.com/common/oauth2/nativeclient.
- Implicit grant tokens = Access tokens and ID tokens. 
- API permissions = Skype and Teams Tenant Admin Access -> Application permissions -> application_access_custom_sba_appliance.
- Client secret: you can use any description and expiration. 
- Remember to copy the client secret immediately after creating it. 
- The Application (client) ID is shown on the Overview tab.

Then follow these steps:

1. Register the application.
2. Set the implicit grant tokens.
3. Set the API permissions.
4. Create the client secret.


## Session Border Controller configuration 

For step-by-step guidance on how to configure your Session Border Controller with the embedded Survivable Branch Appliance, see the documentation provided by your SBC vendor: 

- [AudioCodes](https://www.audiocodes.com/library/technical-documents?query=sba)

- [Ribbon](https://support.sonus.net/pages/viewpage.action?pageId=248644034)

- [Oracle](https://www.oracle.com/technical-resources/documentation/acme-packet.html#Link-MicrosoftTeams) 

- [TE-Systems](https://www.anynode.de/microsoft-teams-sba/)

## Reporting issues

Report any issues to your SBC vendor's support organization. When reporting the issue, indicate that you have a configured Survivable Branch Appliance.

## Known issues

- When you add new Survivable Branch Appliances, it might take some time before you can use them in Survivable Branch Appliance policies.

- When you assign a Survivable Branch Appliance policy to a user, it might take some time before the SBA is shown in the output of Get-CsOnlineUser. 

- Reverse number lookup against Azure AD Contacts is not performed. 

- The SBA does not support call forwarding settings. 

- Making an emergency call to an emergency number configured for dynamic emergency calling (E911) is not supported.
