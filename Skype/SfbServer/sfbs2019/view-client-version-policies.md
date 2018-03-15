---
title: "View client version policies in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: End User
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 6cd9a897-c694-4d6a-8259-2d3c01fce275
description: "Client version policies are used to apply a set of client versioning rules globally or to a particular site, pool, or group of users. You can view the client version policies that have been configured in your Lync Server 2013 environment from Lync Server 2013 Control Panel or Lync Server 2013 Management Shell."
---

# View client version policies in Lync Server 2013
[]
Client version policies are used to apply a set of client versioning rules globally or to a particular site, pool, or group of users. You can view the client version policies that have been configured in your Lync Server 2013 environment from Lync Server 2013 Control Panel or Lync Server 2013 Management Shell.
  
### To view client version policies by using Lync Server Control Panel

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Clients**, and then click the **Client Version Policy** navigation button. 
    
4. If you want to view the rules for a client version policy, on the **Client Version Policy** page, double-click the policy you want to view. 
    
## Viewing Client Version Policies by Using Windows PowerShell Cmdlets

You can view client version policies by using the **Get-CsClientVersionPolicy** cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876).
  
### To view client version policies

- To view information about all your client version policies, type the following command in the Lync Server Management Shell and then press ENTER:
    
  ```
  Get-CsClientVersionPolicy
  ```

    That will return information similar to this:
    
  ```
  Identity    : Global
  Rules       : {RuleId=2336c611-a243-4c5d-994b-eea8a524d0e4;
                Description=;Action=Block;ActionUrl=;MajorVersion=1;
                MinorVersion=3;BuildNumber=;QfeNumber=;
                UserAgent=RTC;UserAgentFullName=;Enabled=True;
                CompareOp=LEQ, RuleId=342c9b90-4cef-483a-a73a-
                4fe75c88711d;Description=;Action=Block;ActionUrl=;
                MajorVersion=5;MinorVersion=;BuildNumber=;QfeNumber=;
                UserAgent=WM;UserAgentFullName=;Enabled=True;
                CompareOp=LEQ,RuleId=ea03af61-9db5-4bf9-af3f-042
                ab8dd9994;Description=;Action=Block;ActionUrl=;
                MajorVersion=3;MinorVersion=5;BuildNumber=6907;
                QfeNumber=83;UserAgent=OC;UserAgentFullName=;
                Enabled=True;CompareOp=LEQ, RuleId=831edb68-
                e482-4431-a10e-add365ba8099;Description=;
                Action=Block;ActionUrl=;MajorVersion=2;MinorVersion=0;
                BuildNumber=5999;QfeNumber=;UserAgent=UCCP;
                UserAgentFullName=;Enabled=True;CompareOp=LEQ...}
  Description :
  ```

For details, see the Help topic for the [Get-CsClientVersionPolicy](get-csclientversionpolicy.md) cmdlet. 
  

