---
title: "What's new in Skype for Business Server 2015"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 12/20/2017
ms.audience: ITPro
ms.topic: overview
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: e62c9229-b738-45ef-b637-0b58ca8225a4
description: "Summary: Read this topic to learn about new features in Skype for Business Server 2015. For detailed information about the new client experience, see Lync is now Skype for Business -- see what's new."
---

# What's new in Skype for Business Server 2015

**Summary:** Read this topic to learn about new features in Skype for Business Server 2015. For detailed information about the new client experience, see [Lync is now Skype for Business -- see what's new](https://go.microsoft.com/fwlink/p/?LinkId=529022).
  
Lync is now Skype for Business, a communications and collaboration platform that brings together an experience inspired by Skype with the enterprise-grade security, compliance, and control of Lync. Skype for Business offers features including presence, IM, voice and video calls, and online meetings. Skype for Business provides a new client experience, a new server release, and updates to the service in Office 365. If users in your organization are already familiar with Skype, they'll appreciate the power and simplicity of Skype for Business where it's easy to find and connect with co-workers. If users in your organization are coming to Skype for Business from Lync, they'll recognize all of the features they already use but in a fresh new interface with simplified controls and new additions. In addition to the new client experience, Skype for Business Server 2015 provides several new features to improve manageability of on-premises servers and hybrid solutions.
  
New features in Skype for Business Server 2015 include improvements to:
  
- User experience  
- Voice and video support
- Mobile support
- Management of on-premises servers
- Deployment and management of hybrid solutions
- Multi-factor authentication support
    
## User experience

The Skype for Business client looks very similar to the consumer version of Skype and uses the same buttons and icons. Fewer menus and a flatter task hierarchy make it easy for users to quickly find the controls and commands they need. 
  
Skype for Business includes the new user experience described above and the Lync 2013 user experience released previously. The inclusion of both experiences allows enterprises to manage change for their users by controlling the process and timing of the new client roll-out. The default user experience depends on which version of the server you're using. Administrators choose the preferred experience by using the **Set-CsClientPolicy** cmdlet with the EnableSkypeUI parameter. For more information about configuring the client experience, see [Configure the client experience with Skype for Business](deploy/deploy-clients/configure-the-client-experience.md) and [Desktop client feature comparison for Skype for Business](plan-your-deployment/clients-and-devices/desktop-feature-comparison.md).
  
> [!NOTE]
> The Lync 2013 client experience is not an option for Skype for Business 2016 client versions. Before you attempt to configure your client environment to use the Lync 2013 client, please check the client version to ensure it does not start with the number 16; for example: 16.x.x.x. 
  
## Voice and video improvements

Skype for Business Server 2015 includes improvements to voice and video functionality, including call data collection and analysis, and improved interoperability with third-party video teleconferencing systems.
  
### Call data collection and analysis

The Rate My Call feature lets Skype for Business Server 2015 administrators collect call data. This feature is available for on-premises deployments only. Users are prompted to take a survey after completing a call. For more information, see [Rate my Call in Skype for Business Server 2015](manage/health-and-monitoring/rate-my-call.md).
  
### Improved interoperability with third-party video teleconferencing systems

The Video Interop Server (VIS) acts as an intermediary between Skype for Business Server and Cisco video teleconferencing (VTC) systems. When joining a meeting, users can now select a Cisco VTC system. The Video Interop Server (VIS) is implemented as a standalone server role for on-premises deployments. For more information, see [Plan for Video Interop Server in Skype for Business Server 2015](plan-your-deployment/video-interop-server.md).
  
### Call via Work

The Call via Work feature allows enterprise users to make voice calls from the Skype for Business client. When a user places a voice call, it is routed from Skype for Business to the originator's PBX or PSTN phone. Once the originator answers the phone, the call is then directed to the destination number. The call recipient answers, and the call is established with Skype for Business serving as the control panel. The originator can manage their presence and call controls from Skype for Business. Server administrators enable and configure Call via Work for the enterprise. For more information, see [Plan for Call Via Work in Skype for Business Server 2015](plan-your-deployment/enterprise-voice-solution/call-via-work.md). 
  
## Mobile device support improvements

Improvements to mobile device support include features to improve the mobile experience for Enterprise Edition users, such as access to conversation history and log data, enhanced mobile meeting experiences, and single sign-on support across Office. In addition, there are improvements to Android support, performance improvements, and features to simplify integration via the Common App Framework. 
  
> [!NOTE]
> Lync 2013 UCWA servers must be upgraded to Skype for Business Server 2015 to support mobile clients. 
  
### Server-side conversation history is now available on mobile devices

To enable mobile access to conversation history, missed IM, and call log data, archiving of this information is now processed through the server for all mobile clients. The Auto-accept feature for IM improves reliability by preventing server time-out messages when a mobile user doesn't respond to an IM immediately. To take advantage of the server based Exchange/Outlook folders integration, Exchange Server 2013 or newer, and updated mobile clients, are required. 
  
### Enhanced meeting experiences

Meeting functionality available on the desktop is now available to mobile users as well. New functionality includes:
  
- Asynchronous navigation of shared PowerPoint content
- Presenter's ability to take control of shared PowerPoint content
- Lobby management for presenters, allowing them to admit or deny participants
    
### Skype for Business on Android improvements

Skype for Business on Android now offers features similar to what's available on Skype for Business on iOS and Skype for Business on Windows:
  
- Continue or re-join conversations
- Enable certificate and passive authentication
- Invite others into a conversation
- Easily start group conversations
- Join a meeting without being a Skype for Business user
- Enable smartphone UI on Android tablets
- Manage meetings by adding or removing participants
    
> [!NOTE]
> These features require Android OS version 4.0 or above. 
  
## Management of on-premises servers

Skype for Business Server 2015 provides several new features to improve manageability of on-premises servers, including in-place upgrade, smart Setup, improved patching and upgrade processes, improved Front End pool cold start capability, SQL Server AlwaysOn support, and centralized logging and troubleshooting.
  
### In-place upgrade for on-premises servers

You can now upgrade Lync Server 2013 systems to Skype for Business Server 2015 using the new in-place upgrade feature, which uses existing Lync Server 2013 hardware and server investments, thereby reducing the overall cost to deploy Skype for Business Server 2015.
  
There are two scenarios for in-place upgrade: The Move User method, which requires no downtime, and the Offline method, which requires downtime. For more information about which upgrade procedure is right for your business, see [Plan to upgrade to Skype for Business Server 2015](plan-your-deployment/upgrade.md). 
  
> [!NOTE]
> The in-place option is not available if you are upgrading from Lync Server 2010. For more information about upgrading from Lync Server 2010, see [Plan to upgrade to Skype for Business Server 2015](plan-your-deployment/upgrade.md). 
  
### Smart Setup

The Smart Setup feature, which automatically detects and downloads updates, is now part of the Setup program. During the installation process, the user is asked if the installation process should check for updates. For more information, see [Install Skype for Business Server 2015](deploy/install/install.md).
  
### Improved Front End Server patching and upgrade process

Skype for Business Server introduces two new cmdlets that help make upgrading or patching Front End Servers much easier than in previous versions of Lync Server.
  
When you need to apply a patch, or perform any other maintenance, to a Front End Server, simply type **Invoke-CsComputerFailOver** and specify that server's name. Skype for Business Server moves that server's workload temporarily to the other servers in the pool. You can then perform the maintenance, and then use the **Invoke-CsComputerFailback** cmdlet to bring that server back into service. If you need to patch each server in a pool, simply follow this procedure for each server, one at a time. These new cmdlets enable you to patch servers much quicker than in previous versions, and with more reliability and a simpler workflow.
  
### Improved Front End pool cold start capability

Skype for Business Server introduces a new cmdlet that simplifies and improves the process of cold-starting an entire Front End pool. When you use the new **Start-CsPool** cmdlet, it checks pre-requisites for all the Front End Servers in the pool, then attempts to start each server. If it encounters any problems, it diagnoses them and alerts you with details and workarounds. In some cases it enables you to start the pool even if some of the individual servers are unable to start.
  
### SQL Server AlwaysOn support for on-premises servers

Skype for Business Server 2015 adds support for both SQL Server AlwaysOn Availability Groups and SQL Server AlwaysOn Failover Cluster Instances. In addition to these features, Skype for Business Server continues support for database mirroring and SQL Server clustering, as in past versions of Lync Server.
  
SQL Server AlwaysOn Availability Groups is a high availability and disaster recovery solution in SQL Server 2012 and SQL Server 2014 that provides an alternative to database mirroring. An availability group supports a failover environment for a discrete set of databases (known as availability databases) that fail over together. An availability group supports a set of read-write primary databases and one to four sets of corresponding secondary databases. Optionally, secondary databases can be made available for read-only access and for some backup operations.
  
SQL Server Failover Cluster Instances leverage Windows Server Failover Clustering (WSFC) functionality to provide local high availability through redundancy at the server-instance level—a failover cluster instance (FCI). An FCI is a single instance of SQL Server that is installed across Windows Server Failover Clustering (WSFC) nodes and, possibly, across multiple subnets.
  
For more information, see [Plan for high availability and disaster recovery in Skype for Business Server 2015](plan-your-deployment/high-availability-and-disaster-recovery/high-availability-and-disaster-recovery.md).
  
### Centralized logging and troubleshooting improvements for on-premises servers

The Centralized Logging Service is the preferred logging environment for Skype for Business Server 2015. There are no new features this release, but reliability and performance have been improved for both the service and the Centralized Logging Service Agent (ClsAgent.exe)--the service executable that communicates with the controller and receives commands that are issued by the administrator.
  
Skype for Business Server 2015 uses Windows PowerShell cmdlets to manage the logging service agents, initiate tracing, and generate reports. (Lync Server 2013 used ClsController.exe to perform these tasks.)
  
The Centralized Logging Service can run on any Skype for Business Server 2015. The built-in scenarios (pre-defined traces) remain the same, as does the ability to create custom scenarios. There is a special scenario called AlwaysOn that is always running, and allows administrators to locate common issues in near real-time.
  
The Snooper debugging tool has also been updated to allow debugging of mobility logs and will work with devices connecting to either Lync 2013 or Skype for Business Server 2015. The tool is available as a Web download from [Debugging tools](https://go.microsoft.com/fwlink/?LinkId=285257).
  
## Hybrid deployment and management

Skype for Business Server 2015 enables hybrid deployment administration and management capabilities by introducing the following features:
  
- Recommendations for hybrid deployments based on the state of the customer's on-premises assets, as determined by the OnRamp for O365 automated assistance tool.
- Enhancements to the Skype for Business Server Control Panel and the Skype for Business Server Admin Center so that administrators can use these tools to manage a hybrid deployment.
- Control Panel enhancements that let administrators sign in to an O365 tenant and set up hybrid with Skype for Business Online using the hybrid configuration wizard.
- Control Panel support for moving on-premises users to Skype for Business Online or moving Skype for Business Online users back to on-premises.
- Control Panel features to identify and filter on-premises user objects that have been moved to Skype for Business Online (that is, hybrid users) from on-premises users.
- Admin Center features to identify and filter cloud users initially created in Skype for Business Online from hybrid users migrated from on-premises to Online.
- The ability to administer hybrid users using the Control Panel for properties manageable from on-premises, and Admin Center for properties manageable from Skype for Business Online.
- Using Password Synchronization with DirSync, the ability to synchronize on-premises Active Directory passwords with the online tenant. If configured, this feature removes the need to deploy AD FS for federated authentication, but AD FS is still required for multi-factor authentication. 
- Continued support for coexistence between Skype for Business Online and Exchange on-premises.
    
> [!NOTE]
> There is no change from the Lync Online 2013 and Exchange on-premises coexistence and support experience. 
  
## Multi-factor authentication

Multi-factor authentication is a method of authentication that requires the use of more than one verification method and adds a critical second layer of security to user sign-ins and transactions. For example, requiring a user name and password, and a certificate. Skype for Business Server 2015 continues to build on the multi-factor authentication features available in the Lync Server 2013 Cumulative Updates. The significant changes in multi-factor authentication are:
  
- Use of the Office 2013 SP1 Active Directory Authentication Library for integration with Exchange and SharePoint
- Support for the multi-factor authentication feature in the Skype for Business Web App client
    
With Skype for Business multi-factor authentication, it is now possible to provide different authentication options based on geography. For example, customers can configure their environment so that internal authentication relies on Integrated Windows Authentication, while employees authenticating from outside the organization use multi-factor authentication. 
  
The Skype for Business multi-factor authentication experience is seamless regardless of:
  
- Geographic Location - Whether the user is signing in from inside or outside the organization 
- Client/Device Type - Which Skype for Business client is used and which device the client is running on (PC, mobile, iPad, etc.)
- Account Location - Whether the user is hosted in an on-premises Active Directory or in Azure Active Directory Online (O365)
