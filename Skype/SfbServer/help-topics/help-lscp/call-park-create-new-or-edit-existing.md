---
title: "Call Park Create New or Edit Existing"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.date: 3/24/2015
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.lscp.VoiceFeaCallParkEdit
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: e834d485-d25a-4eec-9090-2b8534ecf65d
description: "Call Park number ranges define the temporary numbers where parked calls are held until someone retrieves them or they time out."
---

# Call Park: Create New or Edit Existing

Call Park number ranges define the temporary numbers where parked calls are held until someone retrieves them or they time out.

## UI Reference

The following list describes the fields on the page.

- **Name** Type a descriptive name that identifies the number range. After you save the number range, this name cannot be changed.

- **Number range** In the first field, type the beginning number of the number range. In the second field, type the ending number of the number range.

  - The beginning number of the range must be less than or equal to the ending number of the range.

  - The value of the beginning number of the range must be the same length as the ending number of the range.

  - The number range must be unique. This range cannot overlap with any other range.

  - If the number range begins with the character \* or #, the range must be greater than 100.

  - Valid values: Must match the regular expression string ([\\*|#]?[1-9]\d{0,7})|([1-9]\d{0,8}). This means the value must be a string beginning with either the character \* or # or a number 1 through 9 (the first character cannot be a zero). If the first character is \* or #, the following character must be a number 1 through 9 (it cannot be a zero). Subsequent characters can be any number 0 through 9 up to seven additional characters (for example, "#6000", "\*92000", "\*95551212", and "915551212"). If the first character is not \* or #, the first character must be a number 1 through 9 (it cannot be zero), followed by up to eight characters, each a number 0 through 9 (for example: 915551212;41212;300).

  - You should not have more than a total of 50,000 numbers per pool. Each number range typically encompasses 100 or fewer numbers, but it can be much larger as long as it includes fewer than 10,000 numbers. For example, instead of specifying a starting number of "7000000" and an ending number of "8000000," consider specifying a starting number of "7000000" and an ending number of "7000100."

- **FQDN of destination server** Select the fully qualified domain name (FQDN) or service ID of the Application service that hosts the Call Park application. All calls parked to numbers within the range specified by the start number and end number in the number range will be routed to this server or pool.

For details about Call Park features and capabilities, see [Plan for Call Park in Skype for Business 2015](../../plan-your-deployment/enterprise-voice-solution/call-park.md). For details about working with Call Park number ranges, see [Configure Phone Number Extensions for Parking Calls](https://technet.microsoft.com/library/fbf97624-9587-42a6-b276-1b69c574a74d.aspx).


