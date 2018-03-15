---
title: "Enable or disable sending an Archiving disclaimer to federated partners in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c8e9a2fa-9dc1-4e4d-919f-56ece8004864
description: "At the time you deployed your Edge Servers and enabled federation for your organization, you should have specified whether to automatically send the archiving disclaimer to federated partners. If you archive external communications, you should enable the sending of an archiving disclaimer. Use the procedure in this topic to change that configuration."
---

# Enable or disable sending an Archiving disclaimer to federated partners in Lync Server 2013
[]
At the time you deployed your Edge Servers and enabled federation for your organization, you should have specified whether to automatically send the archiving disclaimer to federated partners. If you archive external communications, you should enable the sending of an archiving disclaimer. Use the procedure in this topic to change that configuration.
  
> [!NOTE]
> The following procedure assumes that you have already enabled federation for your organization. For details about enabling federation, see [Enable or disable remote user access in Lync Server 2013](enable-or-disable-remote-user-access.md) in the Deployment documentation or the Operations documentation. 
  
### To enable or disable sending of an archiving disclaimer to federated partners

1. From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **External User Access**, click **Access Edge Configuration**.
    
4. On the **Access Edge Configuration** tab, click **Global**, click **Edit**, and then click **Show details**.
    
5. In **Edit Access Edge Configuration**, under **Enable communications with federated users**, select or clear the **Send archiving disclaimer to federated partners** check box to enable or disable automatically sending the archiving disclaimer. 
    
6. Click **Commit**.
    
To enable federated users to collaborate with users in your Lync Server 2013 deployment, you must have also configured at least one external access policy to support federated user access. For details, see [Manage XMPP federated partners in Lync Server 2013](manage-xmpp-federated-partners-for-your-organization.md) in the Deployment documentation or the Operations documentation. For details about controlling access for specific federated domains, see [Configure support for allowed external domains in Lync Server 2013](configure-support-for-allowed-external-domains.md) in the Deployment documentation or Operations documentation. 
## Enabling or Disabling the Archiving Disclaimer by Using Windows PowerShell Cmdlets

The use of the archiving disclaimer can be managed by using Windows PowerShell and the Set-CsAccessEdgeConfiguration cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876).
  
### To enable the archiving disclaimer

- To enable the archiving disclaimer, set the value of the **EnableArchivingDisclaimer** property to True ($True): 
    
  ```
  Set-CsAccessEdgeConfiguration -EnableArchivingDisclaimer $True
  ```

### To disable the archiving disclaimer

- To disable the archiving disclaimer, set the value of the **EnableArchivingDisclaimer** property to False ($False): 
    
  ```
  Set-CsAccessEdgeConfiguration -EnableArchivingDisclaimer $False
  ```


