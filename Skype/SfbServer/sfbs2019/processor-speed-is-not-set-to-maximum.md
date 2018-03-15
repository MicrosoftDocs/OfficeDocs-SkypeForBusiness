---
title: "Processor speed is not set to maximum"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3339db05-2955-4fb2-81a3-c9ed13ffc54a
description: "Issue: Current Processor speed is less than the maximum possible speed."
---

# Processor speed is not set to maximum
[]
Issue: Current Processor speed is less than the maximum possible speed.
  
## Description of the Issue

The Office 365 Best Practices Analyzer tool for Lync Server queries a Windows Management Instrumentation (WMI) class (Win32_Processor) to determine the value of the MaxClockSpeed and CurrentClockSpeed keys.
  
A warning appears if the value for the **CurrentClockSpeed** is less than the value for the **MaxClockSpeed**. The **CurrentClockSpeed** value is the current speed in megahertz (MHz) of each processor. The **MaxClockSpeed** is the maximum speed in MHz of each processor. If this warning appears, one or more processors on your computer is not operating at full speed. 
  
An incorrect setting in the BIOS of the computer where Lync Server is installed might be forcing the processor to run at a reduced speed in a power-saving mode. To resolve this issue, see your hardware manufacturer for information about how to view and configure system BIOS, processor, and power management settings.
  
## Issue Resolution

For more information about power management in Windows Server 2008 R2, Windows Server 2012, or Windows Server 2012, open the **Start** menu, and then open **Help and Support Center**, and search for "Power Management" and "Power Options."
  

