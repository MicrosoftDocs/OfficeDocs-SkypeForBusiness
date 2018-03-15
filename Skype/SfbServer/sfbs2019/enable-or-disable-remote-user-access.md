---
title: "Enable or disable remote user access in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: cd9d3ddc-4839-457a-86d9-b15413e74002
description: "Remote users are users in your organization who have a persistent Active Directory identity within the organization. Remote users often sign in to Lync Server from outside your network by using a virtual private network (VPN) when they are not connected to your organization's network. Remote users include employees working at home or on the road and other remote workers, such as trusted vendors, who have been granted enterprise credentials. If you enable remote user access for remote users, supported remote users connect over the Internet and do not have to connect using a VPN in order to collaborate with internal users using Lync Server."
---

# Enable or disable remote user access in Lync Server 2013
[]
Remote users are users in your organization who have a persistent Active Directory identity within the organization. Remote users often sign in to Lync Server from outside your network by using a virtual private network (VPN) when they are not connected to your organization's network. Remote users include employees working at home or on the road and other remote workers, such as trusted vendors, who have been granted enterprise credentials. If you enable remote user access for remote users, supported remote users connect over the Internet and do not have to connect using a VPN in order to collaborate with internal users using Lync Server.
  
To support remote user access, you must enable remote user access. When you enable remote user access, you enable it for your entire organization. If you later want to temporarily or permanently prevent remote user access, you can disable it for your organization. Use the procedure in this section to enable or disable remote user access for your organization.
  
> [!NOTE]
> Enabling remote user access only specifies that your servers running the Access Edge service support communications with remote users, but remote users cannot participate in instant messaging (IM) or conferences in your organization until you also configure at least one policy to manage the use of remote user access. Lync Server policy settings that are applied at one policy level can override settings that are applied at another policy level. Lync Server policy precedence is: User policy (most influence) overrides a Site policy, and then a Site policy overrides a Global policy (least influence). This means that the closer the policy setting is to the object that the policy is affecting, the more influence it has on the object. For details about configuring policies for the use of remote user access, see [Configure policies to control remote user access in Lync Server 2013](configure-policies-to-control-remote-user-access.md). 
  
### To enable or disable remote user access for your organization

1. From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Federation and External Access**, and then click **Access Edge Configuration**.
    
4. On the **Access Edge Configuration** page, click **Global**, click **Edit**, and then click **Show details**.
    
5. In **Edit Access Edge Configuration**, do one of the following:
    
  - To enable remote user access for your organization, select the **Enable remote user access** check box. 
    
  - To disable remote user access for your organization, clear the **Enable remote user access** check box. 
    
6. Click **Commit**.
    
To enable remote users to sign in to your servers running Lync Server, you must also configure at least one external access policy to support remote user access. For details, see [Configure policies to control remote user access in Lync Server 2013](configure-policies-to-control-remote-user-access.md) in the Deployment documentation or the Operations documentation. 
## Enabling or Disabling Remote User Access by Using Windows PowerShell Cmdlets

Remote user access can be managed by using Windows PowerShell and the Set-CsAccessEdgeConfiguration cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876).
  
### To enable remote user access

- To enable remote user access, set the value of the **AllowOutsideUsers** property to True ($True): 
    
  ```
  Set-CsAccessEdgeConfiguration -AllowOutsideUsers $True
  ```

### To disable remote user access

- To disable remote user access, set the value of the **AllowOutsideUsers** property to False ($False): 
    
  ```
  Set-CsAccessEdgeConfiguration -AllowOutsideUsers $False
  ```


