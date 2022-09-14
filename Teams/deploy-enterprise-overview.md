---
title: Microsoft Teams enterprise deployment overview
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
description: Learn how to deploy enterprise features of Microsoft Teams.
ms.localizationpriority: high
search.appverid: MET150
f1.keywords:
  - NOCSH
ms.collection: 
  - M365-collaboration
  - m365initiative-deployteams
appliesto: 
  - Microsoft Teams
---

# Teams enterprise deployment overview

If you're a medium or large business, you need to think about how you're going to roll out the service to your users, how you're going to deploy the Microsoft Teams client to them, how your network design could impact the quality of real-time communication, and so on. Check out the following sections for pointers to articles that'll help you plan for Teams in your organization.

> [!NOTE]
> If you haven't done so already, we strongly suggest that you begin your Teams deployment with a pilot. A pilot will allow you and a few early adopters to get familiar with Teams and its features before your planning and eventual roll out. For more information about how to start your pilot, check out [Get started with Microsoft Teams](get-started-with-teams-quick-start.md).

After you've read the sections below and are ready to start deploying Teams in your organization, see [Set up Microsoft Teams in your enterprise](deploy-enterprise-setup.md).

## Architecture

Teams is tightly integrated into Microsoft 365 and uses many features to power chat, file sharing, meetings, telephony, video streaming, and more. Before you roll out Teams, check out [Microsoft Teams IT architecture and telephony solutions posters](teams-architecture-solutions-posters.md) to get familiar with how Teams works with the rest of Microsoft 365 to create a complete collaboration experience for your users.

## Workloads

Teams has three workloads that can be deployed independently of each other: **chat, teams, and channels**; **meetings and conferencing**; and **Phone System and PSTN (public switched telephone network) connectivity**. Each workload has its own section in our documentation to make it easier to find information about that workload. This includes deployment planning information.

To see deployment planning information for the workload you want to deploy, see the following articles:

- [Chat, teams, and channels](deploy-chat-teams-channels-microsoft-teams-landing-page.md)
- [Meetings and conferencing](deploy-meetings-microsoft-teams-landing-page.md)
- [Phone System and PSTN connectivity](cloud-voice-landing-page.md)

## Network planner

Network planning for Teams is extremely important when you have large numbers of users, complex networks, or both. Teams supports voice calling and video conferencing, both of which rely on real-time communications to provide the best experience possible for users. Networks must:

- Have sufficient bandwidth capacity to accommodate the number of concurrent voice calls, video conferences, meetings, screen sharing, and so on.
- Have network hardware that supports real-time communication protocols.
- Allow the required network ports between devices on your networks, Microsoft 365 services, and external users.

See the following articles to help you understand Teams network requirements:

- [Prepare your organization's network for Microsoft Teams](prepare-network.md)
- [Proxy servers for Teams or Skype for Business Online](proxy-servers-for-skype-for-business-online.md)

To help you with your planning, Teams includes the Network planner. The Network planner asks you questions about the number and types of users you have, how many sites your organization has, the bandwidth capacity of your network links, and more. Using this information, the Network planner creates a report that shows the bandwidth requirements for each activity, along with the recommendations.

 > [!div class="nextstepaction"]
> [Go to Network planner](https://admin.teams.microsoft.com/networkplanner/organization)

(You must be a [Microsoft 365 global admin](/microsoft-365/admin/add-users/about-admin-roles#commonly-used-microsoft-365-admin-center-roles) to open the Network planner.)

For details about how the Network planner works, see [Use the Network planner for Microsoft Teams](network-planner.md).

To see an example of how Network planner can plan your network, see [Using Network Planner - example scenario](tutorial-network-planner-example.yml).

## Teams advisor

The Teams advisor is a solution within Teams that brings together teams, channels, file sharing, and Planner, to create a deployment project for your organization. Teams advisor creates project plan, specific to the workload you select (such as chat, teams, and channels), that includes the recommended tasks you should perform during your deployment. Each task contains instructions, suggestions, and links to relevant articles, to guide you through the process. You can easily assign tasks to one or more individuals, and specify start and end dates for each task.

> [!TIP]
> See how you can use Teams advisor to help you plan your Teams deployment by completing the [Roll out using the Teams advisor](/learn/modules/m365-teams-rollout-using-advisor/) module on Microsoft Learn.

> [!div class="nextstepaction"]
> [Go to Teams advisor](https://admin.teams.microsoft.com/teams-deployment)

(You must be a [Microsoft 365 global admin](/microsoft-365/admin/add-users/about-admin-roles#commonly-used-microsoft-365-admin-center-roles) to open the Teams advisor.)

For details about how the Teams advisor works, see [Use Advisor for Teams to help you roll out Microsoft Teams](use-advisor-teams-roll-out.md).

## Lifecycle and governance planning

As you plan your Teams deployment, you need to consider the lifecycle of teams, channels, files, and so on, in your organization. You should also think about what types of information will be stored in them. Teams may be created for a specific project, for a department, or they might be used as a central resource for the entire organization. Each of these uses have different requirements, which drive questions like the following:

- How long will the teams remain active?
- Who should own and manage the teams and their channels?
- Should certain compliance requirements apply to some teams, but not others?
- Should there be a naming policy to help users identify the right team?

Creating policies and guidelines as part of your initial deployment will help ensure that your users can find the information they need. Just as importantly, however, appropriate policies will help protect your organization from information leakage, help you conform to regulatory requirements, and help you retain information as needed for archival purposes.

To learn more about lifecycle management and governance in Teams, see the following:

- [Plan for lifecycle management in Teams](plan-teams-lifecycle.md)
- [Plan for governance in Teams](plan-teams-governance.md)

## Adoption

To ensure that your organization and your users get the most out of Teams, you need an adoption program. An effective adoption program can mobilize early adopters who can:

- Articulate the benefits of Teams to their colleagues and to business or group leaders.
- Spark excitement in others who see how Teams improves collaboration and makes it easier to connect with each other.
- Help evaluate existing business processes and make recommendations for how Teams can be integrated into them.
- Report back to the deployment team both successes and difficulties to help improve the adoption process.

For details about setting up an adoption program, see [Adopt Microsoft Teams](adopt-microsoft-teams-landing-page.md).