---
title: Know about apps in Microsoft Teams
ms.reviewer: 
description: Learn about apps and decide what apps to allow in Teams based on your organization's profile and business requirements.
ms.topic: conceptual
author: ashishguptaiitb
ms.author: guptaashish
manager: prkosh
audience: admin
ms.service: msteams
ms.subservice: teams-apps
ms.date: 10/01/2022
ms.collection: 
  - M365-collaboration
  - m365-frontline
  - tier2
  - highpri
f1.keywords:
- NOCSH
ms.localizationpriority: high
search.appverid: MET150
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020; intro-overview; intro-hub-or-landing
---
# Understand Microsoft Teams apps and their capabilities

Apps in Teams help users bring together their workplace tools and services and collaborate with others. Examples are end-users using a pinned Calendar app in Teams to quickly collaborate with others, an app with bots functionality informing users of the quality of a web service in a Teams channel, and an app to share and assign tasks to various end-users in a channel. Microsoft Teams apps are web-based SaaS apps that don't need to be deployed locally.

As an admin, you set an app governance process that balances wide-ranging requirements of end-users along with your organization's IT policies, standards, and risk-profiles.

Our extensive [catalog](https://appsource.microsoft.com/marketplace/apps?product=office%3Bteams&page=1) of validated and secure Teams apps provides end-users access to the tools and services that your organization needs every day. Teams admin center provides admins enterprise-grade controls and configurations to govern the apps. You control the availability of apps for each user across the various contexts such as meeting, chats, and channels.

This article helps you understand the types of apps and where from your users access those apps. To learn more about the use of apps, read [Overview of apps for end-users](https://support.office.com/article/overview-of-apps-in-teams-747492ee-7cdd-4115-a993-8c7e7f98a3d0).

The different types of apps that your end-users can use in Teams are:

* [Core apps that are part of Teams](#core-apps).
* Other [apps created by Microsoft](#apps-created-by-microsoft).
* [Third-party apps](#third-party-apps-created-by-independent-app-developers) created by partners (validated by Microsoft).
* [Custom apps](#custom-apps-created-within-an-organization-for-internal-use) created by your own organization.

## Core apps

Some Teams functionalities such as activity feed, teams, chat, calendar, calls, files, and assignments (education tenants) are available by default and pinned by default for ease of access for end-users. For frontline workers, only activity, shifts, chat, and calling are available and pinned. As an admin, you can modify this default behavior using [setup policy](/microsoftteams/teams-app-setup-policies).

:::image type="content" source="media/core-apps-pinned1.png" alt-text="Core apps are the apps pinned in Teams by default." lightbox="media/core-apps-pinned2.png":::

## Apps created by Microsoft

Microsoft provides many apps to improve productivity and collaboration. You and end-users can find these apps by looking for Microsoft listed as the Publisher in Teams admin center or listed as Provider in the Teams store.

Teams comes with a set of built-in apps, including Lists, Tasks, Praise, Approvals, and more. We recommend that you include the featured apps—such as Planner—in your initial Teams rollout.

:::image type="content" source="media/microsoft-apps-in-tac1.png" alt-text="Screenshot showing a list of Microsoft apps in Teams admin center." lightbox="media/microsoft-apps-in-tac2.png":::

## Third-party apps created by independent app developers

In addition to Microsoft-provided apps, you can use third-party apps. Microsoft rigorously validates the functionality and security of all these apps. Elaborate manual and automated tests are executed before making these apps available in Teams store and many tests continue at a regular cadence even after the apps are published live. To understand the benefits of app validation, see [validation of third-party apps](overview-of-app-validation.md). Some of the apps subscribe to the [Microsoft compliance program](overview-of-app-certification.md) to undergo multiple tiers of further checks beyond validation.

:::image type="content" source="media/3p-apps-in-teams.png" alt-text="Screenshot of an example of third-party apps in the Teams' store.":::

## Custom apps created within an organization for internal use

Apps created by developers in your organization are called custom apps (or Line of Business apps). Your organization may commission the creation of custom apps for org-specific requirements. You have the control to allow or block such apps for entire organization or for specific users. Developers in your organization can build custom low-code solutions by using Teams integration with [Microsoft Power Platform](/microsoftteams/platform/samples/teams-low-code-solutions).

After an admin allows the use of custom apps, end-users can find such apps by selecting **Built for your org** in the left navigation of Teams store.

:::image type="content" source="media/built-for-your-org1.png" alt-text="Screenshot of custom apps in Teams' store in the Teams' desktop app." lightbox="media/built-for-your-org2.png":::

For more information, see [Understand and manage custom and sideloaded apps](custom-app-overview.md).

## About App Templates

Using the app development methods, Microsoft creates and provides functional and production-ready sample apps. Collectively, these apps are called App templates for Teams and are provided to:

* Illustrate a few collaboration use cases in Teams.
* Showcase app development best practices and methods.
* Provide open-source apps that developers can extend to create their own apps.

Your organization developers customize App Templates with simple changes to the provided source code. You provide these apps as custom apps for your end-users, to meet any organization needs.

To know more, see [Microsoft Teams App Templates](https://adoption.microsoft.com/microsoft-teams/app-templates/).

## Discover and use apps in Teams

Users can view all the apps available in Teams from the Teams apps store in a Teams desktop or web client. Users can search by name, browse by category, and browse by apps built for your org and built with Power Platform to discover and install apps in Teams.

Apps can be pinned to Teams for easy access. Users can [pin apps on their own](https://support.microsoft.com/office/pin-an-app-for-easy-access-3045fd44-6604-4ba7-8ecc-1c0d525e89ec) if their setup policy allows and if the app is allowed by Teams admin. Admins can pin apps and control the behavior of pinned apps, For more information, see [app setup policies](/microsoftteams/teams-app-setup-policies).

:::image type="content" source="media/user-app-experience-find-apps.png" alt-text="Screenshot that shows all the places where the users can browse apps in Microsoft Teams." lightbox="media/user-app-experience-find-apps-full.png":::

Users can find and add apps to Teams from the Teams app store. They can also add apps directly from the context they're working in, such as chat or channel tab, Teams meeting, or messaging area. For more information, see [add an app to Microsoft Teams](https://support.microsoft.com/office/add-an-app-to-microsoft-teams-b2217706-f7ed-4e64-8e96-c413afd02f77).

A user can add and use an app only when an admin allows the app and the app is made available to the user via [permission policies](teams-app-permission-policies.md). An organization's IT admin has complete control over who can install which apps in which context. Users can't add apps that are blocked, any app with a lock icon in the Teams store is blocked for the user. However, [users can request their org’s IT admin for their approval](https://support.microsoft.com/office/request-apps-that-require-approval-by-your-org-924e3a9e-33f0-44c2-9e81-e875214c05ae). After the app is approved, users can add the app from the Teams store.

> [!NOTE]
> Only individuals can request for an approval to add an app in Teams.

## Understand app capabilities

Teams app capabilities are the core functionalities that developers build in an app to fulfill various use cases of Teams apps. Apps contain one or more of the following capabilities. All these are different capabilities of Teams apps and admins govern these apps using the common [app governance methods](manage-apps.md).

<!---
        :::image type="content" source="media/teams-app-capabilities-group.png" alt-text="Graphic that shows the app capabilities of a Microsoft Teams app." border="false":::
--->

* **Bots**: Bots are also referred to as a chatbot or conversational bot. It's an app that executes simple and repetitive tasks. A bot interaction can be a quick question and answer, or it can be a complex conversation that provides access to services or assistance. Users can have a conversation with a bot in a personal chat,  channel, or group chat. For more information, see [Bots in Microsoft Teams](/microsoftteams/platform/bots/what-are-bots).

* **Tabs**: Tabs are Teams-aware webpages pinned at the top of a channel or a chat. Tabs let you interact with content and services with a web-like experience. They're simple HTML `iframe` tags that can be added as part of a channel inside a team, group chat, or personal app for an individual user. For more information, see [Microsoft Teams tabs](/microsoftteams/platform/tabs/what-are-tabs).

* **Webhooks and connectors**: Webhooks and connectors help to connect various web services to channels and teams in Microsoft Teams. Webhooks are user-defined HTTP callback that notifies users about any action that has taken place in the Teams channel. It's a way for an app to get real-time data. Connectors allow users to subscribe to receive notifications and messages from web services. For more information, see [Webhooks and connectors](/microsoftteams/platform/webhooks-and-connectors/what-are-webhooks-and-connectors).

  To allow users to use custom connectors in Teams, see [Use custom connectors in Teams](office-365-custom-connectors.md).

* **Messaging extensions**: Messaging extensions are shortcuts to insert app content or to act on a message without end-users having to move away from the conversation. Users can search or initiate actions in an external system from the compose message area, the command box, or directly from a message. For more information, see [Message extensions](/microsoftteams/platform/messaging-extensions/what-are-messaging-extensions?tabs=dotnet).

* **Meeting extensions**: Users can enhance the meeting experience by integrating message extensions within meetings and make meetings more productive. You can identify various participant roles and user types, get meeting events, and generate in-meeting dialogs. For more information, see [Apps for Teams meetings](/microsoftteams/platform/apps-in-teams-meetings/teams-apps-in-meetings).

<!---
* **Cards and task modules**: Cards provide users with various visual, audio, and selectable messages and help in conversation flow. Task modules help you create modal pop-up experiences in Microsoft Teams. They're useful for starting and completing the tasks, or displaying rich information like videos or Power business intelligence (BI) dashboards. For more information, see [Cards and task modules](/microsoftteams/platform/task-modules-and-cards/cards-and-task-modules).
--->

* **Activity feeds**: Activity Feed in Teams contains a notification of all the activity in various scopes like channels and chats. Apps can broadcast a message to all the members of say a team or a channel to notify of any updates. Users can customize what notifications they view.

To view common use cases mapped to Teams capabilities, see [Map your use cases to Teams app capabilities](/microsoftteams/platform/concepts/design/map-use-cases).

## Related articles

* [Learn more about App Templates for Teams](/microsoftteams/platform/samples/app-templates).
* [Teams app updates and admin role](apps-update-experience.md)
* [Overview of app management and governance in Teams admin center](manage-apps.md)
