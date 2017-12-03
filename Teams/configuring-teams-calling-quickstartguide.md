---
title: Configuring Phone System with Calling Plans in Microsoft Teams Quick Start Guide
author: AgusRachman
ms.author: arachman
manager: lehewe
ms.date: 12/07/2017
ms.topic: quick start guide
ms.prod: teams
description: Quick start guide for configuring calling plans in Microsoft Teams
Set_Free_Tag: Strat_MT_TeamsAdmin
---

Configuring Phone System with Calling Plans in Microsoft Teams Quick Start Guide
================================================================================

We have provided this quick start guide so that you can get an initial set of users up and running to explore the exciting features of Phone System with Calling Plans in Microsoft Teams.

> [!NOTE]
> We do recommend that in parallel to following this guide, you engage with our [practical guidance](https://docs.microsoft.com/en-us/MicrosoftTeams/phone-system-with-calling-plans), [Fast Track and Partners](https://aka.ms/cloudvoide) to plan and drive your successful wider rollout.

By adding Phone System with Calling Plans, a feature in Office 365 which is powered by Skype, you can now use Teams to place/receive phone calls to land lines and mobile phones via the PSTN.

![Calling in Teams](media/Calling_in_Teams.png)

#Prerequisites for enabling the Calls tab in Teams
To enable the Calls tab in Teams and enable your users to place and receive PSTN calls, you will need to have users provisioned with **Phone System and Calling Plans**. For information on how to set this up, please refer to [Set up Calling Plans](https://support.office.com/en-us/article/Set-up-Calling-Plans-57893158-1acd-44ac-acaf-19f58264a9e0) documentation.

> [!IMPORTANT]
> Before configuring Phone System with Calling in  Teams, please be aware of the following limitations:
>> * **Hybrid Voice is not supported in Teams** - Hybrid Voice is currently not supported by Microsoft Teams. Hybrid Voice customers are not advised to change any of the policies to receive calls in Teams as this will cause service interruptions.
>> * **Federated calling is not supported in Teams** - Please be aware that federated calling (VoIP calling between tenants/companies) is currently not supported in Teams. Federated calls will always be routed to Skype for Business regardless of how you configure calling until it is supported in Teams.

#Policy configuration
To enable Teams to begin receiving calls, you will need to update `TeamsInteropPolicy` to redirect calls to Teams. For more information about `TeamsInteropPolicy`, please refer to [Microsoft Teams and Skype for Business Interoperability](https://aka.ms/teamssfbinterop) documentation.

##Default policy
Teams has a default policy configuration designed to ensure that existing business workflows are not interrupted during a Teams deployment. By default, VoIP, PSTN, and federated calls to your users will continue to be routed to Skype for Business until you update the policy to enable inbound calling in Teams. This ensures that there are no unintended interruptions in voice service as you start to trial and deploy Teams.
from Teams.

`TeamsInteropPolicy` has the following default configuration:

    Identity                   : Global
    AllowEndUserClientOverride : False
    CallingDefaultClient       : Default
    ChatDefaultClient          : Default

The behaviors of the default configuration are the following:
* **For existing Skype for Business customers**, this policy is designed to ensure that Skype for Business VoIP calls are directed to Skype for Business, and Teams VoIP calls are directed to Teams. PSTN and federated calls will be directed to Skype for Business when this policy is in effect.
* **For customers without Skype for Business**, when in effect, in addition to VoIP calls among Teams users, only outbound PSTN calling will be available in Teams. You will need to alter the [`TeamsInteropPolicy`](https://docs.microsoft.com/en-us/powershell/module/skype/?view=skype-ps) assigned to your users to receive PSTN calls in Teams.

> [!NOTE]
> Users configured with the default policy and have been provisioned with Phone System and Calling Plans can still place outbound PSTN calls. 

###How to configure Teams to use the default policy
By default, global `TeamsInteropPolicy` is applied to all users in your tenant, and it is configured with the default settings as described above. If for some reason you have granted different policies to your users and would like to revert to the default setting, you will need to apply the global [`TeamsInteropPolicy`](https://docs.microsoft.com/en-us/powershell/module/skype/?view=skype-ps) via Skype for Business remote Windows PowerShell session:

    PS C:\> Grant-CsTeamsInteropPolicy -PolicyName Global -Identity user@contoso.com

##Configuring Teams to receive inbound PSTN calls
To receive inbound PSTN calls in Teams, you will need to configure Teams as the default calling application by applying `TeamsInteropPolicy` with `CallingDefaultClient` parameter set to Teams.

> [!IMPORTANT]
> It is recommended that you apply this configuration to an initial set of users to explore these exciting new capabilities prior to making wider or organization level changes.

The following preconfigured `TeamsInteropPolicy` can be considered to configure inbound PSTN calling in Teams:

    Identity                   : Tag:DisallowOverrideCallingTeamsChatTeams
    AllowEndUserClientOverride : False
    CallingDefaultClient       : Teams
    ChatDefaultClient          : Teams

The behaviors of the policy above are the following:
* **For existing Skype for Business customers**, this policy is designed to redirect incoming VoIP calls to Teams. This includes both VoIP (Teams and Skype for Business) and PSTN calls. Federated calls will continue to be received in Skype for Business.
* **For customers without Skype for Business**, when in effect, VoIP and PSTN calls will be received in Teams. Federated calling is currently **not supported** in Teams.

###How to configure Teams to receive VoIP and PSTN calls
Apply the [`TeamsInteropPolicy`](https://docs.microsoft.com/en-us/powershell/module/skype/?view=skype-ps) as described above via Skype for Business remote Windows PowerShell session to redirect calls to Teams:

    PS C:\> Grant-CsTeamsInteropPolicy -PolicyName tag:DisallowOverrideCallingTeamsChatTeams -Identity user@contoso.com

##Configuring Teams to allow users to change their preferred calling experience
To let users to make their own decision over the preferred calling experience, whether to receive calls in Teams or Skype for Business, you need to create a custom `TeamsInteropPolicy` that enables `AllowEndUserClientOverride` parameter.

The following is the example of `TeamsInteropPolicy` to enable user choice of the preferred calling experience:

    Identity                   : Tag:CustomPolicy
    AllowEndUserClientOverride : True
    CallingDefaultClient       : Default
    ChatDefaultClient          : Default

Once this custom policy is applied to the users, the option to change the preferred calling application will be available in Teams client for users to make the changes themselves.

![Preferred calling application option](media/Preferred_calling_application_option.png)

> [!IMPORTANT]
> It is recommended that you apply this configuration to an initial set of users prior to making wider or organization level changes.

###How to create and apply the custom TeamsInteropPolicy
To create the custom [`TeamsInteropPolicy`](https://docs.microsoft.com/en-us/powershell/module/skype/?view=skype-ps) as described above via Skype for Business remote Windows PowerShell session, perform the following:

    PS C:\> New-CsTeamsInteropPolicy -PolicyName tag:CustomPolicy -AllowEndUserClientOverride:$True -CallingDefaultClient:Default -ChatDefaultClient:Default

    PS C:\> Grant-CsTeamsInteropPolicy -PolicyName tag:CustomPolicy -Identity user@contoso.com
