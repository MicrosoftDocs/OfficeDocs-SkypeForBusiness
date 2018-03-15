---
title: "Modify Quality of Experience settings in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: a6b41de2-1466-4240-8a70-14ce6f0f3ddc
description: "By default, Quality of Experience (QoE) data is purged after 60 days. You can use the settings on the Quality of Experience Data page to retain the data for a longer or shorter period of time. If you disable QoE, data that was captured before QoE was enabled will also be subject to purging."
---

# Modify Quality of Experience settings in Lync Server 2013
[]
By default, Quality of Experience (QoE) data is purged after 60 days. You can use the settings on the **Quality of Experience Data** page to retain the data for a longer or shorter period of time. If you disable QoE, data that was captured before QoE was enabled will also be subject to purging. 
  
> [!NOTE]
> You should configure call detail recording (CDR) and QoE to retain data for the same number of days. Each call in the call detail reports (CDRs), available from the Monitoring Reports homepage, includes CDR and QoE information. If the purging duration for CDR and QoE is different, some calls may only include CDR data, while other may only include QoE data. 
  
The following procedure describes how to configure purge settings for QoE data. 
  
### To specify retention of QoE data by using Lync Server Control Panel

1.  Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the CsVoiceAdministrator, CsServerAdministrator, or CsAdministrator role. For details, see [Delegate setup permissions in Lync Server 2013](delegate-setup-permissions.md).
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Monitoring and Archiving**, and then click **Quality of Experience Data**.
    
4. On the **Quality of Experience Data** page, click the appropriate site from the table, click **Edit**, and then click **Show Details**.
    
5. To turn on purging, select **Enable Purging of QoE**.
    
6. In **Keep QoE for maximum duration (days)** select the maximum number of days that QoE data should be retained. 
    
7. Click **Commit**.
    
## Specifying QoE Retention by Using Windows PowerShell Cmdlets

You can create QoE retention settings by using Windows PowerShell and the **Set-CsQoEConfiguration** cmdlet. You can run this cmdlet either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876).
  
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

For more information, see the help topic for the [Set-CsQoEConfiguration](set-csqoeconfiguration.md) cmdlet. 
  
## See also

#### 

[Deploying monitoring in Lync Server 2013](deploying-monitoring.md)

