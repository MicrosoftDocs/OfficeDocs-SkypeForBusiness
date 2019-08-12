---
title: 'Managing network bandwidth policy profiles'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "Use the procedures in this article to view, create, modify, or delete network bandwidth policy profiles."
---


# Managing network bandwidth policy profiles in Skype for Business Server

Use the procedures in this article to view, create, modify, or delete network bandwidth policy profiles.

## View network bandwidth policy profile information

As part of call admission control (CAC), a bandwidth policy is used to define bandwidth limitations for certain modalities. In Skype for Business Server, only audio and video modalities can be assigned bandwidth limitations. You can set overall bandwidth limitations and session limitations. You can use the Skype for Business Server Control Panel to create, modify, or delete a container profile for these policies. Each bandwidth policy profile can be associated with one or more network sites. Use the following procedures to view a bandwidth policy profile. 

### To view a bandwidth policy profile

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 

3.  In the left navigation bar, click **Network Configuration** and then click **Bandwidth Policy**.

4.  On the **Bandwidth Policy** page, click the bandwidth policy profile that you want to view.

5.  On the **Edit** menu, click **Show details**.


### Viewing network bandwidth policy profile information by using Windows PowerShell cmdlets

Network bandwidth profiles can be viewed by using Windows PowerShell and the Get-CsNetworkBandwidthPolicyProfile cmdlet. This cmdlet can be run either from the Skype for Business Server Management Shell or from a remote session of Windows PowerShell. 


### To view network bandwidth policy profile information

  - To view information about all your network bandwidth policy profiles, type the following command in the Skype for Business Server Management Shell, and then press ENTER:
    
        Get-CsNetworkBandwidthPolicyProfile
    
    That will return information similar to this:
    
        Identity          : RedmondBandwidthPolicy
        BWPolicy          : {BWLimit=200;BWSessionLimit=200;
                            BWPolicyModality=Audio, 
                            BWLimit=1400;BWSessionLimit=500;
                            BWPolicyModality=Video}
        BWPolicyProfileID : RedmondBandwidthPolicy
        Description       :


For more information, see the help topic for the [Get-CsNetworkBandwidthPolicyProfile](https://docs.microsoft.com/powershell/module/skype/Get-CsNetworkBandwidthPolicyProfile) cmdlet.


## Create or modify bandwidth policy profiles

As part of call admission control (CAC), a bandwidth policy is used to define bandwidth limitations for certain modalities. In Skype for Business Server, only audio and video modalities can be assigned bandwidth limitations. You can set overall bandwidth limitations and session limitations. You can use the Skype for Business Server Control Panel to create, modify, or delete a container profile for these policies. Each bandwidth policy profile can be associated with one or more network sites. Use the following procedures to create or modify a bandwidth policy profile. 

### To create a new bandwidth policy profile

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 

3.  In the left navigation bar, click **Network Configuration**, and then click **Bandwidth Policy**.

4.  On the **Bandwidth Policy** page, click **New**.

5.  In **New Bandwidth Policy Profile**, type a name in the **Name** field. This name must be unique among all bandwidth policy profiles.

6.  In the **Audio limit** field, type a numeric value. This value is the maximum amount of bandwidth to allocate for all audio connections, expressed in kbps.

7.  Enter a numeric value in the **Audio session limit** field. This value is the maximum amount of bandwidth to allocate for an individual audio connection, expressed in kbps. This value must be 40 or higher.

8.  Enter a numeric value in the **Video limit** field. This value is the maximum amount of bandwidth to allocate for all video connections, expressed in kbps.

9.  Enter a numeric value in the **Video session limit** field. This value is the maximum amount of bandwidth to allocate for an individual video connection, expressed in kbps. This value must be 100 or higher.

10. (Optional) Type a value in the **Description** field to provide more information about this bandwidth policy profile that cannot be expressed by the name alone.

11. Click **Commit**.

    > [!NOTE]  
    > Creating a new bandwidth policy profile does not automatically enforce bandwidth restrictions. You must first associate the policy profile with a site. 


### To modify a bandwidth policy profile

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 

3.  In the left navigation bar, click **Network Configuration**, and then click **Bandwidth Policy**.

4.  On the **Bandwidth Policy** page, click the bandwidth policy profile that you want to modify.

5.  On the **Edit** menu, click **Show details**.

6.  On the **Edit Bandwidth Policy Profile** page, modify the fields as necessary (for details, see [To create a new bandwidth policy profile](#to-create-a-new-bandwidth-policy-profile)).

7.  Click **Commit**.

    > [!NOTE]  
    > When you modify the bandwidth policy profile, it will immediately update the bandwidth limitations of all network sites associated with this bandwidth policy profile.

  
## Delete network bandwidth policy profiles

As part of call admission control (CAC), a bandwidth policy is used to define bandwidth limitations for certain modalities. In Skype for Business Server, only audio and video modalities can be assigned bandwidth limitations. You can set overall bandwidth limitations and session limitations. You can use the Skype for Business Server Control Panel to create, modify, or delete a container profile for these policies. Use the following procedures to delete a network bandwidth policy profiles. 

### To delete a bandwidth policy profile

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 

3.  In the left navigation bar, click **Network Configuration**, and then click **Bandwidth Policy**.

4.  On the **Bandwidth Policy** page, click the bandwidth policy profile that you want to delete.

    > [!NOTE]  
    > You can delete more than one profile at a time. To do this, press CTRL and select multiple profiles while holding down the CTRL key. Or, to select all profiles, click **Select all** on the **Edit** menu.

5.  On the **Edit** menu, click **Delete**.
   

    > [!WARNING]  
    > You cannot delete a bandwidth policy profile that is associated with a network site. You must first remove the association with the network site before you can delete the profile. 


## See Also

[Managing call admission control for sites](managing-call-admission-control-for-sites.md)
 
[New-CsNetworkBandwidthPolicyProfile](https://docs.microsoft.com/powershell/module/skype/New-CsNetworkBandwidthPolicyProfile)  

[Set-CsNetworkBandwidthPolicyProfile](https://docs.microsoft.com/powershell/module/skype/Set-CsNetworkBandwidthPolicyProfile)  

[Get-CsNetworkBandwidthPolicyProfile](https://docs.microsoft.com/powershell/module/skype/Get-CsNetworkBandwidthPolicyProfile)  

[Remove-CsNetworkBandwidthPolicyProfile](https://docs.microsoft.com/powershell/module/skype/Remove-CsNetworkBandwidthPolicyProfile)  
  

