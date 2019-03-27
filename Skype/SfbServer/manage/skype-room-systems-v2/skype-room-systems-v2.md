---
title: "Management overview for Skype Room Systems v2"
ms.author: jambirk
author: jambirk
ms.reviewer: davgroom
manager: serdars
ms.date: 5/10/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 39d7dc65-22c3-400f-91f1-87ed2fd792b6
description: "Management overview for Skype Room Systems v2."
---

# Management overview 

It’s essential that you develop and execute ongoing maintenance and operations to ensure that your Skype Room Systems v2 systems are available for your users and deliver a great user experience. 

## Monitoring 

Monitoring Skype Room Systems v2 systems consists of two key activities:

-  Device, application, and peripheral device monitoring

-  Quality and reliability monitoring (CQD)

### Skype Room Systems v2 device, application, and peripheral device monitoring

To ensure that users are able to use the Skype Room Systems v2 units, the units must be on, connected to the network with the Skype Room Systems v2 application correctly configured, and be connected to functioning peripheral devices. 


Information about the state of the Skype Room Systems v2 application and connected peripheral devices is written by the Skype Room Systems v2 application to the Windows event log and documented in [Understand the log entries](azure-monitor.md#understand-the-log-entries). 

|**Setting**|**Allows**|
|:-----|:-----|
|HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon AutoAdminLogon = (dword) 1  <br/> |Enables Skype Room Systems v2 to boot up  <br/> |
|Power Management -\> On AC, turn screen off after 10 minutes  <br/> Power Management -\> On AC, never put system to sleep  <br/> |Enables Skype Room Systems v2 to turn off attached displays and wake up automatically  <br/> |
|net accounts /maxpwage:unlimited  <br/> Or equivalent means of disabling password expiration on the local account. Failure to do this will eventually cause the Skype account to fail logon complaining about an expired password. Note that this impacts all local accounts on the machine, and thus failure to set this will also cause the administrative account on the box to eventually expire as well.  <br/> |Enables Skype account to always log in  <br/> |
   
Transferring files using Group Policies is discussed in [Configure a File Item](https://technet.microsoft.com/en-us/library/cc772536%28v=ws.11%29.aspx).
  
## Remote Management using PowerShell
<a name="RemotePS"> </a>


We recommend that you use Microsoft Operations Manager Suite to monitor your Skype Room Systems v2 systems. For guidance on how to set up monitoring and basic alerting, see [Deploy Skype Room Systems v2 management with Azure Monitor](../../deploy/deploy-clients/azure-monitor.md). 

Using this guidance, you can create a simple-to-use dashboard to identify any issues with your Skype Room Systems v2 units across your deployment. 

|    |     |
|-----------|------------|
|![](../../media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Confirm that you'll use Operations Management Suite to monitor your Skype Room Systems v2 deployment.</li><li>Decide the target distribution list you’ll use for email alerts.</li></ul>|
|![](../../media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Define your quality and reliability monitoring approach.</li></ul>|

## Quality and reliability monitoring (CQD)

We recommend that you implement ongoing operational quality and reliability monitoring procedures as part of your deployment to monitor the trending of call and meeting quality and reliability, identifying any areas of concern and working toward a resolution. 

When you upload your building information to CQD you can investigate call quality and reliability trends on a per-building level, which makes it easy to compare buildings and focus your attention on specific problems. For more information, download the [Monitor-CQD for Skype for Business Online-Delivery and Operations Guide](https://myadvisor.fasttrack.microsoft.com/CloudVoice/Downloads?SelectedIDs=6_2_0_15). 

We recommend that you review and follow the [Quality of Experience Review Guide](https://aka.ms/qerguide) to identify quality and reliability trends, and create an action plan to resolve them. 

## Updating the Skype Room Systems v2 OS and Skype Room Systems application 

We recommend that you update the Skype Room Systems v2 OS and Skype Room Systems v2 application to benefit from product updates and improvements. For detailed guidance, see [Manage Skype Room Systems v2](room-systems-v2-operations.md#software-updates). 

## Windows Updates

Skype Room System v2 (SRS v2) runs on Windows 10 Enterprise IoT or Windows 10 Enterprise (VL) and receives the same Windows Updates and OS builds as a standard desktop. See [Manage Windows Updates](updates.md) for details.


## Troubleshooting

We recommend that you set up Operations Management Suite alerting as described in the section above so that your operations team and helpdesk will be alerted to any Skype Room Systems v2 issues. The options you have for PowerShell remote management are described in [Remote Management using PowerShell](room-systems-v2-operations.md#remote-management-using-powershell). In the event that a peripheral device is disconnected, you might need to rely on local “smart hands” or IT support to investigate and reconnect the devices. 

For more information about troubleshooting and admin mode, see [Manage Skype Room Systems v2](room-systems-v2-operations.md#admin-mode-and-device-management). 


## See also

[Skype Room Systems version 2 help](https://support.office.com/en-us/article/Skype-Room-Systems-version-2-help-e667f40e-5aab-40c1-bd68-611fe0002ba2)

[Plan for Skype Room Systems v2](../../plan-your-deployment/clients-and-devices/skype-room-systems-v2-0.md)

[Deploy Skype Room Systems v2](../../deploy/deploy-clients/room-systems-v2.md)

[Configure a Skype Room Systems v2 console](../../deploy/deploy-clients/console.md)

[Manage a Skype Room Systems v2 console settings remotely with an XML configuration file](xml-config-file.md)
