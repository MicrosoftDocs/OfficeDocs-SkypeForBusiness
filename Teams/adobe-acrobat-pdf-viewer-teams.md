---
title: Adobe Acrobat as a default PDF viewer in Teams
author: ashishguptaiitb
ms.author: guptaashish
manager: prkosh
ms.topic: article
ms.service: msteams
audience: admin
ms.subservice: teams-apps
ms.date: 09/09/2024
ms.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
ms.reviewer: mbmanoj
search.appverid: 
f1keywords: 
description: Learn how to set Adobe Acrobat as a default PDF viewer to view and edit PDF files in Microsoft Teams.
appliesto: 
- Microsoft Teams
ms.localizationpriority: medium
---

# Set Adobe Acrobat as the default PDF viewer in Microsoft Teams

> [!NOTE]
> This feature is available only for the Commercial environments and not for GCC, GCC(H), and DoD environments.

As an admin, you can set Adobe Acrobat as the default app to view and edit PDF files in Microsoft Teams. Your users can view and search the PDF files. The users can also comment on and annotate the PDF files for free after they sign in.

To configure Adobe Acrobat app as the default handler for PDF files in your tenant, complete the following steps as prerequisites:

* [Allow Adobe Acrobat app](#allow-adobe-acrobat-app-in-your-tenant).
* [Install Adobe Acrobat app](#install-adobe-acrobat-app-for-all-users).

## Allow Adobe Acrobat app in your tenant

To set up the app as a default PDF viewer, [allow third-party apps in your tenant](manage-apps.md#manage-org-wide-app-settings) and then follow these steps:

1. Sign in to Teams admin center and access **Teams app** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)**.

1. Search for the Adobe Acrobat app and select it. It opens the app details page.

1. Select the **Permissions** tab and then select **Review permission**.

   :::image type="content" source="media/permission-policy.png" alt-text="Screenshot of app permission in Teams admin center." lightbox="media/teams-app-adobe-acrobat-permission.png":::

1. Select **Accept**.

## Install Adobe Acrobat app for all users

To assign and make the Adobe Acrobat app available for all users, follow these steps:

1. In Teams admin center, go to **Teams app** > [**Setup policies**](https://admin.teams.microsoft.com/policies/app-setup).

1. Under **Manage policies** tab, select **Global (Org-wide default)**, and then select **Edit**.

   :::image type="content" source="media/setup-policies.png" alt-text="Screenshot of setup policies for Adobe Acrobat app in Teams admin center.":::

1. Under Installed apps, select **Add apps**.

1. Search **Adobe Acrobat**, select **Add** next to the app name and then select **Add**.

   :::image type="content" source="media/add-adobe-acrobat.png" alt-text="Screenshot that shows how to add Adobe Acrobat app for all users." lightbox="media/add-adobe-acrobat-app.png":::

1. Select **Save**.

1. Optionally, you can allow SSO with Microsoft Entra identity if you own a license of Adobe Acrobat. We recommend configuring SSO using the instructions available at [Set up identity and single sign-on](https://helpx.adobe.com/enterprise/using/set-up-identity.html).

After you complete the configuration, Teams uses Adobe Acrobat app as the default file handler for PDF files.

To selectively allow the Adobe Acrobat app for a few individuals or for a group, use [app permission policies](teams-app-permission-policies.md).

## Considerations and limitations

Know the following information about this functionality:

* After the policy is set up, it typically [takes a few hours](teams-app-setup-policies.md#considerations-and-limitations) for the app to be available for users.
* The PDF files that are pinned as tabs in channels and the PDF files available in the Assignments app continue to open in the native viewer of Teams and not in the Adobe Acrobat app.
* Adobe Acrobat as a default PDF viewer in Teams works only on desktop and web clients. It isn't supported on the mobile client.
* Users need an Adobe Acrobat plan to use the premium tools such as Export PDF, Organize Pages, Combine Files, Compress PDF, and Protect PDF.
* To uninstall the app, users can remove the app from their Teams client. Admin can remove the Adobe Acrobat app using setup policy.
* If you block Adobe Acrobat app, then remove the app from the setup policy. It ensures that the user experience reverts to using the native PDF file viewer.
* If you face any issues to sign in to the Adobe Acrobat app in the Teams desktop client, then use [Teams in browser](https://teams.microsoft.com/) to sign in.
* Sign-in to a free [Adobe account](https://acrobat.adobe.com/us/en/) to comment or annotate on the PDF files. The app in Teams can offer functionality such as annotating, organizing, compressing, and protecting PDF files. For a complete list of functionality and the prerequisites, see [Manage PDF files in Teams with Acrobat app](https://www.adobe.com/content/dam/dx-dc/pdf/ue/acrobat-msft-teams-feature-comp-ue.pdf).
* When you collaborate on a PDF document, it's temporarily stored (for up to 24 hours) on the Adobe servers in the region in which you're located. This temporary storage is to facilitate transient processing. Your documents are encrypted end-to-end when being transferred from your local filesystem to the server and remain encrypted on the server as well. See [security for Acrobat](https://aka.ms/Adobe_Acrobat_Security).
* Once Adobe Acrobat is made the default PDF file handler, then PDF files clicked inside Teams will open inside Teams. Users can't open PDF files in their desktop app using any setting.
