---
title: "Get-CsUICulture"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b8df7083-068b-4d5e-a9b4-448602de6586
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsUICulture
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Returns information about the culture (that is, the language and regional settings) used by the Lync Server Management Shell. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsUICulture
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 returns basic information about the culture currently in use by the Lync Server Management Shell.
  
```
Get-CsUICulture
```

## Detailed Description
<a name="sectionSection1"> </a>

Although Lync Server is available in multiple languages, the software is not a true MUI (multilingual user interface) application. Among other things, this means that the user interface for the Lync Server Management Shell does not change languages any time you change the operating system language. For example, suppose you have installed the U.S. English version of Lync Server and are also running the Windows operating system under U.S. English. If you change the operating system culture (that is, the language and regional settings) to Danish, the Lync Server Management Shell will not automatically follow suit; instead, the Lync Server Management Shell user interface (including error messages and help text) will remain in U.S. English. If you need to change the culture for the Lync Server Management Shell, you must run the **Set-CsUICulture** cmdlet. 
  
The **Get-CsUICulture** cmdlet provides a way for you to determine the culture currently used in the Lync Server Management Shell. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsUICulture** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins, RTCUniversalReadOnlyAdmins. 
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|||||
|This cmdlet provides only common Windows PowerShell parameters.  <br/> ||||
   
## Input Types
<a name="sectionSection2"> </a>

None. The **Get-CsUICulture** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Get-CsUICulture** cmdlet returns instances of the System.Globalization.CultureInfo class. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Set-CsUICulture](set-csuiculture.md)

