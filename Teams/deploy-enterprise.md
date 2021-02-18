---
title: Microsoft Teams enterprise setup
author: dstrome
ms.author: dstrome
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
description: Learn how to deploy enterprise features of Microsoft Teams.
localization_priority: Priority
search.appverid: MET150
f1.keywords:
  - NOCSH
ms.collection: 
  - M365-collaboration
  - m365initiative-deployteams
appliesto: 
  - Microsoft Teams
---

# Teams enterprise setup

If you're a medium or large business, you need to think about how you're going to roll out the service to your users, how you're going to deploy the Microsoft Teams client to them, how your network design could impact the quality of real-time communication, and so on. Check out the following sections for pointers to articles that'll help you plan for, and roll out, Teams in your organization.

## Architecture

Teams is tightly integrated into Microsoft 365 and uses many features to power chat, file sharing, meetings, telephony, video streaming, and more. Before you roll out Teams, check out [Microsoft Teams IT architecture and telephony solutions posters](teams-architecture-solutions-posters.md) to get familiar with how Teams works with the rest of Microsoft 365 to create a complete collaboration experience for your users.

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

> [!div class="nextstepaction"]
> [Go to Teams advisor](https://admin.teams.microsoft.com/teams-deployment)

(You must be a [Microsoft 365 global admin](/microsoft-365/admin/add-users/about-admin-roles#commonly-used-microsoft-365-admin-center-roles) to open the Teams advisor.)

For details about how the Teams advisor works, see [Use Advisor for Teams to help you roll out Microsoft Teams](use-advisor-teams-roll-out.md).

## Adoption

To ensure that your organization and your users get the most out of Teams, you also need an adoption program. An effective adoption program can mobilize early adopters who can:

- Articulate the benefits of Teams to their colleagues and to business or group leaders.
- Spark excitement in others who see how Teams improves collaboration and makes it easier to connect with each other.
- Help evaluate existing business processes and make recommendations for how Teams can be integrated into them.
- Report back to the deployment team both successes and difficulties to help improve the adoption process.

For details about setting up an adoption program, see [Adopt Microsoft Teams](adopt-microsoft-teams-landing-page.md).