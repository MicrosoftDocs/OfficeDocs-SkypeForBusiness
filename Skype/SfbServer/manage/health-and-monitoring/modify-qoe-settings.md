---
title: "Modify Quality of Experience settings in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: a6b41de2-1466-4240-8a70-14ce6f0f3ddc
description: "Summary: Learn how to specify retention of QoE data in Skype for Business Server."
---

# Modify Quality of Experience settings in Skype for Business Server

**Summary:** Learn how to specify retention of QoE data in Skype for Business Server.

By default, Quality of Experience (QoE) data is purged after 60 days. You can use the settings on the **Quality of Experience Data** page to retain the data for a longer or shorter period of time. If you disable QoE, data that was captured before QoE was enabled will also be subject to purging.

> [!NOTE]
> You should configure call detail recording (CDR) and QoE to retain data for the same number of days. Each call in the call detail reports (CDRs), available from the Monitoring Reports homepage, includes CDR and QoE information. If the purging duration for CDR and QoE is different, some calls may only include CDR data, while other may only include QoE data.

The following procedure describes how to configure purge settings for QoE data.

### To specify retention of QoE data by using Skype for Business Server Control Panel

1.  Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the CsVoiceAdministrator, CsServerAdministrator, or CsAdministrator role. For details, see **Delegate Setup Permissions**.

2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel.

3. In the left navigation bar, click **Monitoring and Archiving**, and then click **Quality of Experience Data**.

4. On the **Quality of Experience Data** page, click the appropriate site from the table, click **Edit**, and then click **Show Details**.

5. To turn on purging, select **Enable Purging of QoE**.

6. In **Keep QoE for maximum duration (days)** select the maximum number of days that QoE data should be retained.

7. Click **Commit**.

## Specifying QoE Retention by Using Windows PowerShell Cmdlets

You can create QoE retention settings by using Windows PowerShell and the **Set-CsQoEConfiguration** cmdlet. You can run this cmdlet either from the Skype for Business Server Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Skype for Business Server, see the blog article ["Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell"](https://go.microsoft.com/fwlink/p/?linkId=255876). The process is the same in Skype for Business Server.

### To specify QoE retention for a specific location

- This command enables purging of QoE data for the Redmond site, and configures the site to maintain QoE data for 20 days.

  ```
  Set-CsQoeConfiguration -Identity "site:Redmond" -EnablePurging -KeepQoEDataForDays 20
  ```

### To specify QoE retention for multiple locations

- This command configures QoE retention for all the QoE configuration settings in use in an organization.

  ```
  Get-CsQoEConfiguration | Set-CsQoEConfiguration-EnablePurging -KeepQoEDataForDays 20
  ```

For more information, see the help topic for the [Set-CsQoEConfiguration](https://docs.microsoft.com/powershell/module/skype/set-csqoeconfiguration?view=skype-ps) cmdlet.

## See also

[Deploying Monitoring](https://technet.microsoft.com/library/117f4a3e-0670-4388-a553-b9854921145f.aspx)
