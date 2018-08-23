---
title: Using admin roles to manage Teams
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 08/23/2018
ms.topic: article
ms.service: msteams
description: Learn to use the different adminstrative roles to manage Teams.
appliesto: 
- Microsoft Teams
---

# Using Microsoft Teams admin roles

Using Azure Active Directory (Azure AD), you can designate administrators who need different levels of access for managing Microsoft Teams. Administrators can manage the entire Teams workload, or they can have delegated permissions for troubleshooting call quality problems or managing your organization's telephony needs. 

## Teams roles and capabilities

There are four Teams admin roles available: Teams service administrator, Teams communications administrator, Teams communications support specialist, and Teams communications support engineer. Review the following table to understand what each role can do and which tools the admin can use in the Teams and Skype for Business Admin Center and PowerShell.

<!-- add Global admin role? -->

| Role | Can do these tasks | Can access the following tools |
|----- | ------------------ | ------------------------------ |
| Teams Service Administrator | Manage the Microsoft Teams service and create and manage Office 365 groups | Policies:  <br>TeamsMeetingPolicy<sup>1</sup><br> TeamsCallingPolicy<sup>1</sup><br>Configurations:<br>Tools: full access to Call Analytics<sup>3</sup> |
| Teams Communications Administrator | Manage calling and meetings features within the Microsoft Teams service | Policies:<br>Configurations:<br>Tools: full access to Call Analytics<sup>3</sup> |
| Teams Communications Specialist | Troubleshoot communications issues within Teams by using **basic** tools.| Tools: full access to Call Analytics<sup>3</sup> |
| Teams Communications Support Engineer | Troubleshoot communications issues within Teams by using **advanced** tools. | tools: access to all troubleshooting tools in Call Analytics<sup>3</sup>

<sup>1</sup> [PowerShell - Skype for Business module](https://docs.microsoft.com/en-us/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell)<br>
<sup>2</sup> [PowerShell - Microsoft Teams module](https://www.powershellgallery.com/packages/MicrosoftTeams/)<br>
<sup>3</sup> [Microsoft Teams and Skype for Business Admin Center](https://docs.microsoft.com/en-us/microsoftteams/manage-teams-skypeforbusiness-admin-center)
<!-- <sup>4</sup> Azure Active Directory Admin Center <<note that these are going to come later because they’re related to O365 Group management>> 
<sup>5</sup> Microsoft 365 Admin Center <<note that these are going to come later because they’re related to O365 Group management>> 
-->
For more information about the admin tools available for managing Microsoft Teams, see [Managing Microsoft Teams](https://docs.microsoft.com/en-us/microsoftteams/manage-teams-skypeforbusiness-admin-center).

## Cmdlets available to admin roles

To view the full list of cmdlets currently available to a given role:

1.	Assign the role to a user (and make sure that user has no other roles).
2.	Connect to the Skype for Business PowerShell module:<br>
    a. $session = new-csonlinesession<br>
    b. Import-pssession $session <br>
    c. Use ``Get-Module`` to identify the name of the imported session (it will be a randomly generated name).
1. Use ``Get-Command -Module <name from above>`` to identify all available cmdlets for the role.

### Related topics

- [Microsoft Teams PowerShell](https://docs.microsoft.com/en-us/powershell/module/teams/?view=teams-ps)
- [Assign roles and permissions in Microsoft Teams](https://docs.microsoft.com/en-us/microsoftteams/assign-roles-permissions)
- [Using PowerShell to manage Teams](using-powershell-to-manage-teams.md)


