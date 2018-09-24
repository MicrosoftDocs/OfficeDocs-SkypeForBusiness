---
title: Known issues for retention policies in Microsoft Teams
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 09/11/2018
ms.topic: article
ms.service: msteams
ms.reviewer: anach
description: Current list of known issues for the Microsoft Teams retention policies.
localization_priority: Normal
search.appverid: MET150
MS.collection: Strat_MT_TeamsAdmin
appliesto: 
- Microsoft Teams
---

# Known issues for retention policies in Microsoft Teams

The following are known issues for retention policies in Teams that are being tracked and investigated.

- Under Choose Teams in the Teams Channel messages location row, you may see Office 365 Groups that are not also Teams. This will be addressed in the future.

- Under Choose Users in the Teams Chat location row, you may see guests and non-mailbox users. Retention policies are not meant to be set for guests, and we are working to remove these from the list.

- Exchange Life Cycle assistant (ELC) runs daily, but it has an SLA of 7 days. As a result, it's possible that, if you have a Teams retention policy to delete items older than 60 days, these items could persist for up to 67 days. This isn't a new situation - it follows the Exchange model. Of course, in most cases, there is no delay.


| | | |
|---------|---------|---------|
|![Decison Point icon.](media/Overview_of_security_and_compliance_in_Microsoft_Teams_image3.png)     |Decision point         |What security and compliance features does your organization require? Does your organization have the required licenses to meet Security and Compliance business requirements?         |
|![Next Steps icon.](media/Overview_of_security_and_compliance_in_Microsoft_Teams_image4.png)     |Next steps         |Document your required security and compliance features.         |

Licensing
---------------

When it comes to the information protection capabilities, Office 365 subscriptions and the associated standalone licenses will determine the available feature set.

|Information Protection Capability   |Office 365 Business Essentials   |Office 365 Business Premium   |Office 365 Enterprise E1   |Office 365 Enterprise E3/E4   |Office 365 Enterprise E5   |
|---|---|---|---|---|---|
|Archive|-  |-   |-   |Yes   |Yes   |
|In-Place eDiscovery|-   |-   |-   |Yes   |Yes   |
|Advanced eDiscovery|-   |-   |-   |-   |Yes   |
|Legal Hold|-   |-   |-   |Yes   |Yes   |
|Compliance Content Search|- |- |- |Yes |Yes |
|Auditing and Reporting|Yes |Yes |Yes |Yes |Yes |
|Conditional Access* |Yes |Yes |Yes |Yes |Yes |
> [!NOTE]
> \*Conditional Access requires additional licenses


| |  |  |
|---------|---------|---------|
|![Decision Point icon.](media/Overview_of_security_and_compliance_in_Microsoft_Teams_image3.png)     |Decision point         |Does your organization have the required licenses to meet Compliance and Security business requirements?         |
|![Next Steps icon.](media/Overview_of_security_and_compliance_in_Microsoft_Teams_image4.png)    |Next steps         |Review your organization's current licensing and confirm it meets all business requirements for compliance and security.         |

Before enabling any of these features, ensure you have access to the Security & Compliance Center in the Office 365 admin center. By default, tenant admins have access.

Content Search and eDiscovery do not require enablement in the Security & Compliance Center.
