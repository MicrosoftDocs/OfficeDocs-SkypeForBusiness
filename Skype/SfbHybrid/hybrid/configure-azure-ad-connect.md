---
title: "Configure Azure AD Connect"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- Hybrid 
- M365-voice
- M365-collaboration
- Teams_ITAdmin_Help
- Adm_Skype4B_Online
description: "Instructions for configuring Azure AD Connect in a hybrid environment."

---

# Configure Azure AD Connect for Teams and Skype for Business
 
Organizations that have Skype for Business Server (or Lync Server) on-premises and who are planning to use either Teams or Skype for Business Online must configure Azure AD Connect to synchronize their on-premises directory with Office 365, as described in this document.  This includes organizations that move directly from Skype for Business on-premises to Teams. In particular, organizations with Skype for Business on-premises must ensure that the proper msRTCSIP attributes are synchronized into Azure AD. 

> [!NOTE]
> Existing Teams users who also have Skype for Business on-premises will need to have their Skype for Business on-premises account moved to the cloud in order to get full functionality-- such as the ability to interoperate with Skype for Business users, and to communicate with users in federated organizations. Even if the user will only be using Teams, this online Skype for Business account is required by the infrastructure to deliver the additional functionality.  For this migration to take place, you must ensure that Azure AD Connect is properly configured so that you can enable hybrid.
 

## Background information

Azure Active Directory Connect keeps your on-premises Active Directory continuously synchronized with Office 365.  Your on-premises directory remains the authoritative source of identity, and changes from your on-premises environment are synchronized into Azure AD. For more information, see [Azure AD Connect Sync](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/how-to-connect-sync-whatis).  Even if you are not moving all users from on-premises to the cloud, all users that use Teams, Skype for Business on-premises, or Skype for Business Online must be synchronized from on-premises into Azure AD to ensure communication between on-premises and online users. *Users in your organization will be represented in both your on-premises and online directories.*


## Configuring Azure AD when you have Skype for Business Server 

Whether you have one on-premises Active Directory forest or multiple forests, Azure AD Connect can be used in a variety of supported topologies, as described in [Topologies for Azure AD Connect](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-topologies).  From the perspective of Skype for Business Server, there are three main variations: 

1. A single forest, which contains authoritative user identities and hosts Skype for Business Server. 

2. Multiple forests, only one of which hosts Skype for Business Server, as well as one or more other forests that contain authoritative user identities (the account forests). 

3. Multiple deployments of Skype for Business Server in multiple forests. Provided certain requirements are met, organizations can consolidate these multiple deployments into a single Office 365 tenant.

### Single forest 

If user accounts and Skype for Business are all hosted in a single forest, you must ensure that Azure AD Connect is configured to synchronize users from this forest into Azure AD.  Although the Azure AD Connect installation wizard has a variety of options, the appropriate attributes will automatically be synchronized into Azure Active Directory. Customers are advised against modifying the built-in synchronization rules and/or connectors which manage the configuration (which is not possible from the installation wizard).  

### Multiple forests with one Skype for Business deployment 

This scenario is often referred to as a resource forest topology. Users’ authoritative identities are hosted in one or more account forests, and Skype for Business is deployed in a separate resource forest (which itself may also host authoritative user identities). In general, Skype for Business users’ authoritative identities can be in the same forest as Skype for Business Server and/or in another forest, provided: 

- Users with authoritative identities from the account forest(s) are represented in the resource forest (where Skype for Business Server is deployed) as disabled user objects, and the msRTCSIP-OriginatorSID attribute in the resource forest matches the SID in the account forest. For more details see [Configure a multi-forest environment for hybrid Skype for Business](configure-a-multi-forest-environment-for-hybrid.md).

- The resource forest hosting Skype for Business Server trusts the account forest(s).  

- All relevant user objects and attributes for both identity (from account forests) and Skype for Business (from resource forest) are synchronized into Azure AD with the correct values via Azure AD Connect.  

 To achieve proper object and attribute synchronization into Azure AD in a [multi-forest on-premises scenario](configure-a-multi-forest-environment-for-hybrid.md), Microsoft strongly recommends using Azure AD Connect to synchronize from all forests that have enabled user accounts and the forest that contains Skype for Business.  Assuming you synchronize from all forests, you must then configure Azure AD Connect to merge these identities and synchronize to Azure AD. Azure AD Connect is designed to handle this scenario, and provides a built-in option in the installation wizard to set this up, including setting up anchors to join identities.  Choose the following:  User identities exist across multiple directories. Match using --> ObjectSID and msExchangeMasterAccountSID attributes.


### Multiple Skype for Business Server deployments in multiple forests 

In this scenario, there are multiple forests, each containing Skype for Business Server, and a single Office 365 tenant.  Each forest containing Skype for Business Server can be synchronized into Azure AD for that tenant using AAD Connect. At most, only one forest can be configured for Skype for Business hybrid at a given time. Before enabling hybrid in a forest, all SIP domains from all other forests must be disabled using [disable-csonlineSipDomain](https://docs.microsoft.com/en-us/powershell/module/skype/disable-csonlinesipdomain). For more details on how to consolidate such an environment into Office 365, see [Cloud consolidation for Teams and Skype for Business](cloud-consolidation.md).

## General requirements 

Both the Teams and Skype for Business Online services require that the correct Active Directory attributes exist and are  populated in Azure AD.  Microsoft’s general recommendation is to synchronize all forests that contain user identities as well as any forests that contain Skype for Business Server.

 If users’ identities exist across multiple forests, Azure AD Connect should do the merge. When this guidance is followed,Azure AD Connect will automatically synchronize the correct attributes, provided you do not modify either the Connectors or Sync Rules in Azure AD Connect. 
  
If you do not synchronize from all forests that contain user identities and the Skype for Business Server deployment, you must still ensure the relevant identity and Skype for Business attributes are correctly populated into Azure AD for any user using Teams or Skype for Business (whether on-premises or online)--which will likely require additional on-premises directory synchronization. For more information, see [Azure AD Connect sync: Attributes synchronized to Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized).

In such scenarios, it is the customer’s responsibility to ensure proper configuration for populating the attributes into Azure AD. Keep the following in mind: 

- Using a non-standard configuration for synchronizing to Azure AD is risky because it could lead to misconfiguration, which could cause data corruption in your online directory.

- As products evolve, Microsoft will continue to verify standard synchronization configurations in which all relevant forests are synchronized. Customers with custom synchronization configurations are responsible for ensuring their configurations deliver the correct attributes and values into Azure AD. 

## Related information

- [What is hybrid identity](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/whatis-hybrid-identity?toc=%2Fen-us%2Fazure%2Factive-directory%2Fhybrid%2FTOC.json&bc=%2Fen-us%2Fazure%2Fbread%2Ftoc.json)

- [Azure AD Connect sync: Understand and customize synchronization](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/how-to-connect-sync-whatis)

- [Topologies for Azure AD Connect](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-topologies)

- [Azure AD Connect sync: Attributes synchronized to Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized)
