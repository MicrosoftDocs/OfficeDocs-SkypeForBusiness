---
title: Remove-CsRgsQueue
ms.prod: SKYPEFORBUSINESS
ms.assetid: 7613e72c-f330-4560-88d4-a7386cd18975
---


# Remove-CsRgsQueue
[]
Deletes an existing Response Group queue. With the Response Group application, phone calls are put in a queue and callers are placed on hold until a Response Group agent is available to answer that call. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Remove-CsRgsQueue -Instance <Queue> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]
```


## Examples


  
    
    

### EXAMPLE 1

The command shown in Example 1 deletes all the Response Group queues found on the service ApplicationServer:atl-cs-001.litwareinc.com. To do this, the command first uses **Get-CsRgsQueue** to return a collection of all the queues found on ApplicationServer:atl-cs-001.litwareinc.com. This collection is then piped to **Remove-CsRgsQueue**, which deletes each queue in the collection.
  
    
    

```
Get-CsRgsQueue -Identity service:ApplicationServer:atl-cs-001.litwareinc.com | Remove-CsRgsQueue
```


### EXAMPLE 2

In Example 2, a single Response Group queue is deleted: the queue named "Help Desk Queue", located on the service ApplicationServer:atl-cs-001.litwareinc.com. To delete this queue, **Get-CsRgsQueue** is called along with the Identity and Name parameters; the single queue returned by this call is then piped to, and deleted by, **Remove-CsRgsQueue**.
  
    
    

```
Get-CsRgsQueue -Identity service:ApplicationServer:atl-cs-001.litwareinc.com -Name "Help Desk Queue" | Remove-CsRgsQueue
```


### EXAMPLE 3

Example 3 deletes all the Response Group queues found on the service ApplicationServer:atl-cs-001.litwareinc.com, provided those queues have their OverflowCandidate property set to NewestCall. To do this, **Get-CsRgsQueue** is first called in order to return a collection of all the Response Group queues found on ApplicationServer:atl-cs-001.litwareinc.com. This collection is then piped to the **Where-Object** cmdlet, which selects only those queues where the OverflowCandidate property is equal to "NewestCall". The filtered collection is then piped to **Remove-CsRgsQueue**, which deletes each queue in the collection.
  
    
    

```
Get-CsRgsQueue -Identity service:ApplicationServer:atl-cs-001.litwareinc.com | Where-Object {$_.OverflowCandidate -eq "NewestCall"} | Remove-CsRgsQueue
```


## Detailed Description

When someone calls a phone number associated with the Response Group application one of two things typically happens: either the call is transferred to a question that the caller must answer in order to continue (for example, "Press 1 for hardware support; press 2 for software support") or the call is placed in a queue until a Response Group agent is available to answer the call. 
  
    
    
Instead of having a single queue for all phone calls, the Response Group application enables you to create multiple queues that can be associated with different workflows and different Response Group agent groups. In turn, this means queues can respond differently to events such as a designated number of calls being simultaneously held in the queue, or to callers that have been on hold for specified amount of time.
  
    
    
In addition to creating new queues you can also remove existing queues; that's what the **Remove-CsRgsQueue** cmdlet is for. Note that, by default, you will be prompted if you try to remove a queue that is currently assigned to an active workflow; the prompt will ask you to verify that you want to delete the queue, and Windows PowerShell will pause (and no queue will be deleted) until you answer the prompt. To bypass the prompt, and to delete queues that are being used by an active workflow, add the Force parameter. For example:
  
    
    
Get-CsRgsQueue -Identity "service:ApplicationServer:atl-cs-001.litwareinc.com" | Remove-CsRgsQueue -Force
  
    
    
 **Remove-CsRgsQueue** always checks to see if a queue is being used by an active workflow before it will delete that queue. However, the cmdlet does not verify whether or not the queue is being used by another queue as either the timeout or overflow queue. That means it is possible to delete a queue that is needed by another queue. Because of that, you might want to use the **Get-CsRgsQueue** cmdlet to check the OverflowAction and TimeoutAction properties of your other Response Group queues before running **Remove-CsRgsQueue** to delete a queue.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Instance_ <br/> |Required  <br/> |Microsoft.Rtc.Rgs.Management.WritableSettings.Queue  <br/> |Object reference pointing to the queue to be removed. When piping workflow objects to **Remove-CsRgsQueue** you can leave off the Instance parameter. <br/> To use the Instance parameter use commands similar to this:  <br/>  `$x = Get-CsRgsQueue -Identity ApplicationServer:atl-cs-001.litwareinc.com /1987d3c2-4544-489d-bbe3-59f79f530a83` <br/>  `Remove-CsRgsQueue -Instance $x` <br/> Note that you can only remove a single queue at a time when using the Instance parameter. That means that your object reference ($x) cannot contain multiple queue objects.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Forces the deletion of a Response Group queue. If this parameter is present, the queue will be deleted without warning, even if the queue is assigned to an active workflow. If this parameter is not present then you will be asked to confirm the deletion of any queue currently in use by an active workflow.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   

## Input Types

Microsoft.Rtc.Rgs.Management.WritableSettings.Queue object. **Remove-CsRgsQueue** accepts pipelined instances of the Response Group queue object.
  
    
    

## Return Types

 **Remove-CsRgsQueue** deletes existing instances of the Microsoft.Rtc.Rgs.Management.WritableSettings.Queue object.
  
    
    

## See also


#### 


  
    
    
 [Get-CsRgsQueue](get-csrgsqueue.md)
  
    
    
 [New-CsRgsQueue](new-csrgsqueue.md)
  
    
    
 [Set-CsRgsQueue](set-csrgsqueue.md)
