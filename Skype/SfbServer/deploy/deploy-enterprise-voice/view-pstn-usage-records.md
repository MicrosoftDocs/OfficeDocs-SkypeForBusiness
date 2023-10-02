---
ms.date: 03/17/2018
title: "View PSTN usage records in Skype for Business"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
audience: ITPro
ms.topic: quickstart
ms.service: skype-for-business-server
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.collection:
- IT_Skype16
- Strat_SB_Admin
ms.custom:
ms.assetid: 65025c78-c263-472c-9ff9-e170588f10b5
description: "Summary: Learn how to view PSTN usage records by using the Skype for Business Server Control Panel or the Skype for Business Server Management Shell."
---

# View PSTN usage records in Skype for Business

**Summary:** Learn how to view PSTN usage records by using the Skype for Business Server Control Panel or the Skype for Business Server Management Shell.

A Public Switched Telephone Network (PSTN) usage record specifies a class of call (such as internal, local, or long distance) that can be made by various users or groups of users in an organization. For details, see [PSTN Usage Records](/previous-versions/office/lync-server-2013/lync-server-2013-pstn-usage-records) in the Planning documentation.

### To view a PSTN usage record by using Skype for Business Server Control Panel

1. Open Skype for Business Server Control Panel.

2. In the left navigation bar, click **Voice Routing** and then click **PSTN Usage**.

3. On the **PSTN Usage** page, highlight the PSTN usage record you want to view, click **Edit** and then click **Show details**.

    > [!NOTE]
    > A read-only page of the selected PSTN usage record shows the associated routes and associated voice policies.

### To view PSTN usage information by using Skype for Business Server Management Shell cmdlets

- To view information about all of your PSTN usages, type the following command in the Skype for Business Server Management Shell, and then press ENTER:

  ```powershell
  Get-CsPstnUsage
  ```

    This command returns information similar to the following:

<pre>
  Identity : Global
  Usage    : {Internal, Local, Long Distance}
</pre>

## See also

[Create or modify a voice policy and configure PSTN usage records in Skype for Business](voice-policy-and-pstn-usage-records.md)
