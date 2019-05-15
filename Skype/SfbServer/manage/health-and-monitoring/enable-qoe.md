---
title: "Enable Quality of Experience in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: c8bb3c67-b324-4d94-8158-00c792c7ac42
description: "Summary: learn how to enable Quality of Experience (QoE) in Skype for Business Server."
---

# Enable Quality of Experience in Skype for Business Server

**Summary:** learn how to enable Quality of Experience (QoE) in Skype for Business Server.

Quality of Experience (QoE) records numeric data that indicates the media quality and information about participants, device names, drivers, IP addresses, and endpoint types involved in calls and sessions. For details, see [Planning for Monitoring](https://technet.microsoft.com/library/26cead5a-183c-42f1-a4b0-0e8d61c6159d.aspx) in the Planning documentation.

Use the following procedure to enable QoE for your whole organization or each site in your organization.

> [!NOTE]
> To enable QoE, you must first configure monitoring and a monitoring back-end database. For details, see [Deploying Monitoring](https://technet.microsoft.com/library/117f4a3e-0670-4388-a553-b9854921145f.aspx).

### To enable QoE by using Skype for Business Server Control Panel

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or assigned to the CsServerAdministrator or CsAdministrator role, log on to any computer that is in the network in which you deployed Skype for Business Server.

2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel.

3. In the left navigation bar, click **Monitoring and Archiving**, and then click **Quality of Experience Data**.

4. On the **Quality of Experience Data** page, click the appropriate collection from the table, click **Action**, and then click **Enable QoE**.

## Enabling QoE by Using Windows PowerShell Cmdlets

You can enable QoE by using Windows PowerShell and the **Set-CsQoEConfiguration** cmdlet. You can run this cmdlet either from the Skype for Business Server Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Skype for Business Server, see the blog article ["Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell"](https://go.microsoft.com/fwlink/p/?linkId=255876). The process is the same in Skype for Business Server.

### To enable QoE for a single location

 To enable QoE, set the EnableQoE parameter to True ($True).

  ```
  Set-CsQoEConfiguration -Identity "site:Redmond" -EnableQoE $True
  ```

### To disable QoE for a single location

 To disable QoE, set the EnableQoE parameter to False ($False). This does not uninstall monitoring. It pauses the collection and storage of QoE data.

  ```
  Set-CsQoEConfiguration -Identity "site:Redmond" -EnableQoE $False
  ```

### To use a single command to enable QoE in multiple locations

 This command enables QoE for all the QoE configuration settings currently in use in your organization.

  ```
  Get-CsQoEConfiguration | Set-CsQoEConfiguration "site:Redmond" -EnableQoE $True
  ```

For details, see [Set-CsQoEConfiguration](https://docs.microsoft.com/powershell/module/skype/set-csqoeconfiguration?view=skype-ps).

## See also

[Planning for Monitoring](https://technet.microsoft.com/library/26cead5a-183c-42f1-a4b0-0e8d61c6159d.aspx)

[Deploying Monitoring](https://technet.microsoft.com/library/117f4a3e-0670-4388-a553-b9854921145f.aspx)

