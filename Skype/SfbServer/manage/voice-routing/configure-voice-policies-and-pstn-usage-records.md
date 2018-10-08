---
title: "Configure voice policies and configure PSTN usage records in Skype for Business Server"
ms.author: jambirk
author: jambirk
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "."
---

# Configure voice policies and configure PSTN usage records in Skype for Business Server

Voice policies, PSTN usage records, and voice routes are integrally related. You configure voice policies by selecting a set of calling features and then assigning the policy a set of PSTN usage records, which specify what rights are authorized for the users or groups who are assigned the voice policy. Voice routes are also assigned PSTN usage records, which serve to match routes with the users who are authorized to use them. That is, users can only place calls that use the routes for which they have a matching PSTN usage record.

The recommended workflow for a new Enterprise Voice deployment is to start by configuring a voice policy that includes the appropriate PSTN usage records, and then associate the appropriate routes to each PSTN usage record. 

A voice policy enables a set of calling features and associates one or more PSTN usage records to define the calling features and permissions of users who are assigned the policy.

Voice policy scope can be either Site (which defines the default features and permissions for a network site) or User (which defines the features and permissions to be assigned on a per-user or group basis). Users not assigned to a voice policy will automatically be assigned to the global policy, which is the default voice policy that is installed with the product.

Follow these steps if you want to create a new voice policy or edit an existing voice policy.

> [!Note]
> Each voice policy must have at least one associated public switched telephone network (PSTN) usage record. If a user is assigned to a voice policy has no associated public switched telephone network (PSTN) usage records, the user cannot place outbound calls. To see a listing of all PSTN usage records available in your Enterprise Voice deployment and view their properties, see [View PSTN usage records](ADD LINK).  

**To create or modify a voice policy**

1. Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the CsVoiceAdministrator, CsServerAdministrator, or CsAdministrator role. For details, see [Delegate setup permissions](https://docs.microsoft.com/en-us/lyncserver/lync-server-2013-delegate-setup-permissions).
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start the Skype for Business Server Control Panel, see [Install and open administrative tools](../../management-tools/install-and-open-administrative-tools.md).
3. In the left navigation bar, click **Voice Routing**, and then click **Voice Policy**.
4. On the **Voice Policy** page, do one of the following:
    - To create a new voice policy: 
        1. Click **New**, and then select a scope for the new policy:
            - Site policy applies to an entire site, except any users or groups that are assigned to a user policy. If you select Site for a policy scope, choose the site from the Select a Site dialog box. If a voice policy has already been created for a site, the site does not appear in the Select a Site dialog box.
            - User policy can be applied to specified users or groups.

            > [!Note] 
            > If the voice policy scope is User, enter a descriptive name for the policy in the Name field.
        2. If the voice policy scope is User, enter a descriptive name for the policy in the **Name** field.
    
        > [!NOTE]
        > If the voice policy scope is Site, the **Name** field in **New Voice Policy** is prepopulated with the site name and cannot be changed.  

        3. (Optional) Enter additional descriptive information for the voice policy.

    - To modify an existing voice policy:
        1. Double-click a voice policy name.
        
        > [!Note]
        > The scope and name were set when the voice policy was created. They cannot be changed. 

        2.  (Optional) In **Edit Voice Policy**, enter additional descriptive information for the voice policy.

5. Select or clear the following check boxes to enable or disable each of the **Calling features**:
    - Voice mail escape prevents calls from being immediately routed to the user’s mobile phone voice mail system when simultaneous ringing is configured and the phone is turned off, out of battery, or out of range.

    > [!Note]
    > This feature is only configurable through the Skype for Business Server Management Shell.

    - **Call forwarding** enables users to forward calls to other phones and client devices. Skype for Business Server provides a significantly wider range of configuration options for call forwarding. For example, if an organization does not want to allow incoming calls to be forwarded externally to the PSTN, an administrator can apply a special voice policy to deploy this restriction. Enabled by default.
    - **Delegation** enables users to specify other users to send and receive calls on their behalf. In Skype for Business Server, a delegate can configure simultaneous ringing that enables incoming calls to his or her manager to ring all of the delegate’s simultaneous ringing targets. This provides the delegate with greater flexibility in responding to calls directed to the manager. Enabled by default.
    - **Call transfer** enables users to transfer calls to other users. Enabled by default.
    - **Call park** enables users to park calls on hold and then pick up the call from a different phone or client. Disabled by default.
    - **Simultaneous ringing** enables incoming calls to ring on additional phones (for example, a mobile phone) or other endpoint devices. Skype for Business Server provides a significantly wider range of configuration options for simultaneous ringing. Enabled by default.
    - **Team call** enables users on a defined team to answer calls for other members of the team. Enabled by default.
    - **PSTN re-route** enables calls made by users who are assigned this policy to other enterprise users to be rerouted on the public switched telephone network (PSTN) if the WAN is congested or unavailable. Enabled by default.
    - **Bandwidth policy override** enables administrators to override call admission control policy decisions for a particular user. Disabled by default.

        > [!Note] 
        > The policy will be overridden only for incoming calls to the user and not for outgoing calls that are placed by the user. After the session is established, the bandwidth consumption will be accurately recorded. This setting should be used sparingly and should be reserved for appropriate call admission control decisions. 

    - **Malicious call tracing** enables users to report malicious calls (such as bomb threats) by using the client UI, which in turn flags the calls in the call detail records (CDRs). Disabled by default.

6. To associate and configure PSTN usage records for this voice policy, do any of the following:

    - To choose one or more records from a list of all PSTN usage records available in your Enterprise Voice deployment, click **Select**. Highlight the records that you want to associate with this voice policy, and then click **OK**.
    - To remove a PSTN usage record from this voice policy, highlight the record and click **Remove**.
    - To define a new PSTN usage record and associate it with this voice policy, do the following:

        1. Click **New**. 
        2. In the **Name** field, enter a unique descriptive name for the record. For example, you may want to create a PSTN usage record named Redmond for full-time employees located in **Redmond**, and another named **RedmondTemps** for temporary employees.

            > [!Note] 
            > The PSTN usage record name must be unique within the Enterprise Voice deployment. After the record is saved, the **Name** field cannot be edited.

        3. Use any of the following methods to associate and configure routes for this PSTN usage record:

            - To choose one or more routes from the list of all available routes in your Enterprise Voice deployment, click **Select**, highlight the routes that you want to associate with this PSTN usage record, and then click **O**K.
            - To remove a route from the PSTN usage record, highlight the route, and then click **Remove**.
            - To define a new route and associate it with this PSTN usage record, click **New**. For details, see [Configuring boice routes for outboudn calls](ADD LINK).
            - To edit a route that is already associated with this PSTN usage record, highlight the route and click **Show details**. For details, see [Configuring boice routes for outboudn calls](ADD LINK).

        4. Click **OK**.

    - To edit a PSTN usage record that is already associated with this voice policy, do the following:

       1. Highlight the PSTN usage record that you want to edit, and then click **Show details**.
       2. Use any of the following methods to associate and configure routes for this PSTN usage record:

            - To choose one or more routes from the list of all available routes in your Enterprise Voice deployment, click **Select**, highlight the routes you want to associate with this PSTN usage record, and then click **OK**.
            - To remove a route from this PSTN usage record, highlight the route, and then click **Remove**.
            - To define a new route and associate it with this PSTN usage record, click **New**. For details, see [Configuring boice routes for outboudn calls](ADD LINK).
            - To edit a route that is already associated with this PSTN usage record, highlight the route and lick Show details. For details, see [Configuring boice routes for outboudn calls](ADD LINK).
        3. Click **OK**.

7. Arrange the PSTN usage records for optimum performance. To change a record’s position in the list, highlight the record name and click the up or down arrow.

    > [!Note]
    > The order in which PSTN usage records are listed in the voice policy is significant. Skype for Business Server traverses the list from the top down. We recommend that you organize the list by frequency of use, for example: RedmondLocal, RedmondLongDist, RedmondInternational, RedmondBackup. 

8. To associate and configure PSTN usage records for call forwarding and simultaneous ringing in this voice policy, do any of the following:

    - To use the same PSTN usage records for call forwarding and simultaneous ringing as this voice policy, select the option **Route using the call PSTN usages** from the drop-down menu.
    - To allow call forwarding and simultaneous ringing to internal Skype for Business users only, select **Route to internal Skype for Business users only** from the drop-down menu. Calls will not be forwarded to external PSTN numbers.
    - To specify different PSTN usage records for call forwarding and simultaneous ringing than those used for this voice policy, select the option **Route using custom PSTN usages** from the drop-down menu. This option displays a control to select existing PSTN usage records or to create new PSTN usage records, specifically for call forwarding and simultaneous ringing.
        - To choose one or more records from a list of PSTN usage records for call forwarding and simultaneous ringing, click **Select**. Highlight the records that you want to associate with this call forwarding and simultaneous ringing policy, and then click **OK**.
        - To remove a PSTN usage record from this call forwarding and simultaneous ringing policy, highlight the record and click **Remove**.
        - To define a new PSTN usage record and associate it with this call forwarding and simultaneous ringing policy, do the following:
            1. Click **New**.
            2. In the **Name** field, enter a unique descriptive name for the record.
                > [!Note] 
                > The PSTN usage record name must be unique within the Enterprise Voice deployment. After the record is saved, the **Name** field cannot be edited. 
            3. Use any of the following methods to associate and configure routes for this PSTN usage record:
    
                - To choose one or more routes from the list of all available routes in your Enterprise Voice deployment, click **Select**, highlight the routes that you want to associate with this PSTN usage record, and then click **O**K.
                - To remove a route from the PSTN usage record, highlight the route and click Remove.
                - To define a new route and associate it with this PSTN usage record, click **New**. For details, see [Configuring boice routes for outboudn calls](ADD LINK).
                - To edit a route that is already associated with this PSTN usage record, highlight the route and click **Show details**. For details, see [Configuring boice routes for outboudn calls](ADD LINK).
            4. Click **OK**. 
        
        - To edit a PSTN usage record that is already associated with this voice policy, do the following:

            1. Highlight the PSTN usage record you want to edit and click **Show details**.
            2. Use any of the following methods to associate and configure routes for this PSTN usage record:

                - To choose one or more routes from the list of all available routes in your Enterprise Voice deployment, click **Select**, highlight the routes that you want to associate with this PSTN usage record, and then click **OK**.
                - To remove a route from this PSTN usage record, highlight the route and click **Remove**.
                - To define a new route and associate it with this PSTN usage record, click **New**. For details, see [Configuring boice routes for outboudn calls](ADD LINK).
                - To edit a route that is already associated with this PSTN usage record, highlight the route and click **Show details**. For details, see [Configuring boice routes for outboudn calls](ADD LINK).

            3. Click **OK**. 
9. (Optional) Enter a number to test the voice policy and click **Go**. The test results are displayed under Translated number to test.

    > [!Note]
    > You can save a voice policy that does not yet pass the test and then reconfigure it later. 

10. Click **OK**.
11. On the **Voice Policy** page, click **Commit**, and then click **Commit all**. 

    > [!Note]
    > Any time you create or modify a voice policy, you must run the **Commit all** command to publish the configuration change. For details, see [Publish pending changes to the voice routing configuration in Lync Server 2013](NEW LINK?). 

12. (Optional) Voicemail Escape detects that a call was immediately answered by the user’s mobile phone voice mail, and disconnects the call to the mobile phone voice mail. This allows the call to continue to ring on the user’s other endpoints giving the user the opportunity to answer the call. For details on how to configure a voice mail policy, see [Configuring voice mail escape](ADD LINK).