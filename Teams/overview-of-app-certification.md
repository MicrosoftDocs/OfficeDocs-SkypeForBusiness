---
title: Overview of app certification by Microsoft
description: Learn about the Microsoft 365 app compliance program for security, compliance, and privacy of third-party apps.
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

Microsoft compliance program checks and audits an app against controls that are derived from leading industry-standard frameworks. The program demonstrates that strong security and compliance practices are in place to protect customer data. The program has the following phases:

* Publisher verification.
* Publisher attestation.
* Microsoft 365 certification.

## Publisher verification

Before an app developer can submit their app to Microsoft, the developer is required to undergo a verification. A developer verifies their identity using their Microsoft Partner Network (MPN) account and associates this MPN account with their app registration. Publisher verification helps admins and end users understand the authenticity of application developers. Publisher verification provides the following benefits:

* Increased transparency and risk reduction for customers - this capability helps customers understand which apps being used in their organizations are published by developers they trust.
* Improved branding - a `verified` badge appears on the Azure Active Directory consent prompt, Enterprise Apps page, and other user interfaces used by end-users and admins.
* Smoother enterprise adoption - admins can configure user consent policies, with publisher verification status as a primary policy criteria.

## Publisher attestation

Publisher attestation is the next tier in the app compliance program. Publisher attested apps provide confidence to admins about security and compliance measures of an app. It also helps reduce the time to review this information for an app. The attestation will reflect an app's security, data handling, and compliance practices against more than 80 risk factors identified by [Microsoft Cloud App Security](https://www.microsoft.com/microsoft-365/enterprise-mobility-security/cloud-app-security). Publisher attestation process can start before Publisher verification is complete.

App developers are asked to complete a self-assessment that includes questions frequently asked by customers and IT admins to evaluate the security and compliance of an app. Microsoft then publishes this information for easier and more timely evaluation. To know more, see [Attestation guide](/microsoft-365-app-certification/docs/enterprise-app-attestation-guide).

Admins can quickly check for Published attested apps in three different ways.

* When gathering more information about an app, see the details of a specific app at its link at [Microsoft Teams apps security and compliance](/microsoft-365-app-certification/teams/teams-apps). Alternately, select the `Publisher attestation` link in [Teams admin center](https://admin.teams.microsoft.com/).

  :::image type="content" source="media/attested-app-tac3.png" alt-text="In Teams admin center, select the Publisher attestation link to view details of the attestation of an app.":::

* In Teams admin center, when checking the details of an app from the **[Manage App](https://admin.teams.microsoft.com/policies/manage-apps)** page, see the publisher attested icon on the banner in the app's detail page.

  :::image type="content" source="media/attested-app-tac1.png" alt-text="In Teams admin center, Publisher attested icon is displayed on all attested apps.":::

* In Teams admin center, when you [grant permissions to the app](app-permissions-admin-center.md), a blue checkmark in front of the app name indicates either a publisher attested app or a Microsoft 365 certified app.

   :::image type="content" source="media/attested-app-tac2.png" alt-text="In Teams admin center, on the dialog to grant permissions, the blue checkmark indicates publisher attested app.":::

The attestation details page for an attested or certified app lists the following details.

:::image type="content" source="media/attested-app-doc-details.png" alt-text="Detailed information provided for attested apps.":::

## Microsoft 365 certification

App certification is achieved through:

* A qualified analyst's review.
* Approval of a comprehensive assessment centering on an app's security and compliance frameworks, processes, and procedures.

We check the app against a series of security controls derived from leading industry-standard frameworks.

The certificate demonstrates the strong security and compliance practices that are in place to protect customer data when the app is used in an organization. More information about how admins and end-users benefit from the certification is available at [Overview of Microsoft 365 app compliance program](/microsoft-365-app-certification/docs/enterprise-app-certification-guide).

Administrators can quickly check for Microsoft 365 certified apps in the following ways.

* When gathering more information about an app on the web, see the shield icon in [Microsoft documentation about the app](/microsoft-365-app-certification/teams/teams-apps).

  :::image type="content" source="media/attested-app-doc-details.png" alt-text="View the Microsoft 365 certification information in the detailed help article about security and compliance of an app":::

* When checking an application in [Teams admin center](https://admin.teams.microsoft.com/policies/manage-apps), sort the list of apps using the Certification column. See the icon and optionally, select the link to access the app-specific page mentioned above.

  :::image type="content" source="media/m365cert-apps-list1.png" alt-text="View Microsoft 365 certification status of an app in the Teams admin center." lightbox="media/m365cert-apps-list2.png":::

* When viewing the details of an app, see the Microsoft 365 certified icon in the app banner.

  :::image type="content" source="media/m365cert-app-details-banner.png" alt-text="View Microsoft 365 certification information in the app banner when managing a specific app in Teams admin center":::

* In Teams admin center, when you [grant permissions to the app](app-permissions-admin-center.md), a blue checkmark in front of the app name indicates either a publisher attested app or a Microsoft 365 certified app.

   :::image type="content" source="media/attested-app-tac2.png" alt-text="In Teams admin center, on the dialog to grant permissions, admins can check the blue checkmark to be assured that the app is Microsoft 365 certified":::

## View security, compliance, and privacy information

You can find information about security, privacy, compliance and behaviors for an attested or certified app in [Microsoft documentation](/microsoft-365-app-certification/teams/teams-apps) and [Teams admin center](https://admin.teams.microsoft.com/policies/manage-apps).

### Microsoft documentation

You can find the details about security, privacy, compliance, and more for each app listed it the app-specific help articles linked from [Microsoft Teams apps security and compliance](/microsoft-365-app-certification/teams/teams-apps).

:::image type="content" source="media/attested-app-doc-details.png" alt-text="Detailed information that is provided for apps that undergo Microsoft compliance program.":::

### Teams admin center

When evaluating an app, you can use independent Cloud Access Security Brokers (CASB), such as Microsoft Cloud App Security (MCAS), to find information about security and behaviors of an app. The Teams admin center includes security and compliance information from MCAS for Microsoft 365 Certified apps. Check this information in the app details page, to verify if the app meets your security needs.

> [!NOTE]
> This feature is available to all admins, whether or not your organization has a license that supports MCAS.

To access MCAS information for an app:

1. In the Teams admin center, select **Teams apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)**.

1. Select **Certification** to sort apps and push all Microsoft 365 Certified apps to the top of the table.

1. Choose a Microsoft 365 Certified app.

1. Select the **Security and compliance** tab.

   :::image type="content" source="media/mcas.png" alt-text="Screenshot of Teams admin center security and compliance tab.":::

   To get more details on the supported capabilities for the app, select the dropdown list for each category.

## View privacy policy and terms of use of an app

In Teams admin center, each app page links to the privacy statement and terms of use of the app.

:::image type="content" source="media/tac-app-tou-privacy-info1.png" alt-text="From Teams admin center, admins can access the link to the privacy policy and terms of use for every app." lightbox="media/tac-app-tou-privacy-info2.png":::

## Related articles

* [View app permissions and grant admin consent](app-permissions-admin-center.md).
