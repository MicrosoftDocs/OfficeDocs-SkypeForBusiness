---
title: "Configure a Session Border Controller for multiple tenants"
ms.reviewer: filippse
ms.date: 06/17/2024
ms.author: crowe
author: CarolynRowe
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: msteams
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - Tier1
appliesto: 
  - Microsoft Teams
f1.keywords:
- NOCSH
description: Learn how to configure one Session Border Controller (SBC) to serve multiple tenants for Microsoft partners and/or Public Switched Telephone Network (PSTN) carriers.
ms.custom: seo-marvel-apr2020
---

# Configure a Session Border Controller for multiple tenants

Direct Routing supports configuring one Session Border Controller (SBC) to serve multiple tenants.

> [!NOTE]
> This scenario is designed for Microsoft partners and Public Switched Telephone Network (PSTN) carriers. A carrier sells telephony services delivered to Microsoft Teams to their customers. 

To provide services in the Public cloud, both the customer and carrier tenants must be in the Public cloud. To provide services in the GCCH cloud, both the customer and carrier tenants must be in the GCCH cloud. A carrier tenant registered in the Public cloud can't provide services to a GCCH customer tenant.

A carrier:

- Deploys and manages an SBC in their datacenter. Customers don't need to implement an SBC, and they receive telephony services from the carrier in the Teams client.
- Interconnects the SBC to multiple tenants.
- Provides PSTN services to customers.
- Manages call quality end to end.
- Charges separately for PSTN services.

Microsoft doesn't manage carriers. Microsoft offers Teams Phone—a Private Branch Exchange (PBX)—and a Teams client. Microsoft also certifies phones, and certifies SBCs that can be used with Teams Phone. Before choosing a carrier, ensure that your choice has a certified SBC and can manage voice quality end to end.

To configure an SBC to support multiple tenants, the following steps are required:

**Carrier only:**
1. Deploy the SBC and configure it for the hosting scenario according to the [instructions from the certified SBC vendors](#deploy-and-configure-the-sbc).
2. Register a base domain name in the carrier tenant and request a wildcard certificate.
3. Activate the base domain name in the carrier tenant.

**Carrier with a Customer Global Administrator:**
1. Add the subdomain name to the customer tenant.
2. Activate the subdomain name.
3. Configure the trunk from the carrier to the customer tenant and provision users.

*Make sure you understand DNS basics and how the domain name is managed in Microsoft 365. See [Get help with Microsoft 365 domains](/microsoft-365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) before proceeding further.*

## Deploy and configure the SBC

For detailed steps on how to deploy and configure SBCs for an SBC hosting scenario, see the SBC vendor's documentation.

- **AudioCodes:** See [Direct Routing Configuration notes](https://www.audiocodes.com/solutions-products/products/products-for-microsoft-365/direct-routing-for-Microsoft-Teams) for configuration of the SBC hosting scenario as described in "Connecting AudioCodes SBC to Microsoft Teams Direct Routing Hosting Model Configuration Note." 
- **Oracle:** See [Direct Routing Configuration notes](https://www.oracle.com/technetwork/indexes/documentation/acme-packet-2228107.html) for configuration of the SBC hosting scenario as described in the "Microsoft" section. 
- **Ribbon Communications:** See [Ribbon Communications SBC Core Microsoft Teams Configuration Guide](https://support.sonus.net/display/ALLDOC/SBC+8.2+-+MS+Teams+Solution+Guide) for documentation on how to configure Ribbon Core Series SBCs. See also [Ribbon Best Practice - Configuring Carriers for Microsoft Teams Direct Routing SBC Edge](https://support.sonus.net/display/UXDOC81/Connect+SBC+Edge+to+Microsoft+Teams+Direct+Routing+to+Support+Direct+Routing+Carrier)
- **TE-Systems (anynode):** Register on the [TE-Systems Community page](https://community.te-systems.de/) site for documentation and examples on how to configure anynode SBC for multiple tenants.
- **Metaswitch:** Register on the [Metaswitch Community page](https://manuals.metaswitch.com/MAN39555) site for documentation on how to enable Perimeta SBC for multiple tenants.

> [!NOTE]
> Make sure you know how to configure the "Contact" header. The Contact header is used to find the customer tenant on the incoming invite message. 

## Register a base domain and subdomains - Overview

For the hosting scenario, you need to create:

- One base domain name owned by the carrier.
- A subdomain that is part of the base domain name in every customer tenant.

In the following example:

- Adatum is a carrier that serves several customers by providing Internet and telephony services.
- Woodgrove Bank, Contoso, and Adventure Works are three customers that have Microsoft 365  domains but receive the telephony services from Adatum.

Subdomains **MUST** match the FQDN name of the trunk that is configured for the customer and the FQDN in the Contact header when sending the Invite to Microsoft 365. 

When a call arrives at the Microsoft 365 Direct Routing interface, the interface uses the Contact header to find the tenant where the user should be looked up. Direct Routing doesn't use phone number lookup on the Invite, as some customers might have non-DID numbers that can overlap in several tenants. Therefore, the FQDN name in the Contact header is required to identify the exact tenant to look up the user by the phone number.

For more information about creating domain names in Microsoft 365 organizations, see [Get help with Microsoft 365 domains](/microsoft-365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider).

The following table summarizes the requirements for the default domains, additional domains, Request URI, and Contact header.


| Company | Default domain | Additional domain | Request URI | Contact header |
|---------|---------|---------|---------|---------|
| Adatum (carrier)| adatum.biz | sbc1.adatum.biz<br>(carrier base domain name) | NA | NA |
| Woodgrove Bank (customer)| woodgrovebank.us | woodgrovebank.sbc1.adatum.biz<br>(carrier subdomain) | 18775682495@xxx.com | woodgrovebank.sbc1.adatum.biz |
| Contoso (customer) | contoso.com | contoso.sbc1.adatum.biz<br>(carrier subdomain) | 19055680434@xxx.com | contoso.sbc1.adatum.biz | 
|Adventure Works (customer)| adventureworks.com | adventureworks.sbc1.adatum.biz<br>(carrier subdomain) | 18006427676@xxx.com | adventureworks.sbc1.adatum.biz  |

The SBC requires a certificate to authenticate the connections. For the SBC hosting scenario, the carrier needs to request a certificate with CN and/or SAN \*.base_domain (for example, \*.sbc1.adatum.biz). This certificate is used to authenticate connections to multiple tenants served from a single SBC.

The following table is an example of one configuration.


|New domain name |Type|Registered  |Certificate CN/SAN for SBC  |Tenant default domain in the example  |FQDN name that SBC must present in the Contact header when sending calls to users|
|---------|---------|---------|---------|---------|---------|
| sbc1.adatum.biz |    Base     |     In carrier tenant  |   *.sbc1.adatum.biz   |   adatum.biz      |NA, this is a service tenant, no users |
| woodgrovebank.sbc1.adatum.biz   |  Subdomain  |    In a customer tenant  |  *.sbc1.adatum.biz  | woodgrovebank.us  |  woodgrovebank.sbc1.adatum.biz |
| contoso.sbc1.adatum.biz |   Subdomain | In a customer tenant   |  *.sbc1.adatum.biz   |contoso.com | contoso.sbc1.adatum.biz |
| adventureworks.sbc1.adatum.biz  |   Subdomain | In a customer tenant | *.sbc1.adatum.biz   |  adventureworks.com | adventureworks.sbc1.adatum.biz  |


The example in this article:

1. [Registers a base domain name (sbc1.adatum.biz) in the carrier tenant](#register-a-base-domain-name-in-the-carrier-tenant---example).

2. [Registers a subdomain in one customer tenant (woodgrovebank.sbc1.adatum.biz in the Woodgrove Bank tenant)](#register-a-subdomain-name-in-a-customer-tenant---example).


## Register a base domain name in the carrier tenant - Example

**In the carrier tenant,** you must:

1. [Ensure that you have appropriate rights in the carrier tenant](#ensure-that-you-have-appropriate-rights-in-the-carrier-tenant).
2. [Add a base domain to the carrier tenant and verify it](#add-a-base-domain-to-the-carrier-tenant-and-verify-it).
3. [Activate the domain name in the carrier tenant](#activate-the-domain-name-in-the-carrier-tenant).

### Ensure that you have appropriate rights in the carrier tenant

You can only add new domains if you signed in to the Microsoft 365 admin center as a Global Administrator. 

To validate the role you have, sign in to the Microsoft 365 admin center (https://portal.office.com), go to **Users** > **Active Users**, and then verify that you have a Global Administrator role. 

For more information about admin roles and how to assign a role in Microsoft 365, see [About admin roles](https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d).

### Add a base domain to the carrier tenant and verify it

1. In the Microsoft 365 admin center, go to **Setup** > **Domains** > **Add domain**.

2. In the **Enter a domain you own** box, type the FQDN of the base domain. In this example, the base domain is sbc1.adatum.biz.

3. Select **Next**.

4. In this example, the tenant already has adatum.biz as a verified domain name. The wizard won't ask for additional verification because sbc1.adatum.biz is a subdomain for the already registered name. 

   However, if you add an FQDN that isn't verified, you'll need to [verify the subdomain name](#add-a-subdomain-to-the-customer-tenant-and-verify-it).

5. Select **Next**, and on the **Update DNS Settings** page, select **I'll add the DNS records myself** and select **Next**.

6. On the next page, clear all values (unless you want to use the domain name for Exchange, SharePoint, Teams, or Skype for Business), select **Next**, and then select **Finish**. Make sure your new domain is in the Setup complete status.

### Activate the domain name in the carrier tenant

After you register a domain name, you need to activate it by adding at least one Teams licensed user or resource account. Acceptable accounts are licensed with any one of the following SKUs:

- User Account with Office 365 E1/E3/E5 or Microsoft 365 E3/E5.
- User Account with Office 365 A1/A3/A5 or Microsoft 365 A1/A3/A5.
- User Account with Office 365 F3 or Microsoft 365 F1/F3.
- User Account with Office 365 G1/G3/G5 or Microsoft 365 G3/G5.
- User Account with Microsoft 365 Business Basic/Standard/Premium.
- User Account with a **Microsoft Teams Shared Devices** license.
- Resource Account with a **Microsoft Teams Phone Resource Account** license.

Additionally the account’s UPN (User Principal Name) or Skype for Business on-premises SIP address must use the same FQDN as the newly created domain.

For more information about adding users in Microsoft 365 organizations, see [Get help with Microsoft 365 domains](/microsoft-365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider).


## Register a subdomain name in a customer tenant - Example

You need to create a unique subdomain name for every customer. This example creates a subdomain woodgrovebank.sbc1.adatum.biz in a tenant with the default domain name woodgrovebank.us.

**In the customer tenant,** you must:

1. [Ensure that you have appropriate rights in the customer tenant](#ensure-that-you-have-appropriate-rights-in-the-customer-tenant).
2. [Add a subdomain to the customer tenant and verify it](#add-a-subdomain-to-the-customer-tenant-and-verify-it).
3. [Activate the subdomain name in the customer tenant](#activate-the-subdomain-name-in-the-customer-tenant).

### Ensure that you have appropriate rights in the customer tenant

You can only add new domains if you signed in to the Microsoft 365 admin center as a Global Administrator. 

To validate the role you have, sign in to the Microsoft 365 admin center (https://portal.office.com), go to **Users** > **Active Users**, and then verify that you have a Global Administrator role. 

For more information about admin roles and how to assign a role in Microsoft 365, see [About admin roles](https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d).

### Add a subdomain to the customer tenant and verify it

1. In the Microsoft 365 admin center, go to **Setup** > **Domains** > **Add domain**.

2. In the **Enter a domain you own** box, type the FQDN of the subdomain for this tenant. In this example, the subdomain is *woodgrovebank.sbc1.adatum.biz*.

3. Select **Next**.

4. The FQDN hasn't been registered in the tenant. In the next step, you'll need to verify the domain. Select **Add a TXT record instead**. 

5. Select **Next**, and note the **TXT value** generated to verify the domain name.

6. Create the TXT record with the value from the previous step in the carrier's DNS hosting provider.

    For more information, see [Create DNS records at any DNS hosting provider](https://support.office.com/article/create-dns-records-at-any-dns-hosting-provider-for-office-365-7b7b075d-79f9-4e37-8a9e-fb60c1d95166).

7. Go to the customer's Microsoft 365 admin center and select **Verify**. 

8. On the next page, select **I'll add the DNS records myself** and select **Next**.

9. On the **Choose your online services** page, clear all options, and select **Next**.

10. Select **Finish** on the **Update DNS settings** page.

11. Ensure that the status is **Setup complete**.

> [!NOTE]
> The base URL and the subdomain for the individual client have to be on the same tenant to enable you to add a _direct route_ trunk.

### Activate the subdomain name in the customer tenant

After you register a subdomain name, you need to activate it by adding at least one Teams licensed user or resource account. Acceptable accounts are licensed with any one of the following SKUs:

-	User Account with Office 365 E1/E3/E5/A3/A5 or Microsoft 365 E3/E5/A3/A5
-	User Account with Office 365 F1/F3 or Microsoft 365 F1/F3
-	User Account with Microsoft 365 Business Basic/Standard/Premium and G3/G5 plans
-	User Account with a **Microsoft Teams Shared Devices** license
-	Resource Account with a **Microsoft Teams Phone Resource Account** license

Additionally the account’s UPN (User Principal Name) or Skype for Business on-premises SIP address must use the same FQDN as the newly created subdomain.

For more information about adding users in Microsoft 365 organizations, see [Get help with Microsoft 365](/microsoft-365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider).


## Create a trunk and provision users

With the initial release of Direct Routing, Microsoft required a trunk to be added to each served tenant (customer tenant) using the New-CSOnlinePSTNGateway cmdlet.

However, this method isn't optimal for two reasons:
 
- **Overhead management**. Offloading or draining an SBC, for example, or changes to some parameters, like enabling or disabling media bypass or changing a port requires changing the parameters in multiple tenants (by running Set-CSOnlinePSTNGateway), but it is in fact the same SBC.

-  **Overhead processing**. Gathering and monitoring trunk health data - SIP options collected from multiple logical trunks that are, in reality, the same SBC and the same physical trunk, slows down processing of the routing data.
 
Based on this feedback, Microsoft is bringing in a new logic to provision the trunks for the customer tenants.

Two new entities were introduced:

- A carrier trunk registered in the carrier tenant by using the command New-CSOnlinePSTNGateway. For example: 
   
   ```PowerShell
   New-CSOnlinePSTNGateway -FQDN sbc1.adatum.biz -SIPSignalingport 5068 -ForwardPAI $true
    ```

- A derived trunk that doesn't require registration. It's simply a desired host name added in from of the carrier trunk. It derives all of its configuration parameters from the carrier trunk. The association with the carrier trunk is based on the FQDN name.

**Provisioning logic and example**

- Carriers need to set up and manage only a single trunk (the carrier trunk in the carrier domain) by using the New-CSOnlinePSTNGateway command. In the preceding example, the trunk is sbc1.adatum.biz.

- In the customer tenant, the derived trunk FQDN needs to be added to the voice routes. To add a derived trunk FQDN to a voice route, perform the following steps in Teams Admin Center:
    1.	Open the Teams Admin Center.
    2.	From the left siderail, expand **Voice**, and select **Direct Routing**.
    3.	From Direct Routing tabs, select **Voice routes**.
    4.	 Select **Add** (or select existing Voice route).
    5.	In the Voice route profile, under SBCs enrolled, select **Add SBCs**.
    6.	From the right side panel, under *Add SBC as derived trunk* enter SBC FQDN for your tenant, and select **Add**.
    7.	Select **Apply**.


    Or, use the PowerShell command CsOnlineVoiceRoute with the [-OnlinePstnGatewayList](https://learn.microsoft.com/powershell/module/teams/set-csonlinevoiceroute?view=teams-ps#-onlinepstngatewaylist) parameter:
   ```PowerShell
   Set-CsOnlineVoiceRoute -Identity OnlineVoiceRoute_1 -OnlinePstnGatewayList @{add="woodgrovebank.sbc1.adatum.biz"}
   ```

 - If the specified derived trunk is invalid, then the service will not allow the configuration to be applied.
 - There's no need to run New-CSOnlinePSTNGateway for a trunk.
 - The derived trunk, as the name suggests, inherits and derives all the configuration parameters from the carrier trunk.


Examples:
- sbc1.adatum.biz – the carrier trunk that needs to be created in the carrier tenant.

- woodgrovebank.sbc1.adatum.biz – the derived trunk in a customer tenant. You can add the name of the derived trunk in the customer tenant in the voice routes without creating it.

- Carrier needs to set up a DNS record resolving the derived trunk FQDN to the carrier SBC IP address.

- Any changes made on a carrier trunk (on carrier tenant) are automatically applied to derived trunks. For example, carriers can change an SIP port on the carrier trunk, and this change applies to all derived trunks. New logic to configure the trunks simplifies the management as you don't need to go to every tenant and change the parameter on every trunk.

- The options are sent only to the carrier trunk FQDN. The health status of the carrier trunk is applied to all derived trunks and is used for routing decisions. Find out more about [Direct Routing options](./direct-routing-monitor-and-troubleshoot.md).

- The carrier can drain the carrier trunk, and all derived trunks are drained as well. 
 
> [!NOTE]
> Number translation rules applied on the carrier trunk don't apply to derived trunks. This is a known issue. As an alternative solution, number translation rules must be created for each customer's tenant.
> Some functionality can be configured only by using PowerShell; for example, adding a new voice route. You must use the New-CsOnlineVoiceRoute cmdlet. In such cases, follow the guidance presented in other sections of this documentation related to cmdlets.

**Migration from the previous model to the carrier trunk**
 
For migration from the current implementation of the carrier hosted model to the new model, the carriers need to reconfigure the trunks for customer tenants. Remove the trunks from the customer tenants using Remove-CSOnlinePSTNGateway (leaving the trunk in the carrier tenant)-

We encourage migrating to the new solution as soon as possible because we'll be enhancing monitoring and provisioning using the carrier and derived trunk model.
 
For more information about configuring sending the FQDN name of subdomains in the Contact header, see the [SBC vendor instructions](#deploy-and-configure-the-sbc).

## Considerations for setting up multi-tenant failover 

To set up failover for a multi-tenant environment, follow these steps:

- For each tenant, add the FQDNs for two different SBCs. For example:

   customer1.sbc1.contoso.com <br>
   customer1.sbc2.contoso.com <br>

- In the Online Voice Routes, specify both SBCs. If one SBC fails, the routing policy routes calls to the second SBC.


## Related articles

[Plan Direct Routing](direct-routing-plan.md)<br>
[Configure Direct Routing](direct-routing-configure.md)
