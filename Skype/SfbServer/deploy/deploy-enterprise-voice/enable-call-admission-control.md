---
title: "Enable call admission control in Skype for Business Server"
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
ms.assetid: 80201105-18f7-4c02-9c71-8df5a952f6c7
description: "Enable call admission control in Skype for Business Server Enterprise Voice."
---

# Enable call admission control in Skype for Business Server
 
Enable call admission control in Skype for Business Server Enterprise Voice. 
  
After you have configured your network settings for call admission control deployment, you must enable CAC to put your bandwidth policies into effect.
  
### To enable call admission control by using Skype for Business Server Management Shell

1. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.
    
2. Run the Set-CsNetworkConfiguration cmdlet to enable CAC in your network. For example, run:
    
   ```
   Set-CsNetworkConfiguration -EnableBandwidthPolicyCheck 1
   ```

    If you want to disable CAC in your network, run the following:
    
   ```
   Set-CsNetworkConfiguration -EnableBandwidthPolicyCheck 0
   ```

### To enable call admission control by using Skype for Business Server Control Panel

1. Open Skype for Business Server Control Panel.
    
2. In the left navigation bar, click **Network Configuration**.
    
3. Click the **Global** navigation button.
    
4. Click **Global** in the list, and then select **Show Details** on the **Edit** menu.
    
5. On the **Edit Global Settings** page, select the **Enable call admission control** check box.
    
    > [!NOTE]
    > If you want to disable call admission control throughout your deployment, clear this check box. 
  
6. Click **Commit**. 
    
## See also

[Get-CsNetworkConfiguration](https://docs.microsoft.com/powershell/module/skype/get-csnetworkconfiguration?view=skype-ps)
  
[Set-CsNetworkConfiguration](https://docs.microsoft.com/powershell/module/skype/set-csnetworkconfiguration?view=skype-ps)
  
[Remove-CsNetworkConfiguration](https://docs.microsoft.com/powershell/module/skype/remove-csnetworkconfiguration?view=skype-ps)
