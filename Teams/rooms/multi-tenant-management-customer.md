---
title: Partner management for customers
author: donnah007
ms.author: v-donnahill
manager: serdars
ms.reviewer: dstrome 
ms.date: 06/09/2022
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: partner management for customers.
f1keywords: 
---

# Partner management for customers


Partner management in the Teams Rooms Managed (TRM) service enables customers to seamlessly delegate access and responsibilities to one or many partner organizations. Partners can only manage rooms that they are assigned to manage. 

## On-boarding partners
   Invite partners through the TRM portal to establish the relationship between your organization and the partner organization’s tenant. 

### Invitation to partner

   In this method, you should know the domain name of the partner (ex. Contoso.com).

**To initiate the invite** 

1. Log in to the Teams Rooms Managed portal as an MMR Administrator.
1. Go to **Settings >** **Partners**, then select **Add partner.**
1. Enter the domain name in the first row.
1. Configure the number of days until the invitation expires by entering an integer from 1-30.
1. Configure the events that will require a change control approval. By default, all controls are set to **Auto approval.**

   > [!NOTE]
   > *Only auto-approve is currently available for now.*
   > 
   >  1.  *Manual approval:* When the partner performs the action, an approval request is generated for the customer to review and approve. The action is not implemented until the  request has been approved.
   >  
   >  1. *Auto- approval:* When the partner performs the action, no approval request is generated and the action is implemented immediately.
     
1. Select **Next.**
1. Assign rooms the partner will manage, then select **Next.**
1. To continue, review the terms and select **I agree.**
1. Review the details of the invitation.
1. Select **Add partner** to send the invitation.

The invitation is sent to the Tenant managers in the partner instance for review. The first partner user that accepts the invitation will establish the link between the Partner and your tenant and assign Primary admins. There is no special association with the user that establishes the link, which allows flexibility should the user be reassigned. There must always be at least one user in the primary admin role.

To manage users in the primary admin role, see [Multi-tenant Management for Partners](multi-tenant-management-partner.md).


## Off-boarding partners

**To remove a partner**

1. Login to the TRM-MTM portal as an MMR administrator.
1. Navigate Go to **Settings > Partners.**
1. Select the partner you wish to remove.
1. In the customer detail pane, select **Remove partner.**
1. Select **Delete**. 
1. At the confirmation prompt to terminate the association between your and the customer tenant, select **Delete**.

## Managing partner roles

Partner roles allow for your partner to more granularly delegate responsibilities to additional personnel. The concept of these roles is the same as described in [Role-based access control](microsoft-teams-rooms-premium-rbac.md). It is important to note that partner roles are distinct from your custom roles. 

The **Primary admin** role is the only built-in role for each partner you add. This role has almost all permissions to the rooms you assigned that partner for the TRM service (see [Table 1](#table-1)). For example, if you have rooms across the globe and assign a partner to manage All US rooms, the primary admin would only be able to manage and delegate permissions for those rooms. In this case, the primary admins for this Partner have no visibility to any rooms outside of the US. 

### Adding Primary admins to partner

If you already sent an invitation to a partner and wish to delegate more rooms, you can add rooms to the partner admin role.

**To add new rooms to an existing partner**

1. Log in to the TRM-MTM portal as an MMR administrator.
1. Go to **Settings > Roles.**
1. Select  **Partner roles.** 
1. Select the **Primary admin** role for the corresponding partner name.
1. In the role pane, select **Assignments**.
1. Select the **Assigned admins** assignment.
1. In the Assigned admins assignment pane, select **Scope**.
1. Select **Edit**.
1. Search for the rooms you wish to add and select the desired room.
1. To confirm the changes, select **Save**.




### Table 1

|Feature|Permission|**MMR Admin**|**Site Lead**|**Site Tech**|**Partner admin**|
| :- | :- | :- | :- | :- | :- |
|Rooms|View| &#10004;|&#10004;|&#10004;|&#10004;|
||Modify|&#10004;|&#10004;|&#10004;|&#10004;|
||Reset key|&#10004;||||
||Download key|&#10004;|&#10004;|&#10004;||
||Unenroll|&#10004;|&#10004;|&#10004;||
||Create |&#10004;|&#10004;|||
|Group management|View|&#10004;|&#10004;||&#10004;|
||Modify|&#10004;|&#10004;|||
||Create |&#10004;|&#10004;|||
|Update ring management|View|&#10004;|&#10004;||&#10004;|
||Modify|&#10004;|&#10004;||&#10004;|
|Reports|View|&#10004;|&#10004;||&#10004;|
||Create customer incident|&#10004;|&#10004;|&#10004;|&#10004;|
|Tickets Management|View|&#10004;|&#10004;|&#10004;|&#10004;|
||Update|&#10004;|&#10004;|&#10004;|&#10004;|
|MMR Settings|View|&#10004;||||
||Modify|&#10004;||||
|Role management|View |&#10004;|||&#10004;|
||Modify|&#10004;|||&#10004;|





## Security

As the end customer, you retain control over access to your data and can completely remove a partner at any time. 

With the delegated access feature, a partner does not gain any other privileges outside of the TRM service portal. However, any data present in the TRM service derived from other Microsoft products is considered data in the TRM service. As an example, while call quality reports are derived from Teams call quality data, any data in the TRM portal is in the permission scope. 

No permissions are granted to AAD or the Teams Admin Center or any other Microsoft product. Furthermore, partners do not have any access to view or modify rooms not defined in the invitation scope. 

Data resides in the customer’s tenant and is not copied to the partner’s tenant. 

The MTM portal uses Azure AD authentication to validate the login credentials of the partner. Note that at this time, the customer’s authentication policies do not apply to the partner. For example, if the customer has a multi-factor authentication policy, it does not translate to the partner. 

To pull logs on partner activity, see [Auditing](multi-tenant-auditing.md). 

> [!NOTE]
> AAD auditing and O365 auditing do not capture logs from the TRM portal. 
