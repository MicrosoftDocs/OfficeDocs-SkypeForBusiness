---
title: "Overview of the Lync Server 2013 hybrid environment"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365_Hybrid
ms.assetid: 0d16ec3a-28f0-4483-96e7-8e68f30398fa
description: "In this articleAbout this GuidePrerequisitesAdministrator CredentialsConnecting to Lync Online PowerShell"
---

# Overview of the Lync Server 2013 hybrid environment
[]
 **In this article**
  
[About this Guide](#sectionSection0)
  
[Prerequisites](#sectionSection1)
  
[Administrator Credentials](#sectionSection2)
  
[Connecting to Lync Online PowerShell](#sectionSection3)
  
Lync Server 2013 hybrid environment refers to a deployment in which there are some users homed to the on-premises Lync Server 2013 and other users homed to Skype for Business Online, but users share the same domain, such as user@contoso.com.
  
## About this Guide
<a name="sectionSection0"> </a>

This guide describes the tasks necessary to configure your Lync Server 2013 environment for interoperability with Skype for Business Online, and then to move users from your on-premises deployment to use Skype for Business Online.
  
## Prerequisites
<a name="sectionSection1"> </a>

You will need to have the following applications and utilities installed to complete the tasks for configuring a deployment for hybrid. The installers for these files are included on the installation media provided for your deployment, as well as at the links included in the following list.
  
- [Active Directory Federation Services (AD FS) 2.0](https://go.microsoft.com/fwlink/p/?LinkId=257305)
    
- [Microsoft Directory Synchronization Tool 9.1](http://go.microsoft.com/fwlink/p/?LinkId=257307)
    
- [Install Windows PowerShell for single sign-on with AD FS](https://go.microsoft.com/fwlink/p/?LinkId=398710)
    
- Microsoft Online Services Sign-in Assistant (msoidcli-7.0.msi) is included with the Desktop Setup for Office 365, which can be obtained from the Downloads page linked to from the Office 365 Admin portal.
    
## Administrator Credentials
<a name="sectionSection2"> </a>

When you are asked to provide your administrator credentials, use the username and password for the administrator account for your Office 365 tenant. You will also use these credentials when you configure Active Directory Federation Services (AD FS) 2.0, Directory Synchronization, Single sign-on, federation, and moving users to Lync Online.
  
## Connecting to Lync Online PowerShell
<a name="sectionSection3"> </a>

Administrators now have the ability to use Windows PowerShell to manage Skype for Business Online and their Skype for Business Online user accounts. To do this, you must first download and install the Skype for Business Online Connector Module from the Microsoft Download Center (http://go.microsoft.com/fwlink/?LinkId=294688). For more information on downloading, installing, and using the Skype for Business Online Connector Module, and for detailed information on using Windows PowerShell to manage Skype for Business Online, see [Using Windows PowerShell to manage Skype for Business Online](using-windows-powershell-to-manage-skype-for-business-online.md).
  

