---
title: User requests for admins to allow apps
author: ashishguptaiitb
ms.author: guptaashish
manager: prkosh
ms.topic: article
ms.service: msteams
ms.subservice: teams-apps
audience: admin
ms.collection: 
  - M365-collaboration
  - m365-frontline
ms.reviewer: mhayrapetyan
search.appverid: MET150
f1keywords: 
  - ms.teamsadmincenter.manageapps.overview
description: Learn how to manage and configure end-user request to allow the apps that are blocked in an organization.
appliesto: 
- Microsoft Teams
ms.localizationpriority: high
---
# Manage user requests

The apps that you block in your organization may affect end-user productivity and collaboration. Apps that are available in Teams store but are blocked in your organization can't be used by the end-users. However, to stay informed, the end-users can view blocked apps, view app's information, and the use cases it servers. Users can request admin approval so that they can use these apps in Teams, after you evaluate the request.

This functionality provides you with a signal about the demand for an app within your organization. You can easily view the aggregate number of requests for apps and make informed decisions about which apps to consider allowing in your organization.

You retain complete control of the apps that are allowed or blocked for users. If you choose to allow an app, the controls and UI to manage apps remain the same.

* The default option sends the user requests in Teams admin center where you can [view user requests and allow the requested apps](#view-user-requests-and-allow-the-requested-apps).

   :::image type="content" source="media/user-request-blocked-apps.png" alt-text="Screenshot showing the option to request an admin to approve a blocked app.":::

* A customization lets you [configure end-user experience](#modify-the-default-setting-to-receive-end-user-requests) that is best suited for your organization. You can provide a custom instruction that is displayed to the end-users on blocked apps in the Teams app store and direct the users to an internal site to collect their requests.

   :::image type="content" source="media/user-request-blocked-apps-redirected.png" alt-text="Screenshot showing the end-user experience for apps in store when an admin redirects the allow app request URL to a internal site.":::

## Modify the default setting to receive end-user requests

To configure a custom message and redirect users to an org-specific URL to request app approval, follow these steps:

1. Sign into the Teams admin center and access the **Teams apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)** page.

1. Select Org-wide app settings.

1. To display a custom message or instruction in Teams client store, provide a text message in User requests configuration.

1. To provide an org-specific URL to collect user requests, do the following:

   1. Change Redirect requests to external tool option to On.
   1. Provide your org-specific, custom URL.

      :::image type="content" source="media/user-request-config-org-wide-setting.png" alt-text="Screenshot to toggle the customization of URL for the user request to unblock app in the org-wide settings UI.":::

1. Select **Save**.

## View user requests

The end-user requests received by the default method are displayed in Teams admin center. You can easily view and manage the requests. We recommend having a regular triage to check for end-user requests. To view and allow the apps, follow these steps:

1. Sign into the Teams admin center and access the **Teams apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)** page.

1. Choose to display the **Requests by users** column. You can sort the column, as well.

   :::image type="content" source="media/user-requests-tac.png" alt-text="Screenshot showing the column for user requests in Teams admin center and that it can be sorted." lightbox="media/user-requests-tac-expanded.png":::

1. To open the app details page that you want to allow, select the name of the app.

1. Select **Manage requests**.

   :::image type="content" source="media/apps-manage-user-requests.png" alt-text="Screenshot showing the manage requests option on the app details page." lightbox="media/apps-manage-user-requests-expanded.png":::

1. Follow one or more of the following steps as displayed in the popup dialog. The steps to approve an app vary based on the method used to block it.

   * If the app is blocked using permission policies, [modify the permission policies](teams-app-permission-policies.md).
   * If the app is blocked for all users, [allow the app](manage-apps.md#allow-and-block-apps).
   * If all apps are blocked for all users, [modify org-wide settings](manage-apps.md#manage-org-wide-app-settings).

1. Optionally, to switch to a custom configuration to your org-specific URL, select Configure user requests link on the Manage user requests dialog. It opens the Org-wide app settings pane in which you can [configure the end-user request experience](#modify-the-default-setting-to-receive-end-user-requests-to-allow-an-app).

If you allow an app after receiving requests in Teams admin center, then Teams doesn't inform the end-user that their request is acted upon. The user can check the app in the Teams Store to check if the app is allowed. The option to Add the app is available for the user after you allow it. If you allow an app after receiving requests via your org-specific method, your internal mechanisms to provide status update to the end-user applies.

To reset the number of app requests to zero, dismiss the requests. Just allowing an app doesn't reset its request counter to zero.

## Dismiss user requests

To dismiss the requests to allow app, follow these steps:

1. Select the name of the app for which you want to dismiss the user requests.
1. Select **Manage requests** and select **Dismiss all requests** on the dialog box.

   :::image type="content" source="media/dismiss-user-requests-apps.png" alt-text="Admins can approve a user request by allowing an app or dismiss the request and not take any action.":::​

If you dismiss a request, it doesn't inform the end-user that their request is acted upon. When you dismiss a request to allow an app, the requests count in the admin center resets to zero. Also, after a few hours of you dismissing a request, end-users can again request the same app to be allowed.

## Related article

* [Overview of how to manage third-party apps](manage-apps.md).
