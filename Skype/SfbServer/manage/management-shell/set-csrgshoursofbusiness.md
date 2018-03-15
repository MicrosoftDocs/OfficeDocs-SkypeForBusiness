---
title: "Set-CsRgsHoursOfBusiness"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: be976e84-00aa-46d5-94d3-527c4c9f3963
description: "Configures an existing set of Response Group business hours. Business hour sets are used to indicate the days of the week and the times of day when Response Group agents are typically available to answer phone calls. This cmdlet was introduced in Lync Server 2010."
---

# Set-CsRgsHoursOfBusiness
 
Configures an existing set of Response Group business hours. Business hour sets are used to indicate the days of the week and the times of day when Response Group agents are typically available to answer phone calls. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsRgsHoursOfBusiness -Instance <BusinessHours> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]
```

## Examples

### EXAMPLE 1

Example 1 shows you can assign a new time range value to the SaturdayHours1 and SundayHours1 properties of the business hours set Help Desk Business Hours. To do this, the first command in the example uses **New-CsRgsTimeRange** to create a new time range object (Weekend Hours) with an opening time of 12:00 P.M. (12:00) and a closing time of 5:00 P.M. (17:00). This object is stored in a variable named $weekend.
  
The next command creates an object reference ($x) to the Help Desk Business Hours business hours set on ApplicationServer:atl-cs-001.litwareinc.com. When that command is finished, commands 3 and 4 are used to set the SaturdayHours1 and SundayHours1 properties to the time range value stored in $weekend. Finally, the last command in the example then uses **Set-CsRgsHoursOfBusiness** to write these changes back to the actual business hours set.
  
```
$weekend = New-CsRgsTimeRange -Name "Weekend Hours" -OpenTime "12:00" -CloseTime "17:00"

$x = Get-CsRgsHoursOfBusiness -Identity "service:ApplicationServer:atl-cs-001.litwareinc.com" -Name "Help Desk Business Hours"
$x.SaturdayHours1 = $weekend
$x.SundayHours1 = $weekend
Set-CsRgsHoursOfBusiness -Instance $x
```

### EXAMPLE 2

The commands shown in Example 2 delete the values configured for the SaturdayHours1 and the SaturdayHours2 properties in the business hours set Help Desk Business Hours. To do, this, first command creates an object reference ($x) to the Help Desk Business Hours business hours set on ApplicationServer:atl-cs-001.litwareinc.com. After the object reference has been created, the second command sets the SaturdayHours1 property to a null value ($Null); this effectively erases any value previously assigned to SaturdayHours1. A similar command is then used to erase any value previously assigned to SaturdayHours2. 
  
The final command in the example then uses **Set-CsRgsHoursOfBusiness** to write these changes back to the actual business hours set. When the command finishes running, there will no longer be any Saturday business hours assigned to Help Desk Business Hours.
  
```
$x = Get-CsRgsHoursOfBusiness -Identity "service:ApplicationServer:atl-cs-001.litwareinc.com" -Name "Help Desk Business Hours"
$x.SaturdayHours1 = $Null
$x.SaturdayHours2 = $Null

Set-CsRgsHoursOfBusiness -Instance $x
```

## Detailed Description

In order to provide callers with the best possible experience, the Response Group application makes it possible for you to clearly define when Response Group agents are available to answer calls and when they are not available to answer calls. With the Response Group application, you can define business hours; these hours indicate the days of the week and hours of the day that agents are available to answer calls. For example, if your organization is typically open from 9:00 A.M. to 5:00 P.M. Monday through Friday, then you would configure business hours that show that agents are available from 9:00 A.M. to 5:00 P.M. Monday through Friday (and, by extension, that agents are not available at, say, 8:00 P.M. on a Thursday or 2:30 P.M. on a Sunday).
  
Business hour sets are created by using the **New-CsRgsHoursOfBusiness** cmdlet. After these sets have been created, they can be modified by using the **Set-CsRgsHoursOfBusiness** cmdlet. Typically, this will mean changing the business hours for one or more days of the week. For example, if the help desk used to stay open until 5:00 P.M. on Fridays but now stays open until 7:00 P.M. on Fridays, then you will need to modify the business hours for Friday. If the help desk used to be open on Saturdays but is now closed on Saturdays, you will likewise need to modify the Saturday business hours. (To indicate that a group is not available on a particular day, simply set the business hours for that day to a null value: -SundayTimeRange1 $Null.)
  
When configuring business hours within a business hours set, keep in mind that each day of the week has both a Hours1 and a Hours2 property. If your help desk is open from 8:00 A.M. to 5:00 P.M., you only need to assign values to the appropriate Hours1 property. However, suppose the help desk is open from 8:00 A.M. to 2:00 P.M., then open again from 5:00 P.M. until 11:00 P.M.. In that case you need to assign the time range 8:00 A.M. to 2:00 P.M. to Hours1 and 5:00 P.M. to 11:00 P.M. to Hours2.
  
Note that **Set-CsRgsHoursOfBusiness** does not directly modify a business hours set. Instead, you must use **Get-CsRgsHoursOfBusiness** to create an object reference to the set to be modified. (When you create an object reference you simply retrieve a copy of the business hours set and then store that copy in a variable.) After you have created an object reference, you modify the properties of that in-memory-only object. When your modifications are complete, you then use **Set-CsRgsHoursOfBusiness** to write those changes to the actual business hours set.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Instance_ <br/> |Required  <br/> |Microsoft.Rtc.Rgs.Management.WritableSettings.BusinessHours  <br/> |Object reference to the business hours set to be modified. An object reference is typically retrieved by using the **Get-CsRgsHoursOfBusiness** cmdlet and assigning the returned value to a variable; for example, this command returns an object reference to the Help Desk business hours set, and stores that object reference in a variable named $x: <br/>  `$x = Get-CsRgsHoursOfBusiness -Identity service:ApplicationServer:atl-cs-001.litwareinc.com -Name "Help Desk"` <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types

Microsoft.Rtc.Rgs.Management.WritableSettings.BusinessHours object. **Set-CsRgsHoursOfBusiness** accepts pipelined instances of the Response Group business hours object.
  
## Return Types

Modifies existing instances of the Microsoft.Rtc.Rgs.Management.WriteableSettings.BusinessHours object.
  
## See also

#### 

[Get-CsRgsHoursOfBusiness](get-csrgshoursofbusiness.md)
  
[New-CsRgsHoursOfBusiness](new-csrgshoursofbusiness.md)
  
[New-CsRgsTimeRange](new-csrgstimerange.md)
  
[Remove-CsRgsHoursOfBusiness](remove-csrgshoursofbusiness.md)

