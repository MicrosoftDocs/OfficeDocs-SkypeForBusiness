---
title: "Set-CsRgsWorkflow"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 9/23/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 36cffa89-e5bb-48fd-bd6e-da67066fd273

description: "Modifies an existing Response Group workflow. Workflows determine the actions that are taken when the Response Group application receives a phone call. This cmdlet was introduced in Lync Server 2010."
---

# Set-CsRgsWorkflow
[]
Modifies an existing Response Group workflow. Workflows determine the actions that are taken when the Response Group application receives a phone call. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsRgsWorkflow -Instance <Workflow> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]
```

## Examples

### EXAMPLE 1

The commands shown in Example 1 retrieve an existing set of business hours, and then assign those business hours to a workflow named Help Desk. To do this, the first command in the example uses **Get-CsRgsHoursOfBusiness** to retrieve the business hours collection named U.S. Business Hours from the service ApplicationServer:atl-cs-001.litwareinc.com. These business hours are stored in a variable named $businessHours.
  
After the business hours have been retrieved the **Get-CsRgsWorkflow** cmdlet is used to retrieve the Help Desk workflow from ApplicationServer:atl-cs-001.litwareinc.com. This object is stored in a variable named $y.
  
In the third command in the example, the BusinessHoursId property of the Help Desk workflow is set to the retrieved collection of business hours; that's done by setting BusinessHoursId to the Identity of the retrieved collection ($businessHours.Identity). In the final command, **Set-CsRgsWorkflow** is used to write the new business hours to the actual Help Desk workflow on ApplicationServer:atl-cs-001.litwareinc.com. This last step is important because, until this point, all the changes have taken place only in memory. To actually save these changes to the Help Desk workflow, you must call **Set-CsRgsWorkflow**, passing the cmdlet the object reference ($y) containing the virtual copy of the workflow.
  
```
$businessHours = Get-CsRgsHoursOfBusiness service:ApplicationServer:atl-cs-001.litwareinc.com -Name "US Business Hours"
$y = Get-CsRgsWorkflow Service:ApplicationServer:atl-cs-001.litwareinc.com -Name "Help Desk"
$y.BusinessHoursId = $businessHours.Identity
Set-CsRgsWorkflow -Instance $y
```

### EXAMPLE 2

Example 2 assigns a new description to the Help Desk workflow found on the service ApplicationServer:atl-cs-001.litwareinc.com. To do this, the first command in the example retrieves the specified workflow (-Name "Help Desk") and stores the retrieved object in a variable named $x. In command 2, a new description ("Workflow for the Redmond Help Desk") is added to the virtual copy of the Help Desk workflow. After the description has been changed, command 3 uses the **Set-CsRgsWorkflow** to write these changes back to the actual Help Desk workflow located on ApplicationServer:atl-cs-001.litwareinc.com.
  
```
$x = Get-CsRgsWorkflow service:ApplicationServer:atl-cs-001.litwareinc.com -Name "Help Desk"
$x.Description = "Workflow for the Redmond Help Desk" 
Set-CsRgsWorkflow -Instance $x
```

### EXAMPLE 3

The commands shown in Example 3 import a new Response Group audio file, then assign this audio file to an existing workflow. To do this, the first command in the example imports the new audio file. This is done by calling the **Get-Content** cmdlet in order to read in the audio file (C:\MediaFiles\Hold.wav) byte-by-byte; to ensure that the audio file is read in correctly, you must include the ReadCount parameter (set to 0) and the Encoding parameter (set to Byte). After the audio file has been read in, the data is piped to **New-CsRgsAudioFile**, which creates a new file on ApplicationServer:atl-cs-001.litwareinc.com. An object reference to this file(which has the name HelpDeskHoldMusic.wav), is stored in a variable named $musicFile.
  
After the audio file has been created, command 2 retrieves the workflow Help Desk from ApplicationServer:atl-cs-001.litwareinc.com, storing the returned object in a variable named $y. In command 3, the CustomMusicOnHoldFile property for this workflow is assigned the value $musicFile, which is the variable containing the newly-created audio file.
  
After $musicFile has been assigned to CustomMusicOnHoldFile, the final command uses the **Set-CsRgsWorkflow** cmdlet to write these changes back to the Help Desk. workflow
  
```
$musicFile = Get-Content -ReadCount 0 -Encoding Byte C:\MediaFiles\Hold.wav | Import-CsRgsAudioFile -Identity Service:ApplicationServer:atl-cs-001.litwareinc.com -FileName "HelpDeskHoldMusic.wav"
$y = Get-CsRgsWorkflow -Identity Service:ApplicationServer:atl-cs-001.litwareinc.com -Name "Help Desk"
$y.CustomMusicOnHoldFile = $musicFile
Set-CsRgsWorkflow -Instance $y
```

## Detailed Description

Workflows are perhaps the key element in the Response Group application. Each workflow is uniquely associated with a phone number; when someone calls that number, the workflow determines how the call will be handled. For example, the call might be routed to a series of interactive voice response (IVR) questions that prompt the caller to enter additional information (for example, "Press 1 for hardware support. Press 2 for software support.") Alternatively, the call might be placed in a queue and the caller put on hold until an agent is available to answer the call. The availability of agents to answer calls is also dictated by the workflow: workflows are used to configure both business hours (the days of the week and the times of day when agents are available to answer calls) and holidays (days when no agents are available to answer calls).
  
The **Set-CsRgsWorkflow** cmdlet provides a way for you to modify the properties of an existing workflow; for example, you can change the phone number for a workflow, the agents groups associated with a workflow, or the default action to be taken any time the workflow is triggered (that is, any time someone calls the phone number associated with the workflow).
  
 **Set-CsRgsWorkflow** does not directly modify a workflow itself. Instead, if you need to make changes to a workflow, you must first use **Get-CsRgsWorkflow** to create an object reference to that workflow; this simply means that you retrieve the workflow of interest and then store the returned object in a variable. After the object reference has been created, you modify the properties of the object in memory, and then use **Set-CsRgsWorkflow** to write these changes back to actual Response Group application workflow. If you do not call **Set-CsRgsWorkflow** then your changes will exist only in memory, and will disappear as soon as you close Windows PowerShell or delete the object reference variable.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Instance_ <br/> |Required  <br/> |Microsoft.Rtc.Rgs.Management.WritableSettings.Workflow  <br/> |Object reference to the Response Group application workflow to be modified. An object reference is typically retrieved by using the **Get-CsRgsWorkflow** cmdlet and assigning the returned value to a variable; for example, this command returns an object reference to the Help Desk workflow and stores that object reference in a variable named $x: <br/>  `$x = Get-CsRgsWorkflow service:ApplicationServer:atl-cs-001.litwareinc.com -Name "Help Desk"` <br/> The Instance parameter is a positional parameter: it can be omitted as long as the object reference to the workflow is the first parameter value used in your command. That means that the following two commands are functionally identical:  <br/>  `Set-CsRgsWorkflow -Instance $x` <br/>  `Set-CsRgsWorkflow $x` <br/> > [!NOTE]> If you provide this parameter, it must not be null.           |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types

Microsoft.Rtc.Rgs.Management.WritableSettings.Workflow object. **Set-CsRgsWorkflow** accepts pipelined instances of the Response Group workflow object.
  
## Return Types

 **Set-CsRgsWorkflow** does not return any objects or values. Instead, the cmdlet modifies existing instances of the Microsoft.Rtc.Rgs.Management.WritableSettings.Workflow object.
  
## See also

#### 

[Get-CsRgsWorkflow](get-csrgsworkflow.md)
  
[New-CsRgsWorkflow](new-csrgsworkflow.md)
  
[Remove-CsRgsWorkflow](remove-csrgsworkflow.md)

