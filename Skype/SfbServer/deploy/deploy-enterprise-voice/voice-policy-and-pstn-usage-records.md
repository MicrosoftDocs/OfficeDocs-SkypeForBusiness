---
title: "Create or modify a voice policy and configure PSTN usage records in Skype for Business"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection:
- IT_Skype16
- Strat_SB_Admin
ms.custom:
ms.assetid: e6ff27e0-e2d1-4445-840f-08f738200c20
description: "Summary: Create or modify voice policies and configure PSTN usage records by using the Skype for Business Server Control Panel."
---

# Create or modify a voice policy and configure PSTN usage records in Skype for Business

**Summary:** Create or modify voice policies and configure PSTN usage records by using the Skype for Business Server Control Panel.

> [!NOTE]
> Each voice policy must have at least one associated Public Switched Telephone Network (PSTN) usage record. To see a listing of all PSTN usage records available in your Enterprise Voice deployment and view their properties, see [View PSTN usage records in Skype for Business](view-pstn-usage-records.md).

### To create a voice policy

1. Open Skype for Business Server Control Panel.

2. In the left navigation bar, click **Voice Routing** and then click **Voice Policy**.

3. On the **Voice Policy** page, click **New** and then select a scope for the new policy:

   - **Site policy** applies to an entire site, except any users or groups that are assigned to a user policy. If you select Site for a policy scope, choose the site from the **Select a Site** dialog box. If a voice policy has already been created for a site, the site does not appear in the **Select a Site** dialog box.

   - **User policy** can be applied to specified users or groups.

4. If the voice policy scope is User, enter a descriptive name for the policy in the **Name** field.

    > [!NOTE]
    > If the voice policy scope is Site, the **Name** field in **New Voice Policy** is prepopulated with the site name and cannot be changed.

5. (Optional) Enter additional descriptive information for the voice policy.

6. Select or clear the following check boxes to enable or disable each of the **Calling features** for this voice policy:

   - **Voice mail escape** prevents calls from being immediately routed to the user's mobile phone voice mail system when simultaneous ringing is configured and the phone is turned off, out of battery, or out of range.

     > [!NOTE]
     > This feature is only configurable through the Skype for Business Server Management Shell

   - **Call forwarding** enables users to forward calls to other phones and client devices. Skype for Business Server provides a significantly wider range of configuration options for call forwarding. For example, if an organization does not want to allow incoming calls to be forwarded externally to the PSTN, an administrator can apply a special voice policy to deploy this restriction. Enabled by default.

   - **Delegation** enables users to specify other users to send and receive calls on their behalf. In Skype for Business Server, a delegate can configure simultaneous ringing that enables incoming calls to his or her manager to ring all of the delegate's simultaneous ringing targets. This provides the delegate with greater flexibility in responding to calls directed to the manager. Enabled by default.

   - **Call transfer** enables users to transfer calls to other users. Enabled by default.

   - **Call park** enables users to park calls on hold and then pick up the call from a different phone or client. Disabled by default.

   - **Simultaneous ringing** enables incoming calls to ring on additional phones (for example, a mobile phone) or other endpoint devices. Skype for Business Server provides a significantly wider range of configuration options for simultaneous ringing. Enabled by default.

   - **Team call** enables users on a defined team to answer calls for other members of the team. Enabled by default.

   - **PSTN re-route** enables calls made by users who are assigned this policy to other enterprise users to be rerouted on the PSTN if the WAN is congested or unavailable. Enabled by default.

   - **Bandwidth policy override** enables administrators to override call admission control policy decisions for a particular user. Disabled by default.

     > [!NOTE]
     > The policy will be overridden only for incoming calls to the user and not for outgoing calls that are placed by the user. After the session is established, the bandwidth consumption will be accurately recorded. This setting should be used sparingly and should be reserved for appropriate call admission control decisions.

   - **Malicious call tracing** enables users to report malicious calls (such as threats) by using the client UI, which in turn flags the calls in the Call Detail Records (CDRs). Disabled by default.

   - **Busy options** enables or disables Busy Options for the specified voice policy. Busy Options allows incoming calls to be routed to voice mail or rejected with a busy signal when the call's target user is on the phone. Busy Options is a new voice policy introduced in the July 2016 Cumulative Update. Checking this parameter enables Busy Options, and unchecking it disables Busy Options. For more information, see [Plan for Busy Options for Skype for Business Server](../../plan-your-deployment/enterprise-voice-solution/busy-options.md) and [Install and configure Busy Options for Skype for Business Server](install-and-configure-busy-options.md).

7. To associate and configure PSTN usage records for this voice policy, do any of the following:

   - To choose one or more records from a list of all PSTN usage records available in your Enterprise Voice deployment, click **Select**. Highlight the records that you want to associate with this voice policy, and then click **OK**.

   - To remove a PSTN usage record from this voice policy, highlight the record and click **Remove**.

   - To define a new PSTN usage record and associate it with this voice policy, do the following:

     a. Click **New**.

     b. In the **Name** field, enter a unique descriptive name for the record. For example, you may want to create a PSTN usage record namedRedmond for full-time employees located in Redmond, and another namedRedmondTemps for temporary employees.

     > [!NOTE]
     > The PSTN usage record name must be unique within the Enterprise Voice deployment. After the record is saved, the **Name** field cannot be edited.

     c. Use any of the following methods to associate and configure routes for this PSTN usage record:

   - To choose one or more routes from the list of all available routes in your Enterprise Voice deployment, click **Select**, highlight the routes that you want to associate with this PSTN usage record, and then click **OK**.

   - To remove a route from the PSTN usage record, highlight the route, and then click **Remove**.

   - To define a new route and associate it with this PSTN usage record, click **New**. For details, see [Create or modify a voice route in Skype for Business](create-or-modify-a-voice-route.md).

   - To edit a route that is already associated with this PSTN usage record, highlight the route and click **Show details**.

     d. Click **OK**.

   - To edit a PSTN usage record that is already associated with this voice policy, do the following:

     a. Highlight the PSTN usage record that you want to edit, and then click **Show details**.

     b. Use any of the following methods to associate and configure routes for this PSTN usage record:

   - To choose one or more routes from the list of all available routes in your Enterprise Voice deployment, click **Select**, highlight the routes you want to associate with this PSTN usage record, and then click **OK**.

   - To remove a route from this PSTN usage record, highlight the route, and then click **Remove**.

   - To define a new route and associate it with this PSTN usage record, click **New**. For details, see [Create or modify a voice route in Skype for Business](create-or-modify-a-voice-route.md).

   - To edit a route that is already associated with this PSTN usage record, highlight the route and lick **Show details**.

     c. Click **OK**.

8. Arrange the PSTN usage records for optimum performance. To change a record's position in the list, highlight the record name and click the up or down arrow.

    > [!IMPORTANT]
    > The order in which PSTN usage records are listed in the voice policy is significant. Skype for Business Server traverses the list from the top down. We recommend that you organize the list by frequency of use, for example: RedmondLocal, RedmondLongDist, RedmondInternational, RedmondBackup.

9. To associate and configure PSTN usage records for call forwarding and simultaneous ringing in this voice policy, do any of the following:

   - To use the same PSTN usage records for call forwarding and simultaneous ringing as this voice policy, select the option **Route using the call PSTN usages** from the drop-down menu.

   - To allow call forwarding and simultaneous ringing to internal Skype for Business users only, select the option **Route to internal Skype for Business users only** from the drop-down menu. Calls will not be forwarded to external PSTN numbers.

   - To specify different PSTN usage records for call forwarding and simultaneous ringing than used for this voice policy, select the option **Route using custom PSTN usages** from the drop-down menu. This option displays a control to select existing PSTN usage records or create new PSTN usage records specifically for call forwarding and simultaneous ringing.

   - To choose one or more records from a list of PSTN usage records for call forwarding and simultaneous ringing, click **Select**. Highlight the records that you want to associate with this call forwarding and simultaneous ringing policy, and then click **OK**.

   - To remove a PSTN usage record from this call forwarding and simultaneous ringing policy, highlight the record and click **Remove**.

   - To define a new PSTN usage record and associate it with this call forwarding and simultaneous ringing policy, do the following:

     a. Click **New**.

     b. In the **Name** field, enter a unique descriptive name for the record.

     > [!NOTE]
     > The PSTN usage record name must be unique within the Enterprise Voice deployment. After the record is saved, the **Name** field cannot be edited.

     c. Use any of the following methods to associate and configure routes for this PSTN usage record:

   - To choose one or more routes from the list of all available routes in your Enterprise Voice deployment, click **Select**, highlight the routes that you want to associate with this PSTN usage record, and then click **OK**.

   - To remove a route from the PSTN usage record, highlight the route and click **Remove**.

   - To define a new route and associate it with this PSTN usage record, click **New**. For details, see [Create or modify a voice route in Skype for Business](create-or-modify-a-voice-route.md).

   - To edit a route that is already associated with this PSTN usage record, highlight the route and click **Show details**.

     d. Click **OK**.

   - To edit a PSTN usage record that is already associated with this voice policy, do the following:

     a. Highlight the PSTN usage record you want to edit and click **Show details**.

     b. Use any of the following methods to associate and configure routes for this PSTN usage record:

   - To choose one or more routes from the list of all available routes in your Enterprise Voice deployment, click **Select**, highlight the routes that you want to associate with this PSTN usage record, and then click **OK**.

   - To remove a route from this PSTN usage record, highlight the route and click **Remove**.

   - To define a new route and associate it with this PSTN usage record, click **New**. For details, see [Create or modify a voice route in Skype for Business](create-or-modify-a-voice-route.md).

   - To edit a route that is already associated with this PSTN usage record, highlight the route and click **Show details**.

     c. Click **OK**.

10. (Optional) Enter a number to test the voice policy and click **Go**. The test results are displayed under **Translated number to test**.

11. Click **OK**.

12. On the **Voice Policy** page, click **Commit**, and then click **Commit all**.

    > [!NOTE]
    > Any time you create or modify a voice policy, you must run the **Commit all** command to publish the configuration change. For details, see [Publish pending changes to the voice routing configuration in Skype for Business](voice-route-config-changes.md) in the Operations documentation.

13. (Optional) Voicemail Escape detects that a call was immediately answered by the user's mobile phone voice mail, and disconnects the call to the mobile phone voice mail. This allows the call to continue to ring on the user's other endpoints giving the user the opportunity to answer the call. For details on how to configure a voice mail policy, see [Configure voice mail escape in Skype for Business](configure-voice-mail-escape.md).

### To modify a voice policy

1. Open Skype for Business Server Control Panel.

2. In the left navigation bar, click **Voice Routing**, and then click **Voice Policy**.

3. On the **Voice Policy** page, double-click a voice policy name.

    > [!NOTE]
    > The scope and name were set when the voice policy was created. They cannot be changed.

4. (Optional) In **Edit Voice Policy**, enter additional descriptive information for the voice policy.

5. Select or clear the following check boxes to enable or disable each of the **Calling features**:

   - **Voice mail escape** prevents calls from being immediately routed to the user's mobile phone voice mail system when simultaneous ringing is configured and the phone is turned off, out of battery, or out of range.

     > [!NOTE]
     > This feature is only configurable through the Skype for Business Server Management Shell

   - **Call forwarding** enables users to forward calls to other phones and client devices. Skype for Business Server provides a significantly wider range of configuration options for call forwarding. For example, if an organization does not want to allow incoming calls to be forwarded externally to the PSTN, an administrator can apply a special voice policy to deploy this restriction. Enabled by default.

   - **Delegation** enables users to specify other users to send and receive calls on their behalf. In Skype for Business Server, a delegate can configure simultaneous ringing that enables incoming calls to his or her manager to ring all of the delegate's simultaneous ringing targets. This provides the delegate with greater flexibility in responding to calls directed to the manager. Enabled by default.

   - **Call transfer** enables users to transfer calls to other users. Enabled by default.

   - **Call park** enables users to park calls on hold, and then pick up the call from a different phone or client. Disabled by default.

   - **Simultaneous ringing** enables incoming calls to ring on additional phones (for example, a mobile phone) or other endpoint devices. Skype for Business Server provides a significantly wider range of configuration options for simultaneous ringing. Enabled by default.

   - **Team call** enables users on a defined team to answer calls for other members of the team. Enabled by default.

   - **PSTN re-route** enables calls made by users who are assigned this policy to other enterprise users to be rerouted on the PSTN if the WAN is congested or unavailable. Enabled by default.

   - **Bandwidth policy override** enables administrators to override CAC policy decisions for a particular user. Disabled by default.

     > [!NOTE]
     > The policy will be overridden only for incoming calls to the user and not for outgoing calls that are placed by the user. After the session is established, the bandwidth consumption will be accurately recorded. This setting should be used sparingly.

   - **Malicious call tracing** enables users to report malicious calls (such as threats) using the client UI, which in turn flags the calls in the CDRs. Disabled by default.

6. To associate and configure PSTN usage records for this voice policy, do any of the following:

   - To choose one or more records from a list of all PSTN usage records available in your Enterprise Voice deployment, click **Select**. Highlight the records that you want to associate with this voice policy, and then click **OK**.

   - To remove a PSTN usage record from this voice policy, highlight the record and click **Remove**.

   - To define a new PSTN usage record and associate it with this voice policy, do the following:

     a. Click **New**.

     b. In the **Name** field, enter a unique descriptive name for the record. For example, you may want to create a PSTN usage record namedRedmond for full-time employees located in Redmond, and another record namedRedmondTemps for temporary employees.

     > [!NOTE]
     > The PSTN usage record name must be unique within the Enterprise Voice deployment. After the record is saved, the **Name** field cannot be edited.

     c. Use any of the following methods to associate and configure routes for this PSTN usage record:

   - To choose one or more routes from the list of all available routes in your Enterprise Voice deployment, click **Select**, highlight the routes that you want to associate with this PSTN usage record, and then click **OK**.

   - To remove a route from the PSTN usage record, highlight the route and click **Remove**.

   - To define a new route and associate it with this PSTN usage record, click **New**. For details, see [Create or modify a voice route in Skype for Business](create-or-modify-a-voice-route.md).

   - To edit a route that is already associated with this PSTN usage record, highlight the route and click **Show details**.

     d. Click **OK**.

   - To edit a PSTN usage record that is already associated with this voice policy, do the following:

     a. Highlight the PSTN usage record that you want to edit and click **Show details**.

     b. Use any of the following methods to associate and configure routes for this PSTN usage record:

   - To choose one or more routes from the list of all available routes in your Enterprise Voice deployment, click **Select**, highlight the routes that you want to associate with this PSTN usage record, and then click **OK**.

   - To remove a route from this PSTN usage record, highlight the route and click **Remove**.

   - To define a new route and associate it with this PSTN usage record, click **New**. For details, see [Create or modify a voice route in Skype for Business](create-or-modify-a-voice-route.md).

   - To edit a route that is already associated with this PSTN usage record, highlight the route and click **Show details**.

     c. Click **OK**.

7. Arrange the PSTN usage records for optimum performance. To change a record's position in the list, highlight the record name and click the up or down arrow.

    > [!NOTE]
    > The order in which PSTN usage records are listed in the voice policy is significant. Skype for Business Server traverses the list from the top down. We recommend that you organize the list by frequency of use, for example: RedmondLocal, RedmondLongDist, RedmondInternational, RedmondBackup.

8. To associate and configure PSTN usage records for call forwarding and simultaneous ringing in this voice policy, do any of the following:

   - To use the same PSTN usage records for call forwarding and simultaneous ringing as this voice policy, select the option **Route using the call PSTN usages** from the drop-down menu.

   - To allow call forwarding and simultaneous ringing to internal Skype for Business users only, select **Route to internal Skype for Business users only** from the drop-down menu. Calls will not be forwarded to external PSTN numbers.

   - To specify different PSTN usage records for call forwarding and simultaneous ringing than those used for this voice policy, select the option **Route using custom PSTN usages** from the drop-down menu. This option displays a control to select existing PSTN usage records or to create new PSTN usage records, specifically for call forwarding and simultaneous ringing.

   - To choose one or more records from a list of PSTN usage records for call forwarding and simultaneous ringing, click **Select**. Highlight the records that you want to associate with this call forwarding and simultaneous ringing policy, and then click **OK**.

   - To remove a PSTN usage record from this call forwarding and simultaneous ringing policy, highlight the record and click **Remove**.

   - To define a new PSTN usage record and associate it with this call forwarding and simultaneous ringing policy, do the following:

     a. Click **New**.

     b. In the **Name** field, enter a unique descriptive name for the record.

     > [!NOTE]
     > The PSTN usage record name must be unique within the Enterprise Voice deployment. After the record is saved, the **Name** field cannot be edited.

     c. Use any of the following methods to associate and configure routes for this PSTN usage record:

   - To choose one or more routes from the list of all available routes in your Enterprise Voice deployment, click **Select**, highlight the routes that you want to associate with this PSTN usage record, and then click **OK**.

   - To remove a route from the PSTN usage record, highlight the route and click **Remove**.

   - To define a new route and associate it with this PSTN usage record, click **New**. For details, see [Create or modify a voice route in Skype for Business](create-or-modify-a-voice-route.md).

   - To edit a route that is already associated with this PSTN usage record, highlight the route, and then click **Show details**. For details, see [Modify a Voice Route](https://technet.microsoft.com/library/afc562cc-8807-489b-8850-dbbe1c1ab9f5.aspx).

     d. Click **OK**.

   - To edit a PSTN usage record that is already associated with this voice policy, do the following:

     a. Highlight the PSTN usage record that you want to edit and click **Show details**.

     b. Use any of the following methods to associate and configure routes for this PSTN usage record:

     - To choose one or more routes from the list of all available routes in your Enterprise Voice deployment, click **Select**, highlight the routes you want to associate with this PSTN usage record, and then click **OK**.

     - To remove a route from this PSTN usage record, highlight the route and click **Remove**.

     - To define a new route and associate it with this PSTN usage record, click **New**. For details, see [Create or modify a voice route in Skype for Business](create-or-modify-a-voice-route.md).

     - To edit a route that is already associated with this PSTN usage record, highlight the route and click **Show details**. For details, see [Modify a Voice Route](https://technet.microsoft.com/library/afc562cc-8807-489b-8850-dbbe1c1ab9f5.aspx).

     c. Click **OK**.

9. (Optional) Enter a number to test the voice policy and click **Go**. The test results are displayed under **Translated number to test**.

10. Click **OK**.

11. On the **Voice Policy** page, click **Commit**, and then click **Commit all**.

    > [!NOTE]
    > Whenever you create or modify a voice policy, you must run the **Commit all** command to publish the configuration change. For details, see [Publish pending changes to the voice routing configuration in Skype for Business](voice-route-config-changes.md) in the Operations documentation.

12. (Optional) Voicemail Escape detects that a call was immediately answered by the user's mobile phone voice mail, and disconnects the call to the mobile phone voice mail. This allows the call to continue to ring on the user's other endpoints giving the user the opportunity to answer the call. For details about how to configure a voice mail policy, see [Configure voice mail escape in Skype for Business](configure-voice-mail-escape.md).

## See also

[View PSTN usage records in Skype for Business](view-pstn-usage-records.md)

[Create or modify a voice route in Skype for Business](create-or-modify-a-voice-route.md)

[Publish pending changes to the voice routing configuration in Skype for Business](voice-route-config-changes.md)

[Configure voice mail escape in Skype for Business](configure-voice-mail-escape.md)

