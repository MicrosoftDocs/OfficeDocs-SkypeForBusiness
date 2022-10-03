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

# Use app customization to update branding of apps in your organization's Teams store

Microsoft Teams admins can modify the appearance of some Teams apps to provide a personalized branded experience to their organization's end-users. Such modifications can enhance Teams store experience for end-users and help adhere to organization's branding. For example, admins can modify the description and icon of an app. The customization makes it easy for end-users to identify the app as internal tooling, to understand its org-specific use case, and to use it with confidence. Admins make these updates by changing some metadata or properties of an app. The changes are available only within their organization. This functionality is called app customization.

Admins can only customize apps if the app developer allows their app to be customized. While Teams provides an option to customize the following properties, app developers control which  properties can actually be customized by any admin.

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

## Customize an app

To change the look and feel of an app in your organization's Teams store, follow these steps:

1. Sign in to the Teams admin center and access **Teams apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)**.

1. Search the app that you want to customize using the app name and [ensure that it can be customized](#verify-if-an-app-is-customizable).

1. To open the UI to customize individual metadata fields, follow one of these steps:

   * Select the row of an app and then select **Customize** :::image type="icon" source="media/edit-pen-icon.png"::: in the toolbar in the Manage apps page.

   * Select the app name to open the app details page and then select the edit icon :::image type="icon" source="media/edit-pen-icon.png"::: under **Customizable**.

   * Select the app name to open the app details page and then select **Actions** > **Customize**.

     :::image type="content" source="media/customize-action-menu.png" alt-text="The screenshot shows an option to customize an app by opening Actions menu and selecting Customize option from the app details page." lightbox="media/customize-action-menu-expanded.png":::

1. Customize one or more of the available fields. Only those metadata fields are displayed and are customizable that the app developer has allowed. For the limitations on some of the fields, see [considerations and limitations of customizable fields](#considerations-and-limitations-of-app-customization).

   :::image type="content" source="media/customize-settings.png" alt-text="The screenshot displays name and description on the customize user interface.":::

1. After customizing the app, select **Apply**. To verify the changes that you've made, see [preview app details](#preview-app-customizations). To undo the changes, see [reset app details to default values](#reset-app-details-to-default-values).

1. Select **Publish** to publish the customized app to your organization's store.

The app is listed in the **Manage apps** page and in Teams store and client (available via web, mobile, or desktop client) with the updated details. The modification may take a few hours to display.

## Preview app customizations

To view the changes after saving the customizations, view the app details page.

1. Sign in to the Teams admin center and access **Teams apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)**.

1. To open the app details page, select the app name.

1. View the app details, including the original app name in the field **Short name from publisher**. The field is only visible if you've changed the app's short name.

   :::image type="content" source="media/original-app-version.png" alt-text="The screenshot shows modified short name of an app.":::

After a few hours, your Teams users can see the customized app in the Teams store in their client (web, mobile, and desktop).

   :::image type="content" source="media/contoso-app.png" alt-text="The screenshot shows a customized app in Teams client.":::

## Considerations and limitations of app customization

Consider the following details about app customization functionality:

* You can only customize [third-party apps](deploy-apps-microsoft-teams-landing-page.md#third-party-apps-validated-by-microsoft) and not [custom apps](deploy-apps-microsoft-teams-landing-page.md#custom-apps).

* You can't customize any app in Government Community Cloud High (GCCH) and Department of Defense (DoD) environments.

* An app can be customized only if the app developer allows it.

* Modifications to any apps are available only within your organization.

* You'll have only one version of the app, since customizing the app details doesn't create a copy of the app.

* When you customize apps and any description related to an app, ensure that you follow the guidelines that app developer provide in their documentation, or terms of use. Adhere to the copyright laws when using any third-party images.

* Admin-provided customization data is stored in the nearest data storage region.

* You're responsible to ensure that links to terms of use or privacy policy are valid.

* In case the app developer no longer allows a field to be customizable, a message appears on the app details page notifying the admin about such a field. Any changes made to the field are reverted to the original value.

* We recommend testing app customization changes in a Teams test tenant before making these changes in your production environment. To get a test tenant, follow the instructions at [create your test tenant](/microsoftteams/platform/concepts/build-and-test/prepare-your-o365-tenant).

* Updates take up to 24 hours to show in the client for all the users and admin accounts.

* For an existing app to become customizable, the developer can provide a new version of the app on the Teams store.

* The [app usage report](teams-analytics-and-reports/app-usage-report.md) displays the original name of the app that is provided by the publisher, even if the customized app is used by end-users.

* The Microsoft Graph permission consent dialog displays the original name of the app that is provided by the publisher. It helps you to accurately identify an app while providing permissions to it.

* Customizing an app doesn't change any app functionality.

The limitations on some of the customizable fields are below:

| Customizable field | Consideration |
|:---|:---|
| Any URL fields | Ensure valid and secure URLs using `https`. |
| Short description | The short description must be under 80 characters. Don't repeat what's in the full description. |
| Icon | Transparent outline icon in PNG format that is 32x32 pixel in resolution. |
| Color icon | Full-color icon in PNG format that is 192x192 pixel in resolution. |
| Accent color | Color must match your icon background. |

## Troubleshoot app customization

| Errors and issues | Possible fix or understanding of the issue |
| --- | --- |
| My updates aren't available to my end-users. | Wait a few hours for changes to propagate. |
| I can't customize an app. | Cross-check if the [app is customizable or not](#verify-if-an-app-is-customizable).|
| I started to customize an app but can't save or apply my changes. | Adhere to the limitations of the fields. Look for errors on the UI and the [limitations of app customization](#considerations-and-limitations-of-app-customization) |
| Manage apps page not loading properly. List of apps is not displayed. | Admin account in use must have the Teams license assigned. |

<!--- Check ICM for error string. --->

## Reset app details to default values

You can reset the app details to the original values provided by the app developer. The option is only available for app that you customize.

1. In Teams admin center, access **Teams Apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)**.

1. To open the app details page, select the app name.

1. From the **Actions** menu, select **Reset to default**.

   :::image type="content" source="media/reset-app-customization.png" alt-text="The screenshot shows the reset to default option for a customized app.":::

## Related articles

* [Customize your organization's app store](customize-your-app-store.md)
* [Rebrand your apps community post](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/rebrand-apps-to-your-own-organization-s-branding-with-app/ba-p/2376296)
