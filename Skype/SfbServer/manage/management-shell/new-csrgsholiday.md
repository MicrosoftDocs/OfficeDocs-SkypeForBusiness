---
title: "New-CsRgsHoliday"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 021c6286-207d-4924-b477-15c9a98d6fda
description: "Creates a new Response Group holiday. In the Response Group application, a holiday represents a day when the agents assigned to a queue, who would typically be working that day, will not be working and will not be available to answer calls. For example, if United States (U.S.)-based workers are given Thanksgiving Day off, then a holiday would be configured for November 22, 2013. This cmdlet was introduced in Lync Server 2010."
---

# New-CsRgsHoliday
 
Creates a new Response Group holiday. In the Response Group application, a holiday represents a day when the agents assigned to a queue, who would typically be working that day, will not be working and will not be available to answer calls. For example, if United States (U.S.)-based workers are given Thanksgiving Day off, then a holiday would be configured for November 22, 2013. This cmdlet was introduced in Lync Server 2010.
  
```
New-CsRgsHoliday -EndDate <DateTime> -StartDate <DateTime> [-Name <String>]
```

## Examples

### EXAMPLE 1

The commands shown in Example 1 show how you can create a new holiday (Christmas Day) and then assign that holiday to an existing holiday set. To do this, the first command in the example uses the cmdlet **New-CsRgsHoliday** to create a new holiday, a "virtual" holiday that exists only in memory, and is stored in the variable $christmasDay. **New-CsRgsHoliday** uses three parameters: `StartDate`, which represents the starting date for the holiday (12/25/2013 12:00 AM);  `EndDate`, which represents the end date for the holiday (12/26/2013 12:00 AM); and  `Name`, which represents the unique name to be given to the holiday.
  
After creating the new holiday, the second command uses **Get-CsRgsHolidaySet** to retrieve the holiday set "2013 Holidays" from the service ApplicationServer:atl-cs-001.litwareinc.com. This holiday set is stored in the variable $y.
  
Command 3 uses the Add method to add the new holiday ($christmasDay) to the virtual copy of the holiday set ($y). The final command then calls **Set-CsRgsHolidaySet** to write the changes (that is, to add the new holiday) to the service ApplicationServer:atl-cs-001.litwareinc.com.
  
```
$christmasDay = New-CsRgsHoliday -StartDate "12/25/2013 12:00 AM" -EndDate "12/26/2013 12:00 AM" -Name "Christmas Day"
$y = Get-CsRgsHolidaySet -Identity "service:ApplicationServer:atl-cs-001.litwareinc.com"  -Name "2013 Holidays"
$y.HolidayList.Add($christmasDay)
Set-CsRgsHolidaySet -Instance $y
```

## Detailed Description

The Response Group application uses business hour collections to indicate the days of the week, and the times of day, when agents are typically available to answer phone calls. For example, suppose your help desk is usually staffed from 7:00 A.M. to 7:00 P.M. every Monday. In that case, you would create a business hours collection for the help desk, and configure an opening time of 7:00 A.M. and a closing time of 7:00 P.M. for the typical Monday.
  
However, there might be exceptions to the rule that the help desk is staffed every Monday from 7:00 A.M. to 7:00 P.M.. For example, in the U.S. July 4th is a holiday; consequently, your help desk personnel might not be available on July 4th. In order to account for the fact that the help desk will not be working on Thursday, July 4, 2013, you need to create a holiday for that date and add it to the help desk holiday set.
  
To create a holiday you need to use the **New-CsRgsHoliday** cmdlet. (Note that a "holiday" doesn't have to involve some sort of celebration or festivities; instead, a holiday is simply a day when agents will not be available to answer the phone.) **New-CsRgsHoliday** does not directly add a holiday to a holiday set. Instead, the cmdlet creates a new holiday that exists in memory only. Because of that, you must create an object reference (such $x) that points to this in-memory instance. After the holiday has been created in memory, you then use the **Get-CsRgsHolidaySet** cmdlet to retrieve the appropriate holiday set and the **Set-CsRgsHolidaySet** cmdlet to add the new holiday to that set.
  
Although a holiday set can (and typically does) hold multiple holidays, these holidays must be added to the set one holiday at a time.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _EndDate_ <br/> |Required  <br/> |System.DateTime  <br/> |Ending date for the holiday. The format for the ending date depends on your Regional and Language Options. For example, in the U.S. an ending date of July 4, 2013 would be formatted like this:  `-EndDate "7/5/2013 12:00 AM"`, meaning that the holiday ends at 12:00 A.M. on July 5, 2013.  <br/> |
| _StartDate_ <br/> |Required  <br/> |System.DateTime  <br/> |Starting date for the holiday. The format for the starting date depends on your Regional and Language Options. For example, in the U.S. a starting date of July 4, 2013 would be formatted like this:  `-StartDate "7/4/2013 12:00 AM"`, indicating that the holiday begins at 12:00 A.M. on July 4, 2013.  <br/> |
| _Name_ <br/> |Optional  <br/> |System.String  <br/> |Unique name used to differentiate the holiday from other holidays.  <br/> |
   
## Input Types

None. **New-CsRgsHoliday** does not accept pipelined input.
  
## Return Types

 **New-CsRgsHoliday** creates new instances of the Microsoft.Rtc.Rgs.Management.WritableSettings.Holiday object.
  
## See also

#### 

[New-CsRgsHolidaySet](new-csrgsholidayset.md)
  
[Set-CsRgsHolidaySet](set-csrgsholidayset.md)

