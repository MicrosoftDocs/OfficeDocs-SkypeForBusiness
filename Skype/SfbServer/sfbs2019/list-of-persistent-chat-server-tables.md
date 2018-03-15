---
title: "List of Persistent Chat Server tables in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 26c9e271-3516-4d90-b930-70fec4e359ea
description: "In this articleActive Directory SyncPrincipals, Affiliations, Nodes, Scopes, and RolesInvites, Chats, and Other Client SupportServer Support"
---

# List of Persistent Chat Server tables in Lync Server 2013
[]
 **In this article**
  
[Active Directory Sync](#sectionSection0)
  
[Principals, Affiliations, Nodes, Scopes, and Roles](#sectionSection1)
  
[Invites, Chats, and Other Client Support](#sectionSection2)
  
[Server Support](#sectionSection3)
  
The Persistent Chat database schema consists of the following tables.
  
## Active Directory Sync
<a name="sectionSection0"> </a>

|**Table**|**Description**|
|:-----|:-----|
|[tblADCookie in Lync Server 2013](tbladcookie.md) <br/> |Contains the current Lightweight Directory Access Protocol (LDAP) Sync cookies. Each row corresponds to an Active Directory Domain Services domain that Persistent Chat Server is actively monitoring for changes. (Only the Active Directory domains that are relevant for Persistent Chat Server are represented in this table.)  <br/> |
|[tblPrincipalMemberDifference in Lync Server 2013](tblprincipalmemberdifference.md) <br/> |Contains group membership changes (both added and removed members) that have not yet been processed by the later Active Directory Sync steps and is one of the temporary tables (along with tblADUpdates table) that is used in the first step of Active Directory Sync.  <br/> Membership changes are stored, processed, or both, only for groups that are listed in the tblPrincipal table or that already have members listed there.  <br/> |
|[tblADUpdates in Lync Server 2013](tbladupdates.md) <br/> |Contains changes to Active Directory Domain Services that have not yet been processed by the later Active Directory Sync steps and is one of the temporary tables (along with the tblPrincipalMemberDifference table) that is used in the first step of Active Directory Sync.  <br/> Changes to Active Directory are stored, processed, or both only for principals that are already listed in the tblPrincipal table.  <br/> |
|[tblPrincipalMembers in Lync Server 2013](tblprincipalmembers.md) <br/> |Contains principal memberships.  <br/> |
|[tblPrincipalMeta in Lync Server 2013](tblprincipalmeta.md) <br/> |Contains the principals that have to be refreshed from Active Directory.  <br/> |
|[tblSkippedAffiliations in Lync Server 2013](tblskippedaffiliations.md) <br/> |Contains affiliations that could not be refreshed for some reason, usually due to Active Directory access errors.  <br/> This table is for informational purposes only. Its content is not used.  <br/> The principals with affiliations that could not be refreshed properly are kept in the tblPrincipalMeta table and are given another chance to be refreshed.  <br/> |
   
## Principals, Affiliations, Nodes, Scopes, and Roles
<a name="sectionSection1"> </a>

|**Table**|**Description**|
|:-----|:-----|
|[tblPrincipalType in Lync Server 2013](tblprincipaltype.md) <br/> |Contains principal types to categorize what is in the tblPrincipal table. This table is static. It is set up during database creation and does not change.  <br/> |
|[tblPrincipal in Lync Server 2013](tblprincipal.md) <br/> |Contains all principals (users, folders, groups, and so on). Persistent Chat Server handles this as a flat heterogeneous list. Various columns are based on the type of each principal.  <br/> Most of these principals are cached copies of objects stored in Active Directory. Creating the cached copy in the Principal table of these Active Directory objects is referred as provisioning.  <br/> Some principals are created more aggressively than others, and some Active Directory objects are ignored altogether.  <br/> |
|[tblPrincipalAffiliations in Lync Server 2013](tblprincipalaffiliations.md) <br/> |Contains principal affiliations that describe memberships in Active Directory security groups, Active Directory containers, and so on.  <br/> |
|[tblNode in Lync Server 2013](tblnode.md) <br/> |Contains the category node, as managed in Lync Server Control Panel.  <br/> |
|[tblRoleType in Lync Server 2013](tblroletype.md) <br/> |Contains role types and their associated permission sets. This lookup table is static.  <br/> |
|[tblScopePrincipal in Lync Server 2013](tblscopeprincipal.md) <br/> |Contains scopes assigned to nodes.  <br/> |
|[tblPrincipalRole in Lync Server 2013](tblprincipalrole.md) <br/> |Contains roles assigned to nodes.  <br/> |
|[tblSiopWhiteList in Lync Server 2013](tblsiopwhitelist.md) <br/> |Contains the registered Add-ins that can be associated with nodes.  <br/> |
|[tblEnumAttribute in Lync Server 2013](tblenumattribute.md) <br/> |Contains only the hardcoded "Visibility" and "Behavior" attributes that are used in the tblNode table.  <br/> |
|[tblEnumValue in Lync Server 2013](tblenumvalue.md) <br/> |Contains the values of the hardcoded "Visibility" and "Behavior" attributes that are used in the tblNode table.  <br/> |
   
## Invites, Chats, and Other Client Support
<a name="sectionSection2"> </a>

|**Table**|**Description**|
|:-----|:-----|
|[tblPrincipalInvites in Lync Server 2013](tblprincipalinvites.md) <br/> |Contains invites for all provisioned users in the system for all nodes with Auto Invite enabled.  <br/> |
|[tblChat in Lync Server 2013](tblchat.md) <br/> |Contains all chat messages.  <br/> |
|[tblLastInviteId in Lync Server 2013](tbllastinviteid.md) <br/> |Contains the last invite ID that was generated (and used in the tblPrincipalInvites table) for each user.  <br/> |
|[tblLastChatId in Lync Server 2013](tbllastchatid.md) <br/> |Contains the last chat ID that was generated (and used in the tblChat table) for each user.  <br/> |
|[tblPreference in Lync Server 2013](tblpreference.md) <br/> |Contains user client preferences (used by legacy clients only).  <br/> |
|[tblFileToken in Lync Server 2013](tblfiletoken.md) <br/> |Contains temporary tokens for file transfer purposes. Each time a file is uploaded or downloaded, the Persistent Chat service generates a token that the client uses to access the Web service file store.  <br/> |
   
## Server Support
<a name="sectionSection3"> </a>

|**Table**|**Description**|
|:-----|:-----|
|[tblServerIdentity in Lync Server 2013](tblserveridentity.md) <br/> |Contains the active servers in the Persistent Chat Server pool.  <br/> |
|[tblAdminLock in Lync Server 2013](tbladminlock.md) <br/> |Contains the administrator lock to run some administrator commands. The system revision entry in the tblSystemRevision table is incremented after each release of the lock.  <br/> |
|[tblSystemRevision in Lync Server 2013](tblsystemrevision.md) <br/> |Contains the revision number entry used (along with the tblAdminLock table) for achieving consistency across multiple servers.  <br/> |
|[tblActivePeers in Lync Server 2013](tblactivepeers.md) <br/> |Contains current peer-to-peer connections between Persistent Chat services.  <br/> |
|[tblConfig in Lync Server 2013](tblconfig.md) <br/> |Contains the Persistent Chat Server unsupported configuration.  <br/> |
   

