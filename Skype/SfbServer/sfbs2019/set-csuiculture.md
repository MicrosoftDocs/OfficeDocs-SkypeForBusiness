---
title: "Set-CsUICulture"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 53fbc126-1df9-4ea0-8055-4e9530ab89d6
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Set-CsUICulture
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Enables you to modify the culture (that is, the language and regional settings) used by the Lync Server Management Shell. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsUICulture -Culture <String> [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 sets the culture for the Lync Server Management Shell to U.S. English. This is done by using the language code en-US.
  
```
Set-CsUICulture -Culture "en-US"
```

### EXAMPLE 2

Example 2 sets the culture for the Lync Server Management Shell to the default culture value. The default value is the culture setting used when you originally installed Lync Server.
  
```
Set-CsUICulture -Culture "default"
```

## Detailed Description
<a name="sectionSection1"> </a>

Although Lync Server is available in multiple languages, the software is not a true Multilingual User Interface (MUI) application. Among other things, this means that the user interface for the Lync Server Management Shell does not change languages any time you change the operating system language. For example, suppose you have installed the U.S. English version of Lync Server and are also running the Windows operating system under U.S. English. If you change the operating system culture (that is, the language and regional settings) to Danish, the Lync Server Management Shell will not automatically follow suit; instead, the Lync Server Management Shell user interface (including error messages and help text) will remain in U.S. English. If you need to change the culture for the Lync Server Management Shell, you must run the **Set-CsUICulture** cmdlet. 
  
There are two things to keep in mind when using the **Set-CsUICulture** cmdlet. First, the cmdlet can only be used to modify Lync Server Management Shell settings on the local computer; the **Set-CsUICulture** cmdlet cannot change a remote instance of Lync Server Management Shell. This is due to the fact that all the users of a computer share the same instance of the Lync Server Management Shell: allowing a remote user to change the culture would instantly change the culture for any other users of the Lync Server Management Shell, including the local user. 
  
Second, you can only set the language to U.S. English ("en-US") or to the language used when you initially installed Lync Server ("default"). For example, if you originally installed an Italian version of Lync Server, then you have two choices for configuring the UI culture: English or Italian.
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsUICulture** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins, RTCUniversalReadOnlyAdmins. 
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Culture_ <br/> |Required  <br/> |System.String  <br/> |Enables you to specify the culture used for the Lync Server Management Shell. Set the culture to "en-US" for U.S. English, or set the culture to "default" to use the language used when you originally installed Lync Server.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **Set-CsUICulture** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Set-CsUICulture** cmdlet does not return any values or objects. Instead, the cmdlet modifies existing instances of the System.Globalization.CultureInfo class. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsUICulture](get-csuiculture.md)

