---
title: "Backup and restoration requirements in Lync Server 2013 tools and permissions"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 35ec2e33-f33e-4f84-9e64-6550fd78aa52

description: "In this articleBackupsRestorationRequired Permissions"
---

# Backup and restoration requirements in Lync Server 2013: tools and permissions
[]
 **In this article**
  
[Backups](#sectionSection0)
  
[Restoration](#sectionSection1)
  
[Required Permissions](#sectionSection2)
  
This topic identifies the tools that you can use to back up and restore Lync Server 2013, the permissions that you need, and whether you can run commands remotely or locally. Specifically, this topic focuses on tools that are provided with Lync Server for backup and restoration.
  
## Backups
<a name="sectionSection0"> </a>

To back up Lync Server, use the tools identified in the following table. All the commands that you need to back up Lync Server can be scripted and can be run remotely.
  
**Tools for Backing Up Lync Server**

|**To back up this:**|**Use this tool or cmdlet:**|
|:-----|:-----|
|Topology configuration data (Xds.mdf)  <br/> |Export-CsConfiguration  <br/> |
|Location information service (E9-1-1) data (Lis.mdf)  <br/> |Export-CsLisConfiguration  <br/> |
|Response Group configuration data (RgsConfig.mdf)  <br/> |Export-CsRgsConfiguration  <br/> |
|Persistent user data (Rtcxds.mdf database)  <br/> Conference IDs  <br/> |Export-CsUserData  <br/> |
| Archiving database (LcsLog.mdf)  <br/>  Monitoring call detail record database (LcsCDR.mdf)  <br/>  Monitoring QoE database (QoEMetrics.mdf)  <br/> |SQL Server database tool, such as SQL Server Management Studio  <br/> |
|Persistent Chat database (Mgc.mdf)  <br/> |SQL Server backup procedures or Export-CsPersistentChatData. Export-CsPersistentChatData exports Persistent Chat data as a file.  <br/> |
|All file stores: Lync Server file store, Archiving file store  <br/> > [!NOTE]> Files named **Meeting.Active** should not be backed up. These files are in use and locked while a meeting takes place.           |Standard file system management tool, such as Robocopy.  <br/> |
   
## Restoration
<a name="sectionSection1"> </a>

To restore Lync Server, use the tools in the following table. All the commands that you need to restore Lync Server can be scripted. Some can be run remotely, but others need to be run locally, as specified in the following table.
  
**Tools for Restoring Lync Server**

|**To do this:**|**Use this tool or cmdlet:**|
|:-----|:-----|
|Build a new or clean computer  <br/> | Windows operating system installation software  <br/>  SQL Server installation software  <br/>  Certificates Microsoft Management Console (MMC) snap-in, if restoring certificates with an exportable private key  <br/> |
|Restore file store data  <br/> |Standard file system management tool, such as Robocopy  <br/> |
| Recreate empty databases and set permissions for the following:  <br/>  Central Management store  <br/>  Back End Server  <br/>  Monitoring database  <br/>  Archiving database  <br/> |Install-CsDatabase  <br/> |
|Restore the Active Directory Domain Services pointer to the Central Management store  <br/> > [!NOTE]> If you lose the service connection point at any time, you can rerun this cmdlet.           |Set-CsConfigurationStoreLocation  <br/> |
|Import the topology, policies, and configuration settings to the Central Management store (Xds.mdf)  <br/> |Import-CsConfiguration  <br/> |
|Publish and enable the topology  <br/> |Topology Builder  <br/> -or-  <br/> Publish-CsTopology and Enable-CsTopology  <br/> |
|Enable the last published topology  <br/> |Enable-CsTopology  <br/> |
|Reinstall Lync Server components  <br/> |Lync Server Setup  <br/> > [!NOTE]> Located in the Lync Server installation folder or media at \setup\amd64\Setup.exe.           |
|Restore location information (E9-1-1) data (Lis.mdf)  <br/> |Import-CsLisConfiguration  <br/> |
|Restore persistent user data (Rtcxds.mdf)  <br/> |Import-CsUserData  <br/> |
|Restore Response Group configuration data (RgsConfig.mdf)  <br/> |Import-CsRgsConfiguration  <br/> > [!NOTE]> If the configuration is being restored in a newly deployed pool that has no Response Group data in the database, then you should use the -OverwriteOwner option. Use this option even if the data being restored is in a pool with the same fully qualified domain name (FQDN). Otherwise, the import will not succeed, due to the contact objects to the Response Groups already existing in Active Directory.           |
| Restore the following databases:  <br/>  Archiving database (LcsLog.mdf)  <br/>  Monitoring databases: call detail record database (LcsCDR.mdf) and QoE database (QoEMetrics.mdf)  <br/> |SQL Server database management tools  <br/> |
|Persistent Chat database (Mgs.mdf)  <br/> |SQL Server restore procedures or Import-CsPersistentChatData. You can use Import-CsPersistentChatData with a file created by Export-CsPersistentChatData, and the data will be imported into the Persistent Chat database.  <br/> |
   
## Required Permissions
<a name="sectionSection2"> </a>

Users must be a member of the **RTCUniversalServerAdmins** group to perform all the commands described in this topic. Most backup and restore commands do not support role-based access control (RBAC). Two exceptions are the Persistent Chat cmdlets Export-CsPersistentChatData and Import-CsPersistentChatData, which must be run by a user who is a member of the CsPersistentChatAdministrator group. To run Lync Server Deployment Wizard, a user must also be a member of the Local Adminstrators group. 
  

