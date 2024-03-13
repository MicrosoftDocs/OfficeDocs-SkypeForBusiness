---
title: Use app customization to brand the apps for your organization's needs
author: ashishguptaiitb
ms.author: guptaashish
manager: prkosh
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.subservice: teams-apps
audience: Admin
ms.date: 3/14/2024
ms.reviewer: eddieqiao
ms.collection: 
  - M365-collaboration
f1.keywords: 
  - NOCSH
appliesto: 
- Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Learn how to change the metadata and appearance of an app to rebrand it for better adoption in your organization.
---

# Use app customization to update branding of apps in your org store

Microsoft Teams admins can modify the appearance of some Teams apps to provide a personalized branded experience to their organization's users. Such modifications can enhance Teams store experience for users and help adhere to organization's branding. For example, admins can modify the description and icon of an app. The customization makes it easy for users to identify the app as internal tooling, to understand its org-specific use case, and to use it with confidence. Admins make these updates by changing some metadata or properties of an app. The changes are available only within their organization. This functionality is called app customization.

Admins can only customize apps if the app developer allows their app to be customized. While Teams provides an option to customize the following properties, app developers control the specific properties in their app that can be customized.

* Short name
* Short description
* Full description
* Privacy policy URL
* Website URL
* Terms of use URL
* App icon
* Outline color of the icon
* Accent color

For detailed information about each of these properties, see the [Teams manifest schema](/microsoftteams/platform/resources/schema/manifest-schema) in the Teams developer documentation.

> [!NOTE]
> You must have a Teams client license to customize app information.

## Verify if an app is customizable

All apps aren't customizable. If an app developer allows customization of their app, only then can you modify the appearance of the app. To verify if the app of your choice is customizable or not, follow these steps:

1. Sign in to the Teams admin center and access **Teams apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)**.

1. Optionally, if the **Customizable** column isn't visible, select Edit Columns :::image type="icon" source="media/settings-icon-16px.svg"::: and toggle **Customizable** option to **On**.

1. Search the app that you want to customize using the app name. Verify in the **Customizable** column if the app developer allows the app to be customized or not.

   :::image type="content" source="media/customizable-apps-in-tac.png" alt-text="The screenshot shows that customizable column in admin center helps you verify if an app is customizable or not.":::

To find out all customizable apps in the Teams store, sort the **Customizable** column.

## Understand types of customization

A customizable app can be customized in two ways depending on your organization's needs:

1. **[Default customization](#create-a-default-customization-for-an-app)**: Customize an app for all users to receive a single customized version with constant appearance for all users.

1. **[Additional customization](#create-additional-customizations-to-provide-to-different-users)**: Create multiple customizations of the same app and let users or groups receive differently customized app.

| Requirements, considerations, and behavior | Default customization                                       | Additional customizations                                                      |
|:-------------------------------------------|:------------------------------------------------------------|:-------------------------------------------------------------------------------|
| When to use the customization              | All app users need the same customized appearance of an app | Different users or groups need differently customized versions of the same app |
| Who receives the customized app            | Every user who is allowed to use the app                    | Selected users who are assigned using app setup policy.                        |
| Changes to the app in  the app catalog     | Changes are visible such as updated name                    | Not visible in the app catalog.                                                |
| Where to do it in the admin center         | Manage apps page or app details page                        | App details page only                                                          |
| How do users receive the customized app    | Automatically                                               | You assign users to setup policy and setup policy to customizations.           |

## Create a default customization for an app

To change the look and feel of an app in your organization's Teams store, follow these steps:

1. Sign in to the Teams admin center and access **Teams apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)**.

1. Search the app that you want to customize using the app name and [ensure that it can be customized](#verify-if-an-app-is-customizable).

1. To open the UI to customize individual metadata fields, follow one of these steps:

   * Select the row of an app and then select **Customize** :::image type="icon" source="media/edit-pen-icon.png"::: in the toolbar in the Manage apps page.

   * Select the app name to open the app details page and then select the edit icon :::image type="icon" source="media/edit-pen-icon.png"::: under **Customizable**.

   * Select the app name to open the app details page and then select **Actions** > **Customize**.

     :::image type="content" source="media/customize-action-menu.png" alt-text="Screenshot showing the option to customize an app that is available from the actions menu on the app details page.":::

1. Customize one or more of the available fields. You can customize only those parameters that the admin center displays, which are the parameters that a developer allows you to modify. For the allowed values and limitations on the parameters, see [considerations and limitations of customizable fields](#considerations-and-limitations-of-app-customization).

   :::image type="content" source="media/customize-teams-app.png" alt-text="Screenshot showing the name and description on the user interface to customize the app listing.":::

1. After customizing the app, select **Apply**. To verify the changes that you do, see [preview app details](#preview-default-customization-of-an-app). To undo the changes, see [reset app details to default values](#reset-app-details-to-default-values).

1. Select **Publish** to publish the customized app to your organization's store.

The app is listed in the **Manage apps** page and in Teams store and client (available via web, mobile, or desktop client) with the updated details. The modifications take a few hours to display.

## Preview default customization of an app

To view the changes after saving the customizations, view the app details page.

1. Sign in to the Teams admin center and access **Teams apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)**.

1. To open the app details page, select the app name.

1. View the app details, including the original app name in the field **Short name from publisher**. The field is only visible if you change the app's short name.

   :::image type="content" source="media/customized-app-details.png" alt-text="The screenshot shows modified short name of an app.":::

After a few hours, your Teams users can see the customized app in the Teams store in their client (web, mobile, and desktop).

   :::image type="content" source="media/customized-app-in-store.png" alt-text="The screenshot shows a customized app in Teams client.":::

## Create additional customizations to provide to different users

If the app developer allows any customization, you can specifically create multiple customizations of the same app that lets various users or user groups to receive differently customized app. For example, app users across your current organization and your acquired organization can use the same app but also see the app with different brand logos that they relate with. It helps you as an admin in the following ways:

* You can provide customized apps that all of your users can relate with.
* It helps your app adoption efforts succeed as users with varied needs and trust towards different corporate branding trust the app that you make available.

To create additional customizations of an app, follow these steps:

1. Sign in to the Teams admin center and access **Teams apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)**.

1. Ensure that the app that you want to customize supports customization. See [check if a Teams app is customizable](#verify-if-an-app-is-customizable).

1. Click on the app name to open the app details page. Select the **Settings and Customization** tab.

   :::image type="content" source="media/additional-app-customization1.png" alt-text="Screenshot showing the UI to create additional customizations for an app in the app details page.":::

1. If you're creating this customization for the first time, select **Add a customization** otherwise select **Add**.

   :::image type="content" source="media/add-app-customizations.png" alt-text="Screenshot showing the option to create a new app customization option.":::

1. In the left sidebar, provide the updated values of the app information that you want to customize. Select **Apply**.

1. After it's created, select the additional customization and select **Manage assignments**.

1. Search for and select the appropriate app setup policy to apply to the additional customization. Users who are assigned to this setup policy receive the additional customization. Select **Close**.

   :::image type="content" source="media/app-customization-assign-setup-policy.png" alt-text="Screenshot showing the manage assignments option that is used to apply a setup policy to an additional customization.":::

To remove an additional customization, select it in the **Settings and Customization** tab and select **Remove**. The customization must not be assigned to any setup policy. To remove a default customization, see [reset default customization of an app](#reset-app-details-to-default-values).

## Considerations and limitations of app customization

Consider the following details about app customization functionality:

* You can only customize Teams store apps and not [custom apps](apps-in-teams.md#custom-apps-created-within-an-organization-for-internal-use).

* You can customize an app only if the app developer allows it to be customized.

* Your customizations and changes are available only within your organization.

* When you customize apps and any description related to an app, ensure that you follow the guidelines that app developers provide in [app's documentation](manage-apps.md#support-information-for-apps) or in their terms of use. Adhere to the copyright laws when using any third-party images.

* Admin-provided customization information is stored in the nearest data storage region.

* You're responsible to ensure that the updated links to terms of use or privacy policy are valid.

* In case the app developer no longer allows a field to be customizable, a message appears on the app details page notifying the admin. Your changes to the field revert to the value set by the developer.

* We recommend testing app customization changes in a test tenant before making these changes in your production environment. To get a test tenant, follow the instructions at [create your test tenant](/microsoftteams/platform/concepts/build-and-test/prepare-your-o365-tenant).

* Updates take up to 24 hours to show in the client for all the users and admin accounts.

* To make an existing app customizable, the developer must provide a new version of the app in the Teams store.

* The [app usage report](teams-analytics-and-reports/app-usage-report.md) displays the original name of the app that the app developer provides, even if your users use the customized app.

* The Microsoft Graph permission consent dialog displays the original name of the app that the app developer provides. It helps you to accurately identify an app when providing consent to its permissions.

* Customizing an app doesn't change any app functionality.

The limitations on some of the customizable fields are:

| Customization                       | Consideration                                                              |
|:------------------------------------|:---------------------------------------------------------------------------|
| Any URL fields                      | Ensure valid and secure `https` URLs.                                      |
| Short description                   | Must be under 80 characters; don't repeat the full description.            |
| Icon                                | Transparent outline icon in PNG format that is 32x32 pixels in resolution. |
| Color icon                          | Full-color icon in PNG format that is 192x192 pixels in resolution.        |
| Accent color                        | Color must match your icon background.                                     |
| Number of additional customizations | Can only create 10 customizations.                                         |

## Troubleshoot app customization

| Errors and issues                                                    | Possible fix or understanding of the issue                                                                                                                           |
|:---------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| My updates aren't available to my users.                             | Wait a few hours for changes to propagate.                                                                                                                           |
| I can't customize an app.                                            | Cross-check if the [app is customizable or not](#verify-if-an-app-is-customizable).                                                                                  |
| I started to customize an app but can't save or apply my changes.    | Adhere to the limitations of the fields. Look for errors on the UI and the [limitations of app customization](#considerations-and-limitations-of-app-customization). |
| Manage apps page not loading properly. List of apps isn't displayed. | Admin account in use must have the Teams license assigned.                                                                                                           |

## Reset app details to default values

You can remove the app customizations and display the original app information that is provided by the app developer.

To remove an additional customization that applies to specific users, select it in the **Settings and Customization** tab and select **Remove**. The customization must not be assigned to any setup policy.

To remove a default customization that applies to users of the app who aren't assigned an additional customization, follow these steps:

1. In Teams admin center, access **Teams Apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)** and open the app details page.

1. From the **Actions** menu, select **Reset to default** option.

   :::image type="content" source="media/reset-app-customization.png" alt-text="Screenshot showing the reset to default option that removes any customizations for an app.":::

## Related articles

* [Customize your organization's app store](customize-your-app-store.md)
* [Community post about customizing and rebranding your apps](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/rebrand-apps-to-your-own-organization-s-branding-with-app/ba-p/2376296)
