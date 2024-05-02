---
ms.date: 11/14/2018
title: "Configure Microsoft Entra Connect"
ms.reviewer: 
author: MicrosoftHeidi
ms.author: heidip
manager: jtremper
audience: ITPro
f1.keywords:
- NOCSH
ms.topic: article
ms.service: skype-for-business-server
ms.localizationpriority: medium
ms.collection: 
- Hybrid 
- M365-voice
- m365initiative-voice
- M365-collaboration
- Teams_ITAdmin_Help
- Adm_Skype4B_Online
search.appverid: MET150
description: "Instructions for configuring Microsoft Entra Connect in a hybrid environment."

---

# Configure Microsoft Entra Connect for Teams and Skype for Business

[!INCLUDE [sfbo-retirement](../../Hub/includes/sfbo-retirement.md)]
 
To use Teams, organizations with an on-premises deployment of Skype for Business Server or Lync Server 2013 must configure Microsoft Entra Connect to synchronize their on-premises directory with Microsoft 365. Organizations with Skype for Business Server on-premises must ensure that the proper msRTCSIP attributes are synchronized into Microsoft Entra ID. In this article, any reference to "Skype for Business Server" also applies to Lync Server 2013.

> [!NOTE]
>
> - To get full functionality, existing Teams users who also have Skype for Business on-premises will need to have their Skype for Business on-premises account moved to the cloud. For example, to get functionality such as the ability to interoperate with Skype for Business users, and to communicate with users in federated organizations. If the on-premises user will only be using Teams, you must still move the user to the cloud to provide full Teams functionality as a TeamsOnly user. For this migration to take place, you must configure Microsoft Entra Connect so that you can enable hybrid.
> - If you are not planning to move users from on-premises to the cloud any time soon, you must still configure Microsoft Entra Connect so that the Teams and the Skype for Business Server accounts co-exist.

## Background information

Microsoft Entra Connect keeps your on-premises Active Directory continuously synchronized with Microsoft 365. Your on-premises directory remains the authoritative source of identity, while changes from your on-premises environment are synchronized into Microsoft Entra ID. For more information, see [Microsoft Entra Connect Sync](/azure/active-directory/hybrid/how-to-connect-sync-whatis).  *Users in your organization will be represented in both your on-premises and online directories.*  All users who use Teams or Skype for Business on-premises must be synchronized from on-premises into Microsoft Entra ID to ensure coexistence of these accounts. In addition, you may facilitate communication between on-premises and online users via Skype for Business hybrid connectivity, which also requires configuration of Microsoft Entra Connect.

<a name='configuring-azure-ad-when-you-have-skype-for-business-server'></a>

## Configuring Microsoft Entra ID when you have Skype for Business Server

### General requirements

For an on-premises deployment of Skype for Business Server to coexist with Teams, certain Active Directory attributes from the on-premises deployment must be synchronized into Microsoft Entra ID using Microsoft Entra Connect. Setup for Microsoft Entra Connect automatically configures the required attributes to be synchronized by default when it detects the presence of Skype for Business Server in your on-premises environment. These attributes include general identity attributes, such as user principal name, and attributes prefaced with "msRTCSIP," which are specific to Skype For Business Server. The full set of attributes is listed at [Microsoft Entra Connect Sync: Attributes synchronized to Microsoft Entra ID](/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized#teams-and-skype-for-business-online).

If you choose to customize the synchronization settings in Microsoft Entra Connect, you must ensure that the following attributes are synchronized for user objects:
</br>

|Attribute|Description|
|---|---|
|msRTCSIP-PrimaryUserAddress| The user's sip address in the on-premises environment|
|msRTCSIP-DeploymentLocator| Indicates if the user is homed on-premises or in the cloud|
|msRTCSIP-UserEnabled| Whether the user is enabled for SIP functionality|
|||

</br>
</br>
In addition, if you're managing phone system attributes through your on-premises deployment, you must also synchronize the following attributes:

|Attribute|Description|
|:---|:---|
|msRTCSIP-Line| The user's phone number|
|msRTCSIP-OptionFlags| Indicates if the user is enabled for voice functionality|
|msRTCSIP-OwnerUrn| Used to identify hybrid application endpoints|
|||

</br>
Microsoft recommends that you synchronize all forests that contain user identities and any forests that contain Skype for Business Server. If users’ identities exist across multiple forests, Microsoft Entra Connect should do the merge. When this guidance is followed, Microsoft Entra Connect will automatically synchronize the correct attributes, provided you don't modify either the Connectors or Sync Rules in Microsoft Entra Connect.
  
If you don't synchronize from all forests that contain user identities and the Skype for Business Server deployment, you must ensure the relevant identity and Skype for Business attributes are correctly populated into Microsoft Entra ID for any user using Teams or Skype for Business (whether on-premises or online). This will likely require more on-premises directory synchronization. For more information, see [Microsoft Entra Connect Sync: Attributes synchronized to Microsoft Entra ID](/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized).

It's the customer’s responsibility to ensure proper configuration for populating the attributes into Microsoft Entra ID. Keep the following in mind:

- Using a nonstandard configuration for synchronizing to Microsoft Entra ID is risky. Nonstandard configurations could cause data corruption in your online directory.

- As products evolve, Microsoft will continue to verify standard synchronization configurations in which all relevant forests are synchronized. Customers with custom synchronization configurations are responsible for ensuring their configurations deliver the correct attributes and values into Microsoft Entra ID.

Whether you have one on-premises Active Directory forest or multiple forests, Microsoft Entra Connect can be used in various supported topologies, as described in [Topologies for Microsoft Entra Connect](/azure/active-directory/hybrid/plan-connect-topologies). From the perspective of Skype for Business Server, there are three variations:

1. A single forest, which contains authoritative user identities and hosts Skype for Business Server.

2. Multiple forests, only one of which hosts Skype for Business Server, and one or more other forests that contain authoritative user identities (the account forests).

3. Multiple deployments of Skype for Business Server in multiple forests. Provided certain requirements are met, organizations can consolidate these multiple deployments into a single Microsoft 365 organization.

### Single forest

If user accounts and Skype for Business are all hosted in a single forest, you must ensure that Microsoft Entra Connect is configured to synchronize users from this forest into Microsoft Entra ID.  By default, the appropriate attributes will automatically be synchronized into Microsoft Entra ID. Customers are advised against modifying the built-in synchronization rules and/or connectors that manage the configuration (which isn't possible from the installation wizard).  

### Multiple forests with one Skype for Business deployment

This scenario is often referred to as a resource forest topology. Users’ authoritative identities are hosted in one or more account forests, and Skype for Business is deployed in a separate resource forest (which itself may also host authoritative user identities). In general, Skype for Business users’ authoritative identities can be in the same forest as Skype for Business Server and/or in another forest, provided:

- Users with authoritative identities from the account forest(s) are represented in the resource forest (where Skype for Business Server is deployed) as disabled user objects. The msRTCSIP-OriginatorSID attribute in the resource forest must match the SID in the account forest. For more details, see [Configure a multi-forest environment for hybrid Skype for Business](configure-a-multi-forest-environment-for-hybrid.md).

- The resource forest hosting Skype for Business Server trusts the account forest(s).  

- All relevant user objects and attributes for both identity (from account forests) and Skype for Business (from resource forest) are synchronized into Microsoft Entra ID with the correct values through Microsoft Entra Connect.  

  To achieve proper object and attribute synchronization into Microsoft Entra ID in a [multi-forest on-premises scenario](configure-a-multi-forest-environment-for-hybrid.md), Microsoft strongly recommends using Microsoft Entra Connect to synchronize all forests that have enabled user accounts and the forest that contains Skype for Business. Assuming you synchronize from all forests, you must then configure Microsoft Entra Connect to merge these identities and synchronize to Microsoft Entra ID. Microsoft Entra Connect is designed to handle this scenario, and provides a built-in option in the installation wizard to set this up, including setting up anchors to join identities. Choose the following: **User identities exist across multiple directories**, and **Match using --> ObjectSID and msExchangeMasterAccountSID attributes**.

### Multiple Skype for Business Server deployments in multiple forests

In this scenario, there are multiple forests, each containing Skype for Business Server and a single Microsoft 365 organization. Each forest containing Skype for Business Server can be synchronized into Microsoft Entra ID for that organization using Microsoft Entra Connect. At most, only one forest can be configured for Skype for Business hybrid at a given time. Before enabling hybrid in a forest, all SIP domains from all other forests must be disabled using [disable-csonlineSipDomain](/powershell/module/skype/disable-csonlinesipdomain). For more information, see [Cloud consolidation for Teams and Skype for Business](cloud-consolidation.md).

## Related information

- [What is hybrid identity](/azure/active-directory/hybrid/whatis-hybrid-identity)

- [Microsoft Entra Connect Sync: Understand and customize synchronization](/azure/active-directory/hybrid/how-to-connect-sync-whatis)

- [Topologies for Microsoft Entra Connect](/azure/active-directory/hybrid/plan-connect-topologies)

- [Microsoft Entra Connect Sync: Attributes synchronized to Microsoft Entra ID](/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized)
