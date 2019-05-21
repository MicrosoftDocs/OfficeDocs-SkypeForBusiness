---
title: "Configure CUCM for Interoperation with Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: eab3d9f6-ec40-49bf-9162-1a7f5a59451f
description: "Summary: Configure CUCM to work with Skype for Business Server."
---

# Configure CUCM for Interoperation with Skype for Business Server
 
**Summary:** Configure CUCM to work with Skype for Business Server.
  
> [!CAUTION]
> This capability is tested with Cisco Unified Communications Manager (CallManager, or CUCM) version 10.5 using Trunks setup over TCP only. Verify that the CUCM environment meets these criteria before proceeding. 
  
The settings described here are meant only as examples of how CUCM can be configured to work with a VIS. Other settings and/or usages of alternate CUCM functionality could also be used to achieve the same result. No recommendation is implied as to the optimal configuration for a particular scenario.
  
A number of CUCM settings need to be confirmed or changed for interoperation with the VIS. Follow the procedures below in order to avoid missing required settings.
  
### Configure the CUCM

1. Log in to CUCM and navigate to Cisco Unified CM Administration-\>Call Routing-\>Class of Control-\>Partition.
    
2. In the Partition Configuration screen, enter the partition name and description and click on **Add New**.
    
3. Navigate to Cisco Unified CM Administration-\>Call Routing-\>Class of Control-\>Calling Search Space.
    
4. In the Calling Search Space Configuration screen, enter the name for the calling search space, and in Selected Partitions, enter the name of the partition you just created. Click **Save** when done.
    
5. Navigate to Cisco Unified CM Administration-\>System-\>Security-\>SIP Trunk Security Profile.
    
6. In the SIP Trunk Security Profile Configuration screen, set the SIP Trunk Security Profile Information options as shown, and click on **Add New**.
    
   |**Parameter**|**Recommended setting**|
   |:-----|:-----|
   |Name  <br/> |SfBVideoInterop_SecurityProfile  <br/> |
   |Device Security Mode  <br/> |Non Secure  <br/> |
   |Incoming Transport Type  <br/> |TCP + UDP  <br/> |
   |Outgoing Transport Type  <br/> |TCP  <br/> |
   |Incoming Port  <br/> |5060  <br/> |
   
7. Navigate to Cisco Unified CM Administration-\>Device-\>Device Settings-\>SIP Profile.
    
8. In the SIP Profile Configuration screen, set the SIP Profile Information options as shown. 
    
   |**Parameter**|**Recommended setting**|
   |:-----|:-----|
   |Name  <br/> |SfBVideoInterop_SIPProfile  <br/> |
   |Description  <br/> |SfBVideoInterop_SIPProfile  <br/> |
   
9. On the same screen, scroll down to the SDP Profile Information section. The **SDP Session-level Bandwidth Modifier for Early Offer and Re-invites** option is set by default to TIAS and AS. Change this option to TIAS only. If you leave this option at its default setting, Skype for Business Server will not understand the bandwidth modifier information in the SIP message. TIAS means Transport Independent Application Specific while AS means Application Specific. These are SIP options specified in RFC3890.
    
10. On the same screen, scroll down further. Under the SIP Profile's Trunk Specific Configuration, select **Early Offer Support for voice and video calls** and set it to the **Mandatory (insert MTP if needed)** option. This will enable CUCM to set up an outgoing SIP call with Early Offer. One new feature in CUCM 8.5 and beyond is that it supports outgoing call setup with Early Offer without requiring Media Termination Point (MTP).
    
11. Verify that in the SIP Options ping section, the box is checked next to "Enable OPTIONS Ping to monitor destination status for Trunks with Service Type 'None (Default)'."
    
12. When you are finished, click on **Add New**.
    
13. Navigate to Cisco Unified CM Administration-\>Device-\>Trunk. 
    
14. Set the Device Protocol to SIP and press **Next**.
    
15. Under Device Information, Set the Device Name and Description (probably to something like SfBVideoInterop_SIPTrunk), and set the Media Resource Group List to an MRGL that contains the right media resources. 
    
16. Scroll down further. Media Termination Point (MTP) is not required for Video Calls, if it is not already unchecked, uncheck it. Check the option to **Run on all active Unified CM Nodes**. Please note that you should add all CUCM nodes to the Skype for Business Server configuration.
    
17. Scroll down further. Set the Inbound Calls and Connected Party Settings options as shown.
    
    |**Parameter**|**Recommended setting**|
    |:-----|:-----|
    |Calling Search Space  <br/> |CSS_SfBVideoInterop  <br/> |
    |AAR Calling Search Space  <br/> |CSS_SfBVideoInterop  <br/> |
    |Connected Party Transformation CSS  <br/> |CSS_SfBVideoInterop  <br/> |
   
18. Scroll down further. Under the SIP Information Destination section of the SIP Trunk configuration, specify the VIS Pool's FQDN or the IP address of individual VIS servers in the pool (adding multiple entries). In the Destination Port specify the Port that VIS is listening at for connections from CUCM (the default is 6001). Also specify the SIP Trunk security profile and SIP profile you created earlier, as shown.
    
    |**Parameter**|**Recommended setting**|
    |:-----|:-----|
    |SIP Trunk Security Profile  <br/> |SfBVideoInterop_SecurityProfile  <br/> |
    |Rerouting Calling Search Space  <br/> |CSS_SfBVideoInterop  <br/> |
    |Out-of-Dialog Refer Calling Search Space  <br/> |CSS_SfBVideoInterop  <br/> |
    |Subscribe Calling Search Space  <br/> |CSS_SfBVideoInterop  <br/> |
    |SIP Profile  <br/> |SfBVideoInterop_SIPProfile  <br/> |
    |DTMF Signaling Method  <br/> |RFC 2833  <br/> |
   
19.  Scroll down further. Set the Recording Information as appropriate for your system. It's fine to leave it set to **None**. 
    
20. When you are finished, click on **Add New**.
    
21. Navigate to Cisco Unified CM Administration-\>Call Routing-\>Route/Hunt-\>Route pattern.
    
22. In the Route Pattern Configuration screen, enter the Pattern definition parameters shown below. Scroll down to the Called Party Transformations section and set the mask as shown, and then click on **Add New** when finished.
    
    |**Parameter**|**Recommended setting**|
    |:-----|:-----|
    |Route Pattern  <br/> |7779999  <br/> |
    |Route Partition  <br/> |SfBVideoInterop_RoutePartition  <br/> |
    |Description  <br/> |Partition for SfBVideoInterop  <br/> |
    |Gateway/Route List  <br/> |SfBVideoInterop_SIPTrunk  <br/> |
    |Called Party Transform Mask  <br/> |+14257779999  <br/> |
   
23. Navigate to Cisco Unified CM Administration-\>Call Routing-\>SIP Route Pattern.
    
24. In the SIP Route Pattern Configuration screen, set the Pattern Definition options as shown, and click on **Add New**.
    
    |**Parameter**|**Recommended setting**|
    |:-----|:-----|
    | Pattern Usage <br/> |Domain Routing  <br/> |
    |IPv4 Pattern  <br/> |contoso.com (leave blank if using IPv6)  <br/> |
    |IPv6 Pattern  <br/> |contoso.com (leave blank if using IPv4)  <br/> |
    |Description  <br/> |SIPRoute Pattern to mediarv  <br/> |
    |Route Partition  <br/> |SfBVideoInterop_RoutePartition  <br/> |
    |SIP Trunk/Route List  <br/> |SfBVideoInterop_SIPTrunk  <br/> |
    |Block Pattern checkbox  <br/> |leave unchecked  <br/> |
   
25. If you have changed the audio or video bit rates from the default settings, you will need to return them to the defaults. To set the bit rate for Audio/Video calls, navigate to Cisco Unified CM Administration-\>System-\>Region Information-\>Region. The defaults are shown below for reference:
    
    |**Parameter**|**Recommended setting**|
    |:-----|:-----|
    |Region  <br/> |Default  <br/> |
    |Audio Codec Preference List  <br/> |System Default  <br/> |
    |Maximum Audio Bit Rate  <br/> |64 kbps (G.722, G.711)  <br/> |
    |Maximum Session Bit Rate for Video Calls  <br/> |200000 kbps  <br/> |
    |Maximum Session Bit Rate  <br/> |2000000000 kbps  <br/> |
   
At this point the CUCM video gateway is configured to work with the VIS. Corresponding configuration will need to be done on each VTC you wish to integrate.
> [!NOTE]
> To improve resiliency, you may want to configure this CUCM gateway to work with a second Video Interop Server or VIS pool. See [Resiliency mechanisms](../../plan-your-deployment/video-interop-server.md#resiliency) for more information.
  
## See also

[Configure a VTC for Interoperation with Skype for Business Server](configure-a-vtc-for-interoperation.md)
