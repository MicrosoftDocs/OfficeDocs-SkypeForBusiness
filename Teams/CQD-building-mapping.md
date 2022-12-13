---
title: Create a building map for Call Quality Dashboard (CQD)
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: mikedav, siunies, gageames
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.collection: 
  - M365-voice
search.appverid: MET150
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords: 
  - NOCSH
ms.custom: 
  - Reporting
  - seo-marvel-apr2020
description: Learn how to create a building map that you can use to upload tenant and building data in Call Quality Dashboard (CQD).
---

# Create a building map for Call Quality Dashboard (CQD)

In a Microsoft Teams or Skype for Business Online deployment, all clients are external. As a result, by default, all clients are reported as outside in Call Quality Dashboard (CQD), regardless of whether the client is connected on an internal corporate network.

When you work with CQD, you need to know the location of an endpoint and whether it was connected to a network you can manage or a network you can't manage, the assumption being that you can only improve networks you can manage. By uploading subnet and building information to CQD, you enable CQD to determine whether the endpoint was connected to an internal (managed) network or to an external (unmanaged) network. That's why it's important to create a building map for your organization and [upload it to CQD](CQD-upload-tenant-building-data.md).

## Building mapping tools

There are many ways to map your organization's subnets. If you need help, you can use the CQDTools PowerShell Module described in this [blog post](https://aka.ms/cqdtools). These tools are based on PowerShell and use Active Directory (AD) Sites and Services and Microsoft DHCP services to help pre-populate your building file. These tools will help with the following tasks:

1. Query AD Sites and Services, and create a building file based on the information contained within.
1. Query a Microsoft DHCP server or servers to pull subnet information and automatically create a building file.
1. Validate an existing building file, checking for duplicates and overlaps.
1. Find unmapped subnets in CQD.

## Related topics

[Upload tenant and building data in CQD](CQD-upload-tenant-building-data.md)