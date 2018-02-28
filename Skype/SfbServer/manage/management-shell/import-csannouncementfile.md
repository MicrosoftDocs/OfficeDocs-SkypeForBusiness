---
title: "Import-CsAnnouncementFile"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 66da2361-e325-4085-8b6f-47a8423edaab
description: "Imports an announcement file to the Announcement service audio library. This cmdlet was introduced in Lync Server 2010."
---

# Import-CsAnnouncementFile
[]
Imports an announcement file to the Announcement service audio library. This cmdlet was introduced in Lync Server 2010.
  
```
Import-CSAnnouncementFile -Content <Byte[]> -FileName <String> -Parent <String> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]
```

## Examples

### EXAMPLE 1

These commands import an audio file into the Announcement service File Store. Because audio files must be imported as byte arrays, we first need to call the **Get-Content** cmdlet to retrieve the audio file as an array of individual bytes. **Get-Content** is a Windows PowerShell built-in cmdlet to which we pass the name (including path) of the file we want to use for our announcement. Next we pass a value of 0 to the ReadCount parameter, meaning we want to read the whole file at once. We then pass a value of Byte to the Encoding parameter, which tells **Get-Content** that we want the contents of the file as an array of bytes. We assign that array to the variable $a.
  
In the second line we call the **Import-CsAnnouncementFile** cmdlet to actually import the file. We pass the service Identity ApplicationServer:redmond.litwareinc.com to the Parent parameter, then we pass a name to the FileName parameter (WelcomeMessage.wav). This can be any valid Windows operating system file name, but it should end with a .wav or .wma extension. Finally, we pass the variable $a as the value to the Content parameter to read in our byte array.
  
```
$a = Get-Content ".\GreetingFile.wav" -ReadCount 0 -Encoding Byte
Import-CsAnnouncementFile -Parent ApplicationServer:redmond.litwareinc.com -FileName "WelcomeMessage.wav" -Content $a
```

### EXAMPLE 2

Example 2 is identical to Example 1 except that we included the **Get-Content** command inside parentheses as a value to the Content parameter rather than calling that command on its own and assigning it to a variable.
  
```
Import-CsAnnouncementFile -Parent ApplicationServer:redmond.litwareinc.com -FileName "WelcomeMessage.wav" -Content (Get-Content ".\GreetingFile.wav" -ReadCount 0 -Encoding Byte)
```

### EXAMPLE 3

Example 3 is yet another variation of Example 1. The difference in this example is that rather than use the Content parameter, we first call the **Get-Content** cmdlet, then pipe the results to **Import-CsAnnouncementFile**. This is the most reliable way of importing an announcement file from a remote session.
  
```
Get-Content ".\GreetingFile.wav" -ReadCount 0 -Encoding Byte | Import-CsAnnouncementFile -Parent ApplicationServer:redmond.litwareinc.com -FileName "WelcomeMessage.wav"
```

## Detailed Description

This cmdlet imports an audio file as a byte array to the Announcement service audio library. This makes the file available for playback as an announcement for unassigned numbers.
  
Running this cmdlet imports the audio file to the library. After the file has been imported, the file can be used in an announcement by calling the **New-CsAnnouncement** cmdlet or the **Set-CsAnnouncement** cmdlet and passing the file name and associated service as parameters. At that point the **New-CsUnassignedNumber** or **Set-CsUnassignedNumber** cmdlet can be called to assign the announcement to a specific range of numbers.
  
Imported files must be WAV or WMA files.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Content_ <br/> |Required  <br/> |System.Byte[]  <br/> |The contents of the audio file as a byte array.  <br/> |
| _FileName_ <br/> |Required  <br/> |System.String  <br/> |The name that you want the file to have in the File Store. You will use this name in the AudioFilePrompt parameter in the call to the **New-CsAnnouncement** or **Set-CsAnnouncement** cmdlet to assign the file to an announcement. <br/> |
| _Parent_ <br/> |Required  <br/> |System.String  <br/> |The service ID of the Application Server on which the associated Announcement service is running.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types

Byte[]. Accepts a byte array from an audio file. Byte array must be piped as a single record. See Example 3.
  
## Return Types

This cmdlet does not return a value.
  

