---
title: 'Enabling QoS for devices that are not based on Windows'
ms.reviewer: 
ms:assetid: 26f793df-aef8-4028-9e3b-6c2c37ea61b9
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204750(v=OCS.15)
ms:contentKeyID: 48183661
mtps_version: v=OCS.15
ms.author: jambirk
author: jambirk
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "Learn how to enable QoS for devices used in your organization that use an operating system other than Windows."
---

# Enabling QoS in Skype for Business Server for devices that are not based on Windows


When you install Skype for Business Server, Quality of Service (QoS) will not be enabled for any devices used in your organization that use an operating system other than Windows. You can verify this by running the following command from within the Skype for Business ServerManagement Shell:

    Get-CsMediaConfiguration

Assuming you have not made any changes to your media configuration settings, you should get back information similar to this:

    Identity                          : Global
    EnableQoS                         : False
    EncryptionLevel                   : RequireEncryption
    EnableSiren                       : False
    MaxVideoRateAllowed               : VGA600K
    EnableG722StereoCodec             : True
    EnableH264Codec                   : True
    EnableAdaptiveBandwidthEstimation : True

If the EnableQoS property is set to False (as in the preceding output) that means that Quality of Service is not enabled for computers and devices that use an operating system other than Windows.

To enable Quality of Service at the global scope, run the following command from within the Skype for Business Server Management Shell:

    Set-CsMediaConfiguration -EnableQoS $True

The preceding command enables QoS at the global scope; however, it's important to note that media configuration settings can also be applied to the site scope. If you need to enable Quality of Service for a site, you must include the Identity of the configuration settings when calling Set-CsMediaConfiguration. For example, this command enables QoS for the Redmond site:

    Set-CsMediaConfiguration -Identity site:Redmond -EnableQoS $True



> [!NOTE]  
> Do you need to enable QoS at the site scope? That depends. Settings assigned to the site scope take precedence over settings assigned to the global scope. Suppose you have QoS enabled at the global scope but disabled at the site scope (for the Redmond site). In that case, Quality of Service would be disabled for the Redmond site; that's because the site settings take precedence. To enable QoS for the Redmond site, you would have to do so using the media configuration settings applied to that site.


If you want to simultaneously enable QoS for all your media configuration settings (regardless of scope), run this command from within the LSkype for Business Server Management Shell:

    Get-CsMediaConfiguration | Set-CsMediaConfiguration -EnableQoS $True

You can disable QoS for devices that use an operating system other than Windows by setting the value of the EnableQoS property to False. For example:

    Set-CsMediaConfiguration -Identity site:Redmond -EnableQoS $False

This gives you the ability to implement QoS on some portions of your network (for example, on the Redmond site) while leaving Quality of Service disabled on other portions of your network.

QoS can only be enabled and disabled by using Windows PowerShell. These options are not available in the Skype for Business Server Control Panel.


