---
title: "Changes made by forest preparation in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 10/20/2015
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 2e12613e-59f2-4810-a32d-24a9789a4a6e
description: "This section describes the global settings and objects, and the universal service and administration groups that are created by the forest preparation step."
---

# Changes made by forest preparation in Skype for Business Server

This section describes the global settings and objects, and the universal service and administration groups that are created by the forest preparation step.

## Active Directory Global Settings and Objects

If you store global settings in the Configuration container (as is the case for all new Skype for Business Server deployments), forest preparation uses the existing Services container and adds an **RTC Service** object under the Configuration\Services object. Under the RTC Service object, forest preparation adds a **Global Settings** object of type msRTCSIP-GlobalContainer. The global settings object holds all the settings that apply to the Skype for Business Server deployment. If you store global settings in the System container, forest preparation uses a Microsoft container under the root domain System container and an RTC Service object under the System\Microsoft object.

Forest preparation also adds a new **msRTCSIP-Domain** object for the root domain in which the procedure is run.

## Active Directory Universal Service and Administration Groups

Forest preparation creates universal groups based on the domain that you specify and adds access control entries (ACEs) for these groups. This step creates the universal groups in the User containers of the domain that you specify.

Universal groups allow administrators to access and manage global settings and services. Forest preparation adds the following types of universal groups:

- **Administrative groups** These groups define administrator roles for a Skype for Business Server network.

- **Infrastructure groups** These groups provide permission to access specific areas of the Skype for Business Server infrastructure. They function as components of administrative groups. You should not modify these groups or add users directly to them.

- **Service groups** These groups are service accounts that are required to access various Skype for Business Server services.

The following table describes the administrative groups.

**Administrative Groups Created During Forest Preparation**

|**Administrative group**|**Description**|
|:-----|:-----|
|RTCUniversalServerAdmins  <br/> |Allows members to manage server and pool settings, including all server roles, global settings, and users.  <br/> |
|RTCUniversalUserAdmins  <br/> |Allows members to manage user settings and move users from one server or pool to another.  <br/> |
|RTCUniversalReadOnlyAdmins  <br/> |Allows members to read server, pool, and user settings.  <br/> |

The following table describes the infrastructure groups.

**Infrastructure Groups Created During Forest Preparation**

|**Infrastructure group**|**Description**|
|:-----|:-----|
|RTCUniversalGlobalWriteGroup  <br/> |Grants write access to global setting objects for Skype for Business Server.  <br/> |
|RTCUniversalGlobalReadOnlyGroup  <br/> |Grants read-only access to global setting objects for Skype for Business Server.  <br/> |
|RTCUniversalUserReadOnlyGroup  <br/> |Grants read-only access to Skype for Business Server user settings.  <br/> |
|RTCUniversalServerReadOnlyGroup  <br/> |Grants read-only access to Skype for Business Server settings. This group does not have access to pool level settings, only to settings specific to an individual server.  <br/> |
|RTCUniversalSBATechnicians  <br/> |Grants read-only access to Skype for Business Server configuration and are placed in the Local Administrators group of the survivable branch appliances during installation.  <br/> |

The following table describes the service groups.

**Service Groups Created During Forest Preparation**

|**Service group**|**Description**|
|:-----|:-----|
|RTCHSUniversalServices  <br/> |Includes service accounts used to run Front End Server and Standard Edition servers. This group allows servers read/write access to Skype for Business Server global settings and Active Directory user objects.  <br/> |
|RTCComponentUniversalServices  <br/> |Includes service accounts used to run A/V Conferencing Servers, Web Services, Mediation Server, Archiving Server, and Monitoring Server.  <br/> |
|RTCProxyUniversalServices  <br/> |Includes service accounts used to run Skype for Business Server Edge Servers.  <br/> |
|RTCUniversalConfigReplicator  <br/> |Includes servers that can participate in Skype for Business Server Central Management store replication.  <br/> |
|RTCSBAUniversalServices  <br/> |Grants read-only access to Skype for Business Server settings, but allows for configuration for the installation of a survivable branch server and survivable branch appliance deployment.  <br/> |

Forest preparation then adds service and administration groups to the appropriate infrastructure groups, as follows:

- RTCUniversalServerAdmins is added to RTCUniversalGlobalReadOnlyGroup, RTCUniversalGlobalWriteGroup, RTCUniversalServerReadOnlyGroup, and RTCUniversalUserReadOnlyGroup.

- RTCUniversalUserAdmins is added as a member of RTCUniversalGlobalReadOnlyGroup, RTCUniversalServerReadOnlyGroup, and RTCUniversalUserReadOnlyGroup.

- RTCHSUniversalServices, RTCComponentUniversalServices and RTCUniversalReadOnlyAdmins are added as members of RTCUniversalGlobalReadOnlyGroup, RTCUniversalServerReadOnlyGroup, and RTCUniversalUserReadOnlyGroup.

Forest preparation also creates the following role-based access control (RBAC) groups:

- CSAdministrator

- CSArchivingAdministrator

- CSHelpDesk

- CSLocationAdministrator

- CSResponseGroupAdministrator

- CSServerAdministrator

- CSUserAdministrator

- CSViewOnlyAdministrator

- CSVoiceAdministrator

- CsPersistentChatAdministator

- CsResponseGroupManager

For details about RBAC roles and the tasks allowed for each, see [Role-Based Access Control](https://technet.microsoft.com/library/41204ba3-ce5b-41a8-a6c3-b444468fa328.aspx) in the Planning documentation.

Forest preparation creates both private and public ACEs. It creates private ACEs on the global settings container used by Skype for Business Server. This container is used only by Skype for Business Server and is located either in the Configuration container or the System container in the root domain, depending on where you store global settings. The public ACEs created by forest preparation are listed in the following table.

**Public ACEs created by Forest Preparation**


| **ACE**                                                                 | **RTCUniversalGlobalReadOnlyGroup** |
|:------------------------------------------------------------------------|:------------------------------------|
| Read root domain System Container (not inherited) **\\**\* <br/>        | X  <br/>                            |
| Read Configuration's DisplaySpecifiers container (not inherited)  <br/> | X  <br/>                            |

> [!NOTE]
> <strong>\\</strong>*ACEs that are not inherited do not grant access to child objects under these containers. ACEs that are inherited grant access to child objects under these containers.

On the Configuration container, under the Configuration naming context, forest preparation performs the following tasks:

- Adds an entry **{AB255F23-2DBD-4bb6-891D-38754AC280EF}** for the **RTC property** page under the adminContextMenu and adminPropertyPages attributes of the language display specifier for users, contacts, and InetOrgPersons (for example, CN=user-Display,CN=409,CN=DisplaySpecifiers).

- Adds an **RTCPropertySet** object of type **controlAccessRight** under **Extended-Rights** that applies to the User and Contact classes.

- Adds an **RTCUserSearchPropertySet** object of type **controlAccessRight** under **Extended-Rights** that applies to User, Contact, OU, and DomainDNS classes.

- Adds **msRTCSIP-PrimaryUserAddress** under the **extraColumns** attribute of each language organizational unit (OU) display specifier (for example, CN=organizationalUnit-Display,CN=409,CN=DisplaySpecifiers) and copies the values of the **extraColumns** attribute of the default display (for example, CN=default-Display, CN=409,CN=DisplaySpecifiers).

- Adds **msRTCSIP-PrimaryUserAddress**, **msRTCSIP-PrimaryHomeServer**, and **msRTCSIP-UserEnabled** filtering attributes under the **attributeDisplayNames** attribute of each language display specifier for Users, Contacts, and InetOrgPerson objects (for example, in English: CN=user-Display,CN=409,CN=DisplaySpecifiers).


