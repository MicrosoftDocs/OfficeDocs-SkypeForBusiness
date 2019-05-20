---
title: "Changes made by Grant-CsOUPermission in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 10/20/2015
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: d744d352-1ad9-4447-8e2b-28e768d2ed1b
description: "To delegate Skype for Business Server administration, you can add permissions to specified organizational units (OUs) so that members of the RTC universal groups created by forest preparation can access the OUs without being members of the Domain Admins group."
---

# Changes made by Grant-CsOUPermission in Skype for Business Server
 
To delegate Skype for Business Server administration, you can add permissions to specified organizational units (OUs) so that members of the RTC universal groups created by forest preparation can access the OUs without being members of the Domain Admins group. 
  
The **Grant-CsOuPermission** cmdlet grants permissions to objects in the specified OU as specified in the following tables.
  
## Granting Permission for User Objects

When you run the **Grant-CsOuPermission** cmdlet for User objects on an OU, groups are granted permissions as shown in the following table.
  
**Permissions Granted for User Objects**

|**Group**|**Permission**|**Applies to**|
|:-----|:-----|:-----|
|RTCHSUniversalServices  <br/> |Replicating directory changes  <br/> |This object only  <br/> |
|RTCUniversalServerReadOnlyGroup  <br/> |List contents  <br/> Read all properties  <br/> Read permissions  <br/> |This object only  <br/> |
|RTCUniversalUserReadOnlyGroup  <br/> |List contents  <br/> Read all properties  <br/> Read permissions  <br/> |This object only  <br/> |
|RTCUniversalUserReadOnlyGroup  <br/> |Read RTCUserSearchPropertySet  <br/> Read RTCUserProvisioningPropertySet  <br/> Read RTCPropertySet  <br/> Read Public-Information  <br/> Read General-Information  <br/> Read User-Account-Restrictions  <br/> |Descendant User objects  <br/> |
|RTCUniversalUserAdmins  <br/> |Write RTCUserSearchPropertySet  <br/> Write msExchUCVoiceMailSettings  <br/> Write RTCUserProvisioningPropertySet  <br/> Write RTCPropertySet  <br/> Write proxyAddresses  <br/> |Descendant User objects  <br/> |
   
## Granting Permission for Computer Objects

When you run the **Grant-CsOuPermission** cmdlet for Computer objects on an OU, groups are granted permissions as shown in the following table.
  
**Permissions Granted for Computer Objects**

|**Group**|**Permission**|**Applies to**|
|:-----|:-----|:-----|
|RTCHSUniversalServices  <br/> |Replicating directory changes  <br/> |This object only  <br/> |
|RTCUniversalServerReadOnlyGroup  <br/> |List contents  <br/> Read all properties  <br/> Read permissions  <br/> |This object only  <br/> |
|RTCUniversalUserReadOnlyGroup  <br/> |List contents  <br/> Read all properties  <br/> Read permissions  <br/> |This object only  <br/> |
|RTCUniversalUserReadOnlyGroup  <br/> |Read Public-Information  <br/> Read Validated-DNS-Host-Name  <br/> |Descendant Computer objects  <br/> |
|RTCUniversalUserAdmins  <br/> |Read Public-Information  <br/> Read Validated-DNS-Host-Name  <br/> |Descendant Computer objects  <br/> |
   
## Granting Permission for Contact or AppContact Objects

When you run the **Grant-CsOuPermission** cmdlet for Contact objects or AppContact objects on an OU, groups are granted permissions as shown in the following table.
  
**Permissions Granted for Contact or AppContact Objects**

|**Group**|**Permission**|**Applies to**|
|:-----|:-----|:-----|
|RTCHSUniversalServices  <br/> |Replicating directory changes  <br/> |This object only  <br/> |
|RTCUniversalServerReadOnlyGroup  <br/> |List contents  <br/> Read all properties  <br/> Read permissions  <br/> |This object only  <br/> |
|RTCUniversalUserReadOnlyGroup  <br/> |List contents  <br/> Read all properties  <br/> Read permissions  <br/> |This object only  <br/> |
|RTCUniversalUserReadOnlyGroup  <br/> |Read RTCUserSearchPropertySet  <br/> Read RTCUserProvisioningPropertySet  <br/> Read RTCPropertySet  <br/> Read Public-Information  <br/> Read General-Information  <br/> Read Personal-Information  <br/> Read User-Account-Restrictions  <br/> |Descendant Contact objects  <br/> |
|RTCUniversalUserAdmins  <br/> |Write RTCUserSearchPropertySet  <br/> Write otherIpPhone  <br/> Write displayName  <br/> Write description  <br/> Write telephoneNumber  <br/> Write msExchUCVoiceMailSettings  <br/> Write RTCUserProvisioningPropertySet  <br/> Write RTCPropertySet  <br/> Write proxyAddresses  <br/> |Descendant Contact objects  <br/> |
   
## Granting Permission for Device Objects

When you run the **Grant-CsOuPermission** cmdlet for Device objects on an OU, groups are granted permissions as shown in the following table.
  
**Permissions Granted for Device Objects**

|**Group**|**Permission**|**Applies to**|
|:-----|:-----|:-----|
|RTCHSUniversalServices  <br/> |Replicating directory changes  <br/> |This object only  <br/> |
|RTCUniversalServerReadOnlyGroup  <br/> |List contents  <br/> Read all properties  <br/> Read permissions  <br/> |This object only  <br/> |
|RTCUniversalUserReadOnlyGroup  <br/> |List contents  <br/> Read all properties  <br/> Read permissions  <br/> |This object only  <br/> |
|RTCUniversalUserReadOnlyGroup  <br/> |Read RTCUserSearchPropertySet  <br/> Read RTCUserProvisioningPropertySet  <br/> Read RTCPropertySet  <br/> Read Public-Information  <br/> Read Personal-Information  <br/> Read General-Information  <br/> Read User-Account-Restrictions  <br/> |Descendant Contact objects  <br/> |
|RTCUniversalUserAdmins  <br/> |Create child  <br/> Delete child  <br/> Delete tree  <br/> |Contact  <br/> |
|RTCUniversalUserAdmins  <br/> |Write displayName  <br/> Write description  <br/> Write telephoneNumber  <br/> |Descendant User objects  <br/> |
|RTCUniversalUserAdmins  <br/> |Write RTCUserSearchPropertySet  <br/> Write otherIpPhone  <br/> Write displayName  <br/> Write description  <br/> Write telephoneNumber  <br/> Write msExchUCVoiceMailSettings  <br/> Write RTCUserProvisioningPropertySet  <br/> Write RTCPropertySet  <br/> Write proxyAddresses  <br/> |Descendant Contact objects  <br/> |
   
## Granting Permission for InetOrgPerson Objects

When you run the **Grant-CsOuPermission** cmdlet for InetOrgPerson objects on an OU, groups are granted permissions as shown in the following table.
  
**Permissions Granted for InetOrgPerson Objects**

|**Group**|**Permission**|**Applies to**|
|:-----|:-----|:-----|
|RTCHSUniversalServices  <br/> |Replicating directory changes  <br/> |This object only  <br/> |
|RTCUniversalServerReadOnlyGroup  <br/> |List contents  <br/> Read all properties  <br/> Read permissions  <br/> |This object only  <br/> |
|RTCUniversalUserReadOnlyGroup  <br/> |List contents  <br/> Read all properties  <br/> Read permissions  <br/> |This object only  <br/> |
|RTCUniversalUserReadOnlyGroup  <br/> |Read RTCUserSearchPropertySet  <br/> Read RTCUserProvisioningPropertySet  <br/> Read RTCPropertySet  <br/> Read Personal-Information  <br/> Read Public-Information  <br/> Read General-Information  <br/> Read User-Account-Restrictions  <br/> |Descendant inetOrgPerson objects  <br/> |
|RTCUniversalUserAdmins  <br/> |Write RTCUserSearchPropertySet  <br/> Write RTCUserProvisioningPropertySet  <br/> Write RTCPropertySet  <br/> Write proxyAddresses  <br/> |Descendant inetOrgPerson objects  <br/> |
   

