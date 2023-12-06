---
title: User requests for admins
author: ashishguptaiitb
ms.author: guptaashish
manager: prkosh
ms.topic: how-to
ms.service: msteams
ms.subservice: teams-apps
audience: admin
ms.date: 12/07/2023
ms.collection: 
  - M365-collaboration
  - tier2
  - highpri
ms.reviewer: mhayrapetyan
search.appverid: MET150
f1keywords: 
  - ms.teamsadmincenter.manageapps.overview
description: Learn how to manage and configure user request for approval of the apps that are blocked in an organization.
appliesto: 
- Microsoft Teams
ms.localizationpriority: high
---
# Manage user requests

The apps that are blocked in your organization may affect user productivity and collaboration. Users can't use blocked apps but view such apps and their information in the Teams store, and request approval from admins. After you evaluate the request, you may choose to allow an app or dismiss the request.

This functionality provides you with a signal about the demand for an app within your organization. You can easily view the aggregate number of requests for each requested app. It helps you make an informed decision about which apps to evaluate for allowing.

Users can view all the available apps, including the blocked apps. You can't hide blocked apps, but you retain complete control of the apps that users can or can't use. If you choose to allow an app, the controls and user interface to manage apps remain the same.

* The default option sends the user requests to Teams admin center where you can [view user requests](#view-user-requests-in-teams-admin-center) and [allow the requested apps](#act-on-the-user-requests).

   :::image type="content" source="media/user-request-blocked-apps.png" alt-text="Screenshot showing the option to request an admin to approve a blocked app.":::

* A customization lets you [configure user experience](#modify-the-default-setting-to-receive-user-requests-on-your-custom-webpage) that is best suited for your organization. You can provide an instruction or a custom message that is displayed in the Teams app store and the request approval option directs the users to an org-specific URL to collect their requests.

   :::image type="content" source="media/user-request-blocked-apps-redirected.png" alt-text="Screenshot showing the user experience for apps in store when an admin redirects the allow app request URL to an org-specific URL.":::

>[!NOTE]
> The feature isn't supported in Government Community Cloud (GCC), GCC-High, and Department of Defense (DoD) tenants. It isn't supported for custom apps.

## View user requests in Teams admin center

You can view the requests to allow blocked apps in the following UIs:

* For a quick view of the up to three most requested apps, see the notification in the [Teams admin center dashboard](https://admin.teams.microsoft.com/dashboard).

   :::image type="content" source="media/tac-dashboard-user-requests.png" alt-text="Screenshot showing the user request review option on the admin center dashboard." lightbox="media/tac-dashboard-user-requests-large.png":::

* For the number of requests received for each app, see the [Manage apps page](https://admin.teams.microsoft.com/policies/manage-apps?category=userAppRequest). You can sort the `Requests by users` column.

   :::image type="content" source="media/user-requests-tac.png" alt-text="Screenshot showing the column for user requests in Teams admin center and that it can be sorted." lightbox="media/user-requests-tac-expanded.png":::

* For a detailed list of requesters for each app, see the `User requests` tab in the app details page.

   :::image type="content" source="media/user-requests-tab.png" alt-text="Screenshot showing the user requests tab in the app details page and the admin actions needed to allow an app.":::

We recommend a regular triage to check for user requests. To view and manage the requests and to allow a requested app, follow these steps:

1. Sign into the Teams admin center and go to **Teams apps** > [**Manage apps**](https://admin.teams.microsoft.com/policies/manage-apps).

1. Choose to display the **Requests by users** column if the Manage apps page doesn't display it. You can sort the column.

1. To view details of the requests of a specific app, use any one of the following methods:

   * Select **Review** on the admin center dashboard.
   * Click the number of requests that the column displays.
   * Open the app details page from the Manage apps page and select the **User requests** tab.





## Act on the user requests

You can contact the users who request an app via email or you can allow the app. To allow an app:

1. Sign into the Teams admin center and go to **Teams apps** > [**Manage apps**](https://admin.teams.microsoft.com/policies/manage-apps).

1. Open the app details page for the requested app.

1. Select **Manage requests**.

   :::image type="content" source="media/apps-manage-user-requests.png" alt-text="Screenshot showing the manage requests option on the app details page." lightbox="media/apps-manage-user-requests-expanded.png":::

1. Follow one or more of the following steps that the pop-up dialog displays. The steps to approve an app vary based on the method used to block it and only the relevant steps are displayed.

   * If the app is blocked using permission policies, [modify the permission policies](teams-app-permission-policies.md).
   * If the app is blocked for all users, [allow the app](manage-apps.md#allow-or-block-apps).
   * If all apps are blocked for all users, [modify org-wide settings](manage-apps.md#manage-org-wide-app-settings).

Users can view the **Add** option for an app in the Teams store to check if the app is allowed. If you allow an app, Teams doesn't inform the users that their request is acted upon. When you allow an app, the request counter isn't reset to zero.









## Modify the default setting to receive user requests on your custom webpage

Teams provides a default message for users to request approval to an app. You can modify the default setting to add a custom message with instructions, org-specific URL, or both. The modifications are displayed for each app in Teams store.

To configure a custom message and redirect users to an org-specific URL, follow the steps:

1. Sign into the Teams admin center and go to **Teams apps** > [**Manage apps**](https://admin.teams.microsoft.com/policies/manage-apps).

1. At the upper-right corner, select **Org-wide app settings**.

1. To display a custom message or instruction in Teams store, enter a text message in text field under **User requests configuration**. The field has a limit of 300 characters.

1. To provide an org-specific URL to collect user requests, follow the steps:

   1. Turn on the **Redirect requests to external link** toggle.
   1. Provide your org-specific URL.

      :::image type="content" source="media/user-request-config-org-wide-setting.png" alt-text="Screenshot to toggle the customization of URL for the user requests in the org-wide settings UI.":::

1. Select **Save**.

If you choose to do so, the methods to evaluate third-party apps and allow the requested apps remain the same.






## Dismiss user requests

To dismiss the requests, follow the steps:

1. Select the name of the app for which you want to dismiss the user requests.
1. Select **Manage requests**.
1. In the Manage user requests dialog, select **Dismiss all requests**.

   :::image type="content" source="media/dismiss-user-requests-apps.png" alt-text="Admins can approve a user request by allowing an app or dismiss the request and not take any action.":::

When you dismiss requests for an app, the following happens:

* You can't view the name and email or the requesters.
* Teams doesn't inform the requesters that their request is acted upon.
* Requests count in the admin center resets to zero.
* Users can again request the same app to be allowed, after a few hours of you dismissing requests.

## Related article

* [Overview of how to manage third-party apps](manage-apps.md)
