---
title: "Debug-CsDataConference"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 1bf128a6-d4d8-41ec-a8e9-dc1cdcd73200
description: "Returns diagnostic information for the data conferencing capabilities included in Skype for Business Server 2015."
---

# Debug-CsDataConference
 
Returns diagnostic information for the data conferencing capabilities included in Skype for Business Server 2015.
  
This cmdlet was introduced in the Cumulative Updates for Lync Server 2013:February 2013. 
  
```
Debug-CsDataConference [-Force <SwitchParameter>] [-Report <String>] [-TargetFqdn <Fqdn>]

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 returns diagnostic information for the Conferencing Server installed on the local computer.
  
```
Debug-CsDataConference
```

### Example 2

In Example 2, diagnostic information is returned for the Conferencing Server installed on the remote computer atl-cs-001.litwareinc.com.
  
```
Debug-CsDataConference -TargetFqdn "atl-cs-001.litwareinc.com"
```

### Example 3

Example 3 returns detailed Conferencing Server diagnostic information for the local computer, but displays this information in an easy-to-read format. To do this, the command first calls the **Debug-CsDataConference** cmdlet to return the diagnostic information. That information is then piped to the **Select-Object** cmdlet. The **Select-Object** cmdlet uses the ExpandProperty parameter to return complete information for the Details property. (By default, only a small portion of the data in the Details property is displayed onscreen.) Finally, the data found in the Details property is piped to the **Format-List** cmdlet, which displays the data in an easy-to-read format.
  
```
Debug-CsDataConference | Select-Object -ExpandProperty Details | Format-List
```

## Detailed Description
<a name="Examples"> </a>

 **Skype for Business Server Control Panel:** The functions carried out by the **Debug-CsDataConference** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="Examples"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any nonfatal error message that might occur when running the command.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example:  `-Report "C:\Logs\DataConference.html"` <br/> |
| _TargetFqdn_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name of the computer where the Skype for Business Server 2015 Conferencing Server is installed. If this parameter is not included, the **Debug-CsDataConference** cmdlet will run against the local computer. If Conferencing Server is not installed on the local computer, an error will occur. <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="Examples"> </a>

None. The **Debug-CsDataConference** cmdlet does not accept pipelined input.
  
## Return Types
<a name="Examples"> </a>

The **Debug-CsDataConference** cmdlet returns instances of the Microsoft.Rtc.Management.DataCollabDiag.ServerResult object.
  
## See also
<a name="Examples"> </a>

#### 

[Test-CsDataConference](test-csdataconference.md)

