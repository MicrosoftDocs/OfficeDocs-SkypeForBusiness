---
title: "Configure the Primary Management Server"
ms.reviewer: 
ms.author: jambirk
author: jambirk
manager: serdars
ms.date: 2/1/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
description: "Summary: Configure your primary management server, install System Center Operations Manager, and import management packs for Skype for Business Server 2019."
---

# Configure the Primary Management Server

**Summary:** Configure your primary management server, install System Center Operations Manager, and import management packs for Skype for Business Server 2019.

To take full advantage of the new health monitoring capabilities included in Skype for Business Server 2019, you must first designate a computer to act as your primary management server. You must then install System Center Operations Manager 2012 SP1 or R2 or System Center Operations Manager 2007 R2 on that computer. In addition, you must first install a supported version of SQL Server to function as your Operations Manager back-end database.

When you install System Center Operations Manager, you will need to install all the components of that product, including:

- Operational database

- Server

- Console

- Windows PowerShell cmdlets

- Web console

- Reporting

- Data warehouse

> [!IMPORTANT]
> The "[Microsoft Report Viewer 2010 Redistributable Package](https://www.microsoft.com/en-us/download/details.aspx?id=6442)" needs to be installed before you install System Center Operations Manager 2012.

For details about these products and their installation, see the following links:

- [System Center Operations Manager 2012](https://go.microsoft.com/fwlink/p/?linkid=257527)

- [System Center Operations Manager 2007](https://technet.microsoft.com/en-us/library/bb735860.aspx)

Keep in mind that you can have only one Root Management Server per Skype for Business Server deployment.

## Importing the Skype for Business Server 2019 Management Packs

You can extend the capabilities of System Center Operations Manager by installing management packs—software that dictates which items System Center Operations Manager can monitor, how those items should be monitored, and how alerts should be triggered and reported. Skype for Business Server 2019 includes two System Center Operations Manager management packs that provide the following capabilities:

- **The Component and User Management Pack** (Microsoft.LS.2019.Monitoring.ComponentAndUser.mp) tracks Skype for Business Server issues recorded in event logs, registered by performance counters, or logged in the call detail records (CDRs) or the Quality of Experience (QoE) databases. For critical issues, System Center Operations Manager can be configured to immediately notify administrators through email, instant message, or SMS messaging. (SMS, or Short Message Service, is the technology used to send text messages from one mobile device to another.)

    > [!NOTE]
    >  For details about configuring Operations Manager notification, see [Configuring Notification](https://go.microsoft.com/fwlink/p/?LinkID=268785&amp;amp;clcid=0x409).

- **The Active Monitoring Management Pack** (Microsoft.LS.2019.Monitoring.ActiveMonitoring.mp) proactively tests key Skype for Business Server components, such as signing into to the system, exchanging instant messages, or making calls to a phone located on the public switched telephone network (PSTN). These tests are conducted by using the Skype for Business Server synthetic transaction cmdlets. For example, the **Test-CsIM** cmdlet is used to simulate an instant messaging conversation between a pair of test users. If this simulated conversation fails, an alert is generated.

Importing the management packs is a crucial step. If the management packs are not imported, you will not be able to use Operations Manager to monitor Skype for Business Server events or run Skype for Business Server synthetic transactions.

The Component and User Management Pack is used to monitor only Skype for Business Server 2019. If you are in a coexistence scenario where both Skype for Business Server 2019 and Skype for Business Server 2015 are installed, you should continue to use the Skype for Business Server 2015 management packs for your Skype for Business Server 2015 computers.

> [!NOTE]
> Management packs for Skype for Business Server 2019 include the Skype for Business Server 2019 Component and User Management Pack and the Skype for Business Server 2019 Active Monitoring Management Pack.

You can use one of the following tools to import management packs:

- **System Center Operations Manager** With this method, you use the Operations Manager to add monitoring for Skype for Business Server.

- **Operations Manager Shell** You can use the Operations Manager Shell to import directly, or to troubleshoot any issues that you encounter when you import management packs by using the System Center Operations Manager console.

### Importing the Management Packs by Using System Center Operations Manager

1. Download the SkypeForBusiness2019ManagementPacks.msi from the Microsoft Web downloads, and install the msi.

2. In System Center Operations Manager, click **Administration**.

3. In the Administration pane, right-click **Management Packs**, and then click **Import Management Packs**.

4. In the **Select Management Packs** dialog box, click **Add**, and then click **Add from disk**.

5. In the **Online Catalog Connection** dialog box, click **No**.

6. In the **Select Management Packs to import** dialog box, locate and select the files Microsoft.LS.2019.Monitoring.ActiveMonitoring.mp and Microsoft.LS.2019.Monitoring.ComponentAndUser.mp, and then click **Open**. To select multiple files in the dialog box, click the first file, and then hold down the Ctrl key and click the subsequent files.

7. In the **Select Management Packs** dialog box, click **Install**. If you get an error message and installation fails, that typically means that the management pack files are in a folder protected by the Windows User Account Control. If this occurs, copy the files to a different folder, and then restart the import and installation process.

8. In the **Select Management Packs** dialog box, click **Close**. The import and installation process might require several minutes to complete.

## Importing the Management Packs by Using the Operations Manager Shell

In general, it is easier to import the management packs by using the Operations Manager console. However, if an error occurs and the import fails, the console does not always provide adequate error reports. By comparison, the Operations Manager Shell provides detailed information. If you are using Operations Manager and you encounter issues when importing a management pack, import the pack by using the Operations Manager Shell. The information provided by Operations Manager Shell can help you determine why the import failed.

1. Click **Start**, click **All Programs**, click **Microsoft System Center 2012**, click **Operations Manager**, and then click **Operations Manager Shell**.

2. In Operations Manager Shell, type the following command at the command prompt, using the actual path to your copy of the file Microsoft.LS.2019.Monitoring.ActiveMonitoring.mp, and then press ENTER:

   ```
   Import-SCOMManagementPack -FullName "D:\MP\Microsoft.LS.2019.Monitoring.ActiveMonitoring.mp"
   ```

3. After you have imported the first management pack, repeat the process, using the path to your copy of the file Microsoft.LS.2019.Monitoring.ComponentAndUser.mp:

   ```
   Import-SCOMManagementPack -FullName "D:\MP\Microsoft.LS.2019.Monitoring.ComponentAndUser.mp"
   ```
