---
title: Deploy media bypass in Skype for Business Server 2015
ms.prod: SKYPEFORBUSINESS
ms.assetid: 1bd35f90-8587-48a1-b0c2-095a4053fc77
---


# Deploy media bypass in Skype for Business Server 2015
[]Deploy media bypass in Skype for Business Server Enterprise Voice. Includes prerequisites and deployment process checklist.
This topic assumes that you have already published and configured either at least one or more Mediation Servers and at least one gateway peer to provide PSTN connectivity. For more details on those tasks, see  [Deploy a Mediation Server in Topology Builder in Skype for Business Server 2015](deploy-a-mediation-server-in-topology-builder-in-skype-for-business-server-2015.md) and [Define a gateway in Topology Builder in Skype for Business Server 2015](define-a-gateway-in-topology-builder-in-skype-for-business-server-2015.md).
  
    
    

 If the peer you connect to is the SBC of a SIP trunking provider, make sure that the provider is a qualified provider and that the provider supports media bypass. For example, many SIP trunking providers will only allow their SBC to receive traffic from the Mediation Server. If so, then bypass must not be enabled for the trunk in question. Also, you cannot enable media bypass unless your organization reveals its internal network IP addresses to the SIP trunking provider.
> [!NOTE]
> Media bypass will not interoperate with every PSTN gateway, IP-PBX, and SBC. Microsoft has tested a set of PSTN gateways and SBCs with certified partners and has done some testing with Cisco IP-PBXs. Media bypass is supported only with products and versions listed on Unified Communications Open Interoperability Program - Lync Server at  [https://go.microsoft.com/fwlink/p/?linkId=214406](https://go.microsoft.com/fwlink/p/?linkId=214406). 
  
    
    

If you have already optionally configured call admission control (CAC), another advanced Enterprise Voice feature, note that the bandwidth reservation performed by call admission control does not apply to any calls for which media bypass is employed. The verification of whether to employ media bypass is performed first, and if media bypass is employed, call admission control is not used for the call; only if the media bypass check fails is the check performed for call admission control. The two features are thus mutually exclusive for any particular call that is routed to the PSTN. This is the logic because media bypass assumes that bandwidth constraints do not exist between the media endpoints on a call; media bypass cannot be performed on links with restricted bandwidth. As a result, one of the following will apply to a PSTN call: a) media bypasses the Mediation Server, and call admission control does not reserve bandwidth for the call; or b) call admission control applies bandwidth reservation to the call, and media is processed by the Mediation Server involved in the call.In addition to enabling media bypass for individual trunk connections associated with a peer, you must also enable media bypass globally. Global media bypass settings can either specify that media bypass is always attempted for calls to the PSTN, or that media bypass is employed by using the mapping of subnets to network sites and network regions—similar to what is done by call admission control, another advanced voice feature. When media bypass and call admission control are both enabled, then the network region, network site, and subnet information that is specified for call admission control is automatically used when determining whether to employ media bypass. This means that you cannot specify that media bypass is always attempted for calls to the PSTN when call admission control is enabled.
> [!NOTE]
> When you use these steps to configure media bypass, the assumption is that you have good connectivity between clients and the Mediation Server peer (for example, a PSTN gateway, an IP-PBX, or an SBC at a SIP trunking provider). If there are any bandwidth limitations on the link, media bypass cannot be applied to the call. Media bypass will not interoperate with every PSTN gateway, IP-PBX, and SBC. Microsoft has tested a set of PSTN gateways and SBCs with certified partners and has done some testing with Cisco IP-PBXs. Media bypass is supported only with products and versions listed on Unified Communications Open Interoperability Program - Lync Server at  [https://go.microsoft.com/fwlink/p/?linkId=214406](https://go.microsoft.com/fwlink/p/?linkId=214406). 
  
    
    


## Deployment Process for media bypass

The following table provides an overview of the media bypass deployment process. 
  
    
    


|**Phase**|**Steps**|**Roles**|**Deployment documentation**|
|:-----|:-----|:-----|:-----|
|Configure trunks for media bypass  <br/> |If you have not already done so, configure one or more trunks for media bypass.  <br/> | A member of RTCUniversalServerAdmins group, or a member of the CsVoiceAdministrator, CsServerAdministrator, or CsAdministrator role <br/> | [Configure a trunk with media bypass in Skype for Business Server 2015](configure-a-trunk-with-media-bypass-in-skype-for-business-server-2015.md) <br/> |
|Configure media bypass globally  <br/> |Configure media bypass for either all calls to the PSTN, or certain calls based on network sites and network regions.  <br/> | A member of RTCUniversalServerAdmins group, or a member of the CsVoiceAdministrator, CsServerAdministrator, or CsAdministrator role <br/> | [Configure media bypass in Skype for Business Server 2015 to always bypass the Mediation Server](configure-media-bypass-in-skype-for-business-server-2015-to-always-bypass-the-me.md) <br/>  [Configure media bypass global settings in Skype for Business Server 2015 to use site and region information](configure-media-bypass-global-settings-in-skype-for-business-server-2015-to-use.md) <br/> |
|Associate subnets with network sites, if necessary  <br/> |If you configure media bypass to use site and region information, you must associate the subnets of your deployment with network sites and regions (If you have not already done so for another voice feature.)  <br/> | A member of RTCUniversalServerAdmins group, or a member of the CsVoiceAdministrator, CsServerAdministrator, or CsAdministrator role <br/> | [Associate a subnet with a network site](deploy-network-regions-sites-and-subnets-in-skype-for-business-2015.md#BKMK_AssociateSubnets) <br/> |
   

