---
title: "Configure a VTC for Interoperation with Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: quickstart
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: 1016aed6-99fe-452e-8b20-81c814808c3d
description: "Summary: Configure the VTC devices to work with Skype for Business Server."
---

# Configure a VTC for Interoperation with Skype for Business Server
 
**Summary:** Configure the VTC devices to work with Skype for Business Server.
  
You will need to perform the following configuration customization procedures for each VTC that will connect to the Skype for Business VIS server through a SIP trunk and Cisco Unified Communications Manager (CallManager, or CUCM) video gateway.
  
The settings described here are meant only as examples of how CUCM can be configured to work with a VIS. Other settings and/or usages of alternate CUCM functionality could also be used to achieve the same result. No recommendation is implied as to the optimal configuration for a particular scenario.
  
### Configure a VTC registered with CUCM

1. Log in to the Cisco VTC device and navigate to Configuration-\>System Configuration-\>Provisioning.
    
2. Verify the following settings, correcting as needed: 
    
   |**Parameter**|**Recommended setting**|
   |:-----|:-----|
   |Provisioning Mode  <br/> | CUCM <br/> |
   |ExternalManager Address  <br/> | CUCM's FQDN <br/> |
   | ExternalManager Domain <br/> |CUCM's domain  <br/> |
   
3. Navigate to Configuration-\>System Configuration-\>Network.
    
4. Verify the following settings, correcting as needed: 
    
   |**Parameter**|**Recommended setting**|
   |:-----|:-----|
   |DNS Domain Name  <br/> | CUCM's Domain name <br/> |
   |DNS Server 1 Address  <br/> | your desired DNS server address <br/> |
   
5. Navigate to Configuration-\>System Configuration-\>Network Services. Ensure that H.323 mode is turned off and SIP mode is turned on. 
    
6. These options are set automatically when the endpoint is registered with CUCM. Verify the following settings, correcting as needed: 
    
   |**Parameter**|**Recommended setting**|
   |:-----|:-----|
   |H.323 Mode  <br/> | Off <br/> |
   |HTTP Mode  <br/> | On <br/> |
   | SIP Mode <br/> | On <br/> |
   |Telnet Mode  <br/> | On <br/> |
   |WelcomeText  <br/> | On <br/> |
   |XMLAPI Mode  <br/> | On <br/> |
   
7. Navigate to Configuration-\>System Configuration-\>SIP.
    
8. Verify the following settings, correcting as needed: 
    
   |**Parameter**|**Recommended setting**|
   |:-----|:-----|
   |Profile 1 - DefaultTransport  <br/> | TCP <br/> |
   |Profile 1 - Outbound  <br/> | Off <br/> |
   |Profile 1 - TlsVerify  <br/> | On <br/> |
   |Profile 1 - Type  <br/> | Cisco <br/> |
   |Profile 1 - URI  <br/> | Automatically assigned at CUCM registration <br/> |
   |Proxy 1 - Address  <br/> |The host name of the CUCM  <br/> |
   
The VTC is now configured for interoperation. Before service can begin, there are final steps to perform on the CUCM side.
### Configure VTC devices on CUCM

1. Log in to CUCM and Navigate to Cisco Unified CM Administration-\>Device-\>Phone-\>Find. 
    
2. Select the VTC device to be configured. Verify the following settings on the Phone Configuration screen, correcting as needed. Once these settings have been changed or verified, click on **Save**.
    
   |**Parameter**|**Recommended setting**|
   |:-----|:-----|
   |Device Information - Phone Button Template  <br/> | Standard Cisco Telepresence Codec C40 <br/> |
   |Device Information - Common Phone Profile  <br/> | Standard Common Phone Profile <br/> |
   |Device Information - Calling Search Space  <br/> | CSS_SfBVideoInterop <br/> |
   |Device Information - AAR Calling Search Space  <br/> | CSS_SfBVideoInterop <br/> |
   |Device Information - Media Resource Group List  <br/> | MRGL_SfBVideoInterop <br/> |
   |Protocol Specific Information - Device Security Profile  <br/> | Cisco Telepresence Codec C40 <br/> |
   |Protocol Specific Information - Rerouting Calling Search Space  <br/> | CSS_SfBVideoInterop <br/> |
   |Protocol Specific Information - SUBSCRIBE Calling Search Space  <br/> | CSS_SfBVideoInterop <br/> |
   |Protocol Specific Information -SIP Profile  <br/> | Standard SIP Profile for Telepresence Endpoint <br/> |
   
3. Once VTC configuration is saved, re-navigate to the Phone Configuration screen for the device. At the top of the screen in the Association group, click on the association for the Video Interop. This brings up the Directory Number Configuration screen. 
    
4. Verify the following settings, correcting as needed: 
    
    Make the appropriate changes as shown to the Directory Number Information and the Directory Number Settings.
    
   |**Parameter**|**Recommended setting**|
   |:-----|:-----|
   | Directory Number Information - Route Partition <br/> | SfBVideoInterop_RoutePartition <br/> |
   |Directory Number Settings - Calling Search Space  <br/> | CSS_SfBVideoInterop <br/> |
   |MLPP Alternate Party and Confidential Access Level Settings - MLPP Calling Search Space  <br/> | CSS_SfBVideoInterop <br/> |
   |Line 1 on Device - Display (Caller ID)  <br/> | As desired <br/> |
   |Line 1 on Device - ASCII Display (Caller ID)  <br/> | As desired <br/> |
   
5. When finished, scroll to the top of the screen and press **Save**. 
    
Configuration is now complete for this VTC device. You will need to repeat this process for other VTC devices in your enterprise.

