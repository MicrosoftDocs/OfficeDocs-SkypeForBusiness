---
title: Make Phone System Direct Routing service decisions - Microsoft Teams
author: rmw2890
ms.author: MyAdvisor
manager: serdars
ms.date: 07/09/2018
ms.topic: conceptual
ms.service: msteams
search.appverid: MET150
ms.reviewer: rowille
description: Learn about Direct Routing, licensing, and the decisions that need to be made.
localization_priority: Normal
MS.collection: 
- Teams_ITAdmin_PracticalGuidance
- M365-collaboration
appliesto:
- Microsoft Teams
---

# Make my service decisions

To plan for the technical implementation of Phone System Direct Routing (“Direct
Routing”), you must make a series of service decisions ahead of time to better
prepare your organization to implement a solution that meets the business
requirements you’ve defined.

## Calling in Teams

With Microsoft Teams, your users can place and receive phone calls to or from
the public switched telephone network (PSTN). Your users can use their own
dedicated phone numbers for placing and receiving domestic and international
phone calls (including voicemail) from the Teams client application.

## Direct Routing

For Teams users to be able to place and receive PSTN calls, they need to be
enabled for Phone System, a feature in Office 365.

To enable connectivity to the PSTN, you can use Direct Routing to give people in
your organization the ability to make and receive phone calls outside of the
organization over the PSTN.

With Direct Routing, PSTN connectivity is facilitated by a third-party provider,
giving you the ability to continue using your existing PSTN trunks provided by
your PSTN service provider. This allows for deployment in countries where Phone
System with Calling Plans (“Calling Plans”) aren’t available, or in deployments
where an existing PSTN service provider contract needs to be maintained or
interoperability with certain on-premises systems is required.

<!--ENDOFSECTION-->

## Availability of Direct Routing

Direct Routing is available in any country where Office 365 is available. See
[International availability](https://products.office.com/business/international-availability)
for a list of these countries.

After confirming that your organization can obtain the Phone System feature,
compile the list of user locations or offices where you’ll be implementing Phone
System, based on the list of available countries and regions. Also identify the users 
who you are going to enable Calling Plans or Direct Routing for each location you have.

|         |         |         |
|---------|---------|---------|
|<img src="media/audio_conferencing_image7.png" />|Decision points|<ul><li>Identify the user locations or offices in which you’ll implement Phone System.<li>Identify the users who you are going to enable Calling Plans or Direct Routing for each location you have.</ul>|
|<img src="media/audio_conferencing_image9.png" />|Next steps|<ul><li>Document the user locations or offices to be enabled for Phone System.<li>Document the list of users who you are going to enable Calling Plans or Direct Routing for each location you have</ul>|

> [!TIP]
> Below is an example of a Direct Routing site enablement list.
> 
> | **Office**                     | **Location**   | **Phone System service** |
> |--------------------------------|----------------|--------------------------|
> | One Epping Road                | Australia      | Legacy PSTN service |
> | 100 Cyberport Road             | Hong Kong SAR  | Phone System Direct Routing |
> | One Marina Boulevard           | Singapore      | Phone System Direct Routing |
> | 32 London Bridge Street        | United Kingdom | Phone System with Calling Plans |
> | 39 quai du Président Roosevelt | France         | Phone System with Calling Plans |

<!--ENDOFSECTION-->

## Phone numbers and emergency locations

Phone System requires every user in your organization to have a unique direct
inward dialing (DID) phone number. With Direct Routing, the phone numbers and
the emergency services are provided by your PSTN service provider.

> [!NOTE]
> With Direct Routing, your users can continue using their own phone numbers, provided by the PSTN service provider.
> 
> [!TIP]
> You can use the following template to document the phone numbers details.
> 
> |User |Phone number |
> |-----|-------------|
> |Emily Braun | +44 23 4567 8901 |
> |Lidia Holloway | +44 23 4567 89112 |
> |Louis Lahr | +44 23 4567 8921 |
> |Marcel Beauchamp | TBA |
> |Rachelle Cormier | TBA |
> |Isabell Potvin | TBA |

<!--ENDOFSECTION-->

## Voicemail

Cloud Voicemail, powered by Azure Voicemail services, supports voicemail
deposits to Exchange mailboxes only and doesn’t support third-party email
systems.

Cloud Voicemail includes voicemail transcription, which is enabled for
all users in your organization by default. Your business needs might require
that you disable voicemail transcription for specific users or everyone
throughout the organization. If your organization decided to keep voicemail
transcription enabled, you need to also consider whether voicemail transcription
profanity masking needs to be enabled. See [Setting voicemail policies in your organization](set-up-phone-system-voicemail.md)
for more details.

For more information about voicemail in a Phone System implementation, see [Set up Cloud Voicemail](set-up-phone-system-voicemail.md).

|         |         |         |
|---------|---------|---------|
|<img src="media/audio_conferencing_image7.png" />|Decision points|<ul><li>Decide whether you’ll enable Cloud Voicemail in your Direct Routing implementation.<li>Decide whether you’ll enable or disable voicemail transcription and voicemail transcription profanity masking throughout the organization or for specific users.</ul>|
|<img src="media/audio_conferencing_image9.png" />|Next steps|<ul><li>If applicable, document the decision points to support Cloud Voicemail.<li>If you’ll enable or disable voicemail, voicemail transcription, and voicemail transcription profanity masking only for specific users, document that list of users.</ul>|

> [!TIP]
> Cloud Voicemail details for the Calling Plans implementation can be documented as in the following table.
> 
> | **User**         | **Exchange mailbox** | **Enable voicemail?** | **Voicemail transcription** | **Voicemail transcription profanity masking** |
> |------------------|----------------------|-----------------------|-----------------------------|-----------------------------------------------|
> | Emily Braun      | Online               | Yes                   | Enabled                     | Enabled                                       |
> | Lidia Holloway   | Online               | Yes                   | Enabled                     | Disabled                                      |
> | Louis Lahr       | On-premises          | Yes                   | Enabled                     | Enabled                                       |
> | Marcel Beauchamp | On-premises          | Yes                   | Disabled                    | N/A                                           |
> | Rachelle Cormier | Online               | Yes                   | Disabled                    | N/A                                           |
> | Isabell Potvin   | On-premises          | Yes                   | Disabled                    | N/A                                           |
> 
> [!NOTE]
> To use Teams and voicemail, your users must have Exchange mailboxes. See [How Exchange and Microsoft Teams interact](exchange-teams-interact.md) for more details.

<!--ENDOFSECTION-->

## Licensing for Direct Routing

If your organization intends to use Direct Routing, you need to obtain required
licenses. Users of Direct Routing must have the following licenses assigned in
Office 365:

-   Microsoft Phone System

-   Microsoft Teams

-   Audio Conferencing

Audio Conferencing license is required for adding external participants to
scheduled meetings, either by dialing out to them or by providing the dial-in
number. When an external participant is dialed out to, the Audio Conferencing
service places the call by using online calling capabilities. Audio Conferencing 
license is optional, and only required for users who will be organizing Teams conferences 
that include Audio Conferencing.


> [!NOTE]
> To provide toll-free conference bridge phone numbers and to support conferencing dial-out to international phone numbers, you should set up [Communications Credits](what-are-communications-credits.md) for your organization.

Audio Conferencing and Phone System can be licensed separately as add-on
services for existing customers who have Office 365 E3 or E1 subscription plans;
they’re already included as part of the Office 365 E5 subscription plan.

> [!TIP]
> You can also use Direct Routing for the users who are enabled for Calling Plans
when routing their calls to third-party PBXs. For more details, see [Licensing and other requirements of Direct Routing](direct-routing-plan.md#licensing-and-other-requirements).


|         |         |         |
|---------|---------|---------|
|<img src="media/audio_conferencing_image7.png" />|Decision points|<ul><li>If your organization doesn’t have the required Phone System license, decide whether you’ll acquire the Phone System license by stepping up your existing Office 365 subscriptions or by acquiring the Phone System add-on service.<li>Decide whether you’ll need Communications Credits for your Direct Routing implementation.</ul>|
|<img src="media/audio_conferencing_image9.png" />|Next steps|<ul><li>Document the division, department, office, or user groups you’ll assign a Phone System license.<li>If Audio Conferencing with toll-free numbers is in scope, document the division, department, office, or user groups you’ll enable Communications Credits.</ul>|

<!--ENDOFSECTION-->

## Office 365 considerations

Any user who will be enabled for Direct Routing must be homed in Office 365. For
hybrid deployments with on-premises Skype for Business Server or Lync Server,
you need to move users to Skype for Business Online before configuring them to
use Direct Routing with Teams.

All users who are in scope of Direct Routing implementations must be enabled for
Teams.

Your Office 365 tenant must be enabled with one or more domains, because the
default \*.onmicrosoft.com domain can’t be used with Direct Routing. For more
information about domains and Office 365 tenants, see [Domains
FAQ](https://support.office.com/article/Domains-FAQ-1272bad0-4bd4-4796-8005-67d6fb3afc5a).

|         |         |         |
|---------|---------|---------|
|<img src="media/audio_conferencing_image7.png" />|Decision points|<ul><li>Decide whether any users need to be migrated to Skype for Business Online to support Direct Routing.<li>Identify the users who need to be enabled for Teams.</ul>|
|<img src="media/audio_conferencing_image9.png" />|Next steps|<ul><li>Document the list of users who need to move to Skype for Business Online and be enabled for Teams.</ul>|

<!--ENDOFSECTION-->

## SBC considerations

You need to use certified and supported session border controllers (SBCs) that
need to be paired to the Direct Routing service to provide PSTN connectivity for
your users. For a list of certified SBCs, see [Supported Session Border Controllers](direct-routing-plan.md#supported-session-border-controllers-sbcs).

Depending on your environment, number of locations, and voice routing
requirements, you might need to deploy multiple SBCs to support your user base.

### SBC domain names

Each SBC that you pair with Direct Routing must have a unique DNS name. The SBC
DNS names must be from one of the domain names registered in the Office 365
tenant. If your tenant has been assigned multiple domain names, you can use any
of these domain names when planning for your SBCs’ DNS names.

> [!IMPORTANT]
> The use of *.onmicrosoft.com for the SBC DNS name is not allowed.

### Certificates

Each SBC deployed with Direct Routing requires a certificate obtained from a
list of supported certification authorities. The certificate must include the
SBC DNS name in the subject, subject alternate name, or common name fields.

> [!NOTE]
> The use of wildcard certificates with SBCs is also supported.

For more information and a list of supported certification authorities, see
[Public trusted certificate for the SBC](direct-routing-plan.md#public-trusted-certificate-for-the-sbc).


### SBC IP addresses and ports

Each SBC must be configured by using a public IP address accessible from Office
365 datacenters. You can also configure network address translation (NAT) to
publish your SBCs to Office 365 datacenters.

SBCs require bidirectional connectivity to communicate with the cloud services
for signaling and media. Signaling is handled by the component named *SIP
Proxy*, and the media is handled by the *Media Processors*.

You need to define specific port numbers on each SBC for SIP signaling and
media, and configure your firewalls to allow bidirectional traffic to these
ports and their associated IP addresses.

For more details, see [SIP Signaling: FQDNs and firewall ports](direct-routing-plan.md#sip-signaling-fqdns-and-firewall-ports)
and [Media traffic: Port ranges](direct-routing-plan.md#media-traffic-port-ranges).


> [!NOTE]
> We highly recommend setting a maximum concurrent session limit for each SBC,
> based on the SBC model. That limit would then trigger a notification when the
> SBC is running at or near its capacity.

|         |         |         |
|---------|---------|---------|
|<img src="media/audio_conferencing_image7.png" />|Decision points|<ul><li>Decide at which locations you’ll deploy SBCs.<li>Decide a DNS name for each SBC you’re planning to deploy.<li>Based on the SBC domain name decision, decide whether you’re going to use a wildcard certificate to support all SBCs in your deployment or a dedicated certificate per SBC.<li>Decide which public certificate authority you’ll obtain the certificates for your SBCs from.<li>Define a public IP address/port pair for each SBC you’ll deploy, and decide whether you’ll assign the public IP addresses to the SBCs or use NAT.<li>Identify the maximum number of concurrent sessions each SBC supports or can handle.<li>Decide which SBCs will be configured by using Media Bypass.</ul>|
|<img src="media/audio_conferencing_image9.png" />|Next steps|<ul><li>Document each decision being made for the SBCs by using the following example table.</ul>|


> [!TIP]
> Use the following template to document the SBC details for your Direct Routing deployment.
> 
> | **SBC DNS Name (FQDN)** | **SBC make and model** | **Certificate** | **Location**  | **IP address** | **SIP signaling port** | **NAT?** | **Max concurrent sessions** | **Media bypass enabled?** |
> |-------------------------|------------------------|-----------------|---------------|----------------|------------------------|----------|-----------------------------|---------------------------|
> | SBC-Europe.contoso.com | TBD | \*.contoso.com | Amsterdam | TBD | TBD | Yes | TBD | No |
> | SBC-Asia.contoso.com | TBD | \*.contoso.com | Hong Kong SAR | TBD | TBD | No | TBD | Yes |
> | SBC-Africa.contoso.com | TBD | \*.contoso.com | Johannesburg | TBD | TBD | Yes | TBD | Yes |

<!--ENDOFSECTION-->

## Voice routing

You need to configure Microsoft Phone System to route the calls to the specific
SBCs for Direct Routing. You can configure voice routes based on:

-   Called number pattern.

-   Called number pattern + the user who makes the call.


Call routing is made up of the following elements:

-   Voice Routing Policy – container for PSTN Usages; can be assigned to a user
    or to multiple users

-   PSTN Usages – container for Voice Routes and PSTN Usages; can be shared in
    different Voice Routing Policies

-   Voice Routes – number pattern and set of Online PSTN Gateways to use for
    calls where the calling number matches the pattern

-   Online PSTN Gateway - pointer at SBC, also stores the configuration that’s
    applied when a call is placed via the SBC, such as forward
    P-Asserted-Identity (PAI) or Preferred Codecs; can be added to Voice Routes

You can configure your voice routes with Direct Routing to coexist with Calling
Plans. That configuration allows Calling Plans to route some of the calls to the
specific SBCs by using Direct Routing.

> [!TIP]
> SBCs can be designated as *active* and *backup*. That means when the SBC that’s
> configured as active for this number pattern — or number pattern + specific
> user—isn’t available, the calls will be routed to a backup SBC.

|         |         |         |
|---------|---------|---------|
|<img src="media/audio_conferencing_image7.png" />|Decision points|<ul><li>Decide the voice routing policies, PSTN usages, and voice routes that you’ll create to support user locations or offices in scope for the Direct Routing implementation.</ul>|
|<img src="media/audio_conferencing_image9.png" />|Next steps|<ul><li>Document voice routing policies, PSTN usages, and voice routes  for your organization.<li>Document the users to be assigned for each voice routing policy you define.</ul>|

> [!TIP]
> Use the following template to document the voice policies for your Direct
> Routing deployment.
> 
> | **PSTN usage** | **Voice route** | **Number pattern** | **Priority** | **SBC** | **Description** |
> |----------------|-----------------|----------------------------|--------------|-----------------------------------|-----------------------------------------------------------------------------------------|
> | US only | “Redmond 1” | \^\\+1(425\|206)(\\d{7})\$ | 1 | sbc1.contoso.com sbc2.contoso.com | Active route for called numbers +1 425 XXX XX XX or +1 206 XXX XX XX |
> | US only | “Redmond 2” | \^\\+1(425\|206)(\\d{7})\$ | 2 | sbc3.contoso.com sbc4.contoso.com | Backup route for called numbers +1 425 XXX XX XX or +1 206 XXX XX XX |
> | US only | "Other +1” | \^\\+1(\\d{10})\$ | 3 | sbc5.contoso.com sbc6.contoso.com | Route for called numbers +1 XXX XXX XX XX (except +1 425 XXX XX XX or +1 206 XXX XX XX) |
> | International | International | \\d+ | 4 | sbc2.contoso.com sbc5.contoso.com | Route for any number pattern |
> 
> [!IMPORTANT]
> The PSTN Usages in Voice Routing Policies are applied in order, and if a match
> is found in the first usage, other usages are never evaluated.

<!--ENDOFSECTION-->

## Calling and Interop policies

Direct Routing is only supported with Microsoft Teams. To place or receive PSTN
calls through Direct Routing, you need to configure the necessary policies to
ensure incoming calls are received in Teams.

> [!NOTE]
> Users who are enabled for Direct Routing can’t place or receive Direct Routing 
> calls by using Skype for Business, and therefore must be deployed the Teams client.

You can configure your users to set Teams as their preferred client for calls by
one of the following two methods:

-   Configure the user for Teams-only mode

-   Configure Teams as the preferred calling client by assigning the
    TeamsCallingPolicy and the TeamsInteropPolicy.

For more details, see [Set Microsoft Teams as the preferred calling client for users](direct-routing-configure.md#set-microsoft-teams-as-the-preferred-calling-client-for-users).


|         |         |         |
|---------|---------|---------|
|<img src="media/audio_conferencing_image7.png" />|Decision points|<ul><li>Decide which approach you’ll use to set Teams as the preferred client for calls.</ul>|
|<img src="media/audio_conferencing_image9.png" />|Next steps|<ul><li>Document the users to be configured with Interop and Calling policies.</ul>|

> [!IMPORTANT]
> When a user is configured for Teams-only mode, this user can no longer sign in
> to Skype for Business.

To have your users see the Calls tab in the Teams client, you need to enable private calling at an organizational level for the tenant. See [Enable Calling for Microsoft Teams](direct-routing-configure.md) for more details on how to enable private calls.


<!--ENDOFSECTION-->

## Document service decisions

Use the information from the previous sections of this article to document your
service decisions. In general, this documentation will contain the following
main sections:

-   Phone System with Calling Plans site enablement list

-   Voicemail configuration details

-   License assignment for Phone System Direct Routing users

-   SBC configuration details

-   Voice routing policy and routing details

-   Interop and calling policy details

<!--ENDOFSECTION-->
