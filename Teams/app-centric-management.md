---
title: App centric management to govern app access
author: ashishguptaiitb
ms.author: guptaashish
manager: prkosh
ms.topic: conceptual
audience: admin
ms.service: msteams
ms.subservice: teams-apps
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - M365-collaboration
  - Tier1
search.appverid: MET150
ms.reviewer: 
ms.date: 10/17/2023
ms.reviewer: mhayrapetyan
description: Govern Teams apps using app centric management instead of permissions policies.
f1.keywords:
- NOCSH
ms.localizationpriority: medium
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
---

# Use app centric management to govern apps

The new app centric management feature let admins define who in the tenant can install Teams apps, with the granularity of users and groups. This feature evolves the existing app permission policies and org-wide app settings for third-party apps. It provides admins with the ability to manage access to the app individually. The app permission policies for existing customers are migrated to maintain existing app availability in the tenant.

## What changes with this feature

Currently, three settings determine the ability of a user to add an app. These settings are app permission policy applied to a user, allow or block settings for an app, and an org-wide setting for third-party apps for the tenant. App centric management feature simplifies these settings by having each app define who can use the app. When defining app assignments, admins have the following three options to choose from:

* **Everyone in the organization**: Anyone in the tenant can add and use the app.
* **Specific users or groups**: Only the selected users and groups can use the app. The supported group types are Security, Microsoft 365, Dynamic, and Distributed Lists (DLs).
* **No one**: Nobody in the organization can use the app. Any existing users lose access to the app.

The default value of app assignment is Everyone in the organization. Admins can change the default value to no one. During private preview, this is achieved by modifying the org-wide setting for new third-party apps and will apply to Microsoft and custom apps. This means that if the setting for new third-party apps is checked, new Microsoft, custom and third-party apps will continue to enter the catalog with `everyone` assignment type; if it is unchecked, the new apps will enter the catalog with “no one” assignment type.

## Onboard to the new app management feature with four easy steps

When you participate in the private preview program, you must migrate your tenant from policy-based management to App centric management. Admin center provides a step-by-step migration and a method to check your migration information.

Before you get onboard to use this feature, consider the following:

* Before proceeding with the migration, determine which apps must be assigned to which groups or users.
* During migration, you cannot change org-wide app settings or existing policies. To make any changes to the existing policies or settings during migration, you can stop the migration process and reset the migration.
* During the preview program, app assignments have an upper limit of 2000 assignments for each app. Users and groups are both counted towards this limit.
* Migration can take up to 72 hours to complete. During the migration, access to apps for users is governed by the existing permission policies and tenant settings.
* App assignment changes become effective within 72 hours.

Once your tenant is enabled for app centric management feature, the Manage apps page displays a welcome message and a prompt to migrate.

The migration process uses a dialog-based UI that guides you through the following steps:

1. [Select policies to migrate](#step1-start-the-migration-and-select-policies-to-migrate)
1. [Assign and block apps](#step2-assign-and-block-apps)
1. [Validate assignments](#step3-validate-assignments)
1. [Finalize the migration](#step4-finalize-the-migration)

<!---
1. [Tenant preparation for large tenants](#step5-preparation-for-large-tenants)
--->

### Step1: Start the migration and select policies to migrate

On the **Select app permission policies** page, the Global (Org-wide default) policy is selected by default. You must select the custom policies you want to migrate in addition to the Global (Org-wide default). The apps in the selected policies are checked against org-wide app settings to create a list of allowed and blocked apps. This process can take a few minutes.

1. Access Teams admin center and open **Teams Apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)** page.

1. Select **Actions** > **Switch to manage access by app** in the upper-right corner.

   :::image type="content" source="media/migration-start.png" alt-text="Screenshot showing how to start a migration to app centric management functionality." lightbox="media/migration-start-large.png":::

1. Select the custom policies that you want to migrate. You can choose to select just a few policies and not migrate all your existing policies to app assignments. Select **Next**.

   :::image type="content" source="media/select-policies-migrate.png" alt-text="Screenshot showing how to select permission policies to migrate.":::

The **Global (Org-wide default) policy** is always migrated. An unused permission policy that isn’t assigned to any user can’t be migrated.

### Step2: Assign and block apps

Based on the policies you select to migrate and based on your org-wide app settings, three tabs of apps are populated in this step.

* **Allowed org-wide**: List of apps that are allowed for everyone in your organization.
* **Allowed for users and groups**: List of apps based on the differences between the selected policies. To move to the next step, you must manually provide the assignments to the apps displayed under this tab.
* **Blocked apps**: List of apps that are unavailable for all users.

:::image type="content" source="media/assign-block-apps.png" alt-text="Screenshot showing the three tabs available for app assignments to everyone, to some users and group, or to no one.":::

To proceed, make assignments for the list of presented apps. You can’t do bulk assignments for apps in the private preview program.

#### Allow everyone to use an app

To assign an app to everyone, follow these steps:

1. Search and select an app from one of tabs and select **Manage access**. To filter apps before searching, consider using the filter option.

   :::image type="content" source="media/acm-filter-search-apps.png" alt-text="Screenshot to show filtering and searching of apps to create app assignments.":::

1. Under **Who can access the app**, select **Everyone in the organization** and select **Save**.

   :::image type="content" source="media/acm-user-group-everyone.png" alt-text="Screenshot showing how to create app assignment for everyone in the organization.":::

#### Assign an app to users and groups

You can assign an app to some users and groups. To assign, follow the steps below.

1. Search and select an app from one of tabs and select **Manage access**. To filter apps before searching, consider using the filter option.

1. Under **Who can access the app**, select **Specific users and groups**.

   :::image type="content" source="media/acm-specific-user-group.png" alt-text="Screenshot showing how to create app assignment for a few selected users and groups.":::

1. Select **Assigned users** tab and **Add a user** or select **Assigned groups** tab and select **Add a group**.

1. Search and select the name of a user or a group. Select **Save**.

   :::image type="content" source="media/acm-specific-user-group2.png" alt-text="Screenshot showing users and groups to create app assignments for selected users and groups.":::

1. Select **Next** to proceed with the migration.

#### Block everyone from using an app

To block an app for all your users, follow these steps:

1. Search and select an app from one of tabs and select **Manage access**. To filter apps before searching, consider using the filter option.
1. Under the **Who can access the app** menu, select No one and select **Save**.

   :::image type="content" source="media/acm-access-noone.png" alt-text="Screenshot showing how to create app assignments for no one in the organization.":::

#### Reset the migration

During the migration, you can do either of the following:

* Select **Close** to leave the dialog and return to it later. Admin center automatically saves a draft of the migration progress and you can continue it later. You can’t edit or add permission policies if you have a drafted migration.
* Select **Reset all changes** to discard the progress and discard the draft. Removing migration draft lets you edit or add permission policies and you can restart migration process later.

   :::image type="content" source="media/acm-migration-reset.png" alt-text="Screenshot showing the option to reset the migration progress.":::

### Step3: Validate assignments

Before you finalize the migration, you can validate the migration by testing it in the following two ways. The validation ensures that you’ve assigned the app to the right users or groups before completing the migration process.

* **Test by app**: Select an app and verify the list of all users who will get access to it. Verify all three types of assignments for each app, one app at a time.

   :::image type="content" source="media/acm-test-app.png" alt-text="Screenshot showing validation step in which admin can check the policies assigned to each user.":::

* **Test by user**: Select one user at a time and verify the list of apps that the user will get access to.
If the selected user is not permitted to use any apps, admin center displays, **This user can’t access any apps**.

   :::image type="content" source="media/acm-test-user.png" alt-text="Screenshot showing validation step in which admin can check the app access of each user.":::

If you want to change any assignments, select **Back** and change the assignments.

### Step4: Finalize the migration

After you complete the app assignments and validate those, select **Finish**. Select the check box to agree to the terms and conditions, and then select **Continue** to complete the migration process.

:::image type="content" source="media/acm-confirmation-post-validation.png" alt-text="Screenshot showing the final prompt in the migration step to finalize the change.":::

<!---
### Step5: Preparation for large tenants

For large production tenants with more than 10,000 users, the migration process includes an additional step called, the ‘tenant warm-up’, that is performed right after the migration. Microsoft completes this step in the background and requires admin participation.

During the tenant warm-up we will place your tenant back on permission policy for up to 2 weeks and the app centric management experience will not be available in the UI. The tenant continues to work on the existing app permission policies without disruption for the users.

Once the tenant is ready, we’ll contact you. We’ll make app centric management functionality available with the app assignments you configured during the migration.

--->

## Manage apps after the migration

Once your tenant is migrated, you can manage the apps in Teams admin center by assigning apps from Manage apps, App details and User details pages.

### View and modify access to an app

To modify access to an app, follow these steps:

1. In Teams admin center, go to the **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)** page, search for the required app, and select the app name to open its app details page.
1. Select the **Assignments** tab.
1. To assign a new user or a group, follow these steps:

   1. Select **Manage access** or **Assign**.
   1. Select the required option from **Manage who can install this app** menu.

    :::image type="content" source="media/acm-add-modify-access.png" alt-text="Screenshot showing how to create app assignments from the app details page after the migration.":::

   1. Search and select a user or a group from the **Add users and groups** field. Select **Apply**.

    :::image type="content" source="media/acm-add-modify-access-group.png" alt-text="Screenshot showing how to create an app assignment for selected users and groups from the app details page.":::

1. To remove one or more users or groups from an app, select the rows, and select **Remove**.

### Set default behavior for new apps published in Teams store

To control the default assignment of the new apps that are added to Teams store, use the **New third-party apps published to the store** option in the org-wide app settings.

:::image type="content" source="media/org-wide-third-party-apps.png" alt-text="Screenshot showing third-party settings for new store apps in the org-wide app setting in admin center.":::

* To make new apps available to everyone, set the option on.
* To make new apps available to no one, set the option off.

### View app access for a user

On the **[Manage users](https://admin.teams.microsoft.com/users)** page, select a user, and select **Apps** tab. The tab lists the apps that the user has access to. To easily locate the type of access for an app, you can search for the name of the app.

:::image type="content" source="media/acm-manage-user-apps-tab.png" alt-text="Screenshot showing how to view all the apps that a user has access to, from the Manage users page.":::

### Modify app assignments for a specific user

On the **[Manage users](https://admin.teams.microsoft.com/users)** page, select a user, and select **Apps** tab. The tab lists the apps that the user has access to. Select the row for an app and select **Remove**.

> [!NOTE]
> You can’t remove assignments for a user from Manage users page, if the app is available to everyone or to a group in the organization.

## Limitations and troubleshooting

Consider the following limitations about the functionality:

* You can’t migrate a policy but only an entire tenant. During migration you can choose some policies and ignore the others, but migration is of the complete tenant.
* You can request migration of a test tenant before you migrate your production tenant.
* While the migration is in progress, you can’t modify third-party app settings and policies.

   :::image type="content" source="{source}" alt-text="Screenshot showing that org-wide app settings can't be changed if a migration progress is drafted.":::

* During the private preview program, PowerShell commands or APIs are not available for the above use cases. If you are interested in these methods, indicate your interest in your feedback.
* Bulk operations on multiple apps aren’t supported during the private preview but will be available closer to the general availability.
* You can’t export the app assignments outside the Teams admin center.
* App assignments are limited to 2000 users and groups.
* Nested groups are not supported.

Consider the following tips to troubleshoot any issues that you may encounter during the migration:

* To roll back a migrated tenant, contact Microsoft support.
* App assignments to specific users and groups currently allow guest users to be individually assigned. While this is displays as assigned, only the apps that are allowed for the entire org users are actually available to the guest users.
* If the expected changes are not implemented consider waiting up to 72 hours for app assignments to take effect.
* During the migration, if you see too many apps in the **Allowed for users and groups** tab awaiting admin inputs, then consider checking your permission policies. The selected policies have opposite assignments for these apps in your tenant.
* To block new apps for everyone, see [Set default behavior for new apps published in Teams store](#set-default-behavior-for-new-apps-published-in-teams-store).

<!---
## Related articles

* []()
* []()
* []()
--->
