---
title: "Configuring a watcher node to run synthetic transactions in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: cedda508-8881-4079-88d5-49798f342ddf
description: "After the System Center agent files have been installed, you must next configure the watcher node itself. The steps you take to configure a watcher node will vary depending on whether your watcher node computer lies inside your perimeter network or outside your perimeter network."
---

# Configuring a watcher node to run synthetic transactions in Lync Server 2013
[]
After the System Center agent files have been installed, you must next configure the watcher node itself. The steps you take to configure a watcher node will vary depending on whether your watcher node computer lies inside your perimeter network or outside your perimeter network.
  
When you configure a watcher node, you must also choose the type of authentication method to be employed by that node. Lync Server 2013 enables you to choose one of two authentication methods: Trusted Server or Credential Authentication. The differences between these two methods are outlined in the following table:
  
|**Configuration**|**Description**|**Locations Supported**|
|:-----|:-----|:-----|
|Trusted Server  <br/> |Uses a certificate to impersonate an internal server and bypass authentication challenges.  <br/> This is useful for administrators who would prefer to manage a single certificate instead of many user passwords on each watcher node.  <br/> |Inside the enterprise.  <br/> Note that, with this method, the watcher node must be in the same domain as the pools being monitored. If the watcher node and the monitored pools are in different domains, use Credential Authentication instead.  <br/> |
|Credential Authentication  <br/> |Stores user names and passwords securely in Windows Credential Manager on each watcher node.  <br/> This mode requires more password management, but is the only option for watcher nodes located outside of the enterprise. These watcher nodes cannot be treated as an endpoint trusted for authentication.  <br/> |Outside the enterprise.  <br/> Inside the enterprise.  <br/> |
   
You should also verify that your firewall has inbound rules for both MonitoringHost.exe and PowerShell.exe. If these processes are blocked by the firewall then your synthetic transactions will fail with a 504 (server timeout) error.
  

