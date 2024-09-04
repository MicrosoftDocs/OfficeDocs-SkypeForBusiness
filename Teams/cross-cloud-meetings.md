---
title: Meet with people in other Microsoft 365 cloud environments
ms.author: jtremper
author: jacktremper
manager: pamgreen
ms.topic: article
ms.service: msteams
audience: admin
ms.custom: 
ms.collection: 
  - Teams_ITAdmin_GuestAccess
  - M365-collaboration
  - m365initiative-externalcollab
ms.reviewer: dacarrol
ms.date: 02/15/2024
search.appverid: MET150
ms.localizationpriority: medium
f1.keywords:
- NOCSH
description: Learn how to set up Teams meetings with organizations in other Microsoft 365 cloud environments (for example, between commercial and DoD).
---

# Meet with people in other Microsoft 365 cloud environments

There are three options for users to join meetings between your organization and an organization in a different Microsoft 365 cloud environment (such as commercial and GCC):

- Authenticated access using a cross-cloud meeting connection
- [Authenticated access using a guest account](/microsoft-365/solutions/collaborate-guests-cross-cloud)
- [Anonymous access](anonymous-users-in-meetings.md)

This article covers authenticated meeting access using a cross-cloud meeting connection. This is similar to in-cloud meetings using [external access](trusted-organizations-external-meetings-chat.md) in that participants can join meetings as authenticated participants without requiring guest accounts in the other organization. (Cross-cloud meetings don't require external access to be configured.) Users who are invited as a guest can't join meetings using a cross-cloud authenticated meeting connection and must join using their guest account.

With cross-cloud meeting connections, you can allow or prevent meetings between your organization and an organization in another cloud. Cross-cloud meeting connections use organizational relationships defined in [cross-tenant access settings in Microsoft Entra ID](/azure/active-directory/external-identities/cross-tenant-access-settings-b2b-collaboration).

If a cross-tenant connection between organizations already exists in Microsoft Entra cross-tenant access settings, it appears in meeting settings in the Teams admin center. You can edit this connection to choose if meetings are allowed between the two tenants.

If the connection doesn't exist, you can add it in Teams meeting settings. This adds a new organization in the cross-tenant access settings in Microsoft Entra ID using the [default settings that you've defined for inbound and outbound access and tenant restrictions](/azure/active-directory/external-identities/cross-tenant-access-settings-b2b-collaboration#configure-default-settings). (This enables B2B collaboration with the other organization if the defaults allow it.)

> [!NOTE]
> VDI clients aren't supported for cross-cloud meetings.

> [!IMPORTANT]
> The organization that you're meeting with must also configure these settings for their organization.

## Prerequisites

For the best meeting experiences across Microsoft clouds, make sure your network is ready for Microsoft Teams. [Prepare your organization's network for Microsoft Teams](/microsoftteams/prepare-network#network-requirements) contains guidance on how to optimize your network for Teams. Also ensure that the necessary DNS, IPs and Ports are enabled for each of the M365 clouds where your users are collaborating. The following table links to the endpoint definitions for each of the M365 cloud environments:

|Microsoft 365 Cloud Environment|Endpoints|
|:--------------------------------|:------------------------------|
|Commercial, GCC|[Worldwide endpoints](/microsoft-365/enterprise/urls-and-ip-address-ranges)|
|GCC High|[U.S. Government GCC High endpoints](/microsoft-365/enterprise/microsoft-365-u-s-government-gcc-high-endpoints)|
|DoD|[U.S. Government DoD endpoints](/microsoft-365/enterprise/microsoft-365-u-s-government-dod-endpoints)|
|China (21Vianet)|[Microsoft 365 operated by 21Vianet](/microsoft-365/enterprise/urls-and-ip-address-ranges-21vianet)|

## Allow cross-tenant connections with other Microsoft 365 cloud environments

If you're setting up a cross-cloud meeting connection with a tenant that's in a different Microsoft Azure cloud environment than yours, then you need to enable connections with that cloud before you set up the meeting connection itself.

The following table shows which Microsoft Azure cloud environment your Microsoft 365 cloud environment is located in.

|Microsoft Azure cloud environment|Microsoft 365 cloud environment|
|:--------------------------------|:------------------------------|
|Microsoft Azure Commercial|Commercial, GCC|
|Microsoft Azure Government|GCC High, DoD|
|Microsoft Azure China|China (21Vianet)|

If you're setting up a cross-cloud meeting connection with a tenant in a different Microsoft Azure cloud environment, enable that cloud environment in meeting settings.

1. In the Teams admin center, expand **Meetings**, and then select **Meeting settings**.
1. Under **Microsoft cloud settings**, make sure the Microsoft Azure cloud environment you need to connect to is set to **On**.
    > [!NOTE]
    > This is the same as the [Microsoft cloud settings in Microsoft Entra cross-tenant access settings](/azure/active-directory/external-identities/cross-cloud-settings).

## Add a new cross-cloud meeting connection

To create a new cross-cloud meeting connection, you need the tenant ID or the fully qualified domain name for the organization that you want to meet with. Meetings between tenants in Microsoft Azure Government (Microsoft 365 GCC High and DoD) can't create a cross-cloud meeting connection with tenants in Microsoft Azure China.

### Add a cross-cloud meeting connection

1. In the Teams admin center, expand **Meetings**, and then select **Meeting settings**.
1. Under **Cross-cloud meetings**, select **Add**.
1. Type the Tenant ID of the organization you want to connect to or look it up by using the fully qualified domain name.
1. If you want to allow users in the other organization to attend meetings hosted by your organization, set **Inbound connections** to **On**.
1. If you want to allow users in your organization to attend meetings in the other organization, set **Outbound connections** to **On**.

    ![Screenshot of cross-cloud meetings settings in the Teams admin center.](media/cross-cloud-meetings-settings.png)

## Edit a cross-cloud meeting connection

To edit a cross-cloud meeting connection, you need the tenant ID or the fully qualified domain name for the organization that you want to meet with. The list of tenants in meeting settings shows the tenant ID, but you can use the **Lookup** option to search by fully qualified domain name and find the correct tenant ID in the list.

### Steps to edit a cross-cloud meeting connection

1. In the Teams admin center, expand **Meetings**, and then select **Meeting settings**.
1. Under **Cross-cloud** meetings, select the tenant you want to update, and then select **Edit**.
1. Update the connection settings that you want to change, and then select **Save**.

## Multi-Factor Authentication (MFA)

When setting up the cross-cloud meeting connection, it's important to consider the impact security policies may have on users attempting to join a cross-cloud meeting. When the tenant hosting a cross-cloud meeting has an Entra Conditional Access Policy configured to enforce Multi-Factor Authentication users may be blocked from signing in to the meeting with error AADSTS90072.

To resolve this error either:

- (Recommended) Trust the incoming Multi-Factor Authentication from the user's home tenant as a part of the cross-cloud trust following the instructions here: [To change inbound trust settings for MFA and device claims](/entra/external-id/cross-tenant-access-settings-b2b-collaboration#to-change-inbound-trust-settings-for-mfa-and-device-claims). This trust only impacts the specific tenant configured in cross tenant access settings and makes it possible for the user to satisfy the meeting host's MFA requirements utilizing their own home tenant MFA process.

Or, if the user's home tenant doesn't have MFA enabled:

- Modify the Conditional Access Policy that's enforcing Multi-Factor Authentication to exclude 'Other External Users' following the instructions here: [Assigning Conditional Access policies to external user types](/entra/external-id/authentication-conditional-access#conditional-access-for-external-users). **Note**: This option isn't limited to impacting cross-cloud authenticated meeting users and isn't configurable on a per-tenant basis. Review the definition of 'Other External Users' in the provided link to evaluate the impact to your tenant's external users.

## Related topics

[Collaborate with guests from other Microsoft clouds](/microsoft-365/solutions/collaborate-guests-cross-cloud)

[Manage external access in Teams](manage-external-access.md)
