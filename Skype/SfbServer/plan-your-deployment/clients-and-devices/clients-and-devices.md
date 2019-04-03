---
title: "Plan for clients and devices"
ms.author: jambirk
author: jambirk
ms.reviewer: PhillipGarding
manager: serdars
ms.date: 2/20/2018
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection:
- IT_Skype16
- Strat_SB_Admin
ms.custom:
ms.assetid: 95f0852e-391d-4345-985f-0a2da50491fa
description: "Summary: Review of the supported clients and apps for Skype for Business."
---

# Plan for clients and devices

**Summary:** Review of the supported clients and apps for Skype for Business.

Today's workforce is constantly on the move. Employees need to communicate and collaborate whether working from the corporate office, at regional locations, in home offices, or on the road. Skype for Business Server supports these needs through a collection of client interfaces that you can deploy to your organization's users. Thoughtful planning ensures that employees get what they need and that Skype for Business is available to them wherever they happen to be.

## Available clients

Skype for Business Server supports several types of clients, including computer-installed client software, web-based clients, and clients for mobile devices. The primary clients are introduced in this section, for a detailed listing of all supported clients see either [Desktop client feature comparison for Skype for Business Server 2015](desktop-feature-comparison.md) or [Desktop client feature comparison for Skype for Business Server 2019](../../../SfBServer2019/plan/feature-comparison.md). If you've previously used a combination of Lync clients, note that there are unsupported [Legacy clients](clients-and-devices.md#Legacy) that are incompatible with Skype for Business Server 2019. Updates take place regularly so check this topic periodically for the latest client information.

### Skype for Business (2019)

Skype for Business (2019) is the recommended full-featured client for Skype for Business Server 2015 and 2019. See [Follow the latest updates in Skype for Business](https://support.office.com/en-us/article/What-s-new-in-Skype-for-Business-2016-cece9f93-add1-4d93-9a38-56cc598e5781) for a description of new features. Client feature support is detailed in the [Desktop client feature comparison for Skype for Business](desktop-feature-comparison.md), and user documentation is at [Skype for Business help](https://support.office.com/en-US/Skype-for-business). This client is included when a user installs Office 365.

A free basic client supporting fewer features is also available. Both versions are available for download at [Download Skype for Business across all your devices](https://products.office.com/en-us/skype-for-business/download-app?tab=tabs-3). The differences between Full and Basic clients are described in the [Basic client limitations](desktop-feature-comparison.md#Full-Basic) section.

### Skype for Business 2016

Skype for Business 2016 is a full-featured client for Skype for Business Server 2015 or 2019. See [What's new in Skype for Business 2016](https://support.office.com/en-us/article/What-s-new-in-Skype-for-Business-2016-cece9f93-add1-4d93-9a38-56cc598e5781) for a description of new features. Client feature support is detailed in the [Desktop client feature comparison for Skype for Business](desktop-feature-comparison.md), and user documentation is at [Skype for Business help](https://support.office.com/en-US/Skype-for-business). This client is included when a user installs Office 365.

A free basic client supporting fewer features is also available. Both versions are available for download at [Download Skype for Business across all your devices](https://products.office.com/en-us/skype-for-business/download-app?tab=tabs-3). The differences between Full and Basic clients are described in the [Basic client limitations](desktop-feature-comparison.md#Full-Basic) section.

### Skype for Business 2015

Skype for Business 2015 is a full-featured client for Skype for Business Server 2015 or 2019. The Skype for Business user interface has been fully redesigned and includes newly integrated features, such as Call Monitor, Skype directory integration, emoticons, and more. For a summary of changes, see [Lync is now Skype for Business — see what's new](https://support.office.com/en-in/article/aba02d7e-c801-4a82-bccd-e7207240f612). Client feature support is detailed in the [Desktop client feature comparison for Skype for Business](desktop-feature-comparison.md), and user documentation is at [Skype for Business help](https://support.office.com/en-US/Skype-for-business). This client is included when a user installs Office 365.

A free basic client supporting fewer features is also available. Both versions are available for download at [Download Skype for Business across all your devices](https://products.office.com/en-us/skype-for-business/download-app?tab=tabs-3). The differences between Full and Basic clients are described in the [Basic client limitations](desktop-feature-comparison.md#Full-Basic) section.

### Skype for Business on Mac

The [Skype for Business on Mac](https://www.microsoft.com/en-us/download/details.aspx?id=54108) client is available for download. See [Skype for Business on Mac client requirements](mac-requirements.md) to review prerequisites.

### Skype for Business for mobile devices

Clients are available for Windows Phone, iPhone/iPad, and Android. Users can get them at [Download Skype for Business across all your devices](https://products.office.com/en-us/skype-for-business/download-app?tab=tabs-3). Feature support for these clients is detailed in [Mobile client feature comparison for Skype for Business](mobile-feature-comparison.md).

> [!NOTE]
> MCX (Mobility Service) support for legacy mobile clients is no longer available in Skype for Business Server 2019. All current Skype for Business mobile clients already use Unified Communications Web API (UCWA) to support instant messaging (IM), presence, and contacts. Users with legacy clients using MCX will need to upgrade to a current client.

### Online Meeting Add-in for Skype for Business

The Online Meeting Add-in for Skype for Business supports meeting management from within Microsoft Outlook messaging and collaboration client on Windows. The Online Meeting Add-in for Skype for Business software installs automatically with Skype for Business.

### Skype for Business Web App and Skype Meetings App

If Skype for Business is not installed on a user's computer and the user clicks a meeting link in a meeting request, the Skype Meetings App or Skype for Business Web App will be installed and open.  Skype Meetings App is the client of choice for participants outside your organization. See [Plan for Meetings clients (Web App and Meetings App)](meetings-clients.md) for the requirements to use these clients.


### Skype for Business Web Scheduler

[Skype for Business Web Scheduler](https://sched.lync.com) is a web-based meeting scheduling and management tool for users of Skype for Business Online who don't have access to Microsoft Outlook, or who are on an operating system not based on Windows. With Skype for Business Web Scheduler, users can create new meetings, modify existing meetings, and send invitations using their preferred email program. Skype for Business Web Scheduler [documentation](https://support.office.com/en-us/article/Skype-for-Business-Web-Scheduler-3b24a211-6470-4a2d-81b7-22d9399d0fec?ui=en-US&amp;rs=en-US&amp;ad=US)  provides further details.

### VDI plugins

A Virtual Desktop Infrastructure (VDI) environment is used in some organizations where security and compliance issues are especially sensitive. Using Skype for Business with full audio and video on a connection like that requires heavy loads of audio and video processing on the client homed on a virtual desktop. Additional VDI plug-in software is available that offloads that processing to the end user's local machine, and reduces the load on the virtual desktop. See [Plan for Skype for Business in VDI environments](vdi-environments.md) for details on using these plugins.

### Microsoft Teams Rooms

Microsoft Teams Rooms is Microsoft's latest conferencing solution which uses a familiar interface and is easily deployed and managed, leveraging existing equipment like LCD panels for ease of installation. Microsoft Teams Rooms uses a purpose-built UWP app running on a Surface Pro 4 or Surface Pro in a console mode (once deployed the UWP app is the only app that will run on the device) and it requires its own device account on your implementation. Software is updated via both Windows store and Windows Update. See https://aka.ms/MTRDocs for details on using these room consoles in your deployment. 

### Skype for Business on Surface Hub

Microsoft Surface Hub is an all-in-one productivity device that is intended for brainstorming, collaboration, and presentations. It has its own iteration of the Skype for Business client, documented in the [Microsoft Surface Hub admin guide](https://docs.microsoft.com/surface-hub/).

## Choosing your organization's preferred client
<a name="BK_client_choose"> </a>

If your organization bought the appropriate licenses, choose the Full client, otherwise choose the Basic client.

Your users can install the client for themselves from [Download Skype for Business across all your devices](https://products.office.com/en-us/skype-for-business/download-app?tab=tabs-3). The client is also installed when users install Office 365 on Windows. If some of your users have Macs, those users will have a different set of features as described in earlier sections.

Some features available with Skype for Business Server 2015 are not available in Skype for Business Online or Skype for Business Server 2019, see [Online or Hybrid user account limitations for 2015](desktop-feature-comparison.md#Online-Hybrid) or [Online or Hybrid user account limitations for 2019](desktop-feature-comparison.md#Online-Hybrid) for specifics. Skype for Business Online Admins may want to refer to [Skype for Business Online Service Description](https://technet.microsoft.com/library/skype-for-business-online-service-description.aspx) for information on the different plans available to them.

 Before you deploy or upgrade to Skype for Business, check which clients are already in use in your organization. Use the [Desktop client feature comparison for Skype for Business](desktop-feature-comparison.md) to understand the feature support impact on those clients. This can help you communicate changes to users, pace the roll-out process, and fully understand the benefits of upgrading to the latest client.

## Ways to deploy the client to your users
<a name="BK_User_Deploy"> </a>

Client installers are available for both MSI and click-to-run type installers. The Skype for Business client-sustainment strategy may affect your choices, so you should understand the following points:

- In general Skype for Business does NOT add new features to previously released clients

- In general Skype for Business does NOT plan on shipping new features in the Skype for Business MSI after its initial release. MSI improvements between releases will primarily be quality/security in nature.

- The latest and greatest Skype for Business client experience will be found in the Skype for Business 2019 click-to-run installer.

You can do a customized deployment of the client as described in [Customize Windows client installation in Skype for Business Server](../../deploy/deploy-clients/customize-windows-client-installation.md). Installation methods are described in greater detail in [Deploy clients for Skype for Business Server](../../deploy/deploy-clients/deploy-clients.md)

### Click-to-run

Click-to-run is a Microsoft streaming and virtualization technology that you can use to install and update Office products including Skype for Business. These streaming and virtualization capabilities are based on technologies in Microsoft Application Virtualization (App-V). Click-to-run has the following advantages:

- Streamed installation of Office suite that results in short installation time

- Slipstreamed Updates and patches

- Takes up less disk space

- User-base licensing: 5 installs per user

- Customizable via XML Editor for the installation of independent programs

You may want to use the [Office Deployment Tool](https://www.microsoft.com/en-us/download/details.aspx?id=49117) for this type of installer.

Both the basic and full client versions (with choice of 32- and 64-bit versions) are available using a click-to-run installer, your users can download at [Download Skype for Business across all your devices](https://products.office.com/en-us/skype-for-business/download-app?tab=tabs-3).

### MSI

MSI is a more traditional installation method, used on the Skype for Business 2015 and 2016 clients. It allows you to manually install updates and patches, use volume licensing and activation, and is customizable via the [Office Customization Tool](https://www.microsoft.com/en-us/download/details.aspx?id=49030). You can distribute clients by applying Group Policies, by using System Center Configuration Manager, or using a third party tool.



## Legacy clients
<a name="Legacy"> </a>

Skype for Business Server 2019 and Skype for Business Online support the following previously released clients: Skype for Business 2016, Skype for Business 2015, Lync 2013.

Skype for Business Server 2015 supports the following previously released clients: Lync 2013, Lync 2010, Lync 2010 Mobile, Lync Phone Edition, and Lync 2010 Attendant. For information about these clients when used with other servers, see the [Client comparison tables for Lync Server 2013](https://technet.microsoft.com/en-us/library/gg425836%28v=ocs.15%29.aspx) and [Client comparison tables for Lync Server 2010](https://technet.microsoft.com/en-us/library/gg425836%28v=ocs.14%29.aspx).


## Client system requirements
<a name="Legacy"> </a>

See the following articles to understand the supported features, platforms, operating systems, browsers, and integration required for Skype for Business clients.

- [Plan the Skype for Business client experience for your users](user-experience.md)

- [Desktop client feature comparison for Skype for Business](desktop-feature-comparison.md)

- [Mobile client feature comparison for Skype for Business](mobile-feature-comparison.md)

- [Windows client requirements and software support](windows-requirements.md)

- [Skype for Business compatibility with Office apps](compatibility-with-office.md)

- [Skype for Business client video resolutions](video-resolutions.md)

- [Plan for Meetings clients (Web App and Meetings App)](meetings-clients.md)

- [System requirements for Skype for Business for Windows Phone](requirements-for-windows-phone.md)

- [Skype for Business on Mac client requirements](mac-requirements.md)

- [Plan for Microsoft Teams Rooms](skype-room-systems-v2-0.md)

- [Plan for Skype for Business in VDI environments](vdi-environments.md)

- Refer to the [System requirements](https://products.office.com/en-us/office-system-requirements) for the required hardware.


## See also

[Latest updates for versions of Skype for Business that use Windows Installer (MSI)](../../sfb-client-updates.md)
