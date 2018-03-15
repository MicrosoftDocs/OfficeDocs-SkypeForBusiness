---
title: "Working with parameters in Skype for Business Online"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 6/22/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365_Hybrid
ms.assetid: 29ebda0f-ae5f-4512-ad59-240c3605b240

description: "When using the Identity parameter, you may notice that the parameter value kenmyer@litwareinc.com is enclosed in double quotation marks:"
---

# Working with parameters in Skype for Business Online
[]
When using the Identity parameter, you may notice that the parameter value kenmyer@litwareinc.com is enclosed in double quotation marks:
  
```
-Identity "kenmyer@litwareinc.com"
```

One of the questions that people new to Windows PowerShell invariably ask is this: when should I use double quotation marks and when should I not use double quotation marks? There is no simple answer to this question, but there are some general rules to follow:
  
- Double quotation marks are typically not required when the parameter value is a number. For example, to limit the number of users returned by the [Get-CsOnlineUser](get-csonlineuser.md) cmdlet, use this syntax: 
    
  ```
  -ResultSize 100
  ```

    In fact, you should never put double quotation marks around a number. If you do, Windows PowerShell might have difficulty interpreting the value as a number.
    
    Similarly, make sure that you do not include commas in a number. For example, if you wanted to set the result size to 10,000, this syntax would be incorrect:
    
  ```
  -ResultSize 10,000
  ```

    This syntax will create an error, because Windows PowerShell uses the comma as a way to separate argument values. In this case, Windows PowerShell will assume that you are passing two separate parameter values: 10 and 000. Because you can't set a result size simultaneously to 10 and to 0, an error occurs. Use this comma-free syntax instead:
    
  ```
  -ResultSize 10000
  ```

- Double quotation marks are typically also not required when the parameter value is a date:
    
  ```
  -StartDate 6/1/2013
  ```

    However, this is true only when the time is not included. If you include the time (which means putting a blank space between the date and time), then the parameter value must be enclosed in double quotation marks:
    
  ```
  -StartDate "6/1/2013 10:00AM"
  ```

    Keep in mind that the preceding command is formatted for computers using US English for their Region settings. If you are not using US English, you should format dates and times based on the settings for your computer. To check for the Region settings used by Windows PowerShell, run this command from the Windows PowerShell prompt:
    
  ```
  Get-Host | Select-Object CurrentUICulture
  ```

- String values (such as a person's name) typically do not require double quotation marks. The main exceptions occur when that string value includes restricted characters, such as a blank space, a comma, or other punctuation marks. For example, this syntax works because the user's identity does not include any of the restricted characters:
    
  ```
  -Identity "kenmyer@litwareinc.com"
  ```

    However, this command will fail because the Identity includes a blank space:
    
  ```
  -Identity Ken Myer
  ```

    The preceding command fails because Windows PowerShell uses blank spaces to separate individual parameters. In turn, that means that Windows PowerShell thinks that the Identity parameter is Ken and that Myer is a brand-new parameter. As a result, you'll get back the following error message:
    
  ```
  Get-CsOnlineUser : A positional parameter cannot be found that accepts argument 'Myer'.
  ```

    To use a parameter value that includes a blank space (or a comma or any other restricted character), enclose that value in double quotation marks:
    
  ```
  -Identity "Ken Myer"
  ```

    In most cases Windows PowerShell lets you use single quotation marks instead of double quotation marks. For example, this is valid Windows PowerShell syntax:
    
  ```
  -Identity 'Ken Myer'
  ```

    Note, however, that you must use the same type of quotation mark at the beginning and at the end of the string. This is not valid Windows PowerShell syntax:
    
  ```
  -Identity "Ken Myer'
  ```

    If you try to run this command you will see the following displayed in the Windows PowerShell console:
    
  ```
  >>
  ```

    The double arrow is a way of prompting you to complete your command: because you started with double quotation marks, Windows PowerShell expects you to finish with double quotation marks. If you get the \>\> prompt, press Ctrl-C to cancel your command, and try again.
    
- Double quotation marks should not be used with Boolean (True/False) values. Note, too, that you must use the Windows PowerShell variables $True and $False when specifying True/False values. For example:
    
  ```
  -EnterpriseVoiceEnabled $True
  ```

There are also certain Windows PowerShell parameters known as switch parameters that do not accept parameter values: 
  
```
-WhatIf
```

Not only are parameter values not required when using a switch parameter, but including a parameter value will actually generate an error. For example, if you try to run this command:
  
```
-WhatIf $True
```

That command will fail with an error message similar to this:
  
```
Set-CsUserAcp : A positional parameter cannot be found that accepts argument 'True'.
```

Your ability to manage Skype for Business Online by using Windows PowerShell requires that you know which cmdlets are available for use. You must also know which parameters are available for each cmdlet, and you must know the data type of each parameter (that is, whether the parameter accepts a date value, a string value, a number, and so on). This information (along with numerous examples on how to use the cmdlets) can be found in the Help topics for the Skype for Business Online cmdlets. For example, here are the parameters available for use with the [Set-CsTenantPublicProvider](set-cstenantpublicprovider.md) cmdlet: 
  
![Parameters for a specific PowerShell cmdlet](media/LyncOnlinePowerShell_Parameters_Table.png)
  
As you can see, the parameter table provides a description of the cmdlet; indicates whether the parameter is required (mandatory) or optional; and tells you the data type of each parameter. Note that the data type shown in the table is the official data type used by the .NET Framework. This means the data type is shown as System.Management.Automation.SwitchParameter instead of just Switch Parameter. Here's a quick guide to the data types most commonly used by the Skype for Business Online cmdlets:
  
|**Parameter**|**Description**|
|:-----|:-----|
|Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |A string value representing the Identity of a user. This is typically the user's UPN or SIP address:  <br/> ```-Identity "kenmyer@litwareinc.com"```|
|Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |An FQDN is a fully qualified domain name. For example:  <br/> ```-Fqdn "atl-lync-001.litwareinc.com"```|
|System.Boolean  <br/> |A Boolean value is a True/False value. Remember, you must use the Windows PowerShell variables $True and $False when specifying Boolean values:  <br/> ```-Enabled $True -EnterpriseVoiceEnabled $False```|
|System.Guid  <br/> |GUID is the acronym for globally unique identifier, a unique identifier which, in Skype for Business Online, is assigned to each Skype for Business Online tenant. For example:  <br/> ```-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"```You can retrieve the GUID assigned to your Skype for Business Online tenants by using this command:  <br/> ```Get-CsTenant | Select-Object TenantId```|
|System.Management.Automation.SwitchParameter  <br/> |Switch parameters are named this because they are either switched on or they off. If the parameter is present, then the switch is on, so to speak; if the parameter is not present, the switch is off. For example, to use the Confirm parameter to require confirmation before running a command, include the Confirm parameter (without a parameter value) as part of the command. For example:  <br/> ```Remove-CsUserAcp -Identity "Ken Myer" -Confirm```If you do not want to require confirmation, then do not include the Confirm parameter:  <br/> ```Remove-CsUserAcp -Identity "Ken Myer"```|
|System.String  <br/> |A string value is an alphanumeric value; that is, it can contain (in general) any character that can be typed on the keyboard. For example:  <br/> ```-Password "abc123%&amp;*"```It's a good idea to enclose string values in double quotation marks. This isn't always required. However, it is required if your string value contains a blank space or comma, or if it happens to be a reserved Windows PowerShell keyword. (A keyword is a command or other element that is part of the Windows PowerShell language itself. For example, "If" and "End" are both Windows PowerShell keywords. For more information, type the following command from the Windows PowerShell command prompt:  <br/> Get-Help about_Reserved_Words  <br/> |
   
## See also

#### 

[An introduction to Windows PowerShell and Skype for Business Online](an-introduction-to-windows-powershell-and-skype-for-business-online.md)

