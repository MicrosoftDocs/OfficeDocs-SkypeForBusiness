---
title: Use Microsoft Teams administrator roles to manage Teams
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 09/19/2018
ms.topic: article
ms.service: msteams
ms.collection: 
- M365-collaboration
- Teams_ITAdmin_Help
ms.reviewer: islubin
description: Learn to use the different administrative roles to manage Teams.
appliesto: 
- Microsoft Teams
---

# Use Microsoft Teams administrator roles to manage Teams

Using Azure Active Directory (Azure AD), you can designate administrators who need different levels of access for managing Microsoft Teams. Administrators can manage the entire Teams workload, or they can have delegated permissions for troubleshooting call quality problems or managing your organization's telephony needs. 

## Teams roles and capabilities

There are four Teams admin roles available: Teams service administrator, Teams communications administrator, Teams communications support specialist, and Teams communications support engineer. Review the following table to understand what each role can do and which tools the admin can use in the Microsoft Teams admin center and PowerShell.



<!-- add Global admin role? -->

| Role | Can do these tasks | Can access the following tools |
|----- | ------------------ | ------------------------------ |
| Teams Service Administrator | Manage the Teams service, and manage and create Office 365 Groups | Everything in the Microsoft Teams admin center and associated PowerShell controls, including:<ul><li> Manage meetings, including meeting policies, configurations, and conference bridges.<sup>1,3</sup></li><li>Manage voice, including calling policies and phone number inventory and assignment.<sup>1</sup></li><li>Manage messaging, including messaging policies.<sup>1,3</sup></li><li>Manage all org-wide settings, including federation, teams upgrade, and teams client setting.s<sup>1,3</sup></li><li>Manage the teams in the organization and their associated settings, including membership (group management supported via PowerShell, team management in the Teams admin center).<sup>23</sup></li><li>View user profile page and troubleshoot user call quality problems using advanced troubleshooting toolset.<sup>3</sup> </li><li> Access, monitor and troubleshoot tenant's call quality and reliability using data exposed in Call Quality Dashboard (CQD) down to the users impacted by poor call quality. Create new reports, update and remove reports as needed. Upload and update CQD building data.</li><li> [Publish apps to the Tenant App Catalog from the Teams client](https://docs.microsoft.com/en-us/microsoftteams/tenant-apps-catalog-teams)</li></ul> |
| Teams Communications Administrator | Manage calling and meetings features within the Teams service. | Manage meetings, including meeting policies, configurations, and conference bridges.<sup>1,3</sup><br><br> Manage voice, including calling policies and phone number inventory and assignment.<sup>1</sup><br><br> View user profile page and troubleshoot user call quality problems using advanced troubleshooting toolset.<sup>3</sup> <br><br> Access, monitor, and troubleshoot tenant's call quality and reliability using data exposed in Call Quality Dashboard (CQD) down to the users who are impacted by poor call quality. Create new reports, update and remove reports as needed. Upload and update CQD building data.|
| Teams Communications Support Engineer | Troubleshoot communications issues within Teams by using **advanced** tools. | View user profile page and troubleshoot user call quality problems using advanced troubleshooting toolset.<sup>3</sup> <br><br> Access, monitor, and troubleshoot tenant's call quality and reliability using data exposed in Call Quality Dashboard (CQD) down to the users who are impacted by poor call quality. |
| Teams Communications Support Specialist | Troubleshoot communications issues within Teams by using **basic** tools.| Access user profile page for troubleshooting calls in Call Analytics. Can only view user information for the specific user being searched for.<sup>3</sup> <br><br> Access, monitor, and troubleshoot tenant's call quality and reliability using data exposed in Call Quality Dashboard (CQD).  

<sup>1</sup> [PowerShell - Skype for Business module](https://docs.microsoft.com/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell)<br>
<sup>2</sup> [PowerShell - Microsoft Teams module](https://www.powershellgallery.com/packages/MicrosoftTeams/)<br>
<sup>3</sup> [Microsoft Teams admin center](https://docs.microsoft.com/microsoftteams/manage-teams-skypeforbusiness-admin-center)
<!-- <sup>4</sup> Azure Active Directory admin center <<note that these are going to come later because they’re related to O365 Group management>> 
<sup>5</sup> Microsoft 365 Admin Center <<note that these are going to come later because they’re related to O365 Group management>> 
-->
For more information about the admin tools available for managing Microsoft Teams, see [Managing Microsoft Teams](https://docs.microsoft.com/microsoftteams/manage-teams-skypeforbusiness-admin-center).

For more information about limits, specifications, and other requirements that apply to Teams, see [Limits and specifications for Microsoft Teams](limits-specifications-teams.md).

## Assign users to each role

You can assign users to these roles in Azure AD. To learn how to assign administrative roles to a user in Azure AD, see [Assign a user to administrator roles in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal).

## Cmdlets available for each role

Most of the PowerShell tools for these admin roles live in the Skype for Business PowerShell module, and it's important to note that some of the cmdlets that these admin roles have access to control shared settings that are also used for Skype for Business Online. The Skype for Business admin role also has access to all the cmdlets in the Skype for Business PowerShell module.

To view the full list of cmdlets currently available to a given role in the Skype for Business PowerShell module, follow these steps:

1. Assign that role to a user (and make sure that the user has no other roles).
2. Connect to the Skype for Business PowerShell module:<br>
   a. $session = new-csonlinesession<br>
   b. Import-pssession $session<br>
   c. Use **Get-Module** to identify the name of the imported session (it will be a randomly generated name).<br>
3. Use **Get-Command -Module** <*name from above*> to identify all available cmdlets

### Related topics

- [Microsoft Teams PowerShell Overview](teams-powershell-overview.md)
- [Microsoft Teams PowerShell](https://docs.microsoft.com/powershell/module/teams/?view=teams-ps)
- [Assign team owners and members in Microsoft Teams](https://docs.microsoft.com/microsoftteams/assign-roles-permissions)

