---
title: "Configure a trunk with media bypass in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: quickstart
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection:
- IT_Skype16
- Strat_SB_Admin
ms.custom:
ms.assetid: 99d729ea-5a4c-4ff2-a4a3-93a24368da6d
description: "Summary: Configure a trunk with media bypass enabled for Skype for Business Server. This will let you minimize the number of Mediation Servers, presuming your SIP trunk provider supports it."
---

# Configure a trunk with media bypass in Skype for Business Server

**Summary:** Configure a trunk with media bypass enabled for Skype for Business Server. This will let you minimize the number of Mediation Servers, presuming your SIP trunk provider supports it.

Follow these steps to configure a trunk with media bypass enabled. To configure a trunk with media bypass disabled, see [Configure a trunk without media bypass in Skype for Business Server](configure-trunk-without-media-bypass.md).

Media bypass is useful when you want to minimize the number of Mediation Servers deployed. For more information, see [Plan for media bypass in Skype for Business](../../plan-your-deployment/enterprise-voice-solution/media-bypass.md)

We strongly recommend that you enable media bypass. However, before you enable media bypass on a SIP trunk, confirm that your qualified SIP trunk provider supports media bypass and is able to accommodate the requirements for successfully enabling the scenario. Specifically, the provider must have the IP addresses of servers in your organization's internal network.

> [!NOTE]
> Media bypass will not interoperate with every Public Switched Telephone Network (PSTN) gateway, IP-PBX, and Session Border Controller (SBC). Microsoft has tested a set of PSTN gateways and SBCs with certified partners. Media bypass is supported only with products and versions that are listed on the [Telephony Infrastructure for Skype for Business Server](https://docs.microsoft.com/SkypeForBusiness/certification/infra-gateways) page.

A trunk configuration as described below groups a set of parameters that are applied to trunks assigned this trunk configuration. A particular trunk configuration can be scoped globally (to all trunks that do not have more specific site or pool configuration), or to a site, or to a pool. The pool-level trunk configuration is used to scope a specific trunk configuration to a single trunk.

### To configure a trunk with media bypass

1. Open Skype for Business Server Control Panel

2. In the left navigation bar, click **Voice Routing**, and then click **Trunk Configuration**.

3. On the **Trunk Configuration** page, use one of the following methods to configure a trunk:

   - Double-click an existing trunk (for example, the **Global** trunk) to display the **Edit Trunk Configuration** dialog box.

   - Click **New**, and then select a scope for the new trunk configuration:

   - **Site trunk**: Choose the site for this trunk configuration from **Select a Site**, and then click **OK**. Note that if a trunk configuration has already been created for a site, the site does not appear in **Select a Site**. This trunk configuration will be applied to all trunks in the site.

   - **Pool trunk**: Choose the name of the trunk that this trunk configuration applies to. This trunk can be the root trunk or any additional trunks defined in Topology Builder. From **Select a Service**, click **OK**. Note that if a trunk configuration has already been created for a specific trunk, the trunk does not appear in **Select a Service**.

      > [!NOTE]
      > After you select the scope of the trunk configuration, it cannot be changed. > The **Name** field is prepopulated with the name of the trunk configuration's associated site or service and cannot be changed.

4. Specify a value in **Maximum early dialogs supported**. This is the maximum number of forked responses a public switched telephone network (PSTN) gateway, IP-PBX, or ITSP Session Border Controller (SBC) can receive to an INVITE that it sent to the Mediation Server. The default value is 20.

    > [!NOTE]
    > Before you change this value, consult your service provider or equipment manufacturer for details about the capabilities of your system.

5. Select one of the following **Encryption support level** options:

   - **Required**: Secure real-time transport protocol (SRTP) encryption must be used to help protect traffic between the Mediation Server and the gateway or private branch exchange (PBX).

   - **Optional**: SRTP encryption will be used if the service provider or equipment manufacturer supports it.

   - **Not Supported**: SRTP encryption is not supported by the service provider or equipment manufacturer and therefore will not be used.

6. Select the **Enable media bypass** check box if you want media to bypass the Mediation Server for processing by the trunk peer.

    > [!IMPORTANT]
    > For media bypass to work successfully, the PSTN gateway, IP-PBX, or ITSP Session Border Controller must support certain capabilities. For details, see [Plan for media bypass in Skype for Business](../../plan-your-deployment/enterprise-voice-solution/media-bypass.md).

7. Select the **Centralized media processing** check box if there is a well-known media termination point (for example, a PSTN gateway where the media termination has the same IP as the signaling termination). Clear this check box if the trunk does not have a well-known media termination point.

8. If the trunk peer supports receiving SIP REFER requests from the Mediation Server, select the **Enable sending refer to the gateway** check box.

    > [!NOTE]
    > If you disable this option while the **Enable media bypass** option is selected, additional settings are required. If the trunk peer does not support receiving SIP REFER requests from the Mediation Server and media bypass is enabled, you must also run the **Set-CsTrunkConfiguration** cmdlet to disable RTCP for active and held calls in order to support proper conditions for media bypass. Alternatively, you can select **Enable refer using third-party-call control** if you want transferred calls to be media bypassed, and the gateway does not support SIP REFER requests.

9. (Optional) To enable inter-trunk routing, associate and configure PSTN usage records to this trunk configuration. The PSTN usages associated to this trunk configuration will be applied for all incoming calls through the trunk that is not originating from a Skype for Business Server endpoint. To manage PSTN usage records associated to a trunk configuration, use one of the following methods:

   - To select one or more records from a list of all PSTN usage records available in your Enterprise Voice deployment, click **Select**. Highlight the records you want to associate with this trunk configuration and then click **OK**.

   - To remove a PSTN usage record from this trunk configuration, select the record and click **Remove**.

   - To define a new PSTN usage record and associate it with this trunk configuration, do the following:

     a. Click **New**.

     b. In the **Name** field, specify a descriptive name for the record that is unique.

     > [!NOTE]
     > The PSTN usage record name must be unique within the Enterprise Voice deployment. After the record is saved, the **Name** field cannot be edited.

     c. Use one of the following methods to associate and configure routes for this PSTN usage record:

     - To select one or more routes from the list of all available routes in your Enterprise Voice deployment, click **Select**. Highlight the routes you want to associate with this PSTN usage record, and click **OK**.

     - To remove a route from the PSTN usage record, select the route, and click **Remove**.

   - To define a new route and associate it to this PSTN usage record, click **New**. For details, see [Create or modify a voice route in Skype for Business](create-or-modify-a-voice-route.md).

     - To edit a route that is associated with this PSTN usage record, select the route, and click **Show details**.

     d. Click **OK**.

     - To edit a PSTN usage record that is already associated with this trunk configuration, do the following:

       a. Select the PSTN usage record you want to edit, and click **Show details**.

       b. Use one of the following methods to associate and configure routes for this PSTN usage record:

   - To select one or more routes from the list of all available routes in your Enterprise Voice deployment, click **Select**. Highlight the routes you want to associate with this PSTN usage record, and click **OK**.

   - To remove a route from the PSTN usage record, select the route, and click **Remove**.

   - To define a new route and associate it to this PSTN usage record, click **New**. For details, see [Create or modify a voice route in Skype for Business](create-or-modify-a-voice-route.md).

   - To edit a route that is associated with this PSTN usage record, select the route, and click **Show details**.

     c. Click **OK**.

     > [!IMPORTANT]
     > It is important to associate PSTN usage records according to the Mediation Server peer that is associated to the trunk being configured. If the Mediation Server peer is a PSTN gateway or a Session Border Controller (SBC), it is strongly recommended that the trunk configuration is not associated to a PSTN usage record that routes to a PSTN destination or any other downstream systems connected via Skype for Business Server.

10. Arrange the PSTN usage records for optimum performance. To change a record's position in the list, select the PSTN usage record, and click the up or down arrows.

    > [!IMPORTANT]
    > The order in which PSTN usage records are listed in the trunk configuration is significant. Skype for Business Server traverses the list from top to down.

11. **Enable RTP Latching** should be selected to enable bypass media for clients behind a network address translation (NAT) or firewall and an SBC that supports latching.

12. **Enable forward call history** should be selected to enable sending of call history information to the gateway peer of the Mediation Server.

13. **Enable forward P-Asserted-Identity data** should be selected to enable the P-Asserted-Identity (PAI) call originator information to be forwarded between the Mediation Server side and gateway side (and vice versa), when present.

14. **Enable outbound routing failover timer** should be selected to enable fast failover. The gateway associated with this trunk can give notification within 10 seconds that it is processing an outbound call. Rerouting to another trunk will occur if this notification is not received by the Mediation Server. On networks where latency may delay the response time or the gateway takes longer than 10 seconds to respond, the fast failover should be disabled.

15. (Optional) Associate and configure **calling number translation rules** for the trunk. These translation rules apply to the calling number for outbound calls

    - To choose one or more rules from a list of all translation rules that are available in your Enterprise Voice deployment, click **Select**. In **Select Translation Rules**, click the rules that you want to associate with the trunk, and then click **OK**.

    - To define a new translation rule and associate it with the trunk, click **New**. For details about translation rules, see [Translation rules in Skype for Business Server](../../plan-your-deployment/enterprise-voice-solution/translation-rules.md).

    - To edit a translation rule that is already associated with the trunk, click the rule name, and then click **Show details**.

    - To copy an existing translation rule to use as a starting point for defining a new rule, click the rule name and click **Copy**, and then click **Paste**.

    - To remove a translation rule from the trunk, highlight the rule name and click **Remove**.

    > [!CAUTION]
    > Do not associate translation rules with a trunk if you have configured translation rules on the associated trunk peer, because the two rules might conflict.

16. (Optional) Associate and configure **called number translation rules** for the trunk. The translation rules apply to the called number in an outbound call.

    - To choose one or more rules from a list of all translation rules that are available in your Enterprise Voice deployment, click **Select**. In **Select Translation Rules**, click the rules that you want to associate with the trunk, and then click **OK**.

    - To define a new translation rule and associate it with the trunk, click **New**. For details about translation rules, see [Translation rules in Skype for Business Server](../../plan-your-deployment/enterprise-voice-solution/translation-rules.md).

    - To edit a translation rule that is already associated with the trunk, click the rule name, and then click **Show details**.

    - To copy an existing translation rule to use as a starting point for defining a new rule, click the rule name and click **Copy**, and then click **Paste**.

    - To remove a translation rule from the trunk, highlight the rule name and click **Remove**.

    > [!CAUTION]
    > Do not associate translation rules with a trunk if you have configured translation rules on the associated trunk peer, because the two rules might conflict.

17. Make sure that the trunk's translation rules are arranged in the correct order. To change a rule's position in the list, highlight the rule name and then click the up or down arrow.

    > [!IMPORTANT]
    > Skype for Business Server traverses the translation rule list from the top down and uses the first rule that matches the dialed number. If you configure a trunk so that a dialed number can match more than one translation rule, be sure that the more restrictive rules are sorted above the less restrictive rules. For example, if you have included a translation rule that matches any 11-digit number and a translation rule that matches only 11-digit numbers that start with +1425, be sure that the rule that matches any 11-digit number is sorted  *below*  the more restrictive rule.

18. When you are finished configuring the trunk, click **OK**.

19. On the **Trunk Configuration** page, click **Commit**, and then click **Commit all**.

    > [!NOTE]
    > Whenever you create or modify a trunk configuration, you must run the **Commit all** command to publish the configuration change. For details, see [Publish pending changes to the voice routing configuration in Skype for Business](voice-route-config-changes.md) in the Operations documentation.

After you have configured the trunk, continue configuring media bypass by choosing between global media bypass options, as described in [Deploy media bypass in Skype for Business Server](deploy-media-bypass.md) in the Deployment documentation.
## See also

[Configure a trunk without media bypass in Skype for Business Server](configure-trunk-without-media-bypass.md)

[Deploy media bypass in Skype for Business Server](deploy-media-bypass.md)

[Defining Translation Rules](https://technet.microsoft.com/library/4f6b975a-77e6-474c-9171-b139d84138c2.aspx)

[Configure Media Bypass](https://technet.microsoft.com/library/f50a7a13-c6a0-48f1-bee1-e45fa2b2f9b8.aspx)

