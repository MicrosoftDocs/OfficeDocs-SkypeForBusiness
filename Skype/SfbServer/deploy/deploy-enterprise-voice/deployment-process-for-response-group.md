---
title: "Deployment process for Response Group in Skype for Business"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection:
- IT_Skype16
- Strat_SB_Admin
ms.custom:
ms.assetid: d390c8a1-dc6e-44d8-b386-2be1fca9877c
description: "Deployment process and steps for Response Group in Skype for Business Server Enterprise Voice."
---

# Deployment process for Response Group in Skype for Business

Deployment process and steps for Response Group in Skype for Business Server Enterprise Voice.

Response Group is an Enterprise Voice feature that routes and queues incoming calls to groups of people, called agents, such as a help desk or a customer service desk.

The components that Response Group requires are installed and enabled automatically on the Front End Server or Standard Edition server when you deploy Enterprise Voice. To make Response Group available to users, you must configure agent groups, then queues, and then workflows. Additionally, a Response Group Administrator can delegate configuration of an existing workflow to a Response Group Manager, who can then modify and reconfigure the workflow and its associated agent groups and queues.

To configure response groups, you must be a member of at least one of the following administrative roles:

|**Active Directory Security Group (1)** <br/> |Create Workflow  <br/> |Assign Manager  <br/> |Create /assign agents, queues  <br/> |Create / manage holiday and business hours  <br/> |Activate / deactivate workflow  <br/> |Configure workflow (IVR or Hunt Group)  <br/> |
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|**CsResponseGroupAdministrator** <br/> |√  <br/> |√  <br/> |√  <br/> |√  <br/> |√  <br/> |√  <br/> |
|**CsResponseGroupManager** <br/> ||√(2)  <br/> |√(3)  <br/> |√(3)  <br/> |√(3)  <br/> |√(3)  <br/> |
|**CsVoiceAdministrator** <br/> |√  <br/> |√  <br/> |√  <br/> |√  <br/> |√  <br/> |√  <br/> |
|**CsServerAdministrator** <br/> |√  <br/> |√  <br/> |√  <br/> |√  <br/> |√  <br/> |√  <br/> |
|**CsAdministrator** <br/> |√  <br/> |√  <br/> |√  <br/> |√  <br/> |√  <br/> |√  <br/> |
|**CsViewOnlyAdministrator** <br/> |√(4)  <br/> |√(4)  <br/> |√(4)  <br/> |√(4)  <br/> |√(4)  <br/> |√(4)  <br/> |

> [!NOTE]
> **(1)** An Active Directory Domain Services user object must be a member of the specified Active Directory security group listed. An administrator or other delegated Active Directory group member with appropriate permissions to add users to a security group (For example, Administrator, Account Operators) must add a user object to the listed security group or group for the user to be able to perform the functions listed. **(2)** Only for workflows that the CsResponseGroupAdministrator has assigned to the CsResponseGroupManager. **(3)** A Response Group Manager can assign another member of CsResponseGroupManager to a workflow that the current manager already manages. **(4)** CsViewOnlyAdministrator can only run verb "Get" cmdlets.

## Response Group Configuration Prerequisites

Response Group requires the following components:

- Application service

- Response Group application

- Language packs

- File store (to hold audio files)

- Web Services (includes the Response Group Configuration Tool and the agents' sign-in and sign-out console)

All of these components are installed by default when you deploy Enterprise Voice.

You might need to perform the following tasks before configuring Response Group:

- Enable users for Lync Server 2013 and Enterprise Voice.

- Modify a configuration file to be compliant with Federal Information Processing Standards (FIPS).

- Modify the database collation to support Yi, Meng, and Zang characters for queue names and agent group names.

### Enabling Users

The first step in configuring Response Group is to create agent groups. Before you can create an agent group, you must enable the users who will be agents for Response Group for Skype for Business and Enterprise Voice. Enabling users for Skype for Business is typically a step in the Enterprise Edition server or Standard Edition server deployment. For details about enabling users for Skype for Business, see [Enable or Disable Users for Lync Server 2013 Preview](https://technet.microsoft.com/library/12497d00-f665-4a97-be68-854c5a8be4fc.aspx). Enabling users for Enterprise Voice is typically a step in the Enterprise Voice deployment. For details, see [Enable users for Enterprise Voice in Skype for Business Server](enable-users-for-enterprise-voice.md).

### Complying with FIPS requirements

This section applies to you only if your organization needs to comply with Federal Information Processing Standards (FIPS).

To be compliant with FIPS, you need to modify the application-level Web.config file to use a different cryptography algorithm after you install Web Services. You need to specify that ASP.NET use the Triple Data Encryption Standard (3DES) algorithm to process view state data. For the Response Group application, this requirement applies to the Response Group Configuration Tool and the agent sign-in and sign-out console. For details about this requirement, see Microsoft Knowledge Base article 911722, "You may receive an error message when you access ASP.NET webpages that have ViewState enabled after you upgrade from ASP.NET 1.1 to ASP.NET 2.0," at [https://go.microsoft.com/fwlink/p/?linkId=196183](https://go.microsoft.com/fwlink/p/?linkId=196183).

To modify the Web.config file, do the following:

1. In a text editor such as Notepad, open the application-level Web.config file.

2. In the Web.config file, locate the  `<system.web>` section.

3. Add the following  `<machineKey>` section to in the `<system.web>` section:

   ```
   <machineKey validationKey="AutoGenerate,IsolateApps" decryptionKey="AutoGenerate,IsolateApps" validation="3DES" decryption="3DES"/>
   ```

4. Save the Web.config file.

5. Restart the Internet Information Services (IIS) service by running the following command at a command prompt:

   ```
   iisreset
   ```

### Supporting Yi, Meng, and Zang Characters

This section applies to you only if your organization needs to support Yi, Meng, or Zang characters.

> [!NOTE]
> For information on what the Yi, Meng, and Zang characters are and why they may be important to your deployment, see the information on the GB18030 character sets [https://go.microsoft.com/fwlink/p/?linkId=240223](https://go.microsoft.com/fwlink/p/?linkId=240223).

To support Yi, Meng, or Zang characters, you need to modify the collation for the Rgsconfig database. Change the collation of the **Name** column in the following tables in each Rgsconfig database:

- dbo.AgentGroups

- dbo.BusinessHours

- dbo.HolidaySets

- dbo.Queues

- dbo.Workflows

For SQL Server 2008 R2 and SQL Server 2012, use the Latin_General_100 (Accent Sensitive) collation. If you use this collation, all object names are not case-sensitive.

You can change the collation by using Microsoft SQL Server Management Studio. For details about using this tool, see ["Using SQL Server Management Studio"](https://go.microsoft.com/fwlink/p/?linkId=196184). Follow these steps to change the collation:

1. Be sure that SQL Server Management Studio is configured to allow changes that require tables to be recreated. For details, see ["Save (Not Permitted) Dialog Box"](https://go.microsoft.com/fwlink/p/?linkId=196186). For details about setting a column collation, see at ["How to: Set Column Collation (Visual Database Tools)"](https://go.microsoft.com/fwlink/p/?linkId=196185).

2. Using Microsoft SQL Server Management Studio, connect to the Rgsconfig database.

3. Find the table you want to change in the Rgsconfig database, right-click the table, and click **Design**.

4. Change the collation of the **Name** column and save the table.

## Response Group deployment steps

**Response Group Deployment Process**

|**Phase**|**Steps**|**Permissions**|**Deployment documentation**|
|:-----|:-----|:-----|:-----|
|Enable users for Skype for Business and for Enterprise Voice  <br/> |Enable users who will be agents for Skype for Business and Enterprise Voice. Users must be enabled before you can add them to agent groups. Typically, users are enabled for Skype for Business during the Enterprise Edition or Standard Edition server deployment. Users are enabled for Enterprise Voice during the Enterprise Voice deployment.  <br/> |RTCUniversalUserAdmins  <br/> CsUserAdministrator  <br/> CsAdministrator  <br/> |[Enable or Disable Users for Lync Server 2013 Preview](https://technet.microsoft.com/library/12497d00-f665-4a97-be68-854c5a8be4fc.aspx) <br/> [Enable users for Enterprise Voice in Skype for Business Server](enable-users-for-enterprise-voice.md) <br/> |
|Create and configure response groups, which consist of agent groups, queues, and workflows  <br/> |1. Use the Skype for Business Server Control Panel or Skype for Business Server Management Shell to do the following:  <br/> a. Create and configure agent groups.  <br/> b. Create and configure queues.  <br/> 2. Optionally, use Skype for Business Server Management Shell to create predefined response group business hours and holidays.  <br/> 3. Use the Response Group Configuration Tool or Skype for Business Server Management Shell to create workflows (hunt groups or interactive voice response (IVR) call flows), including custom response group business hours and holidays.  <br/> You can access the Response Group Configuration Tool through Skype for Business Server Control Panel.  <br/> |RTCUniversalServerAdmins  <br/> CsResponseGroupAdministrator  <br/> CsVoiceAdministrator  <br/> CsServerAdministrator  <br/> CsAdministrator  <br/> CsResponseGroupManager  <br/> |[Create Response Group Agent Groups](https://technet.microsoft.com/library/2a80de17-ead0-46e8-8a27-7a4e233dbde0.aspx) <br/> [Create Response Group Queues](https://technet.microsoft.com/library/49cb86c7-2cfd-4a53-8408-d407475174ed.aspx) <br/> [(Optional) Define Response Group business hours in Skype for Business](optional-define-response-group-business-hours.md) <br/> [(Optional) Define Response Group holiday sets in Skype for Business](optional-define-response-group-holiday-sets.md) <br/> [Designing and creating response group workflows in Skype for Business](designing-and-creating-response-group-workflows.md) <br/> |
|(Optional) Customize application-level settings  <br/> |Use Skype for Business Server Management Shell to customize the default music-on-hold configuration, the default music-on-hold audio file, the agent ringback grace period, and the call context configuration.  <br/> |RTCUniversalServerAdmins  <br/> CsResponseGroupAdministrator  <br/> CsVoiceAdministrator  <br/> CsServerAdministrator  <br/> CsAdministrator  <br/> |[Managing application-level Response Group settings in Skype for Business](managing-application-level-response-group-settings.md) <br/> |
|(Optional) Delegate management of response groups  <br/> |Assign users the CsResponseGroupManager role to delegate configuration of response groups. Response Group Managers can then configure the response groups assigned to them.  <br/> |RTCUniversalServerAdmins  <br/> CsResponseGroupAdministrator  <br/> CsVoiceAdministrator  <br/> CsServerAdministrator  <br/> CsAdministrator  <br/> |[Planning for Role-Based Access Control](https://technet.microsoft.com/library/41204ba3-ce5b-41a8-a6c3-b444468fa328.aspx) <br/> |
|Verify your Response Group deployment  <br/> |Test answering calls to your hunt group and interactive voice response workflows to ensure that your configuration works as expected.  <br/> |-  <br/> |-  <br/> |

## Overview of workflow creation scenarios

When you create workflows, there are two possible scenarios:

- **The Administrator creates and configures the workflow** — The CsResponseGroupAdministrator role member (or equivalent) creates and activates the workflow and all elements in the workflow, such as the agent groups, queues, holiday and business hours, music on hold, and so on.

- **The Administrator creates the workflow and the Manager configures options** — The CsResponseGroupAdministrator role member (or equivalent) defines the primary SIP URI, Display Name, assigns a member or members of the CsResponseGroupManager role, and selects a queue and activates the workflow. The CsResponseGroupManager can then log on and edit the configuration of the workflow by creating agent groups and also assigns the group to the queue, configuring the telephone number, holiday and business hours, music on hold, and so on.

    > [!NOTE]
    > When you want to create a managed workflow, you need to create the workflow as active. After you save an active, managed workflow, you can then modify and deactivate the workflow.


