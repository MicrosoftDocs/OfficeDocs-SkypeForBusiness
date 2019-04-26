---
title: Plan users' experience of Microsoft Teams
author: rmw2890
ms.author: Rowille
manager: serdars
ms.date: 03/13/2018
ms.topic: conceptual
ms.service: msteams
search.appverid: MET150
ms.reviewer: rowille
description: Choose Teams client apps, plan for endpoint quality, get recommendations for deploying Wi-Fi endpoints and choosing audio devices. 
localization_priority: Normal
MS.collection: 
- Teams_ITAdmin_PracticalGuidance
- M365-collaboration
appliesto:
- Microsoft Teams
---

# Plan my users’ experience

This article gives an overview of the requirements for properly identifying the elements of your cloud voice services deployment that directly affect your users’ experience. By preparing for these items before deployment, you’ll increase your chances of successfully delivering a high-quality, reliable experience for users. 

## Client deployment

Microsoft Teams has clients available for web, desktop (Windows and Mac), and
mobile (Android and iOS). For additional details about how the
desktop (Windows and Mac) and mobile clients are installed, see [Get
clients for Microsoft
Teams](https://docs.microsoft.com/microsoftteams/get-clients).

## Client updates

One of the key benefits of Teams is that the client is kept up to date
automatically. The clients on the PC and Mac are updated by using a background
process that checks for new builds and downloads the new client when the app is
idle.

<!--ENDOFSECTION-->

## Plan for endpoint quality

As you can see from the diagram below, endpoints are an important building block
in providing a quality experience for users.

![Diagram describing the three components of quality, and how service management overlaps all three components. With a focus on endpoints.](media/plan-my-users-experience-image1.png "Diagram describing the three components of quality, and how service management overlaps all three components. With a focus on endpoints.")

Teams endpoints can run on many devices, including PCs, Macs, tablets,
and mobile devices. Part of the experience not only encompasses the device, but
how a user connects to the device—for example, using the device’s built-in
mic/speaker, earbuds, or an optimized headset. Using an optimized headset can
enrich the overall user experience.

The following guidance on endpoint planning will help you ensure your
organization has a successful onboarding experience with Teams.

## Endpoint capability

The first part of planning is to ensure all the PCs and other devices in your
organization can run Teams. This involves not just looking at the
hardware requirements, but also understanding what else the PC is doing in the
background. Many organizations run other software, including intrusion detection
systems and antimalware software, which can affect the base performance of a
device.

For information about the software requirements for Teams clients on each
platform (web, desktop, and mobile), see [Get clients for Microsoft
Teams](https://docs.microsoft.com/microsoftteams/get-clients).

## Endpoint firewalls

Client-side firewalls can have a significant impact on the user experience.
Client-side firewalls can affect call quality in addition to preventing a call
from being established. Configure the appropriate exclusions on the client
firewall based on the information in [Office 365 URLs and IP address
ranges](https://aka.ms/o365ips). Your third-party vendor will have specific
guidance on how to create the exclusions.

>[!NOTE]
> Microsoft Teams will automatically update the Windows Firewall with an
appropriate firewall configuration.

## Wi-Fi recommendations for endpoints

It takes significant planning to deploy an optimized Wi-Fi network to support
real-time workloads in Microsoft Teams. The following sections provide some
general guidance that can help you avoid common pitfalls when planning for
endpoints.

### Wi-Fi drivers

Some Wi-Fi drivers can be problematic. As an example, a driver might have very
aggressive roaming behaviors between access points, causing poor call quality.
This isn’t a common occurrence, but it’s important to ensure that Wi-Fi drivers
on the PC have been updated and tested prior to deployment.

### Wi-Fi bands

There are primarily two types of bands used in Wi-Fi equipment today, 2.4 GHz
and 5.0 GHz. If your organization provides both bands, you should configure your
driver settings to prefer the 5.0 GHz band. This band is much denser in terms of
throughput and is less affected by the interference seen in the 2.4 GHz band.
This recommendation assumes that you’ve properly optimized the 5.0 GHz network
band.

### Wi-Fi radio type

Plan for devices that support the newer Wi-Fi radio types. You can get very good
Wi-Fi performance if you leverage 802.11ac or newer on the devices you
provision.

### Wireless avoidance

Some organizations prefer to avoid Wi-Fi altogether. Sometimes this guidance is
provided through a recommendation to users to connect directly to a wired
network. In some cases, the network binding order might have the wireless
connection preferred and continue to use that connection even though the PC is
connected to the wired connection. To avoid this unintended behavior, configure
the binding order to avoid this scenario.

### 802.11 Power Save protocol

If your organization uses wireless access points or routers that don’t support
the 802.11 Power Save protocol, you might experience dropped calls or poor call
quality in Microsoft Teams running on Windows devices. If it’s not possible to
upgrade your wireless access point or routers, you should update Windows Power
Plan settings on devices that run on battery power. Further detail and
configuration guidance is provided in the following [support
article](https://support.microsoft.com/help/928152/you-may-experience-connectivity-issues-or-performance-issues-when-you).

<table>
<tr><td><img src="media/audio_conferencing_image7.png" alt=""/> <br/>Decision points</td><td><ul><li>What Teams clients will be deployed in your organization?</li><li>How will you initially deploy Teams clients to your users?</li><li>Who is responsible for evaluating endpoints and devices to validate they meet Teams requirements for a quality experience?</li></ul></td></tr>
<tr><td><img src="media/audio_conferencing_image9.png" alt=""/><br/>Next steps</td><td><ul><li>Document the process that will be followed to deploy Teams clients.</li><li>Evaluate endpoints and devices and perform and remediation required.</li></ul></td></tr>
</table>

<!--ENDOFSECTION-->

## Devices for Teams

Microsoft Teams can be used for meetings or as a phone system. When using these
features, the interface device that is used for Teams plays an important role in
the user experience.

Using a built-in PC speaker and microphone might sound acceptable to the user
who has that configuration. But typically, those devices aren’t optimized for
noise cancellation, and any type of ambient noise can have a downstream impact
on others on the call. Leveraging devices optimized for these scenarios will
help ensure a high-quality experience.

Each device needs to meet the needs of your users. You’ll need to tailor devices
such as headsets for the different personas and use cases in your organization.
A persona-to-device mapping exercise should be completed as part of the planning
process.

After you’ve selected the devices, include them in the pilot test plan for final
validation. Leverage surveys during the pilot to collect feedback to ensure your
device strategy is optimal.

> [!NOTE]
> At this time, we recommend using audio devices that were certified
through the Skype for Business Certification program. To find devices certified
under this program, see the [USB Devices Certified for Skype for
Business](http://partnersolutions.skypeforbusiness.com/solutionscatalog/personal-peripherals-pcs)
solutions catalog.

<table>
<tr><td><img src="media/audio_conferencing_image7.png" alt=""/> <br/>Decision points</td><td><ul><li>Decide on your organization’s overall device strategy for user and meeting room experiences.</li></ul></td></tr>
<tr><td><img src="media/audio_conferencing_image9.png" alt=""/><br/>Next steps</td><td><ul><li>Complete a persona-to-device mapping exercise for your organization.</li><li>Document the process for obtaining devices for users and meeting rooms.</li><li>Document the process for deploying and configuration devices for users and meeting rooms.</li><li>Procure initial devices to begin your deployment.</li></ul></td></tr>
</table>

<!--ENDOFSECTION-->