---
title: Overview of app validation and app testing by Microsoft
description: Learn about Teams app validation guidelines based on marketplace certification policies. Understand how Microsoft ensures that Teams apps adhere to high standards of privacy and security.
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
* Apps that require users to sign in have a sign-out option.
* All app developer undergo a detailed verification process on Microsoft Partner Center. The verification includes email verification, business verification and more. To know more about app publishing, see [How developers create a Partner Center account](/microsoftteams/platform/concepts/deploy-and-publish/appsource/prepare/create-partner-center-dev-account), [Submission guide for developers](/office/dev/store/add-in-submission-guide), and [How developers publish apps](https://aka.ms/PublishToTeamsStore).
* Only apps from verified developers can seek Graph permissions from end users.
* No app can download an executable file.
* Apps are tested to not contain ads, promotion for other apps.
* Apps are tested to be work appropriate with no offensive language, cyber-attack bots, spam, or scam content.
* All links in an app are functional and related only to the app offering.
* We test and evaluate all the published Teams app regularly as part of app store health checks.
* Privacy policy and Terms of use that cover Teams apps are published by the app developers.
* The contact details of the app developer are available in the store listing and on their respective [Publisher attestation pages](/microsoft-365-app-certification/teams/teams-apps).

In addition, Microsoft encourages the app developers to participate in its compliance program that is a rigorous, two-tier approach to ensure app quality, security, and compliance. Teams store has hundreds of apps that go beyond fulfilling the already detailed validation guidelines and comply with these programs.

## Related article

* [Overview for admins of Microsoft 365 app compliance program](overview-of-app-certification.md)
