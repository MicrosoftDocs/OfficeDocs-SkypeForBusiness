---
title: Perform network and environment planning
author: v-judegn
ms.author: v-judegn
manager: serdars
ms.date: 06/11/2019
ms.topic: conceptual
audience: admin
ms.service: msteams
search.appverid: MET150
ms.reviewer: lola
description: Perform network and environment planning.
localization_priority: Normal
ms.collection: 
  - M365-voice
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

# Perform network and environment planning

## Why should I plan my network and environment?
Network planning is the process of deciding the topology and capacity of a network. It is important to take the time to review and plan your network before you build and configure it. During network planning, remember to keep future needs in mind as well as present requirements, so that the topology and capacity of the networks can be changed, if required.

Failing to prepare your network will likely lead to dissatisfied users and costly, ad-hoc fixes. By preparing your network—and your organization—for Teams, you can dramatically increase your chance of optimal and consistent performance.

## Where do I begin?
### Step 1: Check your environment readiness
The current state of your environment may have an impact on how Teams will function. You must ensure that your current environment is ready for Teams.

Educational institutions are strongly encouraged to deploy School Data Sync before deploying Microsoft Teams. School Data Sync uses your school’s SIS roster data to automatically create classes and groups for Microsoft Teams and other applications.

To get the best experience with Teams, your organization must have deployed Exchange Online and SharePoint Online.

Refer to these links for help:
- If your organization has not deployed any Office 365 workloads, see [Getting Started with Office 365 for business](https://support.office.com/article/Get-started-with-Office-365-for-Business-d6466f0d-5d13-464a-adcb-00906ae87029).
- If your organization has not added or configured a verified domain for Office 365, see [Verify your Office 365 domain}(https://support.office.com/article/Verify-your-Office-365-domain-to-prove-ownership-nonprofit-or-education-status-or-to-activate-Yammer-87d1844e-aa47-4dc0-a61b-1b773fd4e590).
- If your organization has not synchronized identities to Azure Active Directory, see [Identity models and authentication in Microsoft Teams](https://docs.microsoft.com/en-us/microsoftteams/identify-models-authentication).
- If your organization does not have Exchange Online, see [Understand how Exchange and Microsoft Teams interact](https://docs.microsoft.com/en-us/microsoftteams/exchange-teams-interact).
- If your organization does not have SharePoint Online, see [Understand how SharePoint Online and OneDrive for Business interact with Microsoft Teams](https://docs.microsoft.com/en-us/microsoftteams/sharepoint-onedrive-interact).
- If your organization is an educational institution and you use a Student Information System (SIS), [deploy School Data Sync](https://docs.microsoft.com/schooldatasync/) before deploying Microsoft Teams.
- If your organization has an existing on-premises Skype for Business Server (or Lync Server) deployment, you must configure Azure AD Connect to synchronize your on-premises directory with Office 365. For more information, see [Configure Azure AD Connect for Teams and Skype for Business](https://docs.microsoft.com/en-us/skypeforbusiness/hybrid/configure-azure-ad-connect).

### Step 2: Prepare your network
To ensure optimal and consistent performance, prepare your network for Teams.

![Diagram describing the three components of quality](media/evaluate-my-environment-image1.png "Diagram describing the three components of quality, and how service management overlaps all three components. With a focus on the network.")

1. Evaluate and adjust network bandwidth for internal links and Internet connections to account for traffic.

    When planning on the implementation of Microsoft Teams within your network, you must ensure you have the required bandwidth, you have access to all required IP addresses, the correct ports opened, and you are meeting the performance requirements for real-time media.

    
    > [!NOTE]
    > If you know you will not meet these criteria, your end users will not get an optimal experience from Teams due to bad quality during calls and meetings. Should you not meet these criteria, this is the time to consider pausing the project to ensure you meet the criteria before continuing.


    
    |Bandwidth(up/down)  |Scenarios  |
    |---------|---------|
    |30 kbps  |       Peer-to-peer audio calling  |
    |130 kbps |       Peer-to-peer audio calling and screen sharing |
    |500 kbps |Peer-to-peer quality video calling 360p at 30fps |
    |1.2 Mbps |Peer-to-peer HD quality video calling with resolution of HD 720p at 30fps |
    |1.5 Mbps |Peer-to-peer HD quality video calling with resolution of HD 1080p at 30fps |
    |500kbps/1Mbps |Group Video calling |
    |1Mbps/2Mbps |HD Group video calling (540p videos on 1080p screen) |

	
1. Configure firewall ports and proxy servers.
Microsoft Teams connects to Microsoft Online Services and needs internet connectivity for this. For Teams to function correctly, you must complete the following steps:

    - Review Office 365 URLs and IPs to identify and test the firewall ports that are required for connectivity between on-premises clients and servers and Office 365 services. You must open all ports on your firewalls. Failing to open some ports or ranges will negatively affect user experience.            
    
    - Configure proxy servers so that they are bypassed, and you can connect users directly to Office 365 by using UDP, for the best audio and video quality. When real-time media is forced to traverse a proxy server, the media stack in Teams is forced to fail back to TCP, which negatively affects quality.
 
            > [!NOTE]
            > When it comes to Teams traffic over proxies, Microsoft recommends bypassing proxies. Proxies don't make Teams more secure because the traffic is already encrypted. Using a proxy can cause issues. Performance-related problems can be introduced to the environment through latency and packet loss. Issues such as these will result in a negative experience in such Teams scenarios as audio and video, where real-time streams are essential.    

            If you need to use a proxy server, Microsoft strongly recommends using external DNS resolution, direct UDP based routing, and allowing UDP traffic.

            It’s also a good practice to test whether all ports are opened by running the [Network Assessment Tool](https://www.microsoft.com/download/details.aspx?id=53885) on a regular basis. 

1. Follow the other recommendations in our networking guidelines: [Media Quality and Network Connectivity Performance](https://docs.microsoft.com/en-us/SkypeForBusiness/optimizing-your-network/media-quality-and-network-connectivity-performance?redirectSourcePath=%252fen-us%252farticle%252fMedia-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).
