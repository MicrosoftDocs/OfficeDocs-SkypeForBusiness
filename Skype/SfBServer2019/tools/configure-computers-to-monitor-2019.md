---
title: "Configure the Skype for Business Server computers that will be monitored"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 2/1/2018
audience: ITPro
ms.topic: article
ms.service: skype-for-business-server
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.collection: IT_Skype16
description: "Summary: Install the Operations Manager agent files on the Skype for Business Server 2019 computer to be monitored, and configure the computer to act as a System Center proxy."
---

# Configure the Skype for Business Server computers to monitor

**Summary:** Install the Operations Manager agent files on the Skype for Business Server 2019 computer to be monitored, and configure the computer to act as a System Center proxy.

Each Skype for Business Server 2019 computer that you want to monitor must be able to self-report its existence to the management server. To enable this process, you must install the Operations Manager agent files on each of the computers to be monitored. After installing the agent files, you must configure the computer to act as a System Center proxy. Be sure that you install and configure Skype for Business Server on these computers before carrying out these procedures.

## Installing a Certificate on a Watcher Node Located Outside the Perimeter Network
<a name="watcher_node_outside"> </a>

System Center Operations Manager agents running in a perimeter network (such as a Skype for Business Server Edge Server), outside of the enterprise (such as an external synthetic transaction watcher node), or across an Active Directory trust boundary, might require the configuration of a System Center Operations Manager Gateway Server. This server role enables agents that don't have a trust relationship with the Root Management Server to raise alerts. For details, see [Managing Gateway Servers in Operations Manager 2012](/previous-versions/system-center/system-center-2012-R2/hh212823(v=sc.12)).

If you deploy an agent in one of these locations, you need to request and configure a certificate that enables the watcher node to send alerts to System Center Operations Manager. To simplify this process, the Operations Manager team creates a set of utilities that enable you to request and install the correct type of certificate on the watcher node computer. For details, and to download these utilities, see [Obtaining Certificates for Non-Domain Joined Agents Made Easy With Certificate Generation Wizard](https://techcommunity.microsoft.com/t5/system-center-blog/obtaining-certificates-for-non-domain-joined-agents-made-easy/ba-p/340467).

### Installing the Operation Manager Agent Files

1. On your System Center setup media, double-click **Setup.exe**.

2. In the System Center Operation Manager setup wizard, select **Install Operations Manager Agent**, from Install Agent under Optional Installations

3. In the System Center setup wizard, on the Welcome to the System Center Operations Manager Setup wizard page, select **Next**.

4. On the Destination Folder page, select the folder where the Operations Manager Agent files are installed and select **Next**.

5. On the Management Group Configuration page, select **Specify Management Group information** and select **Next**.

6. On the Management Group Configuration page, type the name of your Operations Manager Management Group in the **Management Group Name** box, and then type the host name of your Operations Manager server (for example, atl-scom-001) in the **Management Server** box. If you changed the port number used by Operations Manager, enter the new port number in the **Management Server Port** box. Otherwise, leave the port at the default value of 5723, and then select **Next**.

7. On the Agent Action Account page, select **Local System** and select **Next**.

8. On the Microsoft Update page, select **I don't want to use Microsoft Update** and select **Next**.

9. On the Ready to Install page, select **Install**.

10. On the Completing the System Center Operations Manager Setup wizard page, select **Finish**.

11. Select **Exit**.

For System Center 2012, you can verify that the agent is created by clicking **Start**, clicking **All Programs**, clicking **System Center Operations Manager 2012**, and then clicking **Operations 2012 Manager Shell**. In the Operations Manager Shell, type the following Windows PowerShell command, and then press ENTER:
```PowerShell
Get-SCOMAgent
```

A list of all your Operations Manager agents appears.

## Configuring the Skype for Business Server Computer to Participate in System Center Discovery
<a name="watcher_node_outside"> </a>

To make sure that your new Skype for Business Server agent participates in the discovery process for System Center Operations Manager, you must complete the following procedure on each computer where the System Center Operations Manager console has been installed:

1. On the Administration tab, click **Agent Managed**.

2. Click on **Discovery Wizard** and complete the wizard for the computer to be discovered.

3. Reboot the Health Agent service. Rebooting the service will force discovery of the new machine. If you do not reboot the service, it could take as long as 4 hours before the new machine is discovered by System Center Operations Manager.

4. Verify that no error events were recorded in the Operations Manager event log.

5. The computer where the agent is pushed successfully will be shown under "Agent Managed" list and the computer where agent was installed manually will be shown under "Pending Management", click on the computer name and approve.

6. Right-click the name of the computer, and then click **Properties**. In the Properties dialog box, on the Security tab, select **Allow this agent to act as a proxy and discover managed objects on other computers**, and then click **OK**.