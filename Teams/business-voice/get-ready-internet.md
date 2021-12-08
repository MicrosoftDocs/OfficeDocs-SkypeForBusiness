---
title: Check your Internet connection for Teams Phone with Calling Plan
author: dstrome 
ms.author: dstrome
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
f1.keywords:
- NOCSH
ms.localizationpriority: medium
MS.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
- Teams_Business_Voice
search.appverid: MET150
description: 
appliesto: 
- Microsoft Teams
---

# Check your internet connection for Teams Phone

Teams Phone is Microsoft's technology for enabling phone capabilities within Microsoft Teams using the Microsoft 365 cloud. Every device that uses Microsoft Teams and Teams Phone needs a connection to the internet.

To get the best Teams Phone experience, you need a broadband internet connection that can support the maximum number of phone calls that your organization might make at any one time. You also need to make sure that the computers on your network can reach Microsoft 365 services.

You don't need a Teams Phone license to follow these steps.

## Check your internet connection speed

This article helps determine whether your internet connection is fast enough for the number of people who need to make phone calls. You'll provide information about your organization and get back a report that shows how much of your internet connection will be used by Teams and Teams Phone.

### Gather information about your internet connection and users

Before you start, you need the following information:

* The speed of your internet connection
* How many people will use Teams Phone mainly from your office
* How many people will use Teams Phone mainly from a remote location, such as a home office

### Enter your information into the network planner

Follow these steps:

1. In a browser, go to [https://admin.teams.microsoft.com](https://admin.teams.microsoft.com). Sign in by using an account that has Global Administrator permissions. The account that you used to sign up for Microsoft 365 or Office 365 has these permissions.
2. Open **Planning** and select **Network planner**.
3. Under **Network plans**, select **Add**. Enter a name for your plan, and then select **Apply**.
4. Select the name of your network plan.
5. On the next page, select **Add a network site** on the **Network sites** tab.
6. Fill in the **Network site name**, **Network Users**, and **Internet link capacity** fields, and then select **Save**. Leave the other fields on this screen blank, and don't select the **ExpressRoute** or **Connected to WAN** options.
7. On the **Report** tab, select **Start a report**.
8. Enter in a **Report name** and the number of **Network users** (**Office** and **Remote**), and then select **Generate report** to create a report that shows the bandwidth requirements for Teams. We will tell you how to read the report in the next section.

### Find your minimum internet connection speed

When you select **Generate report**, Microsoft 365 or Office 365 creates a report.

Under the **Impact** column and in the **Office 365** row, this number shows how much of your internet connection Teams and Teams Phone will use. We recommend that this number is no more than 30 percent of your total internet connection speed. For example, if your internet connection is *60 Mbps*, Teams and Teams Phone should use no more than *18 Mbps*.

Use this equation to determine your minimum internet connection speed: <*Impact number> / 0.3*.  

Let’s say the Impact number is *4.6875 Mbps*. The calculation to find your minimum internet connect speed would be *4.6875 / 0.3 = 15.6*. In this case, the internet connection speed should be at least *15.6 Mbps*.

If Teams and Teams Phone will use more than 30 percent of your total internet connection speed, the **Impact** number will appear red. In that case, you may need to upgrade your internet connection.

![Connection speed warning.](../media/network-planner-report-speed-warning.png)

>[!NOTE]
> The bandwidth impact provided by the Network Planner is an estimate only. It is recommended to use [Call Quality Dashboard](/microsoftteams/cqd-what-is-call-quality-dashboard.md) to pro-actively monitor user experience for audio and video calls with Microsoft Teams inside your organization.

## Make sure the computers and devices on your network can reach Microsoft 365

Computers and devices that use Teams Phone must use specific network ports to communicate with Microsoft 365 services. These ports are essentially doors through which devices talk to each other over a network or the internet. Your firewall needs to allow devices on your network to reach Microsoft 365 through the following *outbound* network ports:

* **TCP ports** 80 and 443
* **UDP ports** 3478, 3479, 3480, and 3481

The easiest way to check whether your firewall allows communication on these network ports is to perform a connectivity test using the [Microsoft 365 network connectivity tool](/microsoft-365/enterprise/office-365-network-mac-perf-onboarding-tool?view=o365-worldwide.md) from the office location you want to test. After completing the test, verify the results and recommendations.
