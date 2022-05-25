---
title: FAQ - Support your remote workforce
author: SerdarSoysal
ms.author: serdars
manager: serdars
audience: Admin
ms.topic: article
ms.service: msteams
ms.collection:
  - M365-collaboration
  - Teams_ITAdmin_RemoteWorkers
  - remotework
ms.reviewer: nichrose
ms.localizationpriority: high
search.appverid: MET150
description: Use this guidance to support your remote workforce to be productive when they're working from home (WFH) in response to the COVID-19 (Coronavirus) outbreak.
appliesto:
  - Microsoft Teams
---

# FAQ: Support your remote workforce

This article answers the most frequently asked questions about how IT admins can manage the increased number of users working remotely. Use this information to support your remote workforce to be productive when they're working from home (WFH).

Check out [Support your remote workers with Teams](support-remote-work-with-teams.md), which will answer many of your questions and help you get ready to support a remote workforce.

## Is Microsoft taking proactive action to be ready for the added workload of users working from home to avoid service disruption? All those 1:1 calls will now use Microsoft infrastructure.

Microsoft has been significantly expanding capacity in key regions with the recent announcements regarding the COVID-19 (coronavirus) outbreak. We are monitoring the situation and our services very closely to ensure that our services are available for our customers. One of the benefits of a cloud service is the ability to scale dynamically, including utilization of our significant supply chain, reallocation of resources between services, and redistribution of load. We have seen an increase in the utilization of Microsoft Teams which we have responded to and continue to monitor closely. We are also working to stay ahead of Calling Plans demand, and working to procure enough telephone numbers as needed.

> [!NOTE]
> If you're already set up with Microsoft 365, and want to know more about the actions Microsoft is taking, please go to the Message Center and review the **MC205458** message center post.

Don't miss our March 5, 2020 blog post from Jared Spataro, Corporate Vice President for Microsoft 365: [Our commitment to customers during COVID-19](https://www.microsoft.com/microsoft-365/blog/2020/03/05/our-commitment-to-customers-during-covid-19/).

## With the actions that Microsoft is taking, do we anticipate problems?

Although Microsoft is doing what we can to avoid problems, an unexpected peak in an area due to a spread of the virus may create temporary issues. While we're actively monitoring and adding capacity as needed, you might feel impact until we're able to add capacity in those areas. Also, there are external situations that Microsoft doesn't have control over. We foresee ISPs and telephony carriers are also taking proactive action, but they may or may not have the capacity to handle more load with more people working from home. We are working across industry with a focus on networking infrastructure. If you have an outage concern, check the Message Center to learn about any current outages.

## What can admins do if attendees are having trouble joining meetings by dialing in, such as if calls aren't getting through?

During the duration of the COVID-19 outbreak, we recommend that users join meetings by clicking the **Join Teams Meeting** button rather than dialing in by using the PSTN conference numbers or by using **Call me at**</strong>. This is primarily because of congestion in the telephony infrastructures of countries impacted by COVID-19. By avoiding PSTN calls, you'll likely experience better audio quality.

## What are the general Microsoft guidelines regarding network optimization for Microsoft 365? Some of my users in China are having a bad experience; what should I do to optimize our network?

Because of unique needs in China, customers may need to take specific actions:

- [Office 365 global tenant performance optimization for China users](/office365/enterprise/office-365-networking-china)

- [General guidelines for any network where Microsoft 365 is being used](/Office365/Enterprise/assessing-network-connectivity)

- [Prepare your organization's network for Teams](prepare-network.md)

## My users are reporting bad calls, or their calls are not connecting. What should I do to get help?

We're here to help. Before you [contact Support](/microsoft-365/admin/contact-support-for-business-products), make sure you've followed all of our [networking recommendations](#what-are-the-general-microsoft-guidelines-regarding-network-optimization-for-microsoft-365-some-of-my-users-in-china-are-having-a-bad-experience-what-should-i-do-to-optimize-our-network). To help you troubleshoot call quality, use [Call Analytics and Call Quality Dashboard](./monitor-call-quality-qos.md). We also recommend checking the [Service health dashboard](/office365/enterprise/view-service-health) in the Microsoft 365 admin center for any current advisories or issues with Microsoft services.

## What other actions can I take to have a better experience?

We recommend that users install and use our rich desktop clients instead of web clients (e.g., Outlook, [Teams desktop](get-clients.md)). Desktop clients will cache information and deliver a better performance under bandwidth restrictions or networking problems. From a communications perspective, we strongly recommend using Teams instead of Skype for Business, as Teams has more modern communications protocols and will better handle networking issues. We suggest you experiment with Teams in case of issues - read [Get started with your Teams upgrade](upgrade-start-here.md) to learn more.

## Is Teams free to help with the COVID-19 (coronavirus) outbreak? How does this work? I don't have Microsoft 365.

Teams is available for free through a couple of different programs:

**Individuals**:

- Sign in with your work or school credentials at [https://products.office.com/microsoft-teams](https://products.office.com/microsoft-teams). We'll automatically route you to the version of Teams associated with your organization's account, even if you don't have a license.

- If your organization doesn't have a Microsoft cloud account, sign up for the free version of Teams at [https://products.office.com/microsoft-teams/free](https://products.office.com/microsoft-teams/free) and invite your co-workers to join. To learn more, read [Welcome to Teams free](https://support.office.com/article/Welcome-to-Microsoft-Teams-free-6d79a648-6913-4696-9237-ed13de64ae3c). IT admins, read [Manage the free version of Teams](manage-freemium.md).

**IT professionals**:

- If you work for a business and want to get employees set up on Teams, you can sign up for [Teams Exploratory](teams-exploratory.md).

- If you work in Education and want to set up teachers, students, and administrators on Teams, use Office 365 A1, the free version of Office 365 available to educational institutions. Sign up at [https://www.microsoft.com/microsoft-365/academic/compare-office-365-education-plans](https://www.microsoft.com/microsoft-365/academic/compare-office-365-education-plans).

## I have Microsoft 365 already, but I don't use Teams. Are you providing trial licenses?

If you have Microsoft 365, then you already have Teams. [Turn it on](Office-365-set-up.md) for all your users. Once it's turned on, your users can run Teams, either by installing  [desktop](get-clients.md#desktop-clients) and [mobile](get-clients.md#mobile-clients) clients, or [from the browser](get-clients.md#mobile-clients) at [https://teams.microsoft.com](https://teams.microsoft.com).

## How do I get help to get started with Teams and make sure the deployment is successful?

Microsoft offers the [FastTrack Center Benefit for Office 365](/fasttrack/o365-fasttrack-benefit-for-office-365), which will help you to plan, deploy, drive usage, and adopt best practices. This service is offered at no cost when you have at least 150 users. To find out more, read [Requesting FastTrack assistance for Microsoft 365 just got easier](https://techcommunity.microsoft.com/t5/fasttrack-blog/requesting-fasttrack-assistance-for-microsoft-365-just-got/ba-p/393125#). FastTrack setup guidance for Microsoft 365 is available to all Office 365 organization administrators. To access this guidance, sign into [https://aka.ms/setupguidance](https://aka.ms/setupguidance) with your admin credentials.

If you want to get started on your own, read [How to roll out Teams](./deploy-overview.md) and check out our [Teams in 30](./teams-in-30-workshops.md) webinar series, designed to get you up and running with Teams in as few as 30 days.

For Education (EDU) tenants, Microsoft offers [School Data Sync](/schooldatasync/), which helps you to sync information from a school's Student Information System (SIS). For help deploying Microsoft 365, read [Microsoft 365 Education deployment overview](/microsoft-365/education/deploy/). Don't miss our new article, [Get started with Teams for remote learning](remote-learning-edu.md).

## Where do I find help getting Teams running for my company so my users can work from home during this crisis?

Read [Support remote workers using Teams](support-remote-work-with-teams.md). It covers most of the common tasks and questions on getting started with Teams for remote workers.

## I just got started with Microsoft 365 so I can use Teams to support my remote workers or students. I've signed up for the service, but when a user tries to use Teams, they get this error: "You're missing out! Ask your admin to enable Microsoft Teams." What should I do?

After you activate one of the free Teams offers, you'll still need to turn it on for your users. Read [Manage user access to Teams](user-access.md) and  [Add users individually or in bulk](/microsoft-365/admin/add-users/add-users).

If you're licensing or enabling a user for the first time but you've had Microsoft 365 for a while, you might need to [Turn on Teams](Office-365-set-up.md) for your organization. Check [I have Microsoft 365 already, but I don't use Teams. Are you providing trial licenses?](#i-have-microsoft-365-already-but-i-dont-use-teams-are-you-providing-trial-licenses) in this article.

## In meetings, attendees are having trouble joining by dialing in - calls aren't getting through.

During periods of high meeting volume (which we've been experiencing in conjunction with the COVID-19 outbreak), we recommend that users join meetings by clicking the <strong>Join Teams Meeting</strong> button rather than dialing in by using the PSTN conference numbers or by using <strong>Call me at</strong>. This helps ensure quality audio during times when high meeting volume is causing congestion on the PSTN network.

## Can I use Calling Plans with the Office 365 E1 Trial that Microsoft is offering? Can I assign a telephone number to my users? How much am I going to pay?

Users can make app-to-app audio and video calls in any version of Teams. To assign a number to an employee, you'll need [Phone System](what-is-phone-system-in-office-365.md). We recommend working with your Microsoft partner or sales representative to obtain and deploy this. Learn more at [Voice and video calling with Teams](https://products.office.com/microsoft-teams/voice-calling).

## Can I set up an Auto Attendant with the new Teams E1 Trial so I can have an emergency line internally at my company to deal with COVID-19 (coronavirus)?

To set up a [Cloud Auto Attendant](what-are-phone-system-auto-attendants.md) in Teams, you'll need [Phone System](what-is-phone-system-in-office-365.md) in addition to Teams. We recommend working with your Microsoft partner or sales representative to obtain and deploy this.

## Where can I find more information to help remote workers?

End users: [Collaborate with Microsoft 365](https://support.office.com/article/collaborate-with-office-365-ac05a41e-0b49-4420-9ebc-190ee4e744f4) - how to work better together across all Microsoft 365 workloads

IT admins/ITPro: [Support remote workers using Teams](support-remote-work-with-teams.md).

## What is Microsoft doing to support its own employees during the COVID-19 outbreak?

Read our March 5, 2020 blog from Brad Smith, Microsoft President: [As we work to protect public health, we also need to protect the income of hourly workers who support our campus](https://blogs.microsoft.com/on-the-issues/2020/03/05/covid-19-microsoft-hourly-workers/).

Also be sure to visit [Responding to COVID-19 together](https://news.microsoft.com/covid-19-response/?icid=mscom_marcom) on Microsoft.com.