---
title: New-CsRgsWorkflow
ms.prod: SKYPEFORBUSINESS
ms.assetid: 1a2ac5b7-cb1d-4a83-801f-f27671e71743
---


# New-CsRgsWorkflow
[]
Creates a new Response Group workflow. Workflows determine the actions that are taken when the Response Group application receives a phone call. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

New-CsRgsWorkflow -Name <String> -Parent <RgsIdentity> -PrimaryUri <Uri> [-Active <$true | $false>] [-Anonymous <$true | $false>] [-BusinessHoursID <RgsIdentity>] [-Confirm [<SwitchParameter>]] [-CustomMusicOnHoldFile <AudioFile>] [-DefaultAction <CallAction>] [-Description <String>] [-DisplayNumber <String>] [-EnabledForFederation <$true | $false>] [-Force <SwitchParameter>] [-HolidayAction <CallAction>] [-HolidaySetIDList <Collection>] [-InMemory <SwitchParameter>] [-Language <String>] [-LineUri <Uri>] [-Managed <$true | $false>] [-ManagersByUri <Collection>] [-NonBusinessHoursAction <CallAction>] [-TimeZone <String>] [-WhatIf [<SwitchParameter>]]
```


## Examples


  
    
    

### EXAMPLE 1

Example 1 creates a new workflow on the service ApplicationServer:atl-cs-001.litwareinc.com. This workflow is given the Name Help Desk and is assigned a primary URI of sip:helpdesk@litwareinc.com.
  
    
    

```
New-CsRgsWorkflow -Parent service:ApplicationServer:atl-cs-001.litwareinc.com -Name "Help Desk" -PrimaryUri "sip:helpdesk@litwareinc.com"

```


### EXAMPLE 2

The command shown in Example 2 create a new workflow prompt and call action, then assigns those items to a new Response Group workflow. In the first command, the **New-CsRgsPrompt** cmdlet is used to create a text-to-speech prompt "Welcome to the help desk." This new prompt is stored in a variable named $prompt.
  
    
    
The second command uses the **Get-CsRgsQueue** cmdlet to retrieve the Identity of an existing Response Group queue named Help Desk; the returned Identity is stored in a variable named $queue.
  
    
    
Command 3 then creates a new call action (stored in a variable named $callAction) that references both the new prompt ($prompt) and the retrieved queue ($queue). Finally, the last command in the example creates a new workflow named Help Desk. This command sets the PrimaryUri to sip:helpdesk@litwareinc.com and sets the value of the DefaultAction property to the call action created in the previous step.
  
    
    



```

$prompt = New-CsRgsPrompt -TextToSpeechPrompt "Welcome to the help desk."
$queue = (Get-CsRgsQueue -Identity service:ApplicationServer:atl-cs-001.litwareinc.com -Name "Help Desk").Identity
$callAction = New-CsRgsCallAction -Prompt $prompt -Action TransferToQueue -QueueId $queue
New-CsRgsWorkflow -Parent service:ApplicationServer:atl-cs-001.litwareinc.com -Name "Help Desk" -PrimaryUri "sip:helpdesk@litwareinc.com" -DefaultAction $callAction
```


## Detailed Description

Workflows are a key element in the Response Group application. Each workflow is uniquely associated with a phone number; when someone calls that number, the workflow determines how the call will be handled. For example, the call might be routed to a series of interactive voice response (IVR) questions that prompt the caller to enter additional information ("Press 1 for hardware support. Press 2 for software support.") Alternatively, the call might be placed in a queue and the caller placed on hold until an agent is available to answer the call. The availability of agents to answer calls is also dictated by the workflow: workflows are used to configure business hours (the days of the week and the times of day when agents are available to answer calls) and also holidays (days when no agents are available to answer calls).
  
    
    
New workflows are created by using the **New-CsRgsWorkflow** cmdlet.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Name_ <br/> |Required  <br/> |System.String  <br/> |Unique name to be assigned to the workflow. The combination of the Parent property and the Name property enables you to uniquely identify workflows without having to refer to the workflow's globally unique identifier (GUID).  <br/> |
| _Parent_ <br/> |Required  <br/> |Microsoft.Rtc.Rgs.Management.RgsIdentity  <br/> |Service where the new workflow will be hosted. For example:  `-Parent "service:ApplicationServer:atl-cs-001.litwareinc.com"`.  <br/> |
| _PrimaryUri_ <br/> |Required  <br/> |System.Uri  <br/> |SIP address for the workflow. For example:  `-PrimaryUri "sip:helpdesk@litwareinc.com"`. The PrimaryUri must begin with the "sip:" prefix.  <br/> |
| _Active_ <br/> |Optional  <br/> |System.Boolean  <br/> |If set to True, this means that the workflow is active and available to take phone calls. If set to False (the default value), the workflow is not available to take phone calls.  <br/> When the Active property is set to True then the workflow will be validated before it is created. For example, the workflow will not be created if a DefaultAction has not been specified. If Active is set to False (or not configured) then no validation will take place, and the workflow will be created even if a DefaultAction has not been specified.  <br/> |
| _Anonymous_ <br/> |Optional  <br/> |System.Boolean  <br/> |If set to True, the identities of individual Response Group agents will be masked any time these agents answer a call. If set to False (the default value), agent identities will be available to callers.  <br/> |
| _BusinessHoursID_ <br/> |Optional  <br/> |Microsoft.Rtc.Rgs.Management.RgsIdentity  <br/> |Days of the week and times of the day that workflow agents are available to answer calls. The business hour Identities can be retrieved by using the **Get-CsRgsHoursOfBusiness** cmdlet. <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _CustomMusicOnHoldFile_ <br/> |Optional  <br/> |Microsoft.Rtc.Rgs.Management.WritableSettings.AudioFile  <br/> |Represents custom music to be played when callers are placed on hold. (If not defined, callers will hear the default music when placed on hold.) Custom music must be imported by using the **Import-CsRgsAudioFile** cmdlet. <br/> |
| _DefaultAction_ <br/> |Optional  <br/> |Microsoft.Rtc.Rgs.Management.WritableSettings.CallAction  <br/> |Indicates the action to be taken when a workflow is opened during business hours. DefaultAction must be defined by using the **New-CsRgsCallAction** cmdlet, and must either direct the call to a queue or to a question. The DefaultAction parameter is mandatory if the workflow is active, but can be omitted if the workflow is inactive. <br/> |
| _Description_ <br/> |Optional  <br/> |System.String  <br/> |Enables administrators to add additional information about a Response Group workflow. For example, the Description might include contact information for the owner of the workflow. This description appears in the Skype for Business contact card for the workflow.  <br/> |
| _DisplayNumber_ <br/> |Optional  <br/> |System.String  <br/> |Phone number for the workflow as displayed in Skype for Business. The DisplayNumber can be formatted any way you want; for example:  <br/>  `-DisplayNumber "555-1219"` <br/>  `-DisplayNumber "1-(425)-555-1219"` <br/>  `-DisplayNumber "1.425.555.1219"` <br/> |
| _EnabledForFederation_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether the workflow is available to users from a federated domain. If set to False, only users within your organization will have access to the workflow.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _HolidayAction_ <br/> |Optional  <br/> |Microsoft.Rtc.Rgs.Management.WritableSettings.CallAction  <br/> |Action to be taken if a call is received on a holiday. The HolidayAction must be defined by using the **New-CsRgsCallAction** cmdlet. <br/> |
| _HolidaySetIDList_ <br/> |Optional  <br/> |System.Collections.ObjectModel.Collection  <br/> |Represents days when workflow agents are not available to answer calls. The holiday set Identities can be retrieved by using the **Get-CsRgsHolidaySet** cmdlet. <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching **Set-<cmdlet>**. <br/> |
| _Language_ <br/> |Optional  <br/> |System.String  <br/> |Language that is used to read workflow text-to-speech prompts. The language parameter is optional as long as the operating system is using one of the supported languages shown in the list below. (Note that supported speech languages represent a subset of the languages that can be used on the operating system.)  <br/> If the operating system is not using a supported language, then the Language parameter becomes mandatory, and the parameter must specify the language code for a supported language. If your operating system is using a non-supported language on the operating system, and you run the **New-CsRgsWorkflow** cmdlet without including the Language parameter, your command will fail. <br/> For example, suppose your operating system is running under the Faroese language. This language is supported by the Windows operating system, but not by the Response Group application. Therefore, you must include the Language parameter and a supported language when creating a new workflow.  <br/> This is required because, if no language is specified, the workflow uses the operating system language. However, that language can be used in a workflow only if it is a language supported by the Response Group application.  <br/> The language must be specified using one of the following language codes:  <br/> ca-ES - Catalan (Spain)  <br/> da-DK - Danish (Denmark)  <br/> de-DE - German (Germany)  <br/> en-AU - English (Australia)  <br/> en-CA - English (Canada)  <br/> en-GB - English (United Kingdom)  <br/> en-IN - English (India)  <br/> en-US - English (United States)  <br/> es-ES - Spanish (Spain)  <br/> es-MX - Spanish (Mexico)  <br/> fi-FI - Finnish (Finland)  <br/> fr-CA - French (Canada)  <br/> fr-FR - French (France)  <br/> it-IT - Italian (Italy)  <br/> ja-JP - Japanese (Japan)  <br/> ko-KR - Korean (Korea)  <br/> nb-NO - Norwegian, Bokmal (Norway)  <br/> nl-NL - Dutch (Netherlands)  <br/> pl-PL - Polish (Poland)  <br/> pt-BR - Portuguese (Brazil)  <br/> pt-PT - Portuguese (Portugal)  <br/> ru-RU - Russian (Russia)  <br/> sv-SE - Swedish (Sweden)  <br/> zh-CN - Chinese (People's Republic of China)  <br/> zh-HK - Chinese (Hong Kong SAR)  <br/> zh-TW - Chinese (Taiwan)  <br/> For example: -Language "nl-NL".  <br/> |
| _LineUri_ <br/> |Optional  <br/> |System.Uri  <br/> |Phone number for the workflow. The line Uniform Resource Identifier (URI) must be specified by using the following format: the TEL: prefix followed by a plus sign, followed by the country/region calling code, area code, and phone number (using only digits: no blank spaces, periods, or hyphens). For example:  `-LineUri "TEL:+14255551219"` <br/> |
| _Managed_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True indicates that the workflow will be managed by one or more users. Those users can be specified by using the ManagedByUri parameter.  <br/> |
| _ManagersByUri_ <br/> |Optional  <br/> |System.Collections.ObjectModel.Collection  <br/> |SIP addresses of the user (or users) who will manage the workflow. For example:  <br/>  `-ManagedByUri "sip:kenmyer@litwareinc.com"` <br/> To specify multiple managers separate the manager SIP addresses by using commas:  <br/>  `-ManagedByUri "sip:kenmyer@litwareinc.com", "sip:pilar@litwareinc.com"` <br/> |
| _NonBusinessHoursAction_ <br/> |Optional  <br/> |Microsoft.Rtc.Rgs.Management.WritableSettings.CallAction  <br/> |Action to be taken if a call is received outside the workflow's business hours. The NonBusinessHoursAction must be defined by using the **New-CsRgsCallAction** cmdlet. <br/> |
| _TimeZone_ <br/> |Optional  <br/> |System.String  <br/> |Time zone information used when determining holidays and business hours. For example:  `-TimeZone "Pacific Standard Time"` <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   

## Input Types

None. The **New-CsRgsWorkflow** cmdlet does not accept pipelined input.
  
    
    

## Return Types

The **New-CsRgsWorkflow** cmdlet creates new instances of the Microsoft.Rtc.Rgs.Management.WritableSettings.Workflow object.
  
    
    

## See also


#### 


  
    
    
 [Get-CsRgsWorkflow](get-csrgsworkflow.md)
  
    
    
 [Remove-CsRgsWorkflow](remove-csrgsworkflow.md)
  
    
    
 [Set-CsRgsWorkflow](set-csrgsworkflow.md)
