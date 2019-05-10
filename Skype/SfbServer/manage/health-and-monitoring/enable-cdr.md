---
title: "Enable call detail recording in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 3b28e432-596f-45a5-a070-577d6fa748d9
description: "Summary: Learn how to enable Call detail recording (CDR) records in Skype for Business Server."
---

# Enable call detail recording in Skype for Business Server

**Summary:** Learn how to enable Call detail recording (CDR) records in Skype for Business Server.

Call detail recording (CDR) records usage and diagnostic information about peer-to-peer activities including instance messaging, Voice over Internet Protocol (VoIP) calls, application sharing, file transfer, and meetings. The usage data can be used to calculate return on investment (ROI) and the diagnostic data can be used to troubleshoot peer-to-peer activities and meetings.

Use the following procedure to enable CDR for your whole organization or each site in your organization.

> [!NOTE]
> In order to enable CDR you must configure monitoring and a monitoring database. For details, see [Deploying Monitoring](https://technet.microsoft.com/library/117f4a3e-0670-4388-a553-b9854921145f.aspx).

### To enable CDR with Skype for Business Server Control Panel

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or assigned to the CsServerAdministrator or CsAdministrator role, log on to any computer that is in the network in which you deployed Skype for Business Server.

2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel.

3. In the left navigation bar, click **Monitoring and Archiving**, and then click **Call Detail Recording**.

4. On the **Call Detail Recording** page, click the appropriate site from the table, click **Action**, and then click **Enable CDR**.

    > [!NOTE]
    > CDR is enabled by default.

## Enabling CDR by using Windows PowerShell cmdlets

You can enable CDR by using Windows PowerShell and the **Set-CsCdrConfiguration** cmdlet. You can run this cmdlet either from the Skype for Business Server Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Skype for Business Server, see the blog article ["Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell"](https://go.microsoft.com/fwlink/p/?linkId=255876). The process is the same in Skype for Business Server.

### To enable CDR for a single location

 To disable CDR, set the EnableCDR parameter to True ($True).

  ```
  Set-CsCdrConfiguration -Identity "site:Redmond" -EnableCDR $True
  ```

### To disable CDR for a single location

 To disable CDR, set the EnableCDR parameter to False ($False). Disabling CDR does not uninstall monitoring. It pauses the collection and storage of CDR data.

  ```
  Set-CsCdrConfiguration -Identity "site:Redmond" -EnableCDR $False
  ```

### To use a single command to enable CDR in multiple locations

 This command enables CDR for all the CDR configuration settings currently in use in your organization.

  ```
  Get-CsCdrConfiguration | Set-CsCdrConfiguration "site:Redmond" -EnableCDR $True
  ```

For more information, see the help topic for the [Set-CsCdrConfiguration](https://docs.microsoft.com/powershell/module/skype/set-cscdrconfiguration?view=skype-ps) cmdlet.

## See also

[Planning for Monitoring](https://technet.microsoft.com/library/26cead5a-183c-42f1-a4b0-0e8d61c6159d.aspx)

[Deploying Monitoring](https://technet.microsoft.com/library/117f4a3e-0670-4388-a553-b9854921145f.aspx)
