---
title: 'Verify communications with a Skype for Business Online customer'
ms:assetid: c8287b15-e1bb-4b26-8354-0ec90b2fcfe7
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Hh202189(v=OCS.15)
ms:contentKeyID: 48185378
mtps_version: v=OCS.15
ms.author: jambirk
author: jambirk
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: ""
---


# Verify communications with a Skype for Business Online customer in Skype for Business Server

To enable Skype for Business users in your organization to communicate with users of a Skype for Business Online customer, you must have completed the following steps:

  - Met all prerequisites. This includes deploying your internal and edge servers, enabling federation support for your organization, and setting up user accounts. For details, see [Prerequisites for federating with a Skype for Business Online customer](prerequisites-for-federating.md).

  - Configured domain access support in your internal deployment. This includes creating a host provider entry and configuring your deployment to allow access from the Skype for Business Online customer’s domain. For details, see [Configure federation support for a Skype for Business Online domain](configure-federation-support-for-domain.md).

  - Configured your user accounts to support federation. For details, see [Configure user access for federation with a Skype for Business Online customer](configure-user-access-for-federation.md).

After you complete all of these steps and the administrator of the Skype for Business Online customer completes all configuration of their online services to support federation with your organization, verify communications by testing communications between an internal user in your organization and a user of the Skype for Business Online customer. If communication is not successful, use the Logging Tool from your Edge Server to capture log and trace files in order to troubleshoot the problem. 

