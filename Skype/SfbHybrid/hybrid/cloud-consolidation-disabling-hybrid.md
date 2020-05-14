---
title: "Disable hybrid to complete migration to the cloud"
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.reviewer: bjwhalen
ms.topic: article
ms.prod: skype-for-business-itpro
search.appverid: MET150
ms.collection: 
- Hybrid 
- M365-voice
- M365-collaboration
- Teams_ITAdmin_Help
- Adm_Skype4B_Online
audience: ITPro
f1.keywords:
- NOCSH
appliesto:
- Skype for Business 
- Microsoft Teams
localization_priority: Normal
description: "This appendix includes detailed steps for disabling hybrid as part of cloud consolidation for Teams and Skype for Business."
---

# Disable hybrid to complete migration to the cloud

After you have moved all users from on-premises to the cloud, you can decommission the on-premises Skype for Business deployment. Aside from removing any hardware, a critical step is to logically separate that on-premises deployment from Microsoft 365 or Office 365 by disabling hybrid. Disabling hybrid consists of 3 steps:

1. Update DNS records to point to Microsoft 365 or Office 365.

2. Disable split domain in the Microsoft 365 or Office 365 organization.

3. Disable the ability in on-premises to communicate with Microsoft 365 or Office 365.

These steps should be done together as a unit. Details are provided below. In addition, guidelines are provided for managing phone numbers for migrated users once the on-premises deployment is disconnected.

> [!Important] 
>You should continue to let the msRTCSIP attributes in Active Directory sync via Azure AD Connect into Azure AD.  Do not clear any of these attributes unless directed to by Support.  Do not run Disable-CsUser in the on-premises environment. If you need to modify a user’s SIP address, do this in your on-premises Active Directory and let this change sync into Azure AD via Azure AD Connect as described below. Similarly, if you need to change a telephone number and the user’s LineURI is already defined on-premises, you should modify this in the on-premises Active Directory.
>Clearing the on-premises msRTCSIP attributes after you have migrated from on-premises could result in loss of service for users!

> [!Note] 
> In rare cases, changing DNS from pointing on premises to Microsoft 365 or Office 365 for your organization may cause federation with some other organizations to stop working until that other organization updates their federation configuration:<ul><li>
Any federated organizations that are using the older Direct Federation model (also known as Allowed Partner Server) will need to update their allowed domain entries for their organization to remove the proxy FQDN. This legacy federation model is not based on DNS SRV records, so such a configuration will become out of date once your organization moves to the cloud. </li><li>Any federated organization that does not have an enabled hosting provider for sipfed.online.lync.<span>com will need to update their configuration to enable that. This situation is only possible if the federated organization is purely on premises and has never federated with any hybrid or online tenant. In such a case, federation with these organizations will not work until they enable their hosting provider.</li></ul>If you suspect that any of your federated partners may be using Direct Federation or have federated with any online or hybrid organization, we suggest you send them a communication about this as you prepare to complete your migration to the cloud.

1.	*Update DNS to point to Microsoft 365 or  Office 365.*
The organization’s external DNS for the on-premises organization needs to be updated so that Skype for Business records point to Microsoft 365 or Office 365 instead of the on-premises deployment. Specifically:

    |Record type|Name|TTL|Value|
    |---|---|---|---|
    |SRV|_sipfederationtls._tcp|3600|100 1 5061 sipfed.online.lync.<span>com|
    |SRV|_sip._tls|3600|100 1 443 sipdir.online.lync.<span>com|
    |CNAME|	lyncdiscover|	3600|	webdir.online.lync.<span>com|
    |CNAME|	sip|	3600|	sipdir.online.lync.<span>com|
    |CNAME|	meet|	3600|	webdir.online.lync.<span>com|
    |CNAME|	dialin	|3600|	webdir.online.lync.<span>com|

    In addition, CNAME records for meet or dialin (if present) can be deleted. Finally, any DNS records for Skype for Business in your internal network should be removed.

    > [!Note] 
    > In rare cases, changing DNS from pointing on premises to Office 365 for your organization may cause federation with some other organizations to stop working until that other organization updates their federation configuration:
    >
    > - Any federated organizations that are using the older Direct Federation model (also known as Allowed Partner Server) will need to update their allowed domain entries for their organization to remove the proxy FQDN. This legacy federation model is not based on DNS SRV records, so such a configuration will become out of date once your organization moves to the cloud.
    > 
    > - Any federated organization that does not have an enabled hosting provider for sipfed.online.lync.<span>com will need to update their configuration to enable that. This situation is only possible if the federated organization is purely on-premises and has never federated with any hybrid or online tenant. In such a case, federation with these organizations will not work until they enable their hosting provider.
    >
    > If you suspect that any of your federated partners may be using Direct Federation or have not federated with any online or hybrid organization, we suggest you send them a communication about this as you prepare to complete your migration to the cloud.


2.	*Disable shared SIP address space in Microsoft 365 or Office 365 organization.*
The command below needs to be done from a Skype for Business Online PowerShell window.

    ```PowerShell
    Set-CsTenantFederationConfiguration -SharedSipAddressSpace $false
    ```
 
3.	*Disable ability in on-premises to communicate with Microsoft 365 or Office 365.*  
The command below needs to be done from an on-premises PowerShell window:

    ```PowerShell
    Get-CsHostingProvider|Set-CsHostingProvider -Enabled $false
    ```

### Manage sip addresses and phone numbers for users who were migrated from on-premises

Administrators can manage users who were previously moved from an on-premises Skype for Business Server to the cloud, even after the on-premises deployment is decommissioned. If you want to make changes to a user’s SIP address or to a user’s Line URI (and the SIP address or Line URI is already defined in the on-premises Active Directory), you must do this in the on-premises Active Directory and let the value(s) flow up to Azure AD. This does NOT require on-premises Skype for Business Server. Rather, you can modify these attributes directly in the on-premises Active Directory, using either the Active Directory Users and Computers MMC snap-in, or by using PowerShell. If you are using the MMC snap-in, open the properties page of the user, click Attribute Editor tab, and find the appropriate attributes to modify:

- To modify a user’s SIP address, modify the `msRTCSIP-PrimaryUserAddress`. In addition, if the `ProxyAddresses` attribute contains a SIP value, update that SIP value to match the new value of `msRTCSIP-PrimaryUserAddress`. If it does not contain a SIP value, you can leave it blank.

- To modify a user’s phone number, modify `msRTCSIP-Line` *if it already has a value*.

  ![Active Directory users and computers tool](../media/disable-hybrid-1.png)
  
If the user did not originally have a value for `LineURI` on-premises before the move, you can modify the LineURI using the -`onpremLineUri` parameter in the [Set-CsUser cmdlet](https://docs.microsoft.com/powershell/module/skype/set-csuser?view=skype-ps) in the Skype for Business Online PowerShell module.


## See also

[Cloud Consolidation for Teams and Skype for Business](cloud-consolidation.md)
