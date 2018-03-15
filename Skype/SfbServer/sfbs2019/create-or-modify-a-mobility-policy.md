---
title: "Create or modify a mobility policy in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: fc2dfea0-2215-440d-9f4b-7c985da29211
description: "You can create or modify mobility policy to allow mobile users to use supported mobile devices for Lync functionality such as instant messaging (IM), presence, and contacts. You can create or modify mobility policies from Lync Server 2013 Control Panel or Lync Server 2013 Management Shell"
---

# Create or modify a mobility policy in Lync Server 2013
[]
You can create or modify mobility policy to allow mobile users to use supported mobile devices for Lync functionality such as instant messaging (IM), presence, and contacts. You can create or modify mobility policies from Lync Server 2013 Control Panel or Lync Server 2013 Management Shell
  
### To create a mobility policy with Lync Server Control Panel

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Clients**, and then click the **Mobility Policy** navigation button. 
    
4. On the **Mobility Policy** page, click **New**, and do one of the following:
    
1. To create a site mobility policy, click **Site policy**, click a site, click **OK**, review the default settings, and, if you want to, make any changes.
    
2. To create a user mobility policy, click **User policy**, type a name, review the default settings, and if you want to, make any changes.
    
5. Click **Commit**.
    
### To modify a mobility policy with Lync Server Control Panel

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Clients**, and then click the **Mobility Policy** navigation button. 
    
4. On the **Mobility Policy** page, click one of the existing mobility policies. 
    
5. On the **Edit** menu, click **Show details**.
    
6. Edit any of the settings.
    
7. Click **Commit**.
    
## Creating External Access Policies by Using Windows PowerShell Cmdlets

You can create mobility policies (at the site scope or the per-user scope) by using Windows PowerShell and the **New-CsMobilityPolicy** cmdlet. Additionally, you can use the **Set-CsMobilityPolicy** cmdlet to modify any of your existing policies, including the global policy. These cmdlets can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876).
  
### To create a mobility policy at the site scope

- This command creates a new mobility policy for the Redmond site:
    
  ```
  New-CsMobilityPolicy -Identity "site:Redmond"
  ```

    Because no parameters (other than the mandatory Identity parameter) were specified in the preceding command, the policies will use the default values for all its properties.
    
### To create a mobility policy at the per-user scope

- To create a mobility policy at the per-user scope, specify a unique Identity for the policy:
    
  ```
  New-CsMobilityPolicy -Identity "RedmondMobilityPolicy"
  ```

### To change a single property value when creating a mobility policy

- To create policies that use different property values, include the appropriate parameter and parameter value. For example, this command creates mobility policy that disables Call via Work:
    
  ```
  New-CsMobilityPolicy -Identity "site:Redmond" -EnableOutsideVoice $False
  ```

### To change multiple property values when creating a mobility policy

- Multiple property values can be modified by including multiple parameters. For example, this command creates a policy that disables both mobility and Call via Work:
    
  ```
  New-CsMobilityPolicy "site:Redmond" -EnableMobility $False -EnableOutsideVoice $False
  ```

For details, see the Help topic for the [New-CsMobilityPolicy](new-csmobilitypolicy.md) and the [Set-CsMobilityPolicy](set-csmobilitypolicy.md) cmdlets. 
  
## See also

#### 

[Configuring mobility policy in Lync Server 2013](configuring-mobility-policy.md)

