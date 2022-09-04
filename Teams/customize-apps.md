---
title: Modify the appearance of apps in your organization's Teams store
author: ashishguptaiitb
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

# Customize appearance of apps in your organization's Teams store

Microsoft Teams admins can modify the appearance of some Teams apps to provide a personalized branded experience to their organization's end-users. Such modifications can enhance Teams store experience for end-users and help adhere to organization's branding. For example, admins can modify the description and icon of an app that makes it easier for their organizations end-users to identify the app, to understand its use, and for added prominence. Admins make these changes by changing some metadata or properties of an app. The changes are available only within their organization. This functionality is called app customization.

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

> [!NOTE]
> App customization functionality is not available for custom apps. Admins cannot customize any app in Government Community Cloud High (GCCH) and Department of Defense (DoD) environments.

## Verify if an app is customizable

All apps aren't customizable. If an app developer allows you to customize their app, only then can you use the app customization functionality to modify the appearance of the app. To verify if the app of your choice is customizable or not, follow these steps:

1. Sign in to the Teams admin center and access **Teams apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)**.

1. Search the app that you want to customize using the app name. Verify in the **Customizable** column if the app developer allows the app to be customized or not. If the column isn't visible, select Edit Columns :::image type="icon" source="media/settings-icon-16px.svg"::: and toggle **Customizable** option to **On**.

   :::image type="content" source="media/customizable-apps-in-tac.png" alt-text="The screenshot shows that customizable column in admin center helps you verify if an app is customizable or not.":::

To find out all customizable apps in the Teams store, sort the Customizable column.

## Customize the details of an app

To change the look and feel of an app as it appears in your organization's Teams store, follow these steps:

1. Sign in to the Teams admin center and access **Teams apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)**.

1. Search the app that you want to customize using the app name and ensure that it can be customized.

1. Follow one of these steps:

   * Select the row of an app and then select **Customize** :::image type="icon" source="media/edit-pen-icon.png"::: in the toolbar in the Manage apps page.

   * Select the app name to open the app details page and then select the edit icon :::image type="icon" source="media/edit-pen-icon.png"::: under **Customizable**.

   * Select the app name, select **Actions**, and select **Customize**.

     :::image type="content" source="media/customize-action-menu.png" alt-text="The screenshot shows an option to customize an app by opening Actions menu and selecting Customize option from the app details page." lightbox="media/customize-action-menu-expanded.png":::

1. Customize one or more of the available fields. An app developer may allow only a few of the metadata fields to be customized. See [considerations and limitations of customizable fields](#know-the-considerations-and-limitations-for-customizable-metadata).

   :::image type="content" source="media/customize-settings.png" alt-text="The screenshot displays name and description on the customize user interface.":::

1. After customizing the app, select **Apply**.

1. Select **Publish** to publish the customized app and see it listed in the **Manage apps** page.

<!---
   :::image type="content" source="media/customize-app-colors.png" alt-text="Screenshot showing the icon color options that can be customized.":::
--->

Consider the following details about app customization functionality:

* You'll have only one version of the app, since customizing the app features doesn't create a copy of the app.

* When you customize apps and any description related to an app, ensure that you follow the guidelines that app developer provide in their documentation or terms of use. Adhere to the copyright laws when using any third-party images.

* Admin-provided customization data is stored in the nearest region.

* You're responsible to ensure that links to terms of use or privacy policy are valid.

* In case the app developer no longer allows a field to be customizable, a message appears on the app details page notifying the admin about the fields that can't be customized any longer. All the changes made to that field will be reverted to the original values.

* We recommend testing app customization changes in a Teams test tenant before making these changes in your production environment. To get a test tenant, follow the instructions at [create your test tenant](/microsoftteams/platform/concepts/build-and-test/prepare-your-o365-tenant).

* Changes take up to 24 hours to propagate to all the users.

* For an app to become customizable, the developers can provide a new version of the app. You upload the new version and remove the previous version of the app. If you've customized an app and published it, the new app customized using the app customization feature won't replace the current app.

* The [app usage report](teams-analytics-and-reports/app-usage-report.md) displays the original name of the app that is provided by the publisher.

* The Microsoft Graph permission consent dialog displays the original name of the app that is provided by the publisher. It helps you to accurately identify an app while providing permissions to it.

## Know the considerations and limitations for customizable metadata

The limitations on the customizable fields are below:

| Customizable field | Consideration |
|:---|:---|
| Any URL fields | Ensure valid and secure URLs using `https`. |
| Short description | The short description must be under 80 characters and not repeat what's in the full description. |
| Icon | Transparent outline icon in PNG format that is 32x32 pixel in resolution. |
| Color icon | Full-color icon in PNG format that is 192x192 pixel in resolution. |
| Accent color | Color must match your icon background. |

## Review app details

To view the changes after saving the customization, view the app details page.

1. Sign in to the Teams admin center and access **Teams apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)**.

1. To open the app details page, select the app name.

1. View the app details, including the original app name in the field **Short name from publisher**. The **Short name from publisher** field is only visible if you've changed the app's short name.

   :::image type="content" source="media/original-app-version.png" alt-text="The screenshot shows modified short name of an app.":::

Your Teams users can see the customized app in the Teams store in their client.

   :::image type="content" source="media/contoso-app.png" alt-text="The screenshot shows a customized app in Teams client.":::

## Reset app details to default values

You can reset the app details to the original values provided by the app developer. The option is only available for app that you customize.

1. In Teams admin center, access **Teams Apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)**.

1. To open the app details page, select the app name.

1. From the **Actions** menu, select **Reset to default**.

   :::image type="content" source="media/reset-app-customization.png" alt-text="The screenshot shows the reset to default option for a customized app.":::

## Related articles

* [Customize your organization's app store](customize-your-app-store.md)
* [Rebrand your apps](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/rebrand-apps-to-your-own-organization-s-branding-with-app/ba-p/2376296)
