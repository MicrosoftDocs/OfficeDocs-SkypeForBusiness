---
title: "Configuring media port range settings in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: End User
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 2c4b7c0b-0dce-48f4-a489-336d6e526f7c
description: "Media port range settings can significantly impact client performance and should be configured. You can configure these settings by using Lync Server Management Shell."
---

# Configuring media port range settings in Lync Server 2013
[]
Media port range settings can significantly impact client performance and should be configured. You can configure these settings by using Lync Server Management Shell.
  
**Media Port Range Settings**

|**Setting**|**Description**|**Lync Server Management Shell cmdlet**|**Cmdlet parameters**|
|:-----|:-----|:-----|:-----|
|Portrange\Enabled  <br/> |Specifies whether the port ranges sent by the server should be used by the client for media and signaling. Used in conjunction with the subvalues MinMediaPort and MaxMediaPort.  <br/> |**CsConferencingConfiguration** <br/> |ClientMediaPortRangeEnabled  <br/> |
|Portrange\MinMediaPort  <br/> |Specifies the starting port number to use for media. Combines with MaxMediaPort to specify the range of ports. The recommended minimum range is 40 ports.  <br/> |**CsConferencingConfiguration** <br/> |ClientMediaPort (represents the starting port number to use for client media)  <br/> |
|Portrange\MaxMediaPort  <br/> |Specifies the highest port number to use for media. Combines with MinMediaPort to specify the range of ports. The recommended minimum range is 40 ports.  <br/> |**CsConferencingConfiguration** <br/> |ClientMediaPortRange (indicates the total number of ports available for client media; default is 40)  <br/> |
   
### To Configure Media Port Range Settings

1. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
2. Run the following cmdlet:
    
  ```
  Get-CsConferencingConfiguration
  ```

    This cmdlet returns the conferencing configuration settings.
    
3. Run the following cmdlet with the parameters and values you want to change (for details about the parameters for this cmdlet, see the Lync Server Management Shell documentation):
    
  ```
  Set-CsConferencingConfiguration
  ```

    > [!NOTE]
    > You can create additional sets of conferencing configuration settings for specific sites. Use the **New- CsConferencingConfiguration** cmdlet with a site identity. When you create new conferencing configuration settings for sites, the site settings take precedence over the global settings. For details, see the Lync Server Management Shell documentation. 
  

