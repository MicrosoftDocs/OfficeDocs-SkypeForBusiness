---
title: "Virtualization support for Skype for Business Server 2019 "
ms.reviewer: corbinm
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 06/04/2020
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.collection: IT_Skype16
description: "Summary: Learn about the virtualization support for Skype for Business Server 2019."
---

# Virtualization support for Skype for Business Server 2019

Skype for Business Server 2019 is supported on virtualization.

While virtualization is supported, there are some key points to remember:

- Maintain a 1:1 ratio of virtual CPU to physical CPU.
- Don't move a guest server while it's operating.
- Migration of a live system and portability of a virtual machine aren't supported.
- Disable hyper-threading on all hosts.
- Don't configure dynamic memory on host servers.
- Use fixed or pass-through disks rather than dynamic disks.
- Allow for 6-10 percent overhead for hypervisors beyond what the virtual guest requires.

## Supported hypervisors

SfB Server 2019 is supported on Windows Server 2016 and Windows Server 2019.

For third-party hypervisors, you need a hypervisor that has passed the Server Virtualization Validation Program (SVVP) testing for the relevant OS.

- See the [Windows Server 2016 versions](https://www.windowsservercatalog.com/results.aspx?&bCatID=1521&cpID=0&avc=86&ava=88&avt=0&avq=0&OR=1&PGS=25) in the SVVP list.
- See the [Windows Server 2019 versions](https://www.windowsservercatalog.com/results.aspx?&bCatID=1521&cpID=0&avc=86&ava=130&avt=0&avq=0&OR=1&PGS=25) in the SVVP list.

## Stress and performance tool

The Skype for Business Server 2019 Stress and Performance Tool includes tools that simplify capacity planning for Skype for Business Server 2019. The Skype for Business Server 2019 Stress and Performance Tool will help you to:

- Simplify your hardware planning for Skype for Business Server 2019
- Provide you with increased knowledge and best practices for performance tuning
- Measure the performance of your intended Skype for Business Server 2019 deployments
 
You can download the tool from [here](https://www.microsoft.com/download/details.aspx?id=101447).
