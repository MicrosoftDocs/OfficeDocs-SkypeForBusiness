---
title: Purchase third-party apps and manage subscriptions and licenses
author: ashishguptaiitb
ms.author: guptaashish
manager: prkosh
ms.topic: article
ms.service: msteams
ms.subservice: teams-apps
audience: admin
ms.date: 04/08/2024
ms.collection: 
  - M365-collaboration
search.appverid: MET150
ms.reviewer: Christian.Maier
f1keywords: 
description: Learn how to purchase paid app licenses in Teams store using a credit card, a debit card, or via invoice billing.
appliesto: 
- Microsoft Teams
ms.localizationpriority: high
---
# Purchase third-party Microsoft Teams apps and manage subscriptions and licenses

Some Teams apps require purchasing a service subscription to use app functionality. These service subscriptions are called Software as a Service (SaaS) offers. A license is available for purchase from [AppSource](https://appsource.microsoft.com) and in the [Microsoft Teams admin center](https://admin.teams.microsoft.com).

Paid apps require users to authenticate to prevent unwarranted access. Also, user sign-in is required to check for entitlement and to make the corresponding app functionality available for the logged-in user. For authentication, app developers can use single sign-on (SSO) using Microsoft Entra ID or use third-party OAuth Identity Provider. The authentication mechanism is similar for Teams or web apps. For more information, see [How apps authenticate users](/microsoftteams/platform/concepts/authentication/authentication).

You can purchase licenses for services offered by third-party apps from the Manage apps page in the Teams admin center. The **Licenses** column in the table indicates if an app offers a SaaS subscription for purchase. You can purchase apps using a credit card, debit card, or with invoice billing.

:::image type="content" source="media/manage-apps-new-page.png" alt-text="Screenshot showing the purchase licenses option on the manage apps page in Teams admin center." lightbox="media/manage-apps-new-page-large.png":::

## Purchase apps in the Teams admin center

To purchase apps in Teams admin center, follow these steps:

1. Sign in to the Teams admin center and access **Teams apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)**. You must be a Teams Administrator to access the page.

1. Search for the app that you want by its name. To check if the app offers a paid SaaS subscription, see the **Licenses** column. Each app has one of the following values:
    * **Purchase**: The app offers a SaaS subscription and is available to purchase.
    * **Purchased**: The app offers a paid SaaS subscription and you have the licenses for the app.
    * **- -**: The app doesn't offer a SaaS subscription.

1. Select **Purchase** to go to the **Plans and pricing** tab of the app details page. You can review the plans and pricing information available in admin center. You can select **Learn more** link to go to the app's page on [AppSource](https://appsource.microsoft.com/).

1. To subscribe to an app, choose the plan you want, and select **Purchase**. The checkout flow opens directly in the Teams admin center.

   > [!NOTE]
   > Private plans may also be listed for purchase, which include special pricing that your organization can separately negotiate with an app developer. Such plans have the label **Private plan** under the plan name.

1. Select the number of user licenses you want to buy.

1. Verify that the billing account and the sold-to address are correct. If you don't already have an account, select **Add**. Only a Global Administrator can add a new billing account. For more information on billing accounts, see [Understand billing accounts](/microsoft-365/commerce/manage-billing-accounts).

1. Verify that the correct billing profile is selected. If you don't already have a profile, select **Add new**. You can pay with a credit card, debit card, or with [invoice billing](#invoice-billing). The billing profile also lets you add a purchase order number to identify your order later. For more information on billing profiles, see [Understand billing profiles](/microsoft-365/commerce/billing-and-payments/manage-billing-profiles).

1. Select **Place order**.

1. Select **Set up** to activate your subscription on the app developer's website. If you don't set up your subscription after your purchase, you can do it later by selecting **Manage subscriptions**.

After you purchase the SaaS offer associated with a Teams app, you can view the following purchase details on the **Plans and subscriptions** tab of the app details page.

* **License activation date**: Date on which your license was activated.
* **Licenses**: Number of licenses you have.

Select **Manage subscriptions** to view and manage the licenses you already have.

Global Administrators can view the subscriptions purchased by anyone in the organization. They can add more licenses, remove licenses, and cancel subscriptions for purchases made by anyone in their billing account. Teams Administrators can perform the same actions for purchases made by them and not for the purchases made by other admins.

> [!NOTE]
> If a Global Administrator wants to manage a subscription purchased by another Global Administrator, they need to be in the same billing account. You can give another Global Administrator access to a subscription you purchased by selecting the app in the [Microsoft 365 admin center](https://admin.microsoft.com). In admin center, access **View billing profile** > **Select billing account** > **Assign roles** > **Add other Global admins**.

> [!IMPORTANT]
> When you enable app purchasing, it also turns on in-app purchasing. Users may see in-app purchase offers that are controlled by the app developer inside their app. To prevent users from making in-app purchases, you can block the app.

### Invoice billing

* Invoice billing is available as a payment option for some transactions.
* A credit review is required the first time you use invoice billing, which can take up to 24 to 48 hours for approval. Invoice billing isn't available until the credit check is complete. You can place your order with a credit card or try again later after your credit review is approved.
* Invoice billing is only available for an admin account that has Teams Administrator and Billing Administrator role.
* Invoice billing isn't available when purchasing a plan with a 30-day free trial.

## Manage subscriptions in Teams admin center

In Teams admins center, you can manage the app subscriptions and licenses you purchased. You can view the list of app subscriptions and their details and perform the following actions:

* Change a plan
* Buy or remove license
* Update a payment method
* Cancel a subscription
* View your invoice

:::image type="content" source="media/manage-existing-subscriptions-actions.png" alt-text="Screenshot of subscription details of an app." lightbox="media/manage-existing-subscriptions-all.png":::

To manage subscriptions, follow these steps:

1. Sign in to Teams admin center and access **Teams apps** > [**Manage apps**](https://admin.teams.microsoft.com/policies/manage-apps) .

1. Select the **Subscriptions** tab to view the subscriptions you purchased.

   :::image type="content" source="media/subscription-options-in-manage-apps.png" alt-text="Screenshot of subscription option for an app in the manage apps page." lightbox="media/manage-app-subscriptions-manage-apps.png":::

> [!NOTE]
> In Teams admin center, you can manage the app subscriptions purchased by you or other admins who are part of the same billing account. To view all the app subscriptions purchased for the same tenant by other admins or purchased using different billing accounts, visit the [Microsoft 365 admin center](https://admin.microsoft.com/adminportal/home#/homepage).

## List and sell a SaaS offer for a Teams app

Developers can create SaaS offers associated with their Teams apps. These offers are published through [Partner Center](https://partner.microsoft.com) and are available for organizations to purchase through [AppSource](https://appsource.microsoft.com/) and the Microsoft Teams admin center.

For more information for third-party app developers, see [Create a SaaS offer](/azure/marketplace/partner-center-portal/create-new-saas-offer).

## Manage app licenses in Teams admin center

Microsoft Teams lets admins manage licenses for SaaS app offers. It enables admins to easily buy, assign, track, and remove SaaS app licenses purchased in Teams. It helps utilizing the available resources effectively.

As an administrator, it's important to understand how licenses work and how to manage them effectively. For apps that are purchased with a set number of subscription licenses, you have to ensure that these licenses are being utilized properly.

You can perform the following tasks to manage the licenses:

* **[Assign license to users](#assign-a-license-to-a-user)** to assign an app subscription license to an individual or multiple users.
* **[Assign license to a team](#assign-a-license-to-a-team)** when you need to assign an app subscription license to a team.

### Assign a license to a user

You can assign a license to one or more users in your tenant. To view and assign the licenses for an app:

1. Sign in to the Teams admin center and go to **Teams apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)**.

1. To view the licenses, select an app. The app details page shows the number of licenses available for the app on the **Licenses** tab.

   :::image type="content" source="media/purchased-licenses.png" alt-text="Screenshot that shows the purchased licenses of an app."  lightbox="media/purchased-licenses1.png":::

1. To view the license utilization and assign licenses, select **Assign licenses**. The assign licenses window appears.

   :::image type="content" source="media/assign-licenses.png" alt-text="Screenshot that shows the Assign licenses dialog to select the user name."  lightbox="media/assign-licenses1.png":::

1. Search and select the users and select **Assign**.

### Assign a license to a team

To manage licenses across multiple users who are part of the same team, you can select a team from the list of available options. The number of members in the team must be smaller than the number of licenses available for the app. To assign a license to a team, follow these steps:

1. Sign in to the Teams admin center and go to **Teams apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)**.

1. Under **All apps**, select the app to assign its licenses to a team.

1. In the **Licenses** tab, select **Assign licenses**.

   :::image type="content" source="media/assign-licenses-group.png" alt-text="Screenshot that shows the Assign licenses dialog with the list of teams to assign license." lightbox="media/assign-licenses-group1.png":::

1. Search and select the team, and select **Assign**.

After you assign licenses to the users or team, you can view the list of assigned users. This list allows you to view a mapping of licenses and assigned users.

   :::image type="content" source="media/remove-licenses.png" alt-text="Screenshot that shows list of assigned users to remove the licenses." lightbox="media/remove-licenses1.png":::

## Disable app purchases in Teams admin center

To prevent users from purchasing third-party apps, you can disable purchases using the MSCommerce PowerShell module. You can view a list of applicable apps and whether self-service purchase is enabled or disabled, using `AllowSelfServicePurchase` parameter. For more information, see [Use AllowSelfServicePurchase to disable Teams app purchases](/microsoft-365/commerce/subscriptions/allowselfservicepurchase-powershell?view=o365-worldwide). The change applies to all users in your organization.

## Related articles

* [Manage your apps in the Microsoft Teams admin center](manage-apps.md)
* [Create a SaaS offer](/partner-center/marketplace/create-new-saas-offer)
* [Microsoft Entra built-in roles](/azure/active-directory/roles/permissions-reference)
* [Understand how apps authenticate users](/microsoftteams/platform/concepts/authentication/authentication)
