---
title: "Components used by Group Call Pickup in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 45db2f23-d486-4b20-a8cf-7b48a1f9fd3a
description: "Group Call Pickup is automatically deployed when you deploy Enterprise Voice and the Call Park application. You enable Group Call Pickup by configuring the Call Park orbit table with separate ranges of numbers designated as call pickup group numbers, and then by assigning users to call pickup groups and enabling the users for Group Call Pickup. The following Lync Server components support Group Call Pickup:"
---

# Components used by Group Call Pickup in Lync Server 2013
[]
Group Call Pickup is automatically deployed when you deploy Enterprise Voice and the Call Park application. You enable Group Call Pickup by configuring the Call Park orbit table with separate ranges of numbers designated as call pickup group numbers, and then by assigning users to call pickup groups and enabling the users for Group Call Pickup. The following Lync Server components support Group Call Pickup:
  
- **Application service** Application service provides a platform for deploying, hosting, and managing unified communications applications, such as the Call Park application. Application service is automatically installed on every Front End Server in a Front End pool and on every Standard Edition server. 
    
- **Call Park application** The Call Park application is one of the unified communications applications that are hosted by Application service. Group Call Pickup is based on the Call Park application. 
    
- **Lync Server Management Shell** You use Lync Server Management Shell to manage Group Call Pickup groups. 
    
- **SEFAUtil resource kit tool** You use the secondary extension feature activation utility (SEFAUtil) to assign users to a call pickup group and to enable or disable call pickup for users. 
    

