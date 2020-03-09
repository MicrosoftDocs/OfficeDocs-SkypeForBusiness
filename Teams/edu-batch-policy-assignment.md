---
title: Getting ready for school to start?
author: lanachin
ms.author: v-lanac
manager: serdars
ms.reviewer: saragava,karsmith
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
localization_priority: Normal
search.appverid: MET150
description: Learn how to use batch policy assignment to assign policies to your students and teachers in bulk. 
f1keywords: 
---

# Getting ready for school to start?

Do you need to give your students and faculty access to different features in Microsoft Teams? You can quickly identify the students and faculty in your organization by license type and then assign them the appropriate policy by using PowerShell. 

In this tutorial, we’ll show you how to assign meeting policies to large batches of users. We assume you’ve already created two different meeting policies named StudentMeetingPolicy and FacultyMeetingPolicy.

![Screenshot of the Meeting policies page in the Teams admin center](media/edu-batch-policy-assignment.png)

## Connect to the Azure AD PowerShell for Graph module and the Teams PowerShell module

To follow the steps in this article, you’ll need to install and connect to the Azure AD PowerShell for Graph module (to identify users by their assigned licenses) and the pre-release version of the Microsoft Teams PowerShell module (to assign the policies to those users).

### Install and connect to the Azure AD PowerShell for Graph module

Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator), and then run the following to install the Azure Active Directory PowerShell for Graph module.

```powershell
Install-Module AzureAD
```

Run the following to connect to Azure AD.

```powershell
Connect-AzureAD
```

To learn more, see [Connect with the Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/eoffice365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-azure-active-directory-powershell-for-graph-module).

### Install and connect to the pre-release version of the Teams PowerShell module

The cmdlets are in the pre-release version of the Teams PowerShell module. Follow the steps in [Install and connect to the Microsoft Teams PowerShell module](assign-policies.md#install-and-connect-to-the-microsoft-teams-powershell-module) to first uninstall the Generally Available version of the Teams PowerShell module (if it's installed), and then install the latest pre-release version of the module from the PowerShell Test Gallery.

Run the following to connect to Teams and start a session.

```powershell
Connect-MicrosoftTeams
```

When you're prompted, sign in using your admin credentials.

## Identify your students and your teachers

First, run the following to identify all your students and teachers by license type. This tells you what SKUs are in use in your organization. You can identify all the users that have a Student SKU assigned and all teachers that have a Faculty SKU assigned.

```powershell
Get-AzureADSubscribedSku
```

```powershell
$skus = Get-AzureADSubscribedSku
```

Which returns:

```
ObjectId                                                                  SkuPartNumber      SkuId
--------                                                                  -------------      -----
ee1a846c-79e9-4bc3-9189-011ca89be890_e97c048c-37a4-45fb-ab50-022fbf07a370 M365EDU_A5_FACULTY e97c048c-37a4-45fb-ab50-922fbf07a370
ee1a846c-79e9-4bc3-9189-011ca89be890_46c119d4-0379-4a9d-85e4-97c66d3f909e M365EDU_A5_STUDENT 46c119d4-0379-4a9d-85e4-97c66d3f909e
```


In this example, the output shows that the organization’s Faculty license SkuId is “e97c048c-37a4-45fb-ab50-922fbf07a370” and the Student license SkuId is “46c119d4-0379-4a9d-85e4-97c66d3f909e”.

Next, we run the following to identify the users that have each of these licenses and collect them all together.

```powershell
$faculty = Get-AzureADUser -All $true | Where-Object (($_.assignedLicenses).SkuId -contains “e97c048c-37a4-45fb-ab50-922fbf07a370”)
```

```powershell
$students = Get-AzureADUser -All $true | Where-Object (($_.assignedLicenses).SkuId -contains “46c119d4-0379-4a9d-85e4-97c66d3f909e”)
```

## Assign a policy to a batch of users

Now, we assign the appropriate policies to users in bulk. The maximum number of users that you can assign or update policies for is 20,000 at a time. If you have more than 20,000 students or 20,000 faculty, you’ll need to submit multiple batches.

Run the following to assign StudentMeetingPolicy to your students.

```powershell
New-CsBatchPolicyAssignmentOperation -PolicyType TeamsMeetingPolicy -PolicyName StudentMeetingPolicy -Identity $students.ObjectId
```

Run the following to assign FacultyMeetingPolicy to your teachers.

```powershell
New-CsBatchPolicyAssignmentOperation -PolicyType TeamsMeetingPolicy -PolicyName FacultyMeetingPolicy -Identity $faculty.ObjectId
```

> [!NOTE]
> To assign a different policy type in bulk, like TeamsMessagingPolicy, you’ll need to change ```PolicyType``` to the policy that you're assigning and ```PolicyName``` to the policy name.

## Get the status of a batch assignment

Each of these bulk operations returns an operation ID, which you can use to track the progress of the policy assignments or identify any failures. For example, run the following:

```powershell
Get-CsBatchPolicyAssignmentOperation -OperationId 3964004e-caa8-4eb4-b0d2-7dd2c8173c8c | fl
```

## Assign policies in batches if you have more than 20,000 users

First, run the following to see how many students and teachers you have:

```powershell
$students.count
```

```powershell
$faculty.count
```

Instead of providing the whole list of user IDs, run the following to specify the first 20,000, and then the next 20,000, and so on.

```powershell
Assign-CsPolicy -PolicyType TeamsMeetingPolicy -PolicyName StudentPolicy -Identities $students[0..19999].ObjectId
```

You can change the range of user IDs until you reach the full list of users. For example, ```$students[0..19999```.

## FAQ

**I want to make sure that all users that are students or faculty automatically get licenses assigned. How can I do that?**

The Teams product team is doing work to support assigning policies to security groups. At that time, you’ll be able to create groups for your students and teachers, and then the appropriate policies to those groups. Note that explicit user assignments (such as the policies that you’ve assigned using this tutorial) will override policies inherited from a group. When this feature is supported, we’ll provide more instructions on how to use policy assignment to groups and update your users to ensure they get the inherited group policies.

**I’m not familiar with PowerShell for Teams. Where can I learn more?**

See [Teams Powershell overview](teams-powershell-overview.md).

## Related topics

- [Assign policies to your users](assign-policies.md)
- [New-CsBatchPolicyAssignmentOperation](https://docs.microsoft.com/powershell/module/teams/new-csbatchpolicyassignmentoperation)
- [Get-CsBatchPolicyAssignmentOperation](https://docs.microsoft.com/powershell/module/teams/get-csbatchpolicyassignmentoperation)