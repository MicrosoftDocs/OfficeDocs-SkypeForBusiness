---
title: 'Enable or disable sending an Archiving disclaimer to federated partners'
ms.reviewer: 
ms:assetid: c8e9a2fa-9dc1-4e4d-919f-56ece8004864
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg182584(v=OCS.15)
ms:contentKeyID: 48185391
mtps_version: v=OCS.15
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: ""
---

# Enable or disable sending an Archiving disclaimer to federated partners in Skype for Business Server

At the time you deployed your Edge Servers and enabled federation for your organization, you should have specified whether to automatically send the archiving disclaimer to federated partners. If you archive external communications, you should enable the sending of an archiving disclaimer. Use the procedure in this topic to change that configuration.

> [!NOTE]
> The following procedure assumes that you have already enabled federation for your organization. For details about enabling federation, see [Enable or disable remote user access](enable-or-disable-remote-user-access.md).


## To enable or disable sending of an archiving disclaimer to federated partners

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 

3.  In the left navigation bar, click **External User Access**, click **Access Edge Configuration**.

4.  On the **Access Edge Configuration** tab, click **Global**, click **Edit**, and then click **Show details**.

5.  In **Edit Access Edge Configuration**, under **Enable communications with federated users**, select or clear the **Send archiving disclaimer to federated partners** check box to enable or disable automatically sending the archiving disclaimer.

6.  Click **Commit**.

To enable federated users to collaborate with users in your Skype for Business Server deployment, you must have also configured at least one external access policy to support federated user access. For details about controlling access for specific federated domains, see [Configure support for allowed external domains](../sip-domains/manage-sip-federated-domains-for-your-organization.md#configure-support-for-allowed-external-domains-in-skype-for-business-server).


## Enabling or disabling the archiving disclaimer by using Windows PowerShell cmdlets

The use of the archiving disclaimer can be managed by using Windows PowerShell and the Set-CsAccessEdgeConfiguration cmdlet. This cmdlet can be run either from the Skype for Business Server Management Shell or from a remote session of Windows PowerShell. 

## To enable the archiving disclaimer

  - To enable the archiving disclaimer, set the value of the **EnableArchivingDisclaimer** property to True ($True):
    
        Set-CsAccessEdgeConfiguration -EnableArchivingDisclaimer $True

## To disable the archiving disclaimer

  - To disable the archiving disclaimer, set the value of the **EnableArchivingDisclaimer** property to False ($False):
    
        Set-CsAccessEdgeConfiguration -EnableArchivingDisclaimer $False


