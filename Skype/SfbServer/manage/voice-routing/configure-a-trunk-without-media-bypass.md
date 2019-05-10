---
title: "Configure a trunk without media bypass in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "Follow these steps to configure a trunk with media bypass enabled. "
---

# Configure a trunk without media bypass in Skype for Business Server

If you want to configure a trunk with media bypass disabled, follow these steps. If you want to configure a trunk with media bypass enabled, see [Configure a trunk with media bypass in Skype for Business Server](configure-a-trunk-with-media-bypass.md).

A trunk configuration, as described below, groups a set of parameters that are applied to trunks assigned this trunk configuration. A particular trunk configuration can be scoped globally (to all trunks that do not have more specific site or pool configuration), or to a site, or to a pool. The pool-level trunk configuration is used to scope a specific trunk configuration to a single trunk.

**To configure a trunk without media bypass**

1. Open Skype for Busines Server Control Panel.
3. In the left navigation bar, click **Voice Routing**, and then click **Trunk Configuration**.
4. On the **Trunk Configuration** page, use one of the following methods to configure a trunk:
    - Double-click an existing trunk (for example, the **Global** trunk) to display the **Edit Trunk Configuration** dialog box.
    - Click **New**, and then select a scope for the new trunk configuration:
        - **Site trunk**: Choose the site for this trunk configuration in **Select a Site**, and then click **OK**. Note that if a trunk configuration has already been created for a site, the site does not appear in **Select a Site**. This trunk configuration will be applied to all trunks in the site.
        - **Pool trunk**: Choose the name of the trunk that this trunk configuration applies to in **Select a Service** and click **OK**. This trunk can be the root trunk, or any additional trunks defined in Topology Builder. Note that if a trunk configuration has already been created for a specific trunk, the trunk does not appear in **Select a Service**.
    > [!Note] 
    > After you select the scope of the trunk configuration, it cannot be changed. The **Name** field is prepopulated with the name of the trunk configuration’s associated site or service and cannot be changed. 

5. Select one of the following **Encryption support level** options:
    - **Required**: Secure real-time transport protocol (SRTP) encryption must be used to help protect traffic between the Mediation Server and the gateway or private branch exchange (PBX).
    - **Optional**: SRTP encryption will be used if the service provider or equipment manufacturer supports it.
    - **Not Supported**: SRTP encryption is not supported by the service provider or equipment manufacturer and therefore will not be used.
6. Be sure that the **Enable media bypass** check box is cleared.
7. Select the **Centralized media processing** check box if there is a well-known media termination point (for example, a public switched telephone network (PSTN) gateway where the media termination has the same IP as the signaling termination). Clear this check box if the trunk does not have a well-known media termination point.
8. If the trunk peer supports receiving SIP REFER requests from the Mediation Server, select the **Enable sending refer to the gateway** check box.
9. (Optional) To enable inter-trunk routing, associate and configure PSTN usage records to this trunk configuration. The PSTN usages associated to this trunk configuration will be applied for all incoming calls through the trunk that is not originating from a Skype for Business Server endpoint. To manage PSTN usage records associated to a trunk configuration, use one of the following methods:
    - To select one or more records from a list of all PSTN usage records available in your Enterprise Voice deployment, click **Select**. Highlight the records you want to associate with this trunk configuration and then click **OK**.
    - To remove a PSTN usage record from this trunk configuration, select the record and click **Remove**.
    - To define a new PSTN usage record and associate it with this trunk configuration, do the following:
        1. Click **New**.
        2. In the **Name** field, specify a descriptive name for the record that is unique.
            > [!Note] 
            > The PSTN usage record name must be unique within the Enterprise Voice deployment. After the record is saved, the **Name** field cannot be edited. 

        3. Use one of the following methods to associate and configure routes for this PSTN usage record:
            - To select one or more routes from the list of all available routes in your Enterprise Voice deployment, click **Select**. Highlight the routes you want to associate with this PSTN usage record, and click **OK**. 
            - To remove a route from the PSTN usage record, select the route, and click **Remove**.
            - To define a new route and associate it to this PSTN usage record, click **New**. 
            - To edit a route that is associated with this PSTN usage record, select the route, and click **Show details**. 
        4. Click **OK**.
    - To edit a PSTN usage record that is already associated with this trunk configuration, do the following:
        1. Select the PSTN usage record you want to edit, and click **Show details**.
        2. Use one of the following methods to associate and configure routes for this PSTN usage record:
            - To select one or more routes from the list of all available routes in your Enterprise Voice deployment, click **Select**. Highlight the routes you want to associate with this PSTN usage record, and click **OK**. 
            - To remove a route from the PSTN usage record, select the route, and click **Remove**.
            - To define a new route and associate it to this PSTN usage record, click **New**. 
            - To edit a route that is associated with this PSTN usage record, select the route, and click **Show details**. 
        3. Click **OK**.

    > [!Important] 
    > It is important to associate PSTN usage records according to the Mediation Server peer that is associated to the trunk being configured. If the Mediation Server peer is a PSTN gateway or a Session Border Controller (SBC), it is strongly recommended that the trunk configuration is not associated to a PSTN usage record that routes to a PSTN destination or any other downstream systems connected via Skype for Business Server. 

10. Arrange the PSTN usage records for optimum performance. To change a record’s position in the list, select the PSTN usage record, and click the up or down arrows.
    > [!Important] 
    > The order in which PSTN usage records are listed in the trunk configuration is significant. Skype for Business Server traverses the list from top to down. 

11. **Enable RTP Latching** should be selected to enable bypass media for clients behind a NAT or firewall and an SBC that supports latching.
12. **Enable forward call history** should be selected to enable sending of call history information to the gateway peer of the Mediation Server.
13. **Enable forward P-Asserted-Identity data** should be selected to enable PAI call originator information to be forwarded between the Mediation Server side and gateway side (and vice versa), when present.
14. **Enable outbound routing failover timer** should be selected to enable fast failover. The gateway associated with this trunk can give notification within 10 seconds that it is processing an outbound call. Rerouting to another trunk will occur if this notification is not received by the Mediation Server. On networks where latency may delay the response time or the gateway takes longer than 10 seconds to respond, the fast failover should be disabled.
15. (Optional) Associate and **configure calling number translation rules** for the trunk. These translation rules apply to the calling number for outbound calls.
    - To choose one or more rules from a list of all translation rules that are available in your Enterprise Voice deployment, click **Select**. In **Select Translation Rules**, click the rules that you want to associate with the trunk, and then click **OK**.
    - To define a new translation rule and associate it with the trunk, click **New**. For details about defining a new rule, see [Defining translation rules in Skype for Business Server](defining-translation-rules.md).
    - To edit a translation rule that is already associated with the trunk, click the rule name, and then click **Show details**. For details, see [Defining translation rules in Skype for Business Server](defining-translation-rules.md).
    - To copy an existing translation rule to use as a starting point for defining a new rule, click the rule name and click **Copy**, and then click **Paste**. For details, see [Defining translation rules in Skype for Business Server](defining-translation-rules.md).
    - To remove a translation rule from the trunk, highlight the rule name and click **Remove**.

    > [!Warning]
    > Do not associate translation rules with a trunk if you have configured translation rules on the associated trunk peer, because the two rules might conflict. 

16. (Optional) Associate and configure **called number translation rules** for the trunk. The translation rules apply to the called number in an outbound call.
    - To choose one or more rules from a list of all translation rules that are available in your Enterprise Voice deployment, click **Select**. In Select Translation Rules, click the rules that you want to associate with the trunk, and then click **OK**.
    - To define a new translation rule and associate it with the trunk, click **New**. For details about defining a new rule, see [Defining translation rules in Skype for Business Server](defining-translation-rules.md).
    - To edit a translation rule that is already associated with the trunk, click the rule name, and then click **Show details**. For details, see [Defining translation rules in Skype for Business Server](defining-translation-rules.md).
    - To copy an existing translation rule to use as a starting point for defining a new rule, click the rule name and click **Copy**, and then click **Paste**. For details, see [Defining translation rules in Skype for Business Server](defining-translation-rules.md).
    - To remove a translation rule from the trunk, highlight the rule name and click **Remove**.

    > [!Caution] 
    > Do not associate translation rules with a trunk if you have configured translation rules on the associated trunk peer, because the two rules might conflict. 

17. Make sure that the trunk’s translation rules are arranged in the correct order. To change a rule’s position in the list, highlight the rule name, and then click the up or down arrow.

    > [!Important] 
    > Skype for Business Server traverses the translation rule list from the top down and uses the first rule that matches the dialed number. If you configure a trunk so that a dialed number can match more than one translation rule, be sure that the more restrictive rules are sorted above the less restrictive rules. For example, if you have included a translation rule that matches any 11-digit number and a translation rule that matches only 11-digit numbers that start with +1425, be sure that the rule that matches any 11-digit number is sorted below the more restrictive rule. 

18. When you are finished configuring the trunk, click **OK**.
19. On the **Trunk Configuration** page, click **Commit**, and then click **Commit all**. 

    > [!Note]
    > Whenever you create or modify a trunk configuration, you must run the **Commit all** command to publish the configuration change. For details, see Publish pending changes to the voice routing configuration in Lync Server 2013 in the Operations documentation. 
