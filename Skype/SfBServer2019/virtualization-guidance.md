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

Skype for Business Server 2019 is supported on virtualization, provided it is deployed in line with the [Planning a Lync Server 2013 Deployment on Virtual Servers](https://www.microsoft.com/download/details.aspx?id=41936) guidance.

## Virtualization guidance highlights

- Do not use processor oversubscription; maintain a 1:1 ratio of virtual CPU to physical CPU.
- Moving a guest server while operating is not supported.
- Virtual machine portability or failover techniques such as live migration are not supported.
- You should disable hyper-threading on all hosts.
- Do not configure dynamic memory or memory overcommitment on host servers.
- Use fixed or pass-through disks rather than dynamic disks.
- Hypervisors require an amount of overhead (typically 6 percent to 10 percent) above and beyond what the virtual guest requires.

You can check the [Lync 2013 guidance document](https://www.microsoft.com/download/details.aspx?id=41936) for full details.

Note that supported does not in any way mean recommended. It has always been recommended to go physical hardware to reduce the number of potential complications, especially in large or highly utilized environments.

There is no updated guidance specifically for virtualizing SfB Server 2019 at this time, but Microsoft intends to release specific guidance in the future (no public ETA).

**Expect an official support statement from Microsoft when the formal guidance is completed by Microsoft. If you can wait for the official virtualization guidance and support statement that would be the best thing to do.** < I assume we can remove this>

The Lync Server Stress and Performance Tool (LSS) does not run against SfB Server 2019. So today, you cannot use that tool to validate your virtualization platform. There is a plan to update these tools to work with SfB Server 2019

Most of the KHI’s/Perfmon counters are similar, but you should definitely be monitoring and reporting on those in a virtual environment. **Again expect updated guidance in due course.**  < I assume we can remove this>

## Supported hypervisors 

SfB Server 2019 is supported on Windows Server 2016 and Windows Server 2019, so is therefore supported on Hyper-V on those versions of Windows Server

For third-party hypervisors, as before, you need a hypervisor that has passed the Server Virtualization Validation Program (SVVP) testing for the relevant OS.

The Windows Server 2016 versions are:

- VMware
- Citrix XenServer
- Nutanix

See the [SVVP](https://www.windowsservercatalog.com/results.aspx?&bCatID=1521&cpID=0&avc=86&ava=130&avt=0&avq=0&OR=1&PGS=25) reference for more details.

The Windows Server 2019 versions are:

- VMware
- Red Hat
- Citrix Xenserver
- SUSE Linux
- Nutanix

See the [SVVP](https://www.windowsservercatalog.com/results.aspx?&bCatID=1521&cpID=0&avc=126&ava=130&avt=0&avq=0&OR=1&PGS=25) reference for more details.


