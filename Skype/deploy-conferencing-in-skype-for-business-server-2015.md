---
title: Deploy conferencing in Skype for Business Server 2015
ms.prod: SKYPEFORBUSINESS
ms.assetid: 26dff7d8-242a-4576-9870-d6d461758a37
---



# Deploy conferencing in Skype for Business Server 2015
[] **Summary:** Read this topic to learn how to deploy conferencing in Skype for Business Server 2015.
There are four types of conferencing available in Skype for Business Server: web conferencing, audio and video (A/V) conferencing, dial-in conferencing, and instant message (IM) conferencing. You can choose to enable all conferencing types, or to use only one type, depending on your needs. 
  
    
    

When you deploy Skype for Business Server, IM conferencing capabilities are automatically deployed. When you create and publish a new topology by using Topology Builder, you specify whether to deploy web, A/V, and dial-in conferencing, as described in the following checklists: 
-  [Deployment checklist for web and audio/video conferencing](deploy-conferencing-in-skype-for-business-server-2015.md#BKMK_ChecklistWebConferencing)
    
  
-  [Deployment flowchart and checklist for dial-in conferencing](deploy-conferencing-in-skype-for-business-server-2015.md#BKMK_DialinConferencing)
    
  
Before you deploy conferencing, you should read the following planning topics:  [Plan for conferencing in Skype for Business Server 2015](plan-for-conferencing-in-skype-for-business-server-2015.md),  [Hardware and software requirements for conferencing in Skype for Business Server 2015](hardware-and-software-requirements-for-conferencing-in-skype-for-business-server.md),  [Plan your conferencing topology for Skype for Business Server 2015](plan-your-conferencing-topology-for-skype-for-business-server-2015.md),  [Plan for dial-in conferencing in Skype for Business Server 2015](plan-for-dial-in-conferencing-in-skype-for-business-server-2015.md), and  [Plan for large meetings in Skype for Business Server 2015](plan-for-large-meetings-in-skype-for-business-server-2015.md).
## Deployment checklist for web and audio/video conferencing
<a name="BKMK_ChecklistWebConferencing"> </a>


  
    
    
The following table provides an overview of the steps required to deploy web and audio/video conferencing into an existing topology. Links to the associated planning and procedural documentation are included. 
  
    
    


|**Phase**|**Steps**|**Roles and group memberships**|**Documentation**|
|:-----|:-----|:-----|:-----|
|**Install required hardware and software** <br/> |Conferencing runs on Front End Servers of a Front End pool and Standard Edition servers. See the server and environmental requirements for Front End Servers.  <br/> If you are enabling web conferencing, you will need to ensure that Skype for Business Server can communicate with Office Web Apps Server, which is used to handle sharing and rendering of PowerPoint presentations.  <br/> For web conferencing, you also need to specify a file share to be used as the file store.  <br/> Do you want to enable external users with Skype for Business clients to join conferences? If so, you need to deploy Edge Servers.  <br/> |Domain user who is a member of the local Administrators group  <br/> | [Server requirements for Skype for Business Server 2015](server-requirements-for-skype-for-business-server-2015.md) <br/>  [Environmental requirements for Skype for Business Server 2015](environmental-requirements-for-skype-for-business-server-2015.md) <br/>  [Hardware and software requirements for conferencing in Skype for Business Server 2015](hardware-and-software-requirements-for-conferencing-in-skype-for-business-server.md) <br/>  [Configure integration with Office Web Apps Server in Skype for Business Server 2015](configure-integration-with-office-web-apps-server-in-skype-for-business-server-2.md) <br/>  [Create a file share in Skype for Business Server 2015](create-a-file-share-in-skype-for-business-server-2015.md) <br/>  [Plan for Edge Server deployments in Skype for Business Server 2015](plan-for-edge-server-deployments-in-skype-for-business-server-2015.md) <br/>  [Deploy Edge Server in Skype for Business Server 2015](deploy-edge-server-in-skype-for-business-server-2015.md) <br/> |
|**Create the appropriate internal topology to support conferencing** <br/> |You need to run Topology Builder to add conferencing to the topology, and then publish the topology.  <br/> |To define a topology, an account that is a member of the local Users group  <br/> To publish the topology, an account that is a member of the Domain Admins group and RTCUniversalServerAdmins group, and that has full control permissions (read/write/modify) on the file share to be used for the Skype for Business Server file store (so that Topology Builder can configure the required DACLs)  <br/> | [Create and publish new topology in Skype for Business Server 2015](create-and-publish-new-topology-in-skype-for-business-server-2015.md) <br/> |
|**Configure conferencing policies and configuration settings** <br/> |Use Skype for Business Server Control Panel or Skype for Business Server Management Shell to configure conferencing policies and configuration settings.  <br/> |RTCUniversalServerAdmins group (Windows PowerShell only) or assign users to the CSAdministrator role  <br/> | [Manage conferencing policies in Skype for Business Server 2015](manage-conferencing-policies-in-skype-for-business-server-2015.md) <br/>  [Manage meeting configuration settings in Skype for Business Server 2015](manage-meeting-configuration-settings-in-skype-for-business-server-2015.md) <br/>  [New-CsConferencingPolicy](new-csconferencingpolicy.md) <br/>  [Set-CsConferencingPolicy](set-csconferencingpolicy.md) <br/>  [New-CsConferencingConfiguration](new-csconferencingconfiguration.md) <br/>  [Set-CsConferencingConfiguration](set-csconferencingconfiguration.md) <br/>  [New-CsMeetingConfiguration](new-csmeetingconfiguration.md) <br/>  [Set-CsMeetingConfiguration](set-csmeetingconfiguration.md) <br/> |
   

  
    
    

## Deployment flowchart and checklist for dial-in conferencing
<a name="BKMK_DialinConferencing"> </a>

 Dial-in conferencing allows users to dial in from the public switched telephone network (PSTN) to join an audio/video conference.
  
    
    
Some of the components required for dial-in conferencing are also used for Enterprise Voice. For example, if you are deploying Enterprise Voice, you must also deploy a Mediation Server and a PSTN gateway--components that are also required for dial-in conferencing. How you deploy dial-in conferencing, therefore, depends on whether you are also deploying an Enterprise Voice solution. 
  
    
    
The dial-in conferencing flowchart shows the steps you must follow depending on whether you are also deploying an Enterprise Voice solution. The table following the flowchart provides an overview of steps required and recommended for deploying dial-in conferencing. Links to the associated planning and procedural documentation are also included. For more information about planning a complete Enterprise Voice solution, see  [Plan your Enterprise Voice solution in Skype for Business Server 2015](plan-your-enterprise-voice-solution-in-skype-for-business-server-2015.md).
  
    
    

**Dial-in conferencing flowchart**

  
    
    

  
    
    
![Deploy dial-in conferencing flow chart](images/95d2f963-7705-4930-90bc-df6a71a700bf.png)
  
    
    

  
    
    

  
    
    

**Dial-in conferencing deployment checklist**


|**Phase**|**Steps**|**Roles and group membership**|**Documentation**|
|:-----|:-----|:-----|:-----|
|**Install required hardware and software** <br/> | Conferencing runs on Front End Servers of a Front End pool and Standard Edition servers. See the server and environmental requirements for Front End Servers. <br/>  You need to ensure that the following are installed before configuring dial-in conferencing: <br/>  Mediation Server <br/>  PSTN gateway <br/>  Unified Communications Application Service (UCAS) (called the Application service) <br/>  Conferencing Attendant application <br/>  Conferencing Announcement application <br/> |Domain user who is a member of the local Administrators group  <br/> | [Server requirements for Skype for Business Server 2015](server-requirements-for-skype-for-business-server-2015.md) <br/>  [Environmental requirements for Skype for Business Server 2015](environmental-requirements-for-skype-for-business-server-2015.md) <br/>  [Hardware and software requirements for conferencing in Skype for Business Server 2015](hardware-and-software-requirements-for-conferencing-in-skype-for-business-server.md) <br/>  [Plan for dial-in conferencing in Skype for Business Server 2015](plan-for-dial-in-conferencing-in-skype-for-business-server-2015.md) <br/>  [Mediation Server component in Skype for Business Server 2015](mediation-server-component-in-skype-for-business-server-2015.md) <br/>  [Deploy a Mediation Server in Topology Builder in Skype for Business Server 2015](deploy-a-mediation-server-in-topology-builder-in-skype-for-business-server-2015.md) <br/>  [Define a gateway in Topology Builder in Skype for Business Server 2015](define-a-gateway-in-topology-builder-in-skype-for-business-server-2015.md) <br/> |
|**Create a topology that includes the Conferencing workload, including a Mediation Server and PSTN gateway, and deploy the Front End pool or Standard Edition server** <br/> |
Run Topology Builder to configure your topology. While configuring the topology, select the dial-in conferencing option. Publish the topology and deploy the Front End pool or Standard Edition server. If necessary, create a stand-alone Mediation Server and associate it with a PSTN gateway. NoteThis step is required only if you do not deploy Enterprise Voice and do not collocate the Mediation Server with the Enterprise Edition Front End Server or Standard Edition server. If you deploy Enterprise Voice, you install and configure Mediation Servers and PSTN gateways as part of the Enterprise Voice deployment. If you collocate the Mediation Server, you install and configure the Mediation Server as part of the Front End pool or Standard Edition server deployment. |Domain Admins  <br/> RTCUniversalServerAdmins  <br/> Administrator  <br/> | [Create and publish new topology in Skype for Business Server 2015](create-and-publish-new-topology-in-skype-for-business-server-2015.md) <br/>  [Deploy a Mediation Server in Topology Builder in Skype for Business Server 2015](deploy-a-mediation-server-in-topology-builder-in-skype-for-business-server-2015.md) <br/>  [Define a gateway in Topology Builder in Skype for Business Server 2015](define-a-gateway-in-topology-builder-in-skype-for-business-server-2015.md) <br/> |
|**Configure dial plans** <br/> |A dial plan is a set of phone number normalization rules that translate phone numbers dialed from a specific location to a single standard (E.164) format for purposes of phone authorization and call routing. The same phone number dialed from different locations can, based on the respective dial plans, resolve to different E.164 numbers, as appropriate to each location. If you deploy Enterprise Voice, you set up dial plans as part of that deployment, and you need to make sure that the dial plans also accommodate dial-in conferencing. If you do not deploy Enterprise Voice, you need to set up dial plans for dial-in conferencing.  <br/> Use Skype for Business Server Control Panel or Skype for Business Server Management Shell to set up dial plans as follows:  <br/> Create one or more dial plans for routing dial-in access phone numbers. Assign a default dial plan to each pool. Set the Dial-in conferencing region to the geographic location to which the dial plan applies. The region associates the dial plan with dial-in access numbers. |RTCUniversalServerAdmins  <br/> CsVoiceAdministrator  <br/> CsServerAdministrator  <br/> CsAdministrator  <br/> | [Configure dial-in conferencing in Skype for Business Server 2015](configure-dial-in-conferencing-in-skype-for-business-server-2015.md) <br/>  [Create or modify a dial plan in Skype for Business Server 2015](create-or-modify-a-dial-plan-in-skype-for-business-server-2015.md) <br/>  [New-CsDialPlan](new-csdialplan.md) <br/> |
|**Make sure that dial plans are assigned regions** <br/> |Run the **Get-CsDialPlan** and **Set-CsDialPlan** cmdlets to make sure that all dial plans have a region assigned. <br/> |RTCUniversalServerAdmins  <br/> CsVoiceAdministrator  <br/> CsServerAdministrator  <br/> CsAdministrator  <br/> | [Configure dial-in conferencing in Skype for Business Server 2015](configure-dial-in-conferencing-in-skype-for-business-server-2015.md) <br/>  [Create or modify a dial plan in Skype for Business Server 2015](create-or-modify-a-dial-plan-in-skype-for-business-server-2015.md) <br/>  [Get-CsDialPlan](get-csdialplan.md) <br/>  [Set-CsDialPlan](set-csdialplan.md) <br/> |
|**Configure conferencing policy to support dial-in conferencing** <br/> | Use Skype for Business Server Control Panel or Skype for Business Server Management Shell to configure **Conferencing Policy** settings. Specify whether: <br/>  PSTN conference dial-in is enabled. <br/>  Users can invite anonymous participants. <br/>  Unauthenticated users can join a conference by using dial-out phoning. With dial-out phoning, the conference server calls the user, and the user answers the phone to join the conference. <br/> |RTCUniversalServerAdmins  <br/> CsServerAdministrator  <br/> CsAdministrator  <br/> | [Manage conferencing policies in Skype for Business Server 2015](manage-conferencing-policies-in-skype-for-business-server-2015.md) <br/>  [New-CsConferencingPolicy](new-csconferencingpolicy.md) <br/>  [Set-CsConferencingPolicy](set-csconferencingpolicy.md) <br/> |
|**Configure dial-in access numbers** <br/> |Use Skype for Business Server Control Panel or Skype for Business Server Management Shell to set up dial-in access numbers that users call to dial in to a conference, and specify the regions that associate the access number with the appropriate dial plans. The first three access numbers for the region specified by the organizer's dial plan are included in the conference invitation. All access numbers are available on the Dial-in Conferencing Settings page.  <br/> > [!NOTE]> After you create dial-in access numbers, you can use the **Set-CsDialInConferencingAccessNumber** cmdlet to modify the display name of the Active Directory contact objects so that users can more easily identify the correct access number.          |RTCUniversalServerAdmins  <br/> CsServerAdministrator  <br/> CsAdministrator  <br/> | [Create or modify a dial plan in Skype for Business Server 2015](create-or-modify-a-dial-plan-in-skype-for-business-server-2015.md) <br/>  [Manage dial-in conferencing access numbers in Skype for Business Server 2015](manage-dial-in-conferencing-access-numbers-in-skype-for-business-server-2015.md) <br/>  [New-CsDialInConferencingAccessNumber](new-csdialinconferencingaccessnumber.md) <br/>  [Set-CsDialInConferencingAccessNumber](set-csdialinconferencingaccessnumber.md) <br/> |
|**Assign a Line URI to a user account** <br/> |Use Skype for Business Server Control Panel or Skype for Business Server Management Shell to configure the telephony **Line URI** as a unique, normalized phone number (for example, tel:+14255550200). <br/> |RTCUniversalServerAdmins  <br/> CsAdministrator  <br/> CsUserAdministrator  <br/> | [Assign a Line URI to a user account](configure-dial-in-conferencing-in-skype-for-business-server-2015.md#BKMK_AssignaLineURI) <br/> |
|**(Optional) Verify or modify user personal identification number (PIN) requirements** <br/> |Use Skype for Business Server Control Panel or Skype for Business Server Management Shell to view or modify the Conferencing **PIN Policy**. You can specify minimum PIN length, maximum number of logon attempts, PIN expiration, and whether common patterns are allowable.  <br/> |RTCUniversalServerAdmins  <br/> CsServerAdministrator  <br/> CsAdministrator  <br/> | [Manage PIN policies for dial-in conferencing in Skype for Business Server 2015](manage-pin-policies-for-dial-in-conferencing-in-skype-for-business-server-2015.md) <br/>  [Get-CsPinPolicy](get-cspinpolicy.md) <br/>  [Set-CsPinPolicy](set-cspinpolicy.md) <br/> |
|**(Optional) Modify key mapping of DTMF commands** <br/> |Use the **Set-CsDialinConferencingDtmfConfiguration** cmdlet to modify the keys used for dual-tone multi-frequency (DTMF) commands, which participants can use to control conference settings (such as mute and unmute or lock and unlock). <br/> |RTCUniversalServerAdmins  <br/> CsServerAdministrator  <br/> CsAdministrator  <br/> | [Manage key mapping for DTMF commands in Skype for Business Server 2015](manage-key-mapping-for-dtmf-commands-in-skype-for-business-server-2015.md) <br/>  [Set-CsDialInConferencingDtmfConfiguration](set-csdialinconferencingdtmfconfiguration.md) <br/> |
|**(Optional) Modify conference join and leave announcement behavior** <br/> |Use the **Set-CsDialinConferencingConfiguration** to change how announcements work when participants join and leave conferences. <br/> |RTCUniversalServerAdmins  <br/> CsServerAdministrator  <br/> CsAdministrator  <br/> | [Manage conference join and leave announcements in Skype for Business Server 2015](manage-conference-join-and-leave-announcements-in-skype-for-business-server-2015.md) <br/>  [Set-CsDialInConferencingConfiguration](set-csdialinconferencingconfiguration.md) <br/> |
|**(Recommended) Configure conference directories** <br/> |Use the **New-CsConferenceDirectory** cmdlet to create one conference directory for every 999 users in the pool. <br/> |RTCUniversalServerAdmins  <br/> | [(Recommended) Create Conference Directories](http://technet.microsoft.com/library/787f4c94-1c96-468a-a74d-e06b7bd4b8a3.aspx) <br/>  [New-CsConferenceDirectory](new-csconferencedirectory.md) <br/> |
|**(Optional) Verify dial-in conferencing settings** <br/> |Use the **Get-CsDialinConferencingAccessNumber** cmdlet to search for dial plans that have a dial-in conferencing region that is not used by any access number and for access numbers that have no region assigned. <br/> |RTCUniversalServerAdmins  <br/> CsServerAdministrator  <br/> CsAdministrator  <br/> CsViewOnlyAdministrator  <br/> CsHelpDesk  <br/> | [Configure dial-in conferencing in Skype for Business Server 2015](configure-dial-in-conferencing-in-skype-for-business-server-2015.md) <br/>  [Test dial-in conferencing in Skype for Business Server 2015](test-dial-in-conferencing-in-skype-for-business-server-2015.md) <br/>  [Get-CsDialInConferencingAccessNumber](get-csdialinconferencingaccessnumber.md) <br/> |
|**(Optional) Verify dial-in conferencing** <br/> |Use the **Test-CsDialInConferencing** cmdlet to test that the access numbers for the specified pool work correctly. <br/> |RTCUniversalServerAdmins  <br/> CsServerAdministrator  <br/> CsAdministrator  <br/> | [Test dial-in conferencing in Skype for Business Server 2015](test-dial-in-conferencing-in-skype-for-business-server-2015.md) <br/>  [Test-CsDialInConferencing](test-csdialinconferencing.md) <br/> |
|**(Optional) Welcome users to dial-in conferencing and set the initial PIN** <br/> |Use the **Set-CsPinSendCAWelcomeMail** script to set users' initial PINs and send a welcome email that contains the initial PIN and a link to the Dial-in Conferencing Settings page. <br/> |RTCUniversalServerAdmins  <br/> | [Send welcome email to dial-in users in Skype for Business Server 2015](send-welcome-email-to-dial-in-users-in-skype-for-business-server-2015.md) <br/> |
   
