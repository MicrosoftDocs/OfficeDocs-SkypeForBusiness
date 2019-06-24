---
title: "Management overview for Microsoft Teams Rooms"
ms.author: jambirk
author: jambirk
ms.reviewer: davgroom
manager: serdars
ms.date: 5/10/2018
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 39d7dc65-22c3-400f-91f1-87ed2fd792b6
ms.collection: M365-voice
description: "Management overview for Microsoft Teams Rooms."
---

# Management overview 

It’s essential that you develop and execute ongoing maintenance and operations to ensure that your Microsoft Teams Rooms systems are available for your users and deliver a great user experience. 

## Monitoring 

Monitoring Microsoft Teams Rooms systems consists of two key activities:

-  Device, application, and peripheral device monitoring

-  Quality and reliability monitoring (CQD)

### Microsoft Teams Rooms device, application, and peripheral device monitoring

To ensure that users are able to use the Microsoft Teams Rooms units, the units must be on, connected to the network with the Microsoft Teams Rooms application correctly configured, and be connected to functioning peripheral devices. 


Information about the state of the Microsoft Teams Rooms application and connected peripheral devices is written by the Microsoft Teams Rooms application to the Windows event log and documented in [Understand the log entries](azure-monitor-manage.md#understand-the-log-entries). 

|**Setting**|**Allows**|
|:-----|:-----|
|HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon AutoAdminLogon = (dword) 1  <br/> |Enables Microsoft Teams Rooms to boot up  <br/> |
|Power Management -\> On AC, turn screen off after 10 minutes  <br/> Power Management -\> On AC, never put system to sleep  <br/> |Enables Microsoft Teams Rooms to turn off attached displays and wake up automatically  <br/> |
|net accounts /maxpwage:unlimited  <br/> Or equivalent means of disabling password expiration on the local account. Failure to do this will eventually cause the Skype account to fail logon complaining about an expired password. Note that this impacts all local accounts on the machine, and thus failure to set this will also cause the administrative account on the box to eventually expire as well.  <br/> |Enables Skype account to always log in  <br/> |
   
Transferring files using Group Policies is discussed in [Configure a File Item](https://technet.microsoft.com/en-us/library/cc772536%28v=ws.11%29.aspx).
  
## Remote Management using PowerShell
<a name="RemotePS"> </a>

We recommend that you use Microsoft Operations Manager Suite to monitor your Microsoft Teams Rooms systems. For guidance on how to set up monitoring and basic alerting, see [Deploy Microsoft Teams Rooms management with Azure Monitor](azure-monitor-deploy.md). 

Using this guidance, you can create a simple-to-use dashboard to identify any issues with your Microsoft Teams Rooms units across your deployment. 

|    |     |
|-----------|------------|
|![](../media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Confirm that you'll use Operations Management Suite to monitor your Microsoft Teams Rooms deployment.</li><li>Decide the target distribution list you’ll use for email alerts.</li></ul>|
|![](../media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Define your quality and reliability monitoring approach.</li></ul>|

## Quality and reliability monitoring (CQD)

We recommend that you implement ongoing operational quality and reliability monitoring procedures as part of your deployment to monitor the trending of call and meeting quality and reliability, identifying any areas of concern and working toward a resolution. 

When you upload your building information to CQD you can investigate call quality and reliability trends on a per-building level, which makes it easy to compare buildings and focus your attention on specific problems.

We recommend that you review and follow the [Quality of Experience Review Guide](https://aka.ms/qerguide) to identify quality and reliability trends, and create an action plan to resolve them. 

## Updating the Microsoft Teams Rooms OS and Microsoft Teams Rooms application

We recommend that you update the Microsoft Teams Rooms OS and Microsoft Teams Rooms application to benefit from product updates and improvements. For detailed guidance, see [Manage Microsoft Teams Rooms](room-systems-v2-operations.md#software-updates). 

## Windows Updates

Microsoft Teams Rooms runs on Windows 10 Enterprise IoT or Windows 10 Enterprise (VL) and receives the same Windows Updates and OS builds as a standard desktop. See [Manage Windows Updates](updates.md) for details.


## Troubleshooting

We recommend that you set up Operations Management Suite alerting as described in the section above so that your operations team and helpdesk will be alerted to any Microsoft Teams Rooms issues. The options you have for PowerShell remote management are described in [Remote Management using PowerShell](room-systems-v2-operations.md#remote-management-using-powershell). In the event that a peripheral device is disconnected, you might need to rely on local “smart hands” or IT support to investigate and reconnect the devices. 

For more information about troubleshooting and admin mode, see [Manage Microsoft Teams Rooms](room-systems-v2-operations.md#admin-mode-and-device-management). 


## See also

[Microsoft Teams Rooms help](https://support.office.com/en-us/article/Skype-Room-Systems-version-2-help-e667f40e-5aab-40c1-bd68-611fe0002ba2)

[Plan for Microsoft Teams Rooms](skype-room-systems-v2-0.md)

[Deploy Microsoft Teams Rooms](room-systems-v2.md)

[Configure a Microsoft Teams Rooms console](console.md)

[Manage a Microsoft Teams Rooms console settings remotely with an XML configuration file](xml-config-file.md)
