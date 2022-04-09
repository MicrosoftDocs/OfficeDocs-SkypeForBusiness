---
title: Overview of app validation and app testing by Microsoft
ms.reviewer: 
description: Understand the quality checks, app validation, and certification programs for Teams apps.
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
# Validation performed by Microsoft for all Teams apps

Microsoft requires all apps to pass a mandatory validation before being listed in the store for end-uses. It applies to all apps (except custom apps) published on the Teams App store. In addition, Microsoft strongly encourages app developers to participate in an optional certification of apps that indicates enhanced compliance, security, and privacy controls.

All the apps are mandatorily required to adhere to the Microsoft App Certification policies. The Teams store team performs 400+ tests to ensure that the apps are usable and adhere to high standards of privacy and security.

To know the detailed validation guidelines that app developers adhere to, see [Validation guidelines for developers](/microsoftteams/platform/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines). The guidance is based on the [Certification policies for Teams apps](/legal/marketplace/certification-policies#1140-teams).

> [!NOTE]
> Validation and checks by Microsoft are not available for a custom app as it is developed within your organization and is only available to members of your organization.

## App validation and testing

We execute 400+ test cases for every app before it's made available on the Teams Store. The tests ensure appropriate functionality, user experience, and security, and ensure that all apps comply with the publicly listed CMO policies. Following are some of the tests carried out by Microsoft App Validation team for every app before it's published:

* Ensure that Graph permissions requested by the app are really the ones that the app functionality needs and not any extra permissions. Graph permissions for existing apps are regularly checked to ensure no extra permissions are required by an app.
* Apps that require users to log/sign in must have a log/sign out option.
* All app publishers undergo a detailed verification process on Microsoft Partner Center. The verification includes email verification, business verification and more. To know more about app publishing, see [How developers create a Partner Center account](/microsoftteams/platform/concepts/deploy-and-publish/appsource/prepare/create-partner-center-dev-account), [Submission guide for developers](/office/dev/store/add-in-submission-guide), and [How developers publish apps](https://aka.ms/PublishToTeamsStore).
* Only apps from verified publishers can seek Graph permissions from end users.
* No app can download an executable file.
* Apps are tested to not contain ads, promotion for other apps
* Apps are tested to be work appropriate with no offensive language, cyber-attack bots, spam, or scam content.
* All links in an app are functional and related only to the app offering.
* We test and evaluate all the published Teams app regularly as part of app store health checks.
* Privacy policy and Terms of use that cover Teams apps are published by the ISV
* The contact details of the ISV are available in the store listing and on their respective [Publisher Attestation pages](/microsoft-365-app-certification/teams/teams-apps).

## Publisher verification

Publisher verification helps admins and end users understand the authenticity of application developers integrating with the Microsoft identity platform. Having a verified publisher, means that the publisher has verified their identity using their Microsoft Partner Network (MPN) account and has associated this MPN account with their app registration.

Publisher verification provides the following benefits:

* Increased transparency and risk reduction for customers - this capability helps customers understand which apps being used in their organizations are published by developers they trust.
* Improved branding - a `verified` badge appears on the Azure Active Directory consent prompt, Enterprise Apps page, and other user interfaces used by end-users and admins.
* Smoother enterprise adoption - admins can configure user consent policies, with publisher verification status as a primary policy criteria.

In addition, Microsoft encourages the app developers to participate in its compliance program that is a rigorous, two-tier approach to ensure app quality, security, and compliance. Teams store has hundreds of apps that go beyond fulfilling the already detailed validation guidelines and comply with these programs.

## Microsoft 365 app compliance program

Microsoft compliance program demonstrates that an app is vetted against controls derived from leading industry standard frameworks, and that strong security and compliance practices are in place to protect customer data. The program has two phases:

* Publisher attestation.
* Microsoft 365 certification.

### Publisher attestation

Publisher attestation is the next tier in the app compliance program. Publisher attested apps provide added confidence to admins about security and compliance measures of an app and reduce the time to review it for an app. The attestation will reflect an app's security, data handling, and compliance practices against more than 80 risk factors identified by [Microsoft Cloud App Security](https://www.microsoft.com/microsoft-365/enterprise-mobility-security/cloud-app-security).

App developers are asked to complete a self-assessment that includes questions frequently asked by customers and IT admins to evaluate the security and compliance of an app. Microsoft then publishes this information for easier and more timely evaluation. To know more, see [Attestation guide](/microsoft-365-app-certification/docs/enterprise-app-attestation-guide).

Admins can quickly check for Published Attested apps in three different ways.

* On the web, when gathering more information about an app, see the details of a specific app at its link at [Microsoft Teams apps security and compliance](/microsoft-365-app-certification/teams/teams-apps). Alternately, click the Publisher attestation link in Teams admin center.

  :::image type="content" source="media/attested-app-tac3.png" alt-text="In Teams admin center, click Publisher attestation link to view details of the attestation of an app":::

* In Teams admin center, when checking the details of an app from the **Manage App** page, see the publisher attested icon on the banner in the app's detail page.

  :::image type="content" source="media/attested-app-tac1.png" alt-text="In Teams admin center, Publisher attested icon is displayed on all attested apps.":::

* In Teams admin center, when granting permissions to the app, a blue checkmark in front of the app name indicates that it is either a publisher attested app or a Microsoft 365 certified app.

   :::image type="content" source="media/attested-app-tac2.png" alt-text="In Teams admin center, on the dialog to grant permissions, admins can check the blue checkmark to be assured that the app is publisher attested.":::

The attestation details page for an attested or certified app lists the following details.

:::image type="content" source="media/attested-app-doc-details.png" alt-text="Topics on which detailed information is provided for attested apps.":::

### Microsoft 365 certification

App certification is achieved through a qualified analyst's review and approval of a comprehensive assessment centering on an app's security and compliance frameworks, processes, and procedures. The app is vetted against a series of security controls derived from leading industry standard frameworks. The certificate demonstrates that strong security and compliance practices are in place to protect customer data when the app is activated in an organization.

<!--- TBD: Parking some content for later review. Check if this content needs to be published.

We also have a few more quality and security checks for apps. We have launched Microsoft Cloud App Security (MCAS) program for the customer who have E5 or EMS license, where we rate risk for your cloud apps based on regulatory certification, industry standards, and best practices. We are also working on an Apps Quality Score system (launching soon) for all apps on Teams platform, and you will be able to check an app’s quality score quickly on Teams Store.

--->
