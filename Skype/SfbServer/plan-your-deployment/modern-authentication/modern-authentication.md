---
ms.date: 03/17/2018
title: "Plan for Modern Authentication in Skype for Business"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
audience: ITPro
ms.topic: conceptual
manager: serdars
ms.service: skype-for-business-server
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.assetid: 25e68396-96dc-4e4b-8a65-d30ea80d1bc9
description: "Planning articles for Authentication and Authorization for Skype for Business Server, including integration with other products"
---

# Discussing Authentication and Authorization in Skype for Business

Authentication and authorization are related concepts, but do different work for you (though both are necessary). Put in simple terms, authentication (AuthN) depends on secrets only a valid user knows or has, and that can be a password, code, fingerprint, certificate, a combination of claims about the user that are true, or a combination of these things used together. AuthN is a process out to prove you're who you say you are.

Authorization (AuthZ) is concerned with what you have access to after you prove who you are. It determines what you've been allowed to see, edit, and otherwise access. For example, you might have powerful Site Collection Administrator access to SharePoint Online, but if you switch to another online workload, like Skype for Business Online, you might have the privileges to troubleshoot user issues, not change the configuration of the server or servers. In a third workload, such as Exchange Online, you might only have the average user's access. AuthZ checks what and how much access you have to services/worloads, applications, files, and other data.

Our examples involve online properties like SharePoint and Exchange online, but the processes of AuthN and AuthZ work on-premises and in a hybrid premise the same way. Ultimately, tools like Microsoft Entra Connect and ADFS become involved in the AuthN and AuthZ story by either synchronizing on-premises accounts and passwords into the Cloud's AD (which is Microsoft Entra ID), or intruding in the flow of AuthZ so that a user isn't frequently prompted for their credentials, say when switching between workloads in the Cloud, creating single sign-on scenarios. But they aren't, in themselves, responsible AuthN or AuthZ, just part of the mechanics.

Today, many technologies consider these processes (AuthN and AuthZ) to be one mechanism, and you'll hear many references to authentication process that also include authorization in them. It's important to remember that the first step in user access is AuthN, proving you're who you say you are, and that AuthZ uses the knowledge of who the user is to determine who has access to (as you see with Open Authorization or OAuth).

  
## Authentication and Authorization Planning Articles

[How to use Modern Authentication (ADAL) with Skype for Business](plan-adal.md)

[Skype for Business topologies supported with Modern Authentication](topologies-supported.md)

[Planning to turn off Legacy authentication methods internally and externally to your network.](turn-on-modern-auth.md)
