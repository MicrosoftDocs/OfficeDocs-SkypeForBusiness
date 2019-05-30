---
title: Known issues for retention policies in Microsoft Teams
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 09/11/2018
ms.topic: reference
ms.service: msteams
ms.reviewer: anach
description: Current list of known issues for Microsoft Teams retention policies.
localization_priority: Normal
search.appverid: MET150
MS.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
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
|![An icon representing a decision point](media/Overview_of_security_and_compliance_in_Microsoft_Teams_image3.png)     |Decision point         |What security and compliance features does your organization require? Does your organization have the required licenses to meet Security and Compliance business requirements?         |
|![An icon representing the next steps](media/Overview_of_security_and_compliance_in_Microsoft_Teams_image4.png)     |Next steps         |Document your required security and compliance features.         |
