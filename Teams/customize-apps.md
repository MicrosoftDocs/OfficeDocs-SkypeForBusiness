---
title: Modify branding and appearance of apps in your organization's Teams store
author: guptaashish
ms.author: guptaashish
manager: prkosh
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
  - M365-collaboration
f1.keywords: 
  - NOCSH
appliesto: 
- Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Learn how to change the appearance of the app and rebrand an app by editing app details and metadata.
---

# Customize apps and their branding in your organization's Teams store

Microsoft Teams admins can modify the appearance of some Teams apps. Such modifications can enhance Teams store experience for end-users and help adhere to organization's branding. For example, admins can modify the description and icon of an app that makes it easier for their organizations end-users to identify the app, to understand its use, and for added prominence. Admins make these changes by changing some metadata or properties of an app. The changes are available only within their organization. This functionality is called app customization.

Admins can only customize apps if the app developer allows their app to be customized. While Teams provides an option to customize a few properties, app developers control the properties that can actually be customized by any admin.

As an admin, you can customize the following properties.

* Short name
* Short description
* Full description
* Privacy policy URL
* Website URL
* Terms of use URL
* App icon
* Outline color of the icon
* Accent color

For detailed information about each of these metadata fields, see the [Teams manifest schema](/microsoftteams/platform/resources/schema/manifest-schema) in the Teams developer documentation.

A few considerations before you use the feature are:

* You must have Teams license to customize app information.
* You can only customize [third-party apps](deploy-apps-microsoft-teams-landing-page.md#third-party-apps-validated-by-microsoft) and not [custom apps](deploy-apps-microsoft-teams-landing-page.md#custom-apps).
* You can't customize any app in Government Community Cloud High (GCCH) and Department of Defense (DoD) environments.
* An app can be customized only if the app developer allows it.
* Modifications to any apps are available only within your organization.

## Customize the details of an app

To change the look and feel of an app as it appears in your organization's Teams store, follow these steps:

1. Sign in to the Teams admin center and access **Teams apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)**.

1. Search the app that you want to customize using its name. Verify in the **Customizable** column if the app developer allows the app to be customized or not.

   :::image type="content" source="media/customizable-apps-in-tac.png" alt-text="The screenshot shows that customizable column in admin center helps you to sort the app catalog based on which apps are customizable.":::

   There are three entry points to access the customize feature:

   * Select next to the app that you want to customize, and then select **Customize**.

     :::image type="content" source="media/select-app-to-customize-trimmed.png" alt-text="The screenshot shows an option to customize an app by selecting the app from Manage Apps page and selecting Customize from the options." lightbox="media/select-app-to-customize.png":::

   * Select the app name and then select the edit icon in **Customizable**.

     :::image type="content" source="media/communities-microsoft.png" alt-text="The screenshot shows an option to customize an app by selecting the edit option under Customizable mention on the app details page.":::

   * Select the app name, select **Actions**, and select **Customize**.

     :::image type="content" source="media/customize-action-menu.png" alt-text="The screenshot shows an option to customize an app by opening Actions menu and selecting Customize option from the app details page.":::

1. Expand the **Details** section and customize one or more of the available fields. Only the fields marked as customizable by the app developer are available for editing.

   :::image type="content" source="media/customize-settings.png" alt-text="The screenshot displays name and description on the customize user interface.":::

1. Expand the **Icon** section.

1. Upload an icon. Use one icon (192 x 192) pixel in PNG format.

1. Choose an icon outline color. Use one transparent outline (32 x 32) pixel in PNG format.

1. Select an app accent color that matches the icon.

   :::image type="content" source="media/customize-app-colors.png" alt-text="Screenshot showing the icon color options that can be customized.":::

1. After customizing the app, select **Apply**.

1. Select **Publish** to publish the customized app.

   The customized app is now listed in your **Manage apps** page. You'll have only one version of the app, since customizing the app features doesn't create a copy of the app.

Now your Teams end-users can see the customized app in their client.

   :::image type="content" source="media/contoso-app.png" alt-text="The screenshot shows a customized app in Teams client.":::

Consider the following details about app customization functionality:

* When you customize apps and any description related to an app, ensure that you follow the guidelines that app developer provide in their documentation or terms of use. Adhere to the copyright laws when using any third-party images.

* Admin-provided customization data is stored in the nearest region.

* You're responsible to ensure that links to terms of use or privacy policy are valid.

* In case the app developer no longer allows a field to be customizable, a message appears on the app details page notifying the admin about the fields that can't be customized any longer. All the changes made to that field will be reverted to the original values.

* We recommend testing app customization changes in a Teams test tenant before making these changes in your production environment.

* Changes to the branding may require up to 24 hours to propagate to all the users.

* For an app to become customizable, the developers can provide a new version of the app. You upload the new version and remove the previous version of the app. If you've customized an app and published it, the new app customized using the app customization feature won't replace the current app.

* The [app usage report](teams-analytics-and-reports/app-usage-report.md) displays the original name of the app that is provided by the publisher.

* The Microsoft Graph permission consent dialog displays the original name of the app that is provided by the publisher. It helps you to accurately identify an app while providing permissions to it.

## Review app details

To view the changes after saving those, view the app details page.

1. Sign in to the Teams admin center and access **Teams apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)**.

1. To open the app details page, select the app name.

1. View the app details, including the original app name in the field **Short name from publisher**. The **Short name from publisher** field is only visible if you've changed the app's short name.

   :::image type="content" source="media/original-app-version.png" alt-text="The screenshot shows modified short name of an app.":::

## Reset app details to default values

You can reset the app details to the original values provided by the app developer. The option is only available for app that you customize.

1. In Teams admin center, access **Teams Apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)**.

1. To open the app details page, select the app name.

1. From the **Actions** menu, select **Reset to default**.

   :::image type="content" source="media/reset-app-customization.png" alt-text="The screenshot shows the reset to default option for a customized app.":::

## Related articles

* [Customize your organization's app store](customize-your-app-store.md)
* [Rebrand your apps community post](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/rebrand-apps-to-your-own-organization-s-branding-with-app/ba-p/2376296)
