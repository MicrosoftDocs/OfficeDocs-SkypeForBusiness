---
title: New-CsRgsQuestion
ms.prod: SKYPEFORBUSINESS
ms.assetid: 0ed9f3b4-cbc5-41ca-8547-2300b579b119
---


# New-CsRgsQuestion
[]
Creates a new Response Group question. The Response Group application uses questions to provide callers with choices, and then takes action based on those choices. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

New-CsRgsQuestion -Prompt <Prompt> [-AnswerList <PSListModifier>] [-InvalidAnswerPrompt <Prompt>] [-Name <String>] [-NoAnswerPrompt <Prompt>]
```


## Examples


  
    
    

### EXAMPLE 1

The commands shown in Example 1 create a pair of Response Group answers, and then associate those answers with a new Response Group question. In order to create the two answers, you must first specify the call actions that will be taken depending on the answer supplied by the caller. Consequently, the first two commands in the example create object references to a pair of Response Group queues: New Service Request and Existing Service Request. After these object references have been created, the next command uses **New-CsRgsPrompt** to create a text-to-speech prompt that is stored in a variable named $w.
  
    
    
When that operation is complete, the next two commands create a pair of corresponding call actions: one to transfer callers to the New Service Request queue, and the other to transfer callers to the Existing Service Request queue. After the call actions have been created, the **New-CsRgsAnswer** cmdlet is used to create two Response Group answers, one stored in the variable $newRequest and the other stored in the variable $existingRequest.
  
    
    
With the two answers stored, **New-CsRgsPrompt** can then be used to create a prompt for the new question. In this example, the prompt is a text-to-speech prompt that asks the caller to press 1 (or say "New") for a new service request, or to press 2 (or say "Existing") for an existing service request. The prompt itself is stored in a variable named $u.
  
    
    
After the prompt has been created, **New-CsRgsQuestion** can be called in order to create the new question. In addition to the Prompt parameter, the AnswerList parameter is used to indicate the two answers associated with the question: the variables $newRequest and $existingRequest.
  
    
    



```
$new = Get-CsRgsQueue -Identity service:ApplicationServer:pool0.litwareinc.com -Name "New Service Request"
$existing = Get-CsRgsQueue -Identity service:ApplicationServer:pool0.litwareinc.com -Name "Existing Service Request"

$w = New-CsRgsPrompt -TextToSpeechPrompt "Please hold while we transfer your call."

$y = New-CsRgsCallAction -Prompt $w -Action TransferToQueue -QueueID $new.Identity
$z = New-CsRgsCallAction -Prompt $w -Action TransferToQueue -QueueID $existing.Identity

$newRequest = New-CsRgsAnswer -Action $y -DtmfResponse 1 -VoiceResponseList "New" -Name "New Request"
$existingRequest = New-CsRgsAnswer -Action $z -DtmfResponse 2 -VoiceResponseList "Existing" -Name "Existing Request"

$u = New-CsRgsPrompt -TextToSpeechPrompt "Press 1 or say New for a new service request. Press 2 or say Existing for an existing service request."

$question = New-CsRgsQuestion -Prompt $u -AnswerList $newRequest $newRequest, $existingRequest 

```


## Detailed Description

In order to process calls, the Response Group application often makes a statement or poses a question, then takes action based on the caller's response. For example, the service might ask a caller to press 1 for English or to press 2 for Spanish. After a question like this has been posed, the system must wait for the caller to respond and then take the appropriate action. In this case, that means transferring the call to an English language queue if the caller presses 1 on the telephone keypad, or transferring the call to a Spanish language queue if the caller presses 2 on the keypad.
  
    
    
In order to create a question you must use the **New-CsRgsQuestion** cmdlet. When creating a Response Group question you need to, at a minimum, supply a prompt (that is, the actual question itself) and also a set of supported answers. For example, if you are giving callers the option of pressing 1 or 2 you will need to have two answers: one to specify the action to be taken if the caller presses 1, the other to specify the action to be taken if the caller presses 2. If you give callers the option of pressing 1, 2, 3, or 4 then you will need four answers, and so on.
  
    
    
In addition, **New-CsRgsQuestion** gives you the ability to specify a prompt to be used if a caller either provides an invalid answer or does not answer at all. For example, if the caller in the original scenario presses 3, the prompt might state "I'm sorry; I that is not a valid response." At that point, the original prompt will then be replayed.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Prompt_ <br/> |Required  <br/> |Microsoft.Rtc.Rgs.Management.WritableSettings.Prompt  <br/> |Question to be asked of the caller. Prompts must be created by using the **New-CsRgsPrompt** cmdlet. <br/> |
| _AnswerList_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |Array of valid answers to the question. For example, a help desk question might have answers such as Hardware Support, Software Installation, and Network Connections. Answers must be created by using the **New-CsRgsAnswer** cmdlet. <br/> |
| _InvalidAnswerPrompt_ <br/> |Optional  <br/> |Microsoft.Rtc.Rgs.Management.WritableSettings.Prompt  <br/> |Response to be issued in case the caller selects an invalid answer. The InvalidAnswerPrompt must be created by using the **New-CsRgsPrompt** cmdlet. Note that after the playing the InvalidAnswerPrompt the application will then repeat the original prompt. <br/> |
| _Name_ <br/> |Optional  <br/> |System.String  <br/> |Identifier for the question. Question names, which do not have to be unique, are limited to a maximum of 128 characters.  <br/> |
| _NoAnswerPrompt_ <br/> |Optional  <br/> |Microsoft.Rtc.Rgs.Management.WritableSettings.Prompt  <br/> |Response to be issued in case the caller does not respond to the initial prompt. The NoAnswerPrompt must be created by using the **New-CsRgsPrompt** cmdlet. <br/> |
   

## Input Types

None. **New-CsRgsQuestion** does not accept pipelined input.
  
    
    

## Return Types

 **New-CsRgsQuestion** creates instances of the Microsoft.Rtc.Management.WriteableSettings.Question object.
  
    
    

## See also


#### 


  
    
    
 [New-CsRgsAnswer](new-csrgsanswer.md)
