---
title: "Plan for Modern Authentication in Skype for Business"
ms.reviewer: 
ms.author: tracyp
author: MSFTTracyP
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 25e68396-96dc-4e4b-8a65-d30ea80d1bc9
description: "Planning topics for Authentication and Authorization for Skype for Business Server, including integration with other products"
---

# Discussing Authentication and Authorization in Skype for Business

Authentication and authorization are related concepts, but do different work for you (though both are necessary). Put in simple terms, authenciation (AuthN) depends on secrets only a valid user knows or has, and that can be a password, code, fingerprint, certificate, a combination of claims about the user that are true, or a combination of these things used together. AuthN is a process out to prove you are who you say you are.

Authorization (AuthZ) is concerned with what you have access to after you've proven who you are. It determines what you've been allowed to see, edit, and otherwise access. For example, you may have powerful Site Collection Administrator access to SharePoint Online, but if you switch to another online workload, like Skype for Business Online, you may have the privileges to troubleshoot user issues, not change the configuration of the server or servers. In a third workload, such as Exchange Online, you might only have the average user's access. AuthZ checks what and how much access you have to services/worloads, applications, files, and other data.

Our examples involve online properties like SharePoint and Exchange online, but the processes of AuthN and AuthZ work on-premises and in a hybrid premises the same way. Ultimately, tools like AAD Connect and ADFS become involved in the AuthN and AuthZ story by either synchronizing on-premises accounts and passwords into the Cloud's AD (which is Azure AD in the case of either Office 365 or Azure), or intruding in the flow of AuthZ so that a user isn't frequently prompted for their credentials, say when switching between workloads in the Cloud, creating Single Sign-On scenarios. But they aren't, in themselves, responsible AuthN or AuthZ, just part of the mechanics.

Today, many technologies consider these processes (AuthN and AuthZ) to be one mechanism, and you'll hear many references to authentication process that also include authorization in them. It's important to remember that the first step in user access is AuthN, proving you are who you say you are, and that AuthZ uses the knowledge of who the user is to determine what he or she has access to (as you'll see with Open Authorization or OAuth).

  
## Authentication and Authorization Planning Topics

[How to use Modern Authentication (ADAL) with Skype for Business](plan-adal.md)

[Skype for Business topologies supported with Modern Authentication](topologies-supported.md)

[Planning to turn off Legacy authentication methods internally and externally to your network.](turn-on-modern-auth.md)

