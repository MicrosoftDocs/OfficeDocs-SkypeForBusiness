---
title: "Migrate dial-in access numbers [OCS 2007 R2 to W15]"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 568a94b7-a697-4ab2-9008-dc9ecc1c87c8
description: "Migrating dial-in access numbers requires two steps: running the Import-CsLegacyConfiguration cmdlet (completed earlier in Import policies and settings [OCS 2007 R2 to W15]) to migrate dial plans and other dial-in access number settings, and running the Move-CsApplicationEndpoint cmdlet to migrate the contact objects."
---

# Migrate dial-in access numbers [OCS 2007 R2 to W15]
[]
Migrating dial-in access numbers requires two steps: running the **Import-CsLegacyConfiguration** cmdlet (completed earlier in [Import policies and settings [OCS 2007 R2 to W15]](import-policies-and-settings-ocs-2007-r2-to-w15.md)) to migrate dial plans and other dial-in access number settings, and running the **Move-CsApplicationEndpoint** cmdlet to migrate the contact objects. 
  
## To migrate dial-in access numbers

1. Open the Office Communications Server 2007 R2 administrative tool.
    
2. In the console tree, right-click the forest node, click **Properties**, and then click **Conferencing Attendant Properties**.
    
3. On the **Access Phone Numbers** tab, click **Serviced by Pool** to sort the access phone numbers by their associated pool, and identify all the access numbers for the pool from which you are migrating. 
    
4. To identify the SIP URI for each access number, double-click the access number to open the **Edit Conferencing Attendant Number** dialog box, and look under **SIP URI**. 
    
5. Open the Lync Server Management Shell.
    
6. To move each dial-in access number to a pool hosted on Lync Server 2013, run: 
    
  ```
  Move-CsApplicationEndpoint -Identity <SIP URI of the access number to be moved> -Target <FQDN of the pool to which the access number is moving>
  ```

7. In the Office Communications Server 2007 R2 Administrative tool, on the **Access Phone Numbers** tab, verify that no dial-in access numbers remain for the Office Communications Server 2007 R2 pool from which you are migrating. 
    

