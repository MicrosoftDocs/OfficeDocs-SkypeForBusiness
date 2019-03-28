---
title: "Create network region links in Skype for Business Server"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom: 
ms.assetid: f8163910-8935-475d-88a2-3aa44feb9dbe
description: "Create or modify network region links, which are used by Enterprise Voice call admission control in Skype for Business Server."
---

# Create network region links in Skype for Business Server
 
Create or modify network region links, which are used by Enterprise Voice call admission control in Skype for Business Server. 
  
Regions within a network are linked through physical WAN connectivity. A network region link creates a link between two regions configured for Call Admission Control (CAC) and sets the bandwidth limitations on audio and video traffic between these regions.
  
The example topology has a link between the North America and APAC regions, and a link between the EMEA and APAC regions. Each of these region links is constrained by WAN bandwidth, as described in Region Link Bandwidth Information table in [Example: Gathering requirements for call admission control in Skype for Business Server](../../plan-your-deployment/enterprise-voice-solution/example-gathering-requirements.md).
  
### To create network region links by using Skype for Business Server Management Shell

1. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.
    
2. Run the New-CsNetworkRegionLink cmdlet to create the region links and apply appropriate bandwidth policy profiles. For example, run:
    
   ```
   New-CsNetworkRegionLink -NetworkRegionLinkID NA-EMEA-LINK -NetworkRegionID1 NorthAmerica -NetworkRegionID2 EMEA -BWPolicyProfileID 50Mb_Link
   ```

   ```
   New-CsNetworkRegionLink -NetworkRegionLinkID EMEA-APAC-LINK -NetworkRegionID1 EMEA -NetworkRegionID2 APAC -BWPolicyProfileID 25Mb_Link
   ```

### To create network region links by using Skype for Business Server Control Panel

1. Open Skype for Business Server Control Panel.
    
2. In the left navigation bar, click **Network Configuration**.
    
3. Click the **Region Link** navigation button.
    
4. Click **New**.
    
5. On the **New Region Link** page, click **Name** and then type a name for the network region link.
    
6. Click **Network Region #1**, and then click the network region in the list that you want to link to Network Region #2.
    
7. Click **Network Region #2**, and then click a network region in the list that you want to link to Network Region #1.
    
8. Optionally, click **Bandwidth policy**, and then select the bandwidth policy profile that you want to apply to the network region link.
    
    > [!NOTE]
    > Apply a bandwidth policy only if the network region link is bandwidth-constrained and you want to use CAC to control media traffic on that link. 
  
9. Click **Commit**.
    
10. To finish creating network region links for your topology, repeat steps 4 through 9 with settings for other regions.
    
## See also

[New-CsNetworkRegionLink](https://docs.microsoft.com/powershell/module/skype/new-csnetworkregionlink?view=skype-ps)
  
[Get-CsNetworkRegionLink](https://docs.microsoft.com/powershell/module/skype/get-csnetworkregionlink?view=skype-ps)
  
[Set-CsNetworkRegionLink](https://docs.microsoft.com/powershell/module/skype/set-csnetworkregionlink?view=skype-ps)
  
[Remove-CsNetworkRegionLink](https://docs.microsoft.com/powershell/module/skype/remove-csnetworkregionlink?view=skype-ps)
