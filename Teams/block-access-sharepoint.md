---
title: Block access to SharePoint for specific users
author: SerdarSoysal
ms.author: serdars
manager: serdars
ms.reviewer: Nigolc
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
ms.localizationpriority: medium
search.appverid: MET150
description: Learn about how to block access to SharePoint for specific users
---

# Block access to SharePoint for specific users

Applying any Conditional Access (CA) policy on SharePoint in Microsoft 365 is also applied to Teams. However, some organizations want to block access to SharePoint files (upload, download, view, edit, create) yet allow their employees to use Teams desktop, mobile, and web clients on unmanaged devices. Under the CA policy rules, blocking SharePoint would lead to blocking Teams as well. This article explains how you can work around this limitation and allow your employees to continue using Teams while completely blocking access to files stored in SharePoint.

> [!Note]
> Blocking or limiting access on unmanaged devices relies on Azure AD conditional access policies. Learn about [Azure AD licensing](https://azure.microsoft.com/pricing/details/active-directory/). For an overview of conditional access in Azure AD, see [Conditional access in Azure Active Directory](/azure/active-directory/conditional-access/overview). For info about recommended SharePoint Online access policies, see [Policy recommendations for securing SharePoint sites and files](/microsoft-365/enterprise/sharepoint-file-access-policies). If you limit access on unmanaged devices, users on managed devices must use one of the [supported OS and browser combinations](/azure/active-directory/conditional-access/concept-conditional-access-conditions#supported-browsers), or they will also have limited access.

You can block or limit access for:

- Users in the organization or only some users or security groups.

- All sites in the organization or only some sites.

When access is blocked, users will see an error message. Blocking access helps provide security and protects secure data. When access is blocked, users will see an error message.

1. Open the SharePoint Admin Center.

2. Expand **Policies** > **Access Policies**.

3. In the **Unmanaged Devices** section,  select **Block Access** and select **Save**.

   ![the Unmanaged devices section for Policies.](media/no-sharepoint-access1.png)

4. Open the [Azure Active Directory](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies) portal and navigate to **Conditional Access Policies**.

    You'll see a new policy has been created by SharePoint that's similar to this example:

    ![a new policy that's named Use app-enforced Restrictions for browser access.](media/no-sharepoint-access2.png)

5. Update the policy to target only specific users or a group.

    ![the SharePoint admin center with the Select user section highlighted.](media/no-sharepoint-access2b.png)

  > [!Note]
> Setting this policy will cut your access to the SharePoint admin portal. We recommended that you configure the exclusion policy and select the Global and SharePoint admins.

6. Verify that only SharePoint is selected as targeted Cloud App

    ![SharePoint is selected as the targeted app.](media/no-sharepoint-access3.png)

7. Update **Conditions** to include desktop clients, as well.

    ![desktop and mobile apps highlighted.](media/no-sharepoint-access4.png)

8. Make sure that **Grant access** is enabled

    ![grant access is enabled.](media/no-sharepoint-access5.png)

9. Make sure **Use app enforced restrictions** is enabled.

10. Enable your policy and select **Save**.

    ![The app enforced restrictions is enabled.](media/no-sharepoint-access6.png)

To test your policy, you need to sign out from any client such as the Teams desktop app or the OneDrive for Business sync client and sign in again to see the policy working. If your access has been blocked, you'll see a message in Teams that states the item might not exist.

 ![The item not found message.](media/access-denied-sharepoint.png)

In SharePoint, you'll receive an access denied message.

![The access denied message.](media/blocked-access-warning.png)

## Related topics

[Control access for unmanaged devices in SharePoint](/sharepoint/control-access-from-unmanaged-devices)