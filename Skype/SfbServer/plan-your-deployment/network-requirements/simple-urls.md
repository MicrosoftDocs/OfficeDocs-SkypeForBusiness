---
title: "DNS requirements for simple URLs in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 3a3c9b22-892f-45a7-b05c-539d358a1a86
description: "Summary: Review the Simple URL considerations in this topic before implementing DNS records for Skype for Business Server."
---

# DNS requirements for simple URLs in Skype for Business Server

**Summary:** Review the Simple URL considerations in this topic before implementing DNS records for Skype for Business Server.

Simple URLs make joining meetings easier for your users, and make getting to Skype for Business Server administrative tools easier for administrators. Simple URLs use their own domain, which must not match any of the SIP domains you define. 

Skype for Business Server supports the following three simple URLs: Meet, Dial-In, and Admin. You are required to set up simple URLs for Meet and Dial-In, and the Admin simple URL is optional. The Domain Name System (DNS) records that you need to support simple URLs depend on how you have defined these simple URLs, and whether you want to support disaster recovery for Simple URLs. 

## Simple URL scope

You can configure your simple URLs to have global scope, or you can specify different simple URLs for each central site in your organization. If both a global simple URL and a site simple URL are specified, the site simple URL has precedence. 

In most cases, we recommend that you set simple URLs only at the global level, so that a user's Meet simple URL does not change if they move from one site to another. The exception would be organizations that need to use different telephone numbers for dial-in users at different sites. Note that if you set one simple URL (such as the Dial-in simple URL) at a site to be a site-level simple URL, you must also set the other simple URLs at that site to be site-level as well.

You can set global simple URLs in Topology Builder. To set a simple URL at the site level, use the Set-CsSimpleURLConfiguration cmdlet.

Defining a simple URL will also require setting an A and/or AAAA record in your DNS configuration.

## Simple URL naming and validation rules
<a name="BK_Valid"> </a>

Topology Builder and the Skype for Business Server Management Shell cmdlets enforce several validation rules for your simple URLs. You are required to set simple URLs for Meet and Dialin, but setting one for Admin is optional. Each SIP domain must have a separate Meet simple URL, but you need only one Dialin simple URL and one Admin simple URL for your whole organization.

Each simple URL in your organization must have a unique name, and cannot be a prefix of another simple URL (for example, you could not set SfB2015.contoso.com/Meet as your Meet simple URL and SfB2015.contoso.com/Meet/Dialin as your Dialin simple URL). Simple URL names cannot contain the FQDN of any of your pools, or any port information (for example, https://FQDN:88/meet is not allowed). All simple URLs must start with the https:// prefix. 

Simple URLs can contain only alphanumeric characters (that is, a-z, A-Z, 0-9, and the period (.). If you use other characters, the simple URLs might not work as expected.

## Changing Simple URLs after deployment
<a name="BK_Valid"> </a>

If you change a simple URL after initial deployment, you must be aware of how the change impacts your DNS records and certificates for simple URLs. If the base of a simple URL changes, then you must change the DNS records and certificates as well. For example, changing from https://SfB2015.contoso.com/Meet to https://meet.contoso.com changes the base URL from SfB2015.contoso.com to meet.contoso.com, so you would need to change the DNS records and certificates to refer to meet.contoso.com. If you changed the simple URL from https://SfB2015.contoso.com/Meet to https://SfB2015.contoso.com/Meetings, the base URL of SfB2015.contoso.com stays the same, so no DNS or certificate changes are needed.

Whenever you change a simple URL name, however, you must run **Enable-CsComputer** on each Director and Front End Server to register the change.

## Naming examples for Simple URLs
<a name="BK_Valid"> </a>

There are three recommended options for naming your simple URLs. Which option you choose has implications for how you set up your DNS A records and certificates which support simple URLs. In each option, you must configure one Meet simple URL for each SIP domain in your organization. 

You always need just one simple URL in your whole organization for Dial-in, and one for Admin, no matter how many SIP domains you have.

In Option 1, you create a new SIP domain name for each simple URL.

If you use this option, you need a separate DNS A record for each simple URL, and each Meet simple URL must be named in your certificates.

**Simple URL Naming Option 1**


| **Simple URL** <br/> | **Example** <br/>                                                                                                    |
|:---------------------|:---------------------------------------------------------------------------------------------------------------------|
| Meet  <br/>          | https://meet.contoso.com, https://meet.fabrikam.com, and so on (one for each SIP domain in your organization)  <br/> |
| Dial-in  <br/>       | <https://dialin.contoso.com>  <br/>                                                                                  |
| Admin  <br/>         | <https://admin.contoso.com>  <br/>                                                                                   |

With Option 2, simple URLs are based on the domain name SfB2015.contoso.com. Therefore, you need only one DNS A record which enables all three types of simple URLs. This DNS A record references SfB2015.contoso.com. Additionally, you still need separate DNS A records for other SIP domains in your organization. 

**Simple URL Naming Option 2**


| **Simple URL** <br/> | **Example** <br/>                                                                                                                    |
|:---------------------|:-------------------------------------------------------------------------------------------------------------------------------------|
| Meet  <br/>          | https://SfB2015.contoso.com/Meet, https://SfB2015.fabrikam.com/Meet, and so on (one for each SIP domain in your organization)  <br/> |
| Dial-in  <br/>       | <https://SfB2015.contoso.com/Dialin>  <br/>                                                                                          |
| Admin  <br/>         | <https://SfB2015.contoso.com/Admin>  <br/>                                                                                           |

Option 3 is most useful if you have many SIP domains, and you want them to have separate Meet simple URLs but want to minimize the DNS record and certificate requirements for these simple URLs. 

**Simple URL Naming Option 3**


| **Simple URL** <br/> | **Example** <br/>                                                                                                      |
|:---------------------|:-----------------------------------------------------------------------------------------------------------------------|
| Meet  <br/>          | <https://SfB2015.contoso.com/contosoSIPdomain/Meet>  <br/> <https://SfB2015.contoso.com/fabrikamSIPdomain/Meet>  <br/> |
| Dial-in  <br/>       | <https://SfB2015.contoso.com/Dialin>  <br/>                                                                            |
| Admin  <br/>         | <https://SfB2015.contoso.com/Admin>  <br/>                                                                             |

## Disaster Recovery option for simple URLs
<a name="BK_Valid"> </a>

If you have multiple sites that contain Front End pools and your DNS provider supports GeoDNS, you can set up your DNS records for Simple URLs to support disaster recovery, so that Simple URL functionality continues even if one entire Front End pool goes down. This disaster recovery feature supports the Meet and Dial-In simple URLs.

To configure this, create two GeoDNS addresses. Each address has two DNS A or CNAME records that resolve to two pools which are paired together for disaster recovery purposes. One GeoDNS address is used for internal access, and resolves to the internal web FQDN or load balancer IP address for the two pools. The other GeoDNS address is used for external access and resolves to the external web FQDN or load balancer IP address for the two pools. The following is an example for the Meet simple URL, using the FQDNs for the pools. 

```
Meet-int.geolb.contoso.com
     Pool1InternalWebFQDN.contoso.com
     Pool2InternalWebFQDN.contoso.com
```

```
Meet-ext.geolb.contoso.com
     Pool1ExternalWebFQDN.contoso.com
     Pool2ExternalWebFQDN.contoso.com
```

Then create CNAME records that resolve your Meet simple URL (such as meet.contoso.com) to the two GeoDNS addresses.

> [!NOTE]
> If your network uses hairpinning (routing all your Simple URL traffic through the external link, including traffic that comes from within your organization), then you can just configure the external GeoDNS address and resolve your Meet simple URL to only that external address.

When you use this method, you can configure each GeoDNS address to use either a round robin method to distribute requests to the two pools, or to connect primarily to one pool (such as the pool located geographically closer) and use the other pool only in case of connectivity failure. 

You can set up the same configuration for the Dial-In simple URL. To do so, create additional records like those in the previous example, substituting  `dialin` for `meet` in the DNS records. For the Admin simple URL, use one of the three options listed earlier in this section.

Once this configuration is set up, you must use a monitoring application to set up HTTP monitoring to watch for failures. For external access, monitor to make sure that HTTPS GET lyncdiscover.<sipdomain> requests to the external web FQDN or load balancer IP address for the two pools are successful. For example, the following requests must not contain any **ACCEPT** header and must return **200 OK**.

```
HTTPS GET Pool1ExternalWebFQDN.contoso.com/autodiscover/autodiscoverservice.svc/root
HTTPS GET Pool2ExternalWebFQDN.contoso.com/autodiscover/autodiscoverservice.svc/root
```

For internal access, you must monitor port 5061 on the internal web FQDN or load balancer IP address for the two pools. If any connectivity failures are detected, the VIP for these pools must close ports 80, 443 and 4443.


