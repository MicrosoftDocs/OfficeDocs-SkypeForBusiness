---
title: 'Configure policies to control federated user access'
ms.reviewer: 
ms:assetid: 5485e208-81e4-4e59-9aeb-1232c11dd8a2
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398359(v=OCS.15)
ms:contentKeyID: 48184180
mtps_version: v=OCS.15
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "When you configure policies to support communications with federated partners, the policies apply to users of federated domains. "
---


# Configure policies to control federated user access in Skype for Business Server

When you configure policies to support communications with federated partners, the policies apply to users of federated domains. You can configure one or more external user access policies to control whether users of federated domains can collaborate with your Skype for Business Server users. To control federated user access, you can configure policies at the global, site, and user level. Skype for Business Server policy settings that are applied at one policy level can override settings that are applied at another policy level. Skype for Business Server policy precedence is: User policy (most influence) overrides a Site policy, and then a Site policy overrides a Global policy (least influence). This means that the closer the policy setting is to the object that the policy is affecting, the more influence it has on the object.


> [!NOTE]  
> You can configure policies to control federated user access, even if you have not enabled federation for your organization. However, the policies that you configure are in effect only when you have federation enabled for your organization. For details about enabling federation, see [Enable or disable remote user access](../access-edge/enable-or-disable-remote-user-access.md).  Additionally, if you specify a user policy to control federated user access, the policy applies only to users that are enabled for Skype for Business Server and configured to use the policy.


## To configure a policy to support access by users of federated domains

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel.

3.  In the left navigation bar, click **External User Access**, and then click **External Access Policy**.

4.  On the **External Access Policy** page, do one of the following:
    
      - To configure the global policy to support federated user access, click the global policy, click **Edit**, and then click **Show details**.
    
      - To create a new site policy, click **New**, and then click **Site policy**. In **Select a Site**, click the appropriate site from the list and then click **OK**.
    
      - To create a new user policy, click **New**, and then click **User policy**. In **New External Access Policy**, create a unique name in the **Name** field that indicates what the user policy covers (for example, **EnableFederatedUsers** for a user policy that enables communications for federated domain users).
    
      - To change an existing policy, click the appropriate policy listed in the table, click **Edit**, and then click **Show details**.

5.  (Optional) If you want to add or edit a description, specify the information for the policy in **Description**.

6.  Do one of the following:
    
      - To enable federated user access for the policy, select the **Enable communications with federated users** check box.
    
      - To disable federated user access for the policy, clear the **Enable communications with federated users** check box.

7.  Click **Commit**.

To enable federated user access, you must also enable support for federation in your organization. For details, see [Enable or disable federation and public IM connectivity](../access-edge/enable-or-disable-federation-and-public-im-connectivity.md).

If this is a user policy, you must also apply the policy to users that you want to be able to collaborate with federated users. For details, see [Assign an external user access policy](assign-an-external-user-access-policy.md).

## To configure an existing policy using Windows PowerShell to support access by users of federated domains

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Start the Skype for Busines Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business Server**, and then click **Skype for Business Server Management Shell**.

3.  Type the following in the Skype for Business Server Management Shell:
    
    ```
    Set-CsExternalAccessPolicy -Identity <name of global, site or user policy - policy must exist when using Set-CsExternalAccessPolicy > -Description <descriptive name for policy> -EnableFederationAccess <$true, $false> -EnableXmppAccess <$true, $false> -EnablePublicCloudAcess <$true, $false> -EnablePublicCloudAudioVideoAcess <$true, $false> -EnableOutsideAcess <$true, $false>
    ```
       

    > [!TIP]  
    > The parameter “EnablePublicCloudAudioVideoAccess” does not have a corresponding selection in the Skype for Business Server Control Panel


## To create a new policy using Windows PowerShell to support access by users of federated domains

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Skype for Business Server**, and then click **Skype for Business Server Management Shell**.

3.  Type the following in the Skype for Business Server Management Shell:
    
    ```
    New-CsExtenalAccessPolicy -Identity <name of site or user policy - you cannot create a new global policy using New-CsExternalAccessPolicy > -Description <descriptive name for policy> -EnableFederationAccess <$true, $false> -EnableXmppAccess <$true, $false> -EnablePublicCloudAccess <$true, $false> -EnablePublicCloudAudioVideoAccess <$true, $false> -EnableOutsideAccess <$true, $false>
    ```
    
    An example of creating a new site policy:
    
    ```
    New-CsExternalAccessPolicy -Identity site:Redmond -EnableFederationAccess $true -EnableXmppAccess $true -EnableOutsideAccess $true -EnablePublicCloudAccess $true -EnablePublicCloudAudioVideoAccess $true
    ```


## To delete or reset a policy using Windows PowerShell to support access by users of federated domains

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Type the following in the Skype for Business Server Management Shell
    
    `Remove-CsExternalAccessPolicy -Identity <name of global, site or user policy>`
    
    An example of resetting the global policy (The global policy can only have its setting removed. The policy cannot be deleted):
    
    `Remove-CsExternalAccessPolicy -Identity global`
    
    To remove a site policy, type:
    
    `Remove-CsExternalAccessPolicy -Identity site:Redmond` 
    
    Deletes the site policy Redmond. To delete a user policy named UserEAPPolicy, type:
    
    `Remove-CsExternalAccessPolicy -Identity UserEAPPolicy`


## See Also


[Enable or disable federation and public IM connectivity](../access-edge/enable-or-disable-federation-and-public-im-connectivity.md) 

[Assign an external user access policy](assign-an-external-user-access-policy.md)

[Manage SIP federated domains for your organization](../sip-domains/manage-sip-federated-domains-for-your-organization.md)
 
[Manage SIP federated providers for your organization](../sip-providers/manage-sip-federated-providers-for-your-organization.md)

[Set-CsExternalAccessPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsExternalAccessPolicy)  
[New-CsExternalAccessPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsExternalAccessPolicy)  
[Get-CsExternalAccessPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsExternalAccessPolicy)  
[Remove-CsExternalAccessPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsExternalAccessPolicy)  
[Grant-CsExternalAccessPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Grant-CsExternalAccessPolicy)  
  

