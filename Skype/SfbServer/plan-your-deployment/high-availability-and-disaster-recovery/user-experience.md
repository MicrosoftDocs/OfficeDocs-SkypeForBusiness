---
title: "User experience during pool failure in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: b224b0d0-87e3-4cac-ae87-f45f54fabb49
description: "Learn about what users experience when a Front End pool fails over or fails back during disaster recovery in Skype for Business Server."
---

# User experience during pool failure in Skype for Business Server
 
Learn about what users experience when a Front End pool fails over or fails back during disaster recovery in Skype for Business Server.
  
If a pool is failed over, all users in the affected pool are forced to sign out and then sign into the backup pool. For a brief period users who sign into the backup pool may be in resiliency mode. In Resiliency mode, users are unable to perform tasks that would cause a persistent change on Skype for Business Server, such as adding a contact. After the failover is complete, all users can get all services from the backup pool.
  
Any calls, meetings, or conversations a user has when the pool fails are disrupted, and the user must re-establish those sessions after failover to continue.
  
Users are not rehomed during failover or failback. Users who are homed on a pool that fails will be temporarily serviced by the backup pool. When the home pool is restored, the administrator can fail back these users to be serviced by their original pool, where they are still homed.
  
Note that the Location Information Server database is not replicated to the backup pool. For best practice, the administrator should regularly back up the LIS database and use the latest backup copy to restore the LIS database in the backup pool after the failover.
  
## User experience during failover

When a user is in a pool that fails, the user is logged out. Any peer-to-peer session the user was participating in is ended, as are conferences organized by that user. The user cannot log back in until either the registrar resiliency timer expires or the administrator initiates failover procedures, whichever comes first. When the user logs back in, they will log in to the backup pool. If they log in before the failover has completed, they will be in Resiliency mode until failover is complete. Only then can a user establish new sessions or re-establish previous sessions.
  
## User experience during failback

Pool failback can happen while an affected user is logged on to the backup pool, and the user remains logged on and working during the failback. Note that the failback process takes several minutes to complete. For reference, it is expected to take up to 60 minutes for a pool of 20,000 users.
  
The following tables show more details about how a user is affected during and after failback, and also how users in other pools see and interact with a user in a pool who is being failed back. 
  
The term affected user refers to any user who was failed over from the home pool and is being serviced by the backup pool. A user originally homed on the backup pool is not an affected user.
  
**User Experience for an Affected User in a Pool in Failback**

|**User state or task**|**During failback**|**After failback completion**|
|:-----|:-----|:-----|
|User state of user already logged in  <br/> |User stays signed in and connected to backup pool. At some point user will be signed out and sign back in to the original home pool, in Resiliency mode.  <br/> |User remains signed in and goes into regular mode.  <br/> |
|New user logging in  <br/> |User can sign in to the home pool in Resiliency mode.  <br/> |User can sign in to the original home pool in regular mode.  <br/> |
|Ongoing conferences organized by affected user  <br/> |All modalities of conference are terminated. Rejoin button will appear, but no users can rejoin while the affected user is in Resiliency mode.  <br/> |All modalities now work. Every participant needs to click to rejoin the conference.  <br/> |
|Ongoing conferences organized by unaffected user  <br/> |Conference continues and affected user can stay in the conference. Affected user is restricted to what he/she can do in Resiliency mode.  <br/> |Conference continues, and affected user can stay in the conference and all modalities work after user exits Resiliency mode.  <br/> |
|Scheduling or modifying scheduled meetings, creating ad-hoc conferences  <br/> |Not possible while user is in Resiliency mode.  <br/> |Available for all modalities.  <br/> |
|Presence as seen by other users in the same pool  <br/> |Presence unknown while user is signed into backup pool during Resiliency mode.  <br/> |Shows the last presence state set by the user, and presence changes will now be reflected.  <br/> |
|Contacts list and Address Book Service availability  <br/> |Not available  <br/> |Available  <br/> |
|All peer-to-peer sessions and modalities  <br/> |Available  <br/> |Available  <br/> |
   
**User Experience for a User Homed in an Unaffected Pool During Failback of Another Pool**

|**User task**|**During failback**|**After failback completion**|
|:-----|:-----|:-----|
|Viewing presence of affected user  <br/> |Shows the last presence state set by the affected user.  <br/> |Working. Unaffected users see updates made by affected users.  <br/> |
|Ongoing conferences organized by affected user  <br/> |All modalities of conference are terminated.  <br/> |All modalities now work. Every participant needs to click to rejoin the conference.  <br/> |
|Ongoing conferences organized by unaffected user  <br/> |Conference continues, and affected user can stay in the conference and all modalities work.  <br/> |Conference continues, and affected user can stay in the conference and all modalities work.  <br/> |
|All peer-to-peer sessions and modalities  <br/> |Available  <br/> |Available  <br/> |
   

