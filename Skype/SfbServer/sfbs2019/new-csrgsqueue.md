---
title: "New-CsRgsQueue"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: e013533b-6845-44c6-ae5e-e75187b43181
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# New-CsRgsQueue
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Creates a new Response Group queue. With the Response Group application, phone calls are put in a queue and callers are placed on hold until a Response Group agent is available to answer that call. This cmdlet was introduced in Lync Server 2010.
  
```
New-CsRgsQueue -Name <String> -Parent <RgsIdentity> [-AgentGroupIDList <Collection>] [-Confirm [<SwitchParameter>]] [-Description <String>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-OverflowAction <CallAction>] [-OverflowCandidate <NewestCall | OldestCall>] [-OverflowThreshold <Int16>] [-TimeoutAction <CallAction>] [-TimeoutThreshold <Int32>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

Example 1 creates a new Response Group queue for the service ApplicationServer:atl-cs-001.litwareinc.com. The first command in the example uses the **New-CsRgsCallAction cmdlet** to create a call action for the queue; in this example, any time the overflow threshold is exceeded calls will automatically be transferred to voice mail. This is configured by setting the Action parameter to TransferToVoicemailUri and the URI property to the voice mail SIP URI "sip:+14255551298@litwareinc.com". 
  
After the call action has been configured (and stored in the variable $x), **New-CsRgsQueue** is then used to create a new queue named Help Desk. In addition to specifying the OverflowAction, this command also configures values for the OverflowCandidate and OverflowThreshold properties. 
  
```
$x = New-CsRgsCallAction -Action TransferToVoicemailUri -Uri "sip:+14255551298@litwareinc.com"
New-CsRgsQueue -Parent service:ApplicationServer:atl-cs-001.litwareinc.com -Name "Help Desk" -OverflowCandidate "OldestCall" -OverflowAction $x -OverflowThreshold 25

```

## Detailed Description
<a name="sectionSection1"> </a>

When someone calls a phone number associated with the Response Group application, one of two things typically happens: either the call is transferred to a question that the caller must answer in order to continue (for example, "Press 1 for hardware support; press 2 for software support") or the call is placed in a queue until an agent is available to answer the call. 
  
Instead of having a single queue for all phone calls, the Response Group application enables you to create multiple queues that can be associated with different workflows and different Response Group agent groups. In turn, this means queues can respond differently to events such as a designated number of calls being simultaneously held in the queue, or to callers that have been on hold for a specified amount of time.
  
The **New-CsRgsQueue** cmdlet provides an easy way for administrators to create new Response Group queues. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **New-CsRgsQueue** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "New-CsRgsQueue"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Name_ <br/> |Required  <br/> |System.String  <br/> |Unique name to be assigned to the queue. The combination of the Parent property and the Name property enables you to uniquely identify Response Group queues without having to refer to the queue's globally unique identifier (GUID).  <br/> |
| _Parent_ <br/> |Required  <br/> |Microsoft.Rtc.Rgs.Management.RgsIdentity  <br/> |Service where the new queue will be hosted. For example: -Parent "service:ApplicationServer:atl-cs-001.litwareinc.com".  <br/> |
| _AgentGroupIDList_ <br/> |Optional  <br/> |System.Collections.ObjectModel.Collection  <br/> |Identity of the Response Group agent groups to be added to the queue. The agent group Identities can be retrieved using the **Get-CsRgsAgentGroup** cmdlet. For details, see the Examples section in this topic.  <br/> If a call is routed to a queue that has no agent groups assigned to it (or has only been assigned agent groups that do not have any agents) then that call will automatically be disconnected.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Description_ <br/> |Optional  <br/> |System.String  <br/> |Enables administrators to provide additional information about the Response Group queue.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching Set- cmdlet.  <br/> |
| _OverflowAction_ <br/> |Optional  <br/> |Microsoft.Rtc.Rgs.Management.WritableSettings.CallAction  <br/> |Action to be taken if the overflow threshold is reached. The OverflowAction must be created using the **New-CsRgsCallAction** cmdlet.  <br/> |
| _OverflowCandidate_ <br/> |Optional  <br/> |Microsoft.Rtc.Rgs.Management.WritableSettings.OverflowCandidate  <br/> |Indicates which call will be acted upon should the overflow threshold be reached. The OverflowCandidate property must be set to one of the following two values:  <br/> NewestCall  <br/> OldestCall  <br/> The default value is NewestCall.  <br/> |
| _OverflowThreshold_ <br/> |Optional  <br/> |System.Int16  <br/> |Number of simultaneous calls that can be in the queue at any one time before the overflow action is triggered. The OverflowThreshold can be any integer value between 0 and 1000, inclusive. The default value is Null, meaning that an unlimited number of calls can be in the queue at any given time.  <br/> |
| _TimeoutAction_ <br/> |Optional  <br/> |Microsoft.Rtc.Rgs.Management.WritableSettings.CallAction  <br/> |Action to be taken if the timeout threshold is reached. The TimeoutAction must be created using the **New-CsRgsCallAction** cmdlet.  <br/> |
| _TimeoutThreshold_ <br/> |Optional  <br/> |System.Int32  <br/> |Amount of time (in seconds) that a call can be in the queue before that call times out. At that point, the system will take the action specified by the TimeoutAction parameter.  <br/> The timeout threshold can be any integer value between 10 and 65535 seconds (approximately 18 hours), inclusive; the default value is null, meaning that the queue never times out.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. **New-CsRgsQueue** does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

 **New-CsRgsQueue** creates new instances of the Microsoft.Rtc.Rgs.Management.WritableSettings.Queue object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsRgsQueue](get-csrgsqueue.md)
  
[Remove-CsRgsQueue](remove-csrgsqueue.md)
  
[Set-CsRgsQueue](set-csrgsqueue.md)

