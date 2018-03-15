---
title: "Deployment process for Response Group in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d390c8a1-dc6e-44d8-b386-2be1fca9877c

description: "This section provides an overview of the phases and steps involved in deploying the Response Group application."
---

# Deployment process for Response Group in Lync Server 2013
[]
This section provides an overview of the phases and steps involved in deploying the Response Group application. 
  
**Response Group Deployment Process**

|**Phase**|**Steps**|**Permissions**|**Deployment documentation**|
|:-----|:-----|:-----|:-----|
|Install the Response Group application  <br/> |The Response Group application is installed and activated by default when you deploy Enterprise Voice.  <br/> |RTCUniversalServerAdmins  <br/> |[Deploying Enterprise Voice in Lync Server 2013](deploying-enterprise-voice.md) <br/> |
|Install components for Response Group  <br/> |Lync Server cmdlets, the Lync Server Control Panel, Response Group Configuration Tool, agents' sign-in and sign-out console, and Response Group Client Web service are installed as part of Web Services. Web Services is installed when you deploy an Enterprise Edition pool or a Standard Edition server.  <br/> |RTCUniversalServerAdmins  <br/> |[Deploying Lync Server 2013](deploying-lync-server-2013.md) <br/> |
|Enable users for Lync 2013 and for Enterprise Voice  <br/> |Enable users who will be agents for Lync Server and Enterprise Voice. Users must be enabled before you can add them to agent groups. Typically, users are enabled for Lync Server during the Enterprise Edition or Standard Edition server deployment. Users are enabled for Enterprise Voice during the Enterprise Voice deployment.  <br/> |RTCUniversalUserAdmins  <br/> CsUserAdministrator  <br/> CsAdministrator  <br/> |[Disable or re-enable user account for Lync Server 2013](disable-or-re-enable-user-account-for-lync-server.md) <br/> [Enable users for Enterprise Voice in Lync Server 2013](enable-users-for-enterprise-voice.md) <br/> |
|Create and configure response groups, which consist of agent groups, queues, and workflows  <br/> | Use the Lync Server Control Panel or Lync Server Management Shell to do the following:  <br/>  Create and configure agent groups.  <br/>  Create and configure queues.  <br/>  Optionally, use Lync Server Management Shell to create predefined response group business hours and holidays.  <br/>  Use the Response Group Configuration Tool or Lync Server Management Shell to create workflows (hunt groups or interactive voice response (IVR) call flows), including custom response group business hours and holidays.  <br/> > [!NOTE]>  You can access the Response Group Configuration Tool through Lync Server Control Panel.           |RTCUniversalServerAdmins  <br/> CsResponseGroupAdministrator  <br/> CsVoiceAdministrator  <br/> CsServerAdministrator  <br/> CsAdministrator  <br/> CsResponseGroupManager  <br/> |[Create Response Group agent groups Lync Server 2013](create-response-group-agent-groups.md) <br/> [Create Response Group queues in Lync Server 2013](create-response-group-queues.md) <br/> [(Optional) Define Response Group business hours in Lync Server 2013](optional-define-response-group-business-hours.md) <br/> [(Optional) Define Response Group holiday sets in Lync Server 2013](optional-define-response-group-holiday-sets.md) <br/> [Create or modify a workflow in Lync Server 2013](create-or-modify-a-workflow.md) <br/> |
|(Optional) Customize application-level settings  <br/> |Use Lync Server Management Shell to customize the default music-on-hold configuration, the default music-on-hold audio file, the agent ringback grace period, and the call context configuration.  <br/> |RTCUniversalServerAdmins  <br/> CsResponseGroupAdministrator  <br/> CsVoiceAdministrator  <br/> CsServerAdministrator  <br/> CsAdministrator  <br/> |[Managing application-level Response Group settings in Lync Server 2013](managing-application-level-response-group-settings.md) <br/> |
|(Optional) Delegate management of response groups  <br/> |Assign users the CsResponseGroupManager role to delegate configuration of response groups. Response Group Managers can then configure the response groups assigned to them.  <br/> |RTCUniversalServerAdmins  <br/> CsResponseGroupAdministrator  <br/> CsVoiceAdministrator  <br/> CsServerAdministrator  <br/> CsAdministrator  <br/> |[Planning for role-based access control in Lync Server 2013](planning-for-role-based-access-control-rbac.md) <br/> |
|Verify your Response Group deployment  <br/> |Test answering calls to your hunt group and interactive voice response workflows to ensure that your configuration works as expected.  <br/> |-  <br/> |-  <br/> |
   

