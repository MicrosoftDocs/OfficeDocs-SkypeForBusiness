---
title: "Get-CsClsAgentStatus"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 9bd15b0e-8f92-4ded-bbe6-0aa381d6e90d
description: "Use the Get-CsClsAgentStatus to return information about the ClsAgent service on the local machine."
---

# Get-CsClsAgentStatus
 
Use the **Get-CsClsAgentStatus** to return information about the ClsAgent service on the local machine.
  
```
Get-CsClsAgentStatus [-CacheFileLocalFolders <String>] [-DefaultXml <SwitchParameter>]

```

## Examples
<a name="Examples"> </a>

### Example 1

Returns information about the ClsAgent service on the local machine.
  
```
Get-CsClsAgentStatus
```

### Example 2

Returns the default.xml file as an **[XmlDocument]** object.
  
```
Get-CsClsAgentStatus -DefaultXml
```

## Detailed Description
<a name="DetailedDescription"> </a>

The **Get-CsClsAgentStatus** cmdlet returns information about the ClsAgent, including version, service status, log storage details, and disk free space.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _CacheFileLocalFolders_ <br/> |Optional  <br/> |System.String  <br/> |Specifies the path to search for log files stored on disk. By default the CacheFileLocalFolders path from the [Get-CsClsConfiguration](get-csclsconfiguration.md) cmdlet is used. <br/> |
| _DefaultXml_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |If specified, the cmdlet will return the default.xml file as an **[XmlDocument]** object for debugging purposes. <br/> |
| _LogFiles_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |PARAMVALUE: SwitchParameter  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None
  
## Return Types
<a name="ReturnTypes"> </a>

Returns a **[Microsoft.Rtc.Management.Cls.AgentInfo]** object, or an **[XmlDocument]** object if the _DefaultXml_ parameter is used.
  

