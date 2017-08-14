---
title: Set-CsCallParkServiceMusicOnHoldFile
ms.prod: SKYPEFORBUSINESS
ms.assetid: af5e7573-4bfd-47b1-a92b-83b06a537158
---


# Set-CsCallParkServiceMusicOnHoldFile
[]
Changes the audio file that will be played to callers who are on hold in a parked call. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Set-CsCallParkServiceMusicOnHoldFile -Content <Byte[]> -Service <String> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```


## Examples


  
    
    

### EXAMPLE 1

This example sets the file SoothingMusic.wma to be the audio file that is played to callers whose calls are parked. The first line of this example is a call to the **Get-Content** cmdlet. This cmdlet simply reads the contents of a file and assigns them, in this case, to the variable $a. We pass a value of 0 to the ReadCount parameter so the **Get-Content** cmdlet will read the entire file at once (rather than try to read it line by line, which doesn't apply to an audio file). We set the Encoding parameter to byte. This tells the **Get-Content** cmdlet that the content we want to read into variable $a is a byte array rather than the audio file in .wma format.
  
    
    
Line 2 in this example is where we actually assign the audio file. We call the **Set-CsCallParkServiceMusicOnHoldFile** cmdlet and specify the service ID where the Call Park service is running. We then pass the audio file contents that we read into variable $a to the Content parameter. (Remember that these contents must be in byte format.)
  
    
    



```

$a = Get-Content -ReadCount 0 -Encoding byte "C:\\MoHFiles\\soothingmusic.wma"
Set-CsCallParkServiceMusicOnHoldFile -Service ApplicationServer:pool0.litwareinc.com -Content $a
```


## Detailed Description

Call parking is a service that allows a user to "park" an incoming phone call. Parking a call transfers it to a number in a specified range and immediately places it on hold. Based on configuration settings for the Call Park service, music on hold can be played to the caller while the call is parked. Use this cmdlet to change the audio file (music on hold) that is played to a parked caller who is on hold.
  
    
    
Music on hold is played only if the EnableMusicOnHold property of the Call Park service has been set to True. You can check this property by calling the **Get-CsCpsConfiguration** cmdlet. You can set the property either when the Call Park configuration is created with the **New-CsCpsConfiguration** cmdlet or after the Call Park configuration exists by calling the **Set-CsCpsConfiguration** cmdlet. This property is True by default.
  
    
    
Skype for Business Server 2015 ships with a default Call Park service music on hold file. If you don't assign an audio file, the default file will be used.
  
    
    
Audio files must be in the following format: Windows Media Audio 9, 44 kHz, 16 bits, Mono, CBR, or 32 kbps.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Content_ <br/> |Required  <br/> |System.Byte[]  <br/> |The contents of the audio file in byte format.  <br/> Use the **Get-Content** cmdlet to retrieve the contents of the audio file in byte format. (For details, see the Examples section in this topic.) <br/> |
| _Service_ <br/> |Required  <br/> |System.String  <br/> |The ID of the service where the Call Park service resides; for example, ApplicationServer:pool0.litwareinc.com.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types

Byte[]. Accepts pipelined input of a byte array containing the music on hold file.
  
    
    

## Return Types

This cmdlet does not return a value.
  
    
    

## See also


#### 


  
    
    
 [New-CsCpsConfiguration](new-cscpsconfiguration.md)
  
    
    
 [Remove-CsCpsConfiguration](remove-cscpsconfiguration.md)
  
    
    
 [Set-CsCpsConfiguration](set-cscpsconfiguration.md)
  
    
    
 [Get-CsCpsConfiguration](get-cscpsconfiguration.md)
