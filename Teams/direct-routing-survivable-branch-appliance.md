---
title: Direct Routing SBA
author: CarolynRowe
ms.author: crowe
manager: pamgreen
ms.date: 08/15/2024
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - Tier1
ms.reviewer: filippse
search.appverid: MET150
f1.keywords: 
  - NOCSH
  - ms.teamsadmincenter.directrouting.overview
description: Learn about Direct Routing Survivable Branch Appliance (SBA).
ms.custom: 
  - seo-marvel-apr2020
  - seo-marvel-jun2020
appliesto: 
  - Microsoft Teams
---

# Survivable Branch Appliance (SBA) for Direct Routing

Occasionally, a customer site using Direct Routing to connect to Microsoft Teams Phone may experience an internet outage.

In this scenario, assume that the customer site--called a branch--temporarily can't connect to the Microsoft cloud through Direct Routing. However, the intranet inside the branch is still fully functional, and users can connect to the Session Border Controller (SBC) that is providing PSTN connectivity.

This article describes how to use a Survivable Branch Appliance (SBA) to enable Teams Phone to continue to make and receive Public Switched Telephone Network (PSTN) calls in case of an outage.

## Prerequisites

The SBA is distributable code provided by Microsoft to SBC vendors who then embed code into their firmware or distribute it separately to have the SBA run on a separate VM or hardware. 

To get the latest Session Border Controller firmware with the embedded Survivable Branch Appliance, contact your SBC vendor. In addition, the following is required:

- The SBC is configured for Media Bypass to ensure that the Microsoft Teams client in the branch site can have media flowing directly with the SBC. 

- TLS1.2 is enabled on the SBA VM OS.
- Ports 3443, 4444, and 8443 are used by Microsoft SBA Server to communicate with the Teams client and is allowed on the firewall. 
- Port 5061 (or the one configured on the SBC) is used by Microsoft SBA Server to communicate with the SBC and is allowed on the firewall. 
- UDP Port 123 is used by Microsoft SBA Server to communicate with NTP server and is allowed on the firewall.
- Port 443 is used by Microsoft SBA Server to communicate with Microsoft 365 and is allowed on the firewall.
- Azure IP Ranges and Service Tags for the Public Cloud are defined according to the guidelines described at: https://www.microsoft.com/download/details.aspx?id=56519

## Supported Teams clients

The SBA feature is supported on the following Microsoft Teams clients: 

- Microsoft Teams Windows desktop 
- Microsoft Teams macOS desktop
- Teams Phones

## How it works

During an internet outage, the Teams client switches to the SBA automatically, and ongoing calls continue with no interruptions. No action is required from the user. 

As soon as the Teams client detects that the internet is up, and any outgoing calls are finished, the client falls back to normal operation mode, and connects to other Teams services. The SBA uploads collected Call Data Records to the cloud. Call history is updated for review by the tenant administrator. 

The Teams client-side outage mechanism for the SBA is designed to ensure continuous connectivity and service availability during network disruptions. 

The following conditions must be met:

- Client Policy Check: The user is assigned the branch survivability policy for an SBA that the Teams client connects to--only if the appliance is up.

- Network Status Check: The Teams client connects to the SBA when the internet is disconnected, but the user's device is still connected to the SBA appliance.

Once these conditions are met, the Teams client pings the SBA appliance, and the client checks the policy. If both of these conditions are met, the following occurs: 

- Branch Survivability Policy: The branch survivability policy points to the SBA URLs assigned to the user/tenant. 

- Connection to the SBA on the Teams Client Side: Once the Teams client is offline and the user has the required policies, the Teams client switches to Appliance mode where the user is able to make and receive PSTN calls. A banner is displayed to inform users of the switch to the SBA.
  
  The only UI indicator of the switch to Appliance mode is the banner. If the banner isn't present, the user isn't in SBA mode, and calling won't work. 
  
SBA mode is activated only on desktop clients on a physical machine. VMs and web clients aren't supported at the moment.


When the Microsoft Teams client is in offline mode, the following calling-related functionality is available: 

- Making PSTN calls through the local SBA/SBC with media flowing through the SBC.
- Receiving PSTN calls through the local SBA/SBC with media flowing through the SBC.
- Hold and resume of PSTN calls.
- Blind transfer.
- Call forwarding to a single phone number or Teams user.
- Unanswered call forwarding to single phone number or Teams user.
- Redirect of incoming PSTN call to a Call queue or Auto attendant number to a local agent.
- Redirect of incoming PSTN call to a Call queue or Auto attendant number to an alternative Call queue or Auto attendant number.
- VoIP Fallback. If a VoIP call can't be initiated and the receiving party has a PSTN number, a PSTN call is attempted
- VoIP calls between local users. If both users are registered behind the same SBA, a VoIP call can be initiated instead of PSTN call, and the SBA will support the call.

## Configuration

For the SBA feature to work, the Teams client needs to know which SBAs are available in each branch site, and which SBAs are assigned to the users in that site. The configuration steps are as follows:

1. Create the SBAs.
2. Create the Teams branch survivability policy.
3. Assign the policy to users.
4. Register an application for the SBA with Microsoft Entra ID.

All configuration is done by using Teams PowerShell cmdlets. (The Teams admin center doesn't yet support the Direct Routing SBA feature.) 

For information on configuring the SBC, with links to SBC vendor documentation, see [Session Border Controller configuration](#session-border-controller-configuration).

### Create the SBAs

To create the SBAs, use the New-CsTeamsSurvivableBranchAppliance cmdlet. This cmdlet has the following parameters:

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

To create a policy, use the New-CsTeamsSurvivableBranchAppliancePolicy cmdlet. This cmdlet has the following parameters. The policy can contain one or more SBAs.

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

To assign the policy to individual users, use the Grant-CsTeamsSurvivableBranchAppliancePolicy cmdlet. This cmdlet has the following parameters:

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

<a name='register-an-application-for-the-sba-with-azure-active-directory'></a>

### Register an application for the SBA with Microsoft Entra ID

To allow different SBAs used within your tenant to read required data from Microsoft 365, you need to register an application for the SBA with Microsoft Entra ID. 

For more information about application registration, see the following:

- [Develop line-of-business apps for Microsoft Entra ID](/azure/active-directory/manage-apps/developer-guidance-for-integrating-applications)

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



## Known issues and considerations

The following are known issues and considerations:

- Because the SBA relies on authentication tokens that are valid for 24 hours and are renewed daily, the SBA can support outages for up to 24 hours from the last authentication. If an outage occurs 20 hours after the last authentication token renewal, the SBA will be operational only for the remaining 4 hours.

- If the tenant is using Continuous Access Evaluation (CAE) tokens, the SBA will be operational only for about 30 minutes, due to the nature of continuous access evaluation. An alternative would be to dissable CAE for the tenant.

- When you add new Survivable Branch Appliances, it might take time before you can use them in Survivable Branch Appliance policies.

- When you assign a Survivable Branch Appliance policy to a user, it might take time before the SBA is shown in the output of Get-CsOnlineUser. 

- Reverse number lookup against Microsoft Entra ID Contacts isn't performed. 

- Making an emergency call to an emergency number configured for dynamic emergency calling (E911) is not supported.

## Report an issue

Report any issues to your SBC vendor's support organization. When reporting the issue, indicate that you have a configured Survivable Branch Appliance.
