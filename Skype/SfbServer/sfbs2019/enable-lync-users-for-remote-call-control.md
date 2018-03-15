---
title: "Enable Lync users for remote call control in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f39bc10d-034c-4875-a0b8-554e1109e7e6
description: "You can configure Lync users for remote call control by using in-band provisioning policies that are server-based. You can manage in-band provisioning settings by using Lync Server Control Panel or the Lync Server Management Shell command-line interface. These tools replace the Windows Management Instrumentation (WMI) snap-in that was used to manage Group Policy settings in earlier releases."
---

# Enable Lync users for remote call control in Lync Server 2013
[]
You can configure Lync users for remote call control by using in-band provisioning policies that are server-based. You can manage in-band provisioning settings by using Lync Server Control Panel or the Lync Server Management Shell command-line interface. These tools replace the Windows Management Instrumentation (WMI) snap-in that was used to manage Group Policy settings in earlier releases.
  
If you prefer to let users to configure their own remote call control settings in Lync, you can configure remote call control settings for users on the server without specifying **Line Server URI** and **Line URI** values. Be sure that you communicate the appropriate **Line Server URI** and **Line URI** values to your users, and provide your users with the instructions to configure these settings. For the procedure to manually configure remote call control in Lync Server, see "Set Phones options and numbers" at [https://go.microsoft.com/fwlink/p/?linkid=210132](https://go.microsoft.com/fwlink/p/?linkid=210132) in the Lync client documentation on the Microsoft Office website. 
  
If you have an existing Communications Server 2007 R2 or Communications Server 2007 deployment, Communicator 2007 R2 and Communicator 2007 clients will continue to use Group Policy during side-by-side migration. However, if you want policy settings to carry over to Lync clients, you need to configure the equivalent Lync Server in-band provisioning settings. 
  
> [!NOTE]
> To enable a user for remote call control, you need to provide the user with both a Line URI and a Line Server URI. As described in [Deployment tasks for remote call control in Lync Server 2013](deployment-tasks-for-remote-call-control.md), you need to be sure to use the syntax that is required by the gateway for these settings. > Be sure that the domain in the Line Server URI is the same as the destination domain that you specified in the MatchUri parameter when you configured the static route to the gateway. > The Line URI specifies the phone number assigned to the user in E.164 format, with the "TEL:" prefix (for example, tel:+14255550150). If you want to configure an extension number, then the format is tel:+14255550150;ext=111. If you previously configured the user's Line URI and the value has not changed, you do not need to specify the Line URI when you enable the user for remote call control. 
  
### To enable remote call control for Lync-enabled users by using Management Shell

1. Log on to a computer where Lync Server Management Shell is installed as a member of the RTCUniversalServerAdmins group or as a role-based access control role to which you have assigned the **Set-CsUser** cmdlet. 
    
2. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
3. To use the **Set-CsUser** cmdlet to configure remote call control for an existing Lync-enabled user, do the following: 
    
  ```
  Set-CsUser -Identity <User ID> -EnterpriseVoiceEnabled $false -LineServerUri <SIP URI of the SIP/CSTA gateway> -LineUri <TEL URI of the user> -RemoteCallControlTelephonyEnabled $true
  ```

    For example:
    
  ```
  Set-CsUser -Identity "Katie Jordan" -EnterpriseVoiceEnabled $false -LineServerUri sip:rccgateway@contoso.net -LineUri tel:+14255550150 -RemoteCallControlTelephonyEnabled $true
  ```

### To configure users for remote call control by using Lync Server Control Panel

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Users**.
    
4. In the **Search users** box, type all (or the first portion) of the display name, first name, last name, Security Accounts Manager (SAM) account name, SIP address, or line Uniform Resource Identifier (URI) of the user account that you want, and then click **Find**.
    
5. In the table, click the user account that you want to modify.
    
6. On the **Edit** menu, click **Modify**.
    
7. In **Telephony**, do one of the following:
    
  - To enable remote call control to enable the user to control their private branch exchange (PBX) phone from Lync 2013 to make PC-to-PC audio calls and PC-to-phone calls, click **Remote call control**. In **Line URI**, specify the telephone number of the user. In **Line Server URI**, specify the SIP URI of the SIP/CSTA gateway.
    
  - To enable remote call control, but disable PC-to-PC audio calls, and to enable only the user to control their PBX phone from Lync 2013 to make PC-to-phone calls, click **Remote call control only**. In **Line URI**, specify the telephone number of the user. In **Line Server URI**, specify the SIP URI of the SIP/CSTA gateway.
    
8. When you are finished, click **Commit**.
    

