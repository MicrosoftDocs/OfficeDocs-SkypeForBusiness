---
title: "Virtualization support for Skype for Business Server 2019 "
ms.reviewer: 
ms.author: v-cichur
author: cichur
manager: serdars
ms.date: 05/19/20
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
f1.keywords:
- NOCSH
localization_priority: Normal
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

Follow the deployment criteria in [Planning a Lync Server 2013 Deployment on Virtual Servers](https://www.microsoft.com/download/details.aspx?id=41936) for best practices.

**Supported hypervisors** 

SfB Server 2019 is supported on Windows Server 2016 and Windows Server 2019.

For third-party hypervisors, you need a hypervisor that has passed the Server Virtualization Validation Program (SVVP) testing for the relevant OS.

- See the [Windows Server 2016 versions](https://www.windowsservercatalog.com/results.aspx?&bCatID=1521&cpID=0&avc=86&ava=88&avt=0&avq=0&OR=1&PGS=25) in the SVVP list.
- See the [Windows Server 2019 versions](https://www.windowsservercatalog.com/results.aspx?&bCatID=1521&cpID=0&avc=86&ava=130&avt=0&avq=0&OR=1&PGS=25) in the SVVP list.




