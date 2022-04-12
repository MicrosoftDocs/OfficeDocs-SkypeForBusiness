---
title: Overview of app certification by Microsoft
ms.reviewer: 
description: Understand the app attestation and certification programs for Teams apps.
ms.topic: article
author: guptaashish
ms.author: guptaashish
manager: prkosh
audience: admin
ms.date: 04/05/2022
ms.service: msteams
ms.collection: 
  - M365-collaboration
f1.keywords:
- NOCSH
ms.localizationpriority: high
search.appverid: MET150
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
---
# Microsoft 365 app compliance program for security, compliance, and privacy of third-party apps

Microsoft compliance program demonstrates that an app is vetted against controls derived from leading industry standard frameworks, and that strong security and compliance practices are in place to protect customer data. The program has two phases:

* Publisher attestation.
* Microsoft 365 certification.

## Publisher attestation

Publisher attestation is the next tier in the app compliance program. Publisher attested apps provide added confidence to admins about security and compliance measures of an app and reduce the time to review it for an app. The attestation will reflect an app's security, data handling, and compliance practices against more than 80 risk factors identified by [Microsoft Cloud App Security](https://www.microsoft.com/microsoft-365/enterprise-mobility-security/cloud-app-security).

App developers are asked to complete a self-assessment that includes questions frequently asked by customers and IT admins to evaluate the security and compliance of an app. Microsoft then publishes this information for easier and more timely evaluation. To know more, see [Attestation guide](/microsoft-365-app-certification/docs/enterprise-app-attestation-guide).

Admins can quickly check for Published attested apps in three different ways.

* On the web, when gathering more information about an app, see the details of a specific app at its link at [Microsoft Teams apps security and compliance](/microsoft-365-app-certification/teams/teams-apps). Alternately, click the Publisher attestation link in Teams admin center.

  :::image type="content" source="media/attested-app-tac3.png" alt-text="In Teams admin center, click Publisher attestation link to view details of the attestation of an app":::

* In Teams admin center, when checking the details of an app from the **Manage App** page, see the publisher attested icon on the banner in the app's detail page.

  :::image type="content" source="media/attested-app-tac1.png" alt-text="In Teams admin center, Publisher attested icon is displayed on all attested apps.":::

* In Teams admin center, when granting permissions to the app, a blue checkmark in front of the app name indicates that it is either a publisher attested app or a Microsoft 365 certified app.

   :::image type="content" source="media/attested-app-tac2.png" alt-text="In Teams admin center, on the dialog to grant permissions, admins can check the blue checkmark to be assured that the app is publisher attested.":::

The attestation details page for an attested or certified app lists the following details.

:::image type="content" source="media/attested-app-doc-details.png" alt-text="Topics on which detailed information is provided for attested apps.":::

## Microsoft 365 certification

App certification is achieved through a qualified analyst's review and approval of a comprehensive assessment centering on an app's security and compliance frameworks, processes, and procedures. The app is vetted against a series of security controls derived from leading industry standard frameworks.

The certificate demonstrates that strong security and compliance practices are in place to protect customer data when the app is activated in an organization. More information about how Microsoft 365 certification is useful for admins and end-users is available at Overview of [Microsoft 365 app compliance program](/microsoft-365-app-certification/docs/enterprise-app-certification-guide).

Administrators can quickly check for Microsoft 365 certified apps in the following ways.

* When gathering more information about an app on the web, see the shield icon in list of apps in  Microsoft Teams apps security and compliance documentation or see the same icon in the app-specific documentation page.

  :::image type="content" source="media/attested-app-doc-details.png" alt-text="View the Microsoft 365 certification information in the detailed help article about security and compliance of an app.":::

* When checking an application in Teams admin center, sort the list of apps using the Certification column. See the icon and optionally, click the link to access the app-specific page mentioned above.

  :::image type="content" source="media/m365cert-apps-list1.png" alt-text="View Microsoft 365 certification status of an app in the Teams admin center." lightbox="media/m365cert-apps-list2.png":::

* When viewing the details of an app, see the Microsoft 365 certified icon in the app banner.

  :::image type="content" source="media/m365cert-app-details-banner.png" alt-text="View Microsoft 365 certification information in the app banner when managing a specific app in Teams admin center":::

* In Teams admin center, when granting permissions to the app, a blue checkmark in front of the app name indicates that it is either a publisher attested app or a Microsoft 365 certified app.

   :::image type="content" source="media/attested-app-tac2.png" alt-text="In Teams admin center, on the dialog to grant permissions, admins can check the blue checkmark to be assured that the app is Microsoft 365 certified.":::

## Know details of third-party apps

As an admin, you can view information related to security, compliance, privacy, and more about any third-party apps.

### View security, compliance, and privacy information in Microsoft documentation

For an attested or certified app, the details about security, privacy, compliance, and more for each app, are listed at the app-specific help articles linked from [Microsoft Teams apps security and compliance](/microsoft-365-app-certification/teams/teams-apps).

:::image type="content" source="media/attested-app-doc-details.png" alt-text="Topics on which detailed information is provided for apps that undergo Microsoft compliance program.":::

### View the granted Graph permissions in Azure Portal

Admins can grant permission to an app on behalf of all organization users. It helps avoid each user to individually request the permissions. Permissions granted of an admin are called delegated permissions in [Azure Portal](https://aad.portal.azure.com/).

Before you grant any permission to an app, review a list of requested permissions in the [Manage Apps](https://admin.teams.microsoft.com/policies/manage-apps) section of Teams admin center.

:::image type="content" source="media/attested-app-tac2.png" alt-text="In Teams admin center, on the dialog to grant permissions, admins can check the permissions requested by an app.":::

After admins grant the org-wide permissions to an app, they can review the Graph permissions in Azure Portal.

:::image type="content" source="media/tac-perms-in-aad-after-granting1.png" alt-text="Admins can see all the app permissions granted by users and admins in the Azure Portal." lightbox="media/tac-perms-in-aad-after-granting2.png":::

### View privacy policy and terms of use of an app

In Teams admin center, each app detail page contains a link to the privacy statement and terms of use by the app publisher.

:::image type="content" source="media/tac-app-tou-privacy-info1.png" alt-text="From Teams admin center, admins can access the link to the privacy policy and terms of use for every app." lightbox="media/tac-app-tou-privacy-info2.png":::

<!--- TBD: Parking some content for later review. Check if this content needs to be published.

We also have a few more quality and security checks for apps. We have launched Microsoft Cloud App Security (MCAS) program for the customer who have E5 or EMS license, where we rate risk for your cloud apps based on regulatory certification, industry standards, and best practices. We are also working on an Apps Quality Score system (launching soon) for all apps on Teams platform, and you will be able to check an app’s quality score quickly on Teams Store.

--->

<!--- TBD: Add related links later.

## See also

* []().
* []().
--->
