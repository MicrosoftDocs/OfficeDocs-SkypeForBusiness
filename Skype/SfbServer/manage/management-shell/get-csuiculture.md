---
title: "Get-CsUICulture"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b8df7083-068b-4d5e-a9b4-448602de6586
description: "Returns information about the culture (that is, the language and regional settings) used by the Skype for Business Server Management Shell. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsUICulture
 
Returns information about the culture (that is, the language and regional settings) used by the Skype for Business Server Management Shell. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsUICulture

```

## Examples

### EXAMPLE 1

The command shown in Example 1 returns basic information about the culture currently in use by the Skype for Business Server Management Shell.
  
```
Get-CsUICulture
```

## Detailed Description

Although Skype for Business Server 2015 is available in multiple languages, the software is not a true MUI (multilingual user interface) application. Among other things, this means that the user interface for the Skype for Business Server 2015 does not change languages any time you change the operating system language. For example, suppose you have installed the U.S. English version of Skype for Business Server 2015 and are also running the Windows operating system under U.S. English. If you change the operating system culture (that is, the language and regional settings) to Danish, the Skype for Business Server Management Shell will not automatically follow suit; instead, the Skype for Business Server Management Shell user interface (including error messages and help text) will remain in U.S. English. If you need to change the culture for the Skype for Business Server Management Shell, you must run the **Set-CsUICulture** cmdlet.
  
The **Get-CsUICulture** cmdlet provides a way for you to determine the culture currently used in the Skype for Business Server Management Shell.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|||||
|This cmdlet provides only common Windows PowerShell parameters.  <br/> ||||
   
## Input Types

None. The **Get-CsUICulture** cmdlet does not accept pipelined input.
  
## Return Types

The **Get-CsUICulture** cmdlet returns instances of the System.Globalization.CultureInfo class.
  
## See also

#### 

[Set-CsUICulture](set-csuiculture.md)

