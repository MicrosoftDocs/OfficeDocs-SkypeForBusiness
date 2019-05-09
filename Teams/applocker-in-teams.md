---
title: AppLocker application control policies in Microsoft Teams
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.topic: article
ms.service: msteams
MS.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
ms.reviewer: rafarhi
search.appverid: MET150
description: Learn how to enable the Teams desktop client application with AppLocker application control policies.
appliesto: 
- Microsoft Teams
---

# AppLocker application control policies in Microsoft Teams

This article explains how to enable the Teams desktop client app with AppLocker application control policies. Use of AppLocker is designed to restrict program and script execution by non-administrative users. For more information and guidance on AppLocker, see [What is AppLocker?](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/applocker/what-is-applocker). 

The process for enabling Teams with AppLocker requires the creation of AppLocker-based whitelisting policies. Policies are created with Group Policy management software and/or the use of Windows PowerShell cmdlets for AppLocker (see the [AppLocker technical reference](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-technical-reference) for more information). The AppLocker policy is saved in XML format and can be edited with any text or XML editor.

## Teams whitelisting with AppLocker

AppLocker rules are organized into collections of rules. AppLocker rules apply to the targeted app, and they are the components that make up the AppLocker policy.  

To whitelist Teams, we recommend that you use the [publisher condition rules](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/applocker/understanding-the-publisher-rule-condition-in-applocker) since all Teams app files are digitally signed.
  
We don't recommend the use of path rules because the Teams installation directory is user-writable. We also don't recommend the use of hash rules because the rules would have to be updated each time the Teams client app is updated.

Since Teams desktop executable files are digitally signed, the publisher condition identifies an app file based on its digital signature and embedded version attributes. The digital signature contains information about the company that created the app file (the publisher). The version information, which is obtained from the binary resource, includes the name of the product that the file is part of and the version number of the application file.

### Examples of publisher condition rules

For the Teams client app (all files, all versions):

`Publisher: O=MICROSOFT CORPORATION, L=REDMOND, S=WASHINGTON, C=US

Product name: MICROSOFT TEAMS`

## Related topics
[What is AppLocker?](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/applocker/what-is-applocker)
[AppLocker technical reference](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-technical-reference)