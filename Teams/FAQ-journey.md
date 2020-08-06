---
title: Upgrading from Skype for Business to Teams FAQ
author: lanachin
ms.author: v-lanac
manager: serdars
ms.topic: conceptual
ms.service: msteams
audience: admin
ms.reviewer: landerl
description: Frequently asked questions about the upgrade journey from Skype for Business to Microsoft Teams.
localization_priority: Priority
search.appverid: MET150
f1.keywords:
- CSH
ms.custom: 
 - Teams-upgrade-guidance
 - seo-marvel-apr2020
ms.collection: 
- Teams_ITAdmin_JourneyFromSfB
- M365-collaboration
appliesto:
- Microsoft Teams
---

# FAQ — Upgrading from Skype for Business to Microsoft Teams


## General questions

**Is there a firm deadline by which customers need to move from Skype for Business Online to Teams?**
Yes. [Skype for Business Online will be retired](skype-for-business-online-retirement.md) on July 31, 2021, at which point it will no longer be accessible or supported. We encourage Skype for Business Online customers to start using Teams and begin planning their upgrades now to allow ample time to complete upgrade prior to the retirement date.


**How long will it take to upgrade my organization to Teams?**
Your organization's journey from Skype for Business to Teams can be defined by you. To assist in your planning and execution, we've developed comprehensive upgrade guidance based upon a proven framework designed to help you navigate the technical and organizational elements of change. Start your journey by familiarizing yourself with our [upgrade success framework](upgrade-framework.md) and associated resources that serve as the cornerstone for navigating your journey from Skype for Business to Teams.


**Is there a recommended upgrade path for Skype for Business?**
We encourage you to plan the journey from Skype for Business to Teams leveraging the guidance and resources at [aka.ms/SkypetoTeams](upgrade-start-here.md) and attend a free [upgrade planning workshop](upgrade-workshops-landing-page.yml) to identify and implement the upgrade path that best meets the needs of your organization.

**Where can I learn more about coexistence modes in the Microsoft Teams admin center?**
Within the Microsoft Teams admin center, you'll notice options for coexistence modes, enabling your organization to manage the Skype for Business to Teams journey that's right for your organization. Learn more about [coexistence and upgrade modes](teams-and-skypeforbusiness-coexistence-and-interoperability.md).

**What should I do to prepare for my upgrade?**
A successful upgrade will include validating technical readiness in addition to user acceptance readiness. Even if you determine your organization isn't quite ready to upgrade to Teams, you can begin the planning process today. Further, you can start realizing the value of Teams by enabling Teams alongside Skype for Business. Get started on your [Skype to Teams journey[(https://aka.ms/skypetoteams-home) today.

Microsoft also offers live, interactive workshops in which we'll share guidance, best practices, and resources designed to kick start upgrade planning and implementation. [Learn about upgrade planning workshops](https://aka.ms/SkypeToTeamsPlanning).



**My organization is already running Teams alongside Skype for Business. Can I just disable Skype for Business?**
No, you'll want to switch users to Teams Only mode to complete the upgrade to Teams. If your organization is ready to upgrade to Teams, take time to communicate to users to let them know what's happening and allow them to acclimate to Teams. This will help ensure they have a positive upgrade experience and help alleviate calls to your helpdesk. For sample communication templates, download our [Upgrade Success Kit](https://aka.ms/UpgradeSuccessKit).





**Who can I contact if I have questions about the upgrade process?**
For questions related to your upgrade, reach out to your current points of contact, which might include your assigned Microsoft account team, partner, or [FastTrack](https://www.microsoft.com/en-us/fasttrack?rtc=1). Alternatively, you can open a help ticket from within your [Microsoft Teams admin center](https://admin.teams.microsoft.com/) by clicking the **Need help** button.

![Need help button](media/need-help-button.png)


**Do I upgrade all users on my tenant together, or can I opt to upgrade select users at a time?**
You have the flexibility to upgrade users to Teams as it makes sense for you, whether it's individuals, groups of users, or your entire organization. To help understand the optimal approach for your organization, review the various [coexistence and upgrade modes](teams-and-skypeforbusiness-coexistence-and-interoperability.md) you can enable.


**What happens after my users are upgraded?**<br>
After your users are upgraded to Teams (**Teams Only** mode)

Their Skype for Business client will be disabled for use as all chat and calls will go to Teams. This client will continue to be used for previously scheduled Skype for Business meetings. If this desktop client is uninstalled, users will be redirected to access previously scheduled Skype for Business meetings via the Skype for Business web app.

Any Skype for Business meetings scheduled before the upgrade will work as designed, but all new meetings will be scheduled in Teams. If users attempt to sign-in to Skype for Business, they'll get a notification from their client that they've been upgraded to Teams. Users will need to manually uninstall the Skype for Business client on their mobile device.



**Will users still be able to use Skype for Business after I activate the upgrade notification in their client?**
Yes, the upgrade notification will simply alert users that Skype for Business will be upgrading to Teams and invite them to get started with Teams if they haven't already. We recommend complementing this notification with an awareness campaign (emails, FAQs, helpdesk readiness, posters/signage) to communicate further details specific to your organization, such as timing for the upgrade, calls-to-action for the user, access to training, and so on. For communication templates, download our [Upgrade Success Kit](https://aka.ms/UpgradeSuccessKit).


**What does this mean from a licensing perspective? How will customers pay for Intelligent Communications services in Teams?**
Teams is available in Microsoft 365 and Office 365 suites. Capabilities that are premium workloads in Skype for Business Online today will continue to be premium workloads in Teams. Existing licensing investments made by customers carry forward to Teams. For example, if a customer has purchased Audio Conferencing standalone or as part of E5 with Skype for Business, Audio Conferencing will be enabled in Teams as it's available today.


**Is Microsoft planning scheduled upgrades?**
Currently, we have no plans to schedule upgrades for enterprise customers. Customers can choose to move to Teams as it makes sense for their organizations before the July 31, 2021 retirement date for Skype for Business Online. We'll empower administrators and users with tools and guidance to help with the transition to Teams.

In effort to support smaller customers that may not have dedicated IT resources, Microsoft is assisting with automated upgrades from Skype for Business Online to Teams. Eligible customers are notified of the upgrade through emails and Message Center notifications. More details are provided in the communications. For more information, see [Automated Upgrades from Skype for Business Online to Microsoft Teams](upgrade-automated.md).



## Microsoft Teams capabilities and roadmap

**What are the benefits of Teams' back-end infrastructure?**
Teams is built for the cloud on a highly scalable microservices architecture that's efficient in bandwidth consumption, provides more robust telemetry, and enables maintenance and upgrades with minimal disruption. As a result, users see faster meeting join times and a better browser experience without needing to download plug-ins. This modern infrastructure makes it easy to tap into Microsoft Cognitive Services—which include transcription, translation, speech recognition, and machine learning capabilities—and have the power to make communication and collaboration easier and more effective.

**How can customers learn when Skype for Business capabilities will be available in Teams?**
See the [Microsoft 365 Roadmap](https://aka.ms/O365Roadmap).

**Which APIs and SDKs will be made available for Teams?**
Visit the [Microsoft Teams developer platform](https://docs.microsoft.com/microsoftteams/platform/) for information about available APIs and SDKs.


**Will you support third-party development opportunities in Teams?**
Yes, app integration is one of the key benefits of adopting Teams. We currently support third-party bots, connectors, and extensions in Teams. In addition, we have a large ecosystem of add-ins available in the Microsoft Teams app store.

**Is Teams available in Microsoft 365 Education?**
Teams is available in all Microsoft 365 Education suite licensing (Microsoft A1, A3 and A5).

**Is Teams available in the government community cloud (GCC)?**
Yes, Teams is available for the US Government Cloud Community (GCC). To learn more, see [plan for Microsoft 365 GCC deployments](https://docs.microsoft.com/microsoftteams/plan-for-government-gcc).



## Calling capabiities


**What is the plan for Microsoft's online voice capabilities?**
The core of our voice solution is Phone System which is available today. Customers can additionally add a Microsoft Calling Plan which provides complete support for calling including number acquisition and assignment directly in Microsoft 365. Customers who want to keep their telecom telephone trunks can use Direct Routing – which is included as part of Phone System. Mix and match both together as you see fit for your organization's needs to have a complete voice solution.

**What is the guidance for customers already deployed on Phone System (Cloud PBX) in Skype for Business Online?**
Calling in Microsoft Teams is ready for all your communication needs. We encourage all Microsoft 365 customers to start using Teams, independently of or in parallel with Skype for Business.


**What is the guidance for customers using Enterprise Voice today who want to move to Teams and use calling capabilities?**
Customers interested in bringing their own telephone service to Teams can now do so with the general availability of [Direct Routing](https://techcommunity.microsoft.com/t5/Microsoft-Teams-Blog/Direct-Routing-is-now-Generally-Available/ba-p/210359). Direct Routing and Calling Plans are the two choices for dial tone in Microsoft Teams.

## Meeting capabilities


**Is Audio Conferencing coverage in Teams different in Skype for Business?**
There will be no change in the coverage for Audio Conferencing as a result of its availability in Teams. The coverage of 90+ countries and 400+ cities we have today will continue to persist in both products. For the current list, see [Country and region availability for Audio Conferencing and Calling Plans](https://docs.microsoft.com/microsoftteams/country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans).



**Are third-party audio conferencing providers (ACP) supported in Teams?**
There are no plans to support third-party audio conferencing providers (ACP) in Teams. We believe the best audio conferencing experience for customers using Teams and Skype for Business will be to use our Audio Conferencing services. Customers who need to leverage ACP support in Skype for Business meetings can continue to use their Skype for Business client to join Skype for Business meetings. Meetings scheduled in Teams will need to utilize the Audio Conferencing services of Microsoft 365.

Support for the integration of third-party party audio conferencing providers (ACP) in Skype for Business Online has been extended to July 31, 2021, with limited support for remaining active tenants to allow additional time for transition. This is an update in the ACP timeline announced in April 2018.



**What's the plan for video interoperability support for Teams meetings?**
[Meeting room devices](https://products.office.com/microsoft-teams/across-devices) are critical to our vision for the modern workplace. [Cloud video interoperability services](https://docs.microsoft.com/microsoftteams/cloud-video-interop) to support Teams meetings with existing VTC systems are available through our partners Pexip, Polycom, and Blue Jeans.

**Will the latest generation of Skype Room Systems v2 support meetings in Teams?**
We rebranded Skype Room Systems to Microsoft Teams Rooms which fully supports Microsoft Teams meetings and offer an easy migration path from Skype for Business to Teams by just enabling Teams on the device.

In addition to the ability for users to identify nearby Microsoft Teams Rooms with proximity detection, Teams meetings can be joined with a single-click, dual screen support, Microsoft Whiteboard and we continue to bring innovative features like content camera with intelligent capture.


**Will Skype Room Systems v1 be updated to support Teams meetings?**
Lync Room System (LRS) devices with Skype Room System Version 1 (SRS v1) software has reached end of support on October 9, 2018. This means Skype Room Systems v1 software will no longer get any product updates or fixes anymore. Customers with Lync Room System devices using Skype Room System v1 software are advised to upgrade their devices to Microsoft Teams Rooms. To learn more, see [Migrate Lync Room System (LRS) devices to Microsoft Teams Rooms](https://docs.microsoft.com/microsoftteams/rooms/lrs-migration).

**Is Skype Meeting Broadcast going to retire at the same time as Skype for Business Online?**
Yes. [Teams live events](https://docs.microsoft.com/microsoftteams/teams-live-events/what-are-teams-live-events) is the successor solution to Skype Meeting Broadcast.


## Management capabilities

**What are the management experiences for Teams?**
Like the Skype for Business Admin Console, the [Microsoft Teams admin ](https://admin.teams.microsoft.com/) within the Microsoft 365 admin center is the single place to administer new Teams experiences. With this portal, administrators can create custom presence, chat, app, meeting, and voice policies and assign those policies to Teams users.

## Device compatibility

**Can I use Teams on Surface Hub?**
Teams meetings is now available on Surface Hub with Calling and Meetings experiences. For more information, see [Deploy Microsoft Teams for Surface Hub](https://docs.microsoft.com/microsoftteams/teams-surface-hub).

**Will current third-party IP (3PIP) phones continue to work with Microsoft Teams? And if so, how long?**
After the Skype for Business Online retirement date of July 31, 2021, users with 3PIP devices who have been migrated over to Teams only will be able to continue using their 3PIP devices with a limited set of functionalities until July 31, 2023.

**Will certified Skype for Business online phones work with Teams?**
For questions related to phone compatibility, read [Certified Skype for Business Online Phones and what this means for Teams](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Certified-Skype-for-Business-Online-Phones-and-what-this-means/bc-p/125309).






