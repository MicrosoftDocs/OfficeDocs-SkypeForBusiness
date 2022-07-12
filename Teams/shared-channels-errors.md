---
title: Shared channels errors in Microsoft Teams
author: MikePlumleyMSFT
ms.author: mikeplum
manager: serdars
ms.reviewer: jasonlewis
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
- M365-collaboration
- Teams_ITAdmin_Help
f1.keywords:
- NOCSH
appliesto: 
- Microsoft Teams
ms.localizationpriority: normal
search.appverid: MET150
description: Learn how to use fix errors in shared channels in Microsoft Teams. 
---

# Shared channels errors in Microsoft Teams

If your users see error messages when trying to add people from outside your organization to shared channels, check the settings in this article. 

## Due to admin policy, you can't add external people to the channel. For more info, talk to your admin.

Teams uses Microsoft 365 Groups for team membership. The Microsoft 365 Groups guest settings must be turned on in order for people outside the organization to be added to a shared channel. If your users see this error, check the Microsoft 

To set Microsoft 365 Groups settings for people outside the organization
1. In the Microsoft 365 admin center, in the left navigation pane, expand **Settings**.
1. Click **Org settings**.
1. In the list, click **Microsoft 365 Groups**.
1. Ensure that the **Let group owners add people outside your organization to Microsoft 365 Groups as guests** and **Let guest group members access group content** check boxes are both checked.
1. If you made changes, click **Save changes**.

## Due to admin policy, you can't add external people to the channel

Teams channel policies determine how users can interact with shared channels. If users see this error message, check the channel policy for that user.

To set the policy for inviting people outside the organization to shared channels
1. In the left navigation of the Microsoft Teams admin center, go to Teams > Teams policies.
1. Select the policy that your user is assigned to.
1. Ensure that **Invite external users to shared channels** is **On**.
1. If you made changes, select **Apply**.

For more information about Teams channel policies, see [Manage channel policies in Microsoft Teams](teams-policies.md).

## You can't share this channel with people from this org

If your users see this error, then they're prevented from sharing the channel with people in the other organization by the Azure Active Directory cross-tenant access settings. This may be due to the inbound settings in your organization or the outbound settings in the other organization.

To check the inbound settings for your organization
1. In [Azure Active Directory](https://aad.portal.azure.com), select **External Identities**, and then select **Cross-tenant access settings**.
1. Select the inbound access link for the organization that you want to check.
1. On the **B2B direct connect** tab, choose **Customize settings**.
1. On the **External users and groups** tab, ensure that **Allow access** and **All external users and groups** are selected, or if you've chosen **Select external users and groups**, make sure that the users who are seeing the error message are members of the selected groups.
1. If you made changes, select **Save** and close the **Inbound access settings** blade.

If users continue to see the error, check with the organization that they're collaborating with. That organization's outbound settings may disallow sharing with your organization. For information about setting up shared channels between organizations, see [Collaborate with external participants in a shared channel](/microsoft-365/solutions/collaborate-teams-direct-connect).

## We couldn't find any matches. Make sure the email address is correct, or talk to your admin

If your users see this error, then Microsoft 365 is not able to find the specified email address in the external organization. You'll need to confirm the address with the external organization.

