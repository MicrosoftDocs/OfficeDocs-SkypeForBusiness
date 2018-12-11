---
title: "Migrate Lync Room System devices to Skype Room System version 2"
ms.author: jambirk
author: jambirk
ms.reviewer: sohailta
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 
description: "Read this topic to learn how to migrate Lync Room System devices to use the Skype Room System v2 software."
---

# Migrate Lync Room System (LRS) devices to Skype Room System v2 
Lync Room System (LRS) devices with Skype Room System Version 1 (SRS v1) software has reached [end of support on October 9, 2018](https://support.microsoft.com/en-us/help/4043450/products-reaching-end-of-support-for-2018). This means Skype Room Systems v1 software will no longer get any product updates or fixes anymore. Customers with Lync Room System devices using Skype Room System v1 software are advised to upgrade their devices to Skype Room System version 2 (SRS v2).

Skype Room System Version 2 (SRS v2) software works with Microsoft Teams in addition to Skype for Business Server and Online services for meetings and calling on all SRS v2 supported devices.

Your existing devices **may** continue to work after the end of Skype Room System v1 software support. However, if this software hits a software bug that needs Microsoft to release a fix, it will not be supported. SRS v1 uses TLS 1.0/ 1.1 which will be deprecated by Microsoft in future. You can learn more about [Preparing for TLS 1.0/1.1 Deprecation](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Preparing-for-TLS-1-0-1-1-Deprecation-O365-Skype-for-Business/bc-p/223608). Skype Room System V2 is adding support for TLS 1.2 and will continue to work past October 31, 2018. Skype for Business on premise customers should not disable TLS 1.0/1.1 until Skype Room System V2 annouces support for TLS 1.2 regardless of general guidelines on TLS 1.0/1.1 deprecation.

## Which devices are affected?
Here is the list of the devices that are affected by this change:
- [SMART Room systems](https://support.smarttech.com/en/hardware/room-systems-skype)
- [Crestron RL2](https://www.crestron.com/en-US/Products/Featured-Solutions/Crestron-RL-2)
- [Polycom CX8000](http://www.polycom.com/products-services/products-for-microsoft/skype-for-business/cx8000.html)
- Crestron RL

## Upgrade options
There are multiple options for upgrading Lync Room Systems to the next generation of Skype Room Systems (SRS v2).

### Crestron hardware Trade-in program
Crestron will provide an upgrade to the [Crestron SR system](https://www.crestron.com/en-us/products/featured-solutions/crestron-sr) or equivalent for all Non-Crestron Lync Room System customers. See details of this program [here](https://support.crestron.com/app/answers/answer_view/a_id/1000220) or <!-- For details, -->[email](mailto:lrsupgrade@crestron.com) Crestron LRS support.  


### Crestron RL2 to RL3
Existing Crestron RL2 (also referred to as Crestron RL200) customers can acquire an upgrade package to upgrade current RL2 to RL3 using a for a minimal cost per device. See details of this program [here](https://support.crestron.com/app/answers/answer_view/a_id/1000220) or <!-- For details, -->[email](mailto:lrsupgrade@crestron.com) Crestron LRS support.  


### SMART Room Systems upgrade 
For SMART LRS customers, apart from Crestron hardware trade-in program, Microsoft and SMART are also working on providing a solution to upgrade to Skype Room System v2. This upgrade will be provided by SMART Technologies Inc. Please see more about this [here](https://support.smarttech.com/docs/hardware/room-systems-skype/srs-skype-v2/en/about/default.cshtml).

<!--  
For later 
### Do-It-Yourself
A Do-It-Yourself option is also available for customers with upgrade to Windows 10 and Skype Room Systems v2 software. Windows 10 Enterprise Licenses are available through [approved resellers](https://www.microsoft.com/en-us/Licensing/how-to-buy/how-to-buy.aspx) and Skype Room System V2 software will be available through this guide. 
 
  
To use this option however, customers must additionaly buy a [Logitech Screen Share](https://www.logitech.com/en-us/product/screen-share) adapter. Microsoft will provide instructions on how to use this adapter with Skype Room System v2 software. 


Look for upgrade instructions on this page shortly. 
  
### Summary of upgrade options
This table lists summary of all available options for existing LRS devices:
<!--  For later 
| Upgrade Option | SMART Room Systems | Crestron RL2 | Polycom CX8000 | Crestron RL |
|:--- |:--- |:--- |:--- |:--- |
|**Crestron hardware </br>Trade-in program**|Available|Available|Available|Available|
|**Crestron RL3**|Not Available|Available|Not Available|Not Available|
|**Do-It-Yourself**|Available|Not Available|Not Available|Not Available|
| | | | | |
-->

## What should you do?
We recommend you plan to update Lync Room System devices to Skype Room Systems v2 before TLS 1.0/1.1 deprecation using upgrade options mentioned above. Additionally, you may also consider replacing existing devices with new devices certified for SRS v2. See [Room devices](https://aka.ms/roomdevices) for details and also take a look at [Skype Room Systems v2 requirements](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/clients-and-devices/requirements).  

> [!NOTE]
> Touch and whiteboard functionality is not yet supported in Skype Room System v2. Touch and whiteboard support is in the backlog for Skype Room System v2 and will be added in H1 CY2019.

> [!NOTE]
> Skype Room System V2 software currently does not support TLS 1.2 protocol. TLS 1.2 support is being worked on and will be completed before TLS 1.0/1.1 deprecation. Customers upgradging to SRS v2 will not see any impact of TLS 1.0/1.1 deprecation on Room devices running latest version of SRS v2 app. Skype for Business on premise customers should not disable TLS 1.0/1.1 until Skype Room System V2 annouces support for TLS 1.2. 
