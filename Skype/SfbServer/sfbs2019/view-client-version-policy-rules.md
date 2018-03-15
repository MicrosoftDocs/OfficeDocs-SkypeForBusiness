---
title: "View client version policy rules in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: End User
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f3a0215f-f72f-4e9b-a07b-25858dc4203a
description: "A client version policy is made up of a set of client version policy rules. These rules define the actions that should be taken when users attempt to log on with specific clients and client versions. You can view client version policy rules from Lync Server 2013 Control Panel or Lync Server 2013 Management Shell."
---

# View client version policy rules in Lync Server 2013
[]
A client version policy is made up of a set of client version policy rules. These rules define the actions that should be taken when users attempt to log on with specific clients and client versions. You can view client version policy rules from Lync Server 2013 Control Panel or Lync Server 2013 Management Shell.
  
### To view client version policy rules by using Lync Server Control Panel

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Clients**, and then click the **Client Version Policy** navigation button. 
    
4. On the **Client Version Policy** page, double-click a client version policy you want to view. 
    
5. The rules appear on the **Edit Client Version Policy** page. To view the details for a rule, select the rule, and then click **Show details**.
    
## Viewing Client Version Policy Rules by Using Windows PowerShell Cmdlets

You can view client version policy rules by using Lync Server Management Shell and the **Get-CsClientVersionPolicyRule** cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876).
  
### To view client version policy rules

- To view the client version policy rules, type the following command in the Lync Server Management Shell and then press ENTER:
    
  ```
  Get-CsClientVersionPolicyRule
  ```

    That will return information similar to this for each configured rule:
    
  ```
  Identity          : Global/2336c611-a243-4c5d-994b-eea8a524d0e4
  Priority          : 0
  RuleId            : 2336c611-a243-4c5d-994b-eea8a524d0e4
  Description       :
  Action            : Block
  ActionUrl         :
  MajorVersion      : 1
  MinorVersion      : 3
  BuildNumber       :
  QfeNumber         :
  UserAgent         : RTC
  UserAgentFullName :
  Enabled           : True
  CompareOp         : LEQ
  ```

For details, see the help topic for the [Get-CsClientVersionPolicyRule](get-csclientversionpolicyrule.md) cmdlet. 
  

