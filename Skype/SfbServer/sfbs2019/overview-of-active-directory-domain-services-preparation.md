---
title: "Overview of Active Directory Domain Services preparation in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: cdd2a652-6a0d-4728-9950-3fcaa7a80066

description: "To prepare Active Directory Domain Services for your Lync Server 2013 deployment, you must perform three steps in a specific sequence."
---

# Overview of Active Directory Domain Services preparation in Lync Server 2013
[]
To prepare Active Directory Domain Services for your Lync Server 2013 deployment, you must perform three steps in a specific sequence.
  
The following table describes the steps required to prepare AD DS for Lync Server.
  
**Active Directory Preparation Steps**

||**Step**|**Description**|**Where run**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |[Preparing the Active Directory schema in Lync Server 2013](preparing-the-active-directory-schema.md) <br/> |Extends the Active Directory schema by adding new classes and attributes that are used by Lync Server.  <br/> Run once for each forest in your deployment where Lync Server will be deployed.  <br/> |Against the schema master in the root domain of each forest where Lync Server will be deployed.  <br/> > [!NOTE]> You do not need to run this step in the root domain if you have permissions on the schema master, but you must be a member of the Schema Admins group in the root domain and a member of the Enterprise Admins group on the schema master. In a resource forest topology, run this step only in the resource forest, not in any user forests. In a central forest topology, run this step only in the central forest, not in any user forests.           |
|2.  <br/> |[Preparing the forest for Lync Server 2013](preparing-the-forest.md) <br/> |Creates global settings and universal groups that are used by Lync Server.  <br/> Run once for each forest in your deployment where Lync Server will be deployed.  <br/> |In the root domain of each forest where Lync Server will be deployed. To run this step, you must be a member of the Enterprise Admins group.  <br/> > [!NOTE]> In a resource forest topology, run this step only in the resource forest, not in any user forests. In a central forest topology, run this step only in the central forest, not in any user forests.           |
|3.  <br/> |[Preparing domains for Lync Server 2013](preparing-domains.md) <br/> |Adds permissions on objects to be used by members of universal groups.  <br/> Run once per user domain or server domain.  <br/> > [!NOTE]> If you are migrating from Lync Server 2010 to Lync Server 2013, the Deployment Wizard may indicate that domain preparation is already complete. You do not need to run domain preparation again. Permissions were not changed from Lync Server 2010 to Lync Server 2013.           |On a member server in each domain where Lync Server will be deployed. To run this step, you must be a member of the Domain Admins group.  <br/> |
   
Lync Server 2013, like Lync Server 2010, stores much of the configuration information in the Central Management store instead of in AD DS as was the case in Office Communications Server 2007 R2. However, the following information is stored in AD DS:
  
- **Schema extensions**:
    
  - User object extensions
    
  - Extensions for Office Communications Server 2007 R2 classes to maintain backward compatibility
    
- **Data** (stored in Lync Server extended schema and in existing schema classes): 
    
  - User SIP Uniform Resource Identifier (URI) and other user settings
    
  - Contact objects for applications such as Response Group and Conferencing Attendant
    
  - A pointer to the Central Management store
    
  - Kerberos Authentication Account (an optional computer object)
    
In Lync Server 2013, you delegate setup and administration by granting setup permissions to the RTCUniversalServerAdmins universal group so that members of that group can install and activate Lync Server 2013 on a local server (after the server has been added to the topology, published, and enabled). The delegated users must be local administrators on the computer where they are installing and activating Lync Server 2013, but they do not need to be members of the Domain Admins group. You can also grant permissions for objects in specified organizational units (OUs) so that members of the universal groups created during forest preparation can access those objects without being members of the Domain Admins group.
  
For new deployments of Lync Server 2013, global settings must be stored in the Configuration container. If your organization is upgrading from an earlier version and you still have global settings in the System container, the System container is still supported. 
  
## See also

#### 

[Preparing the Active Directory schema in Lync Server 2013](preparing-the-active-directory-schema.md)
  
[Active Directory schema extensions, classes, and attributes used by Lync Server 2013](active-directory-schema-extensions-classes-and-attributes-used-by-lync-server-20.md)
#### 

[Preparing the forest for Lync Server 2013](preparing-the-forest.md)
  
[Preparing domains for Lync Server 2013](preparing-domains.md)

