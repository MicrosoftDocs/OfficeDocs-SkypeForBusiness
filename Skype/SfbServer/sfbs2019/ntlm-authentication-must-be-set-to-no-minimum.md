---
title: "NTLM Authentication must be set to No Minimum"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 586186a5-2692-4adc-817f-3025d8f6fb40
description: "Issue: The default security setting on Windows Server 2008 R2 and Windows Server 2012 operating systems for NTLM SSP requires 128-bit encryption. If Lync client is being used on a computer not set to use 128-but encryption, users will be unable to join online meetings. The client computer must have NTLM Authentication set to No Minimum to successfully join meetings."
---

# NTLM Authentication must be set to No Minimum
[]
Issue: The default security setting on Windows Server 2008 R2 and Windows Server 2012 operating systems for NTLM SSP requires 128-bit encryption. If Lync client is being used on a computer not set to use 128-but encryption, users will be unable to join online meetings. The client computer must have NTLM Authentication set to No Minimum to successfully join meetings.
  
## Description of the Issue

Depending on the client operating system mix in the enterprise, you may have to reduce this setting on a Windows Server 2008 R2 or Windows Server 2012 operating systems that are running Lync Server as a down level operating system.
  
For a Windows 7 operating system, the default value is set to "Requires 128-bit encryption." 
  
For more information about the "Changes in NTLM Authentication" as it applies to Windows 2008 R2 and Windows 7 operating systems, please see [Learn more about the changes in NTLM Authentication](https://go.microsoft.com/fwlink/p/?LinkId=396793).
  
## Issue Resolution

If you want to change the NTLM setting, follow these steps: 
  
- Start secpol.msc on a server running Windows Server 2008 R2, Windows Server 2012, or Windows Server 2012 R2.
    
- Click to select **Local Policies** and then click **Security Options** node. 
    
- Make sure that the following values of the policies are set to "No Minimum."
    
    Network Security: Minimum session security for NTLM SSP based (including secure RPC)
    
    Network Security: Minimum session security for NTLM SSP based (including secure RPC) servers
    
For more information about the operating systems that are currently supported for Lync Server 2013, see [Supported hardware for Lync Server 2013](supported-hardware.md).
  

