---
title: "Needs a good title"
ms.author: jambirk
author: jambirk
manager: serdars
ms.date: 5/4/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "Needs a good description."
---

## Adoption and change management 

Skype Room Systems v2 systems introduce new capabilities to your users. It’s
important that you recognize that this will be a change for your users, and you
should ensure your campaign identifies the benefits the new system will have for
your users and the key talking points team leads can use to discuss with their
teams.

## Maintenance and operations 

It’s essential that you develop and execute ongoing maintenance and operations
to ensure that your Skype Room Systems v2 systems are available for your users
and deliver a great user experience.

### Monitoring 

Monitoring Skype Room Systems v2 systems consists of two key activities:

1.  Device, application, and peripheral device monitoring

2.  Quality and reliability monitoring (CQD)

### Skype Room Systems device, application, and peripheral device monitoring

To ensure that users are able to use the Skype Room Systems v2 units, the units
must be on, connected to the network with the Skype Room Systems v2 application
correctly configured, and be connected to functioning peripheral devices.

Information about the state of the Skype Room Systems v2 application and
connected peripheral devices is written by the Skype Room Systems v2 application
to the Windows event log and documented [in this
article](https://docs.microsoft.com/en-us/skypeforbusiness/manage/skype-room-systems-v2/oms#understand-the-log-entries).

We recommend that you use Microsoft Operations Manager Suite to monitor your
Skype Room Systems v2 systems. For guidance on how to set up monitoring and
basic alerting, see [Deploy Skype Room Systems v2 management with
OMS](https://docs.microsoft.com/en-us/skypeforbusiness/deploy/deploy-clients/with-oms).

Using this guidance, you can create a simple-to-use dashboard to identify any
issues with your Skype Room Systems v2 units across your deployment.

| Decision points | Confirm that you will use Operations Management Suite to monitor your Skype Room Systems v2 deployment. |
|-----------------|---------------------------------------------------------------------------------------------------------|


-   Decide the target distribution list you’ll use for email alerts.

| Next steps | Define your quality and reliability monitoring approach. |   |
|------------|----------------------------------------------------------|---|


### Quality and reliability monitoring (CQD)

We recommend that you implement ongoing operational quality and reliability
monitoring procedures as part of your deployment to monitor the trending of call
and meeting quality and reliability, identifying any areas of concern and
working toward a resolution.

When you upload your building information to CQD you can investigate call
quality and reliability trends on a per-building level, which makes it easy to
compare buildings and focus your attention on specific problems. For more
information, download the [Monitor-CQD for Skype for Business Online-Delivery
and Operations
Guide](https://myadvisor.fasttrack.microsoft.com/CloudVoice/Downloads?SelectedIDs=6_2_0_15).

We recommend that you review and follow the [Quality of Experience Review
Guide](https://aka.ms/qerguide) to identify quality and reliability trends, and
create an action plan to resolve them.

### Updating the Skype Room Systems v2 OS and Skype Room Systems application 

We recommend that you update the Skype Room Systems OS and Skype Room Systems
application to benefit from product updates and improvements. For detailed
guidance, see [Manage Skype Room Systems
v2](https://docs.microsoft.com/en-us/skypeforbusiness/manage/skype-room-systems-v2/skype-room-systems-v2#software-updates).

### Troubleshooting

We recommend that you set up Operations Management Suite alerting as described
in the section above so that your operations team and helpdesk will be alerted
to any Skype Room Systems issues. The options you have for PowerShell remote
management are described [in this
article](https://docs.microsoft.com/en-us/skypeforbusiness/manage/skype-room-systems-v2/skype-room-systems-v2#remote-management-using-powershell).
In the event that a peripheral device is disconnected, you might need to rely on
local “smart hands” or IT support to investigate and reconnect the devices.

For more information about troubleshooting and admin mode, see [Manage Skype
Room Systems
v2](https://docs.microsoft.com/en-us/skypeforbusiness/manage/skype-room-systems-v2/skype-room-systems-v2#admin-mode-and-device-management).
