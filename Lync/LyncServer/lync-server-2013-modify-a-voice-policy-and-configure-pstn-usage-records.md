---
title: 'Lync Server 2013: Modify a voice policy and configure PSTN usage records'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Modify a voice policy and configure PSTN usage records
ms:assetid: 6c53aaf5-218b-4bd4-8cea-31bc9d53f1bd
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398511(v=OCS.15)
ms:contentKeyID: 48184419
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Modify a voice policy and configure PSTN usage records in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-11-01_

Follow these steps if you want to modify a voice policy. If you want to create a new voice policy, see [Create a voice policy and configure PSTN usage records in Lync Server 2013](lync-server-2013-create-a-voice-policy-and-configure-pstn-usage-records.md) for the procedure.

<div>


> [!NOTE]  
> If a user is assigned to a voice policy has no associated public switched telephone network (PSTN) usage records, the user cannot place outbound calls. For a listing of all PSTN usage records available in your Enterprise Voice deployment and view their properties, see <A href="lync-server-2013-view-pstn-usage-records.md">View PSTN usage records in Lync Server 2013</A>.



</div>

<div>

## To modify a voice policy

1.  Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the CsVoiceAdministrator, CsServerAdministrator, or CsAdministrator role. For details, see [Delegate setup permissions in Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Voice Routing**, and then click **Voice Policy**.

4.  On the **Voice Policy** page, double-click a voice policy name.
    
    <div>
    

    > [!NOTE]  
    > The scope and name were set when the voice policy was created. They cannot be changed.

    
    </div>

5.  (Optional) In **Edit Voice Policy**, enter additional descriptive information for the voice policy.

6.  Select or clear the following check boxes to enable or disable each of the **Calling features**:
    
      - **Voice mail escape** prevents calls from being immediately routed to the user’s mobile phone voice mail system when simultaneous ringing is configured and the phone is turned off, out of battery, or out of range.
        
        <div>
        

        > [!NOTE]  
        > This feature is only configurable through the Lync Server Management Shell

        
        </div>
    
      - **Call forwarding** enables users to forward calls to other phones and client devices. Lync Server 2013 provides a significantly wider range of configuration options for call forwarding. For example, if an organization does not want to allow incoming calls to be forwarded externally to the PSTN, an administrator can apply a special voice policy to deploy this restriction. Enabled by default.
    
      - **Delegation** enables users to specify other users to send and receive calls on their behalf. In Lync Server 2013, a delegate can configure simultaneous ringing that enables incoming calls to his or her manager to ring all of the delegate’s simultaneous ringing targets. This provides the delegate with greater flexibility in responding to calls directed to the manager. Enabled by default.
    
      - **Call transfer** enables users to transfer calls to other users. Enabled by default.
    
      - **Call park** enables users to park calls on hold, and then pick up the call from a different phone or client. Disabled by default.
    
      - **Simultaneous ringing** enables incoming calls to ring on additional phones (for example, a mobile phone) or other endpoint devices. Lync Server 2013 provides a significantly wider range of configuration options for simultaneous ringing. Enabled by default.
    
      - **Team call** enables users on a defined team to answer calls for other members of the team. Enabled by default.
    
      - **PSTN re-route** enables calls made by users who are assigned this policy to other enterprise users to be rerouted on the public switched telephone network (PSTN) if the WAN is congested or unavailable. Enabled by default.
    
      - **Bandwidth policy override** enables administrators to override call admission control (CAC) policy decisions for a particular user. Disabled by default.
        
        <div>
        

        > [!NOTE]  
        > The policy will be overridden only for incoming calls to the user and not for outgoing calls that are placed by the user. After the session is established, the bandwidth consumption will be accurately recorded. This setting should be used sparingly.

        
        </div>
    
      - **Malicious call tracing** enables users to report malicious calls (such as bomb threats) using the client UI, which in turn flags the calls in the call detail records (CDRs). Disabled by default.

7.  To associate and configure PSTN usage records for this voice policy, do any of the following:
    
      - To choose one or more records from a list of all PSTN usage records available in your Enterprise Voice deployment, click **Select**. Highlight the records that you want to associate with this voice policy, and then click **OK**.
    
      - To remove a PSTN usage record from this voice policy, highlight the record and click **Remove**.
    
      - To define a new PSTN usage record and associate it with this voice policy, do the following:
        
        1.  Click **New**.
        
        2.  In the **Name** field, enter a unique descriptive name for the record. For example, you may want to create a PSTN usage record named **Redmond** for full-time employees located in Redmond, and another record named **RedmondTemps** for temporary employees.
            
            <div>
            

            > [!NOTE]  
            > The PSTN usage record name must be unique within the Enterprise Voice deployment. After the record is saved, the <STRONG>Name</STRONG> field cannot be edited.

            
            </div>
        
        3.  Use any of the following methods to associate and configure routes for this PSTN usage record:
            
              - To choose one or more routes from the list of all available routes in your Enterprise Voice deployment, click **Select**, highlight the routes that you want to associate with this PSTN usage record, and then click **OK**.
            
              - To remove a route from the PSTN usage record, highlight the route and click **Remove**.
            
              - To define a new route and associate it with this PSTN usage record, click **New**. For details, see [Create a voice route in Lync Server 2013](lync-server-2013-create-a-voice-route.md).
            
              - To edit a route that is already associated with this PSTN usage record, highlight the route and click **Show details**. For details, see [Modify a voice route in Lync Server 2013](lync-server-2013-modify-a-voice-route.md).
        
        4.  Click **OK**.
    
      - To edit a PSTN usage record that is already associated with this voice policy, do the following:
        
        1.  Highlight the PSTN usage record that you want to edit and click **Show details**.
        
        2.  Use any of the following methods to associate and configure routes for this PSTN usage record:
            
              - To choose one or more routes from the list of all available routes in your Enterprise Voice deployment, click **Select**, highlight the routes that you want to associate with this PSTN usage record, and then click **OK**.
            
              - To remove a route from this PSTN usage record, highlight the route and click **Remove**.
            
              - To define a new route and associate it with this PSTN usage record, click **New**. For details, see [Create a voice route in Lync Server 2013](lync-server-2013-create-a-voice-route.md).
            
              - To edit a route that is already associated with this PSTN usage record, highlight the route and click **Show details**. For details, see [Modify a voice route in Lync Server 2013](lync-server-2013-modify-a-voice-route.md).
        
        3.  Click **OK**.

8.  Arrange the PSTN usage records for optimum performance. To change a record’s position in the list, highlight the record name and click the up or down arrow.
    
    <div>
    

    > [!NOTE]  
    > The order in which PSTN usage records are listed in the voice policy is significant. Lync Server traverses the list from the top down. We recommend that you organize the list by frequency of use, for example: RedmondLocal, RedmondLongDist, RedmondInternational, RedmondBackup.

    
    </div>

9.  To associate and configure PSTN usage records for call forwarding and simultaneous ringing in this voice policy, do any of the following:
    
      - To use the same PSTN usage records for call forwarding and simultaneous ringing as this voice policy, select the option **Route using the call PSTN usages** from the drop-down menu.
    
      - To allow call forwarding and simultaneous ringing to internal Lync users only, select **Route to internal Lync users only** from the drop-down menu. Calls will not be forwarded to external PSTN numbers.
    
      - To specify different PSTN usage records for call forwarding and simultaneous ringing than those used for this voice policy, select the option **Route using custom PSTN usages** from the drop-down menu. This option displays a control to select existing PSTN usage records or to create new PSTN usage records, specifically for call forwarding and simultaneous ringing.
        
          - To choose one or more records from a list of PSTN usage records for call forwarding and simultaneous ringing, click **Select**. Highlight the records that you want to associate with this call forwarding and simultaneous ringing policy, and then click **OK**.
        
          - To remove a PSTN usage record from this call forwarding and simultaneous ringing policy, highlight the record and click **Remove**.
        
          - To define a new PSTN usage record and associate it with this call forwarding and simultaneous ringing policy, do the following:
            
            1.  Click **New**.
            
            2.  In the **Name** field, enter a unique descriptive name for the record.
                
                <div>
                

                > [!NOTE]  
                > The PSTN usage record name must be unique within the Enterprise Voice deployment. After the record is saved, the <STRONG>Name</STRONG> field cannot be edited.

                
                </div>
            
            3.  Use any of the following methods to associate and configure routes for this PSTN usage record:
                
                  - To choose one or more routes from the list of all available routes in your Enterprise Voice deployment, click **Select**, highlight the routes that you want to associate with this PSTN usage record, and then click **OK**.
                
                  - To remove a route from the PSTN usage record, highlight the route and click **Remove**.
                
                  - To define a new route and associate it with this PSTN usage record, click **New**. For details, see [Create a voice route in Lync Server 2013](lync-server-2013-create-a-voice-route.md).
                
                  - To edit a route that is already associated with this PSTN usage record, highlight the route, and then click **Show details**. For details, see [Modify a voice route in Lync Server 2013](lync-server-2013-modify-a-voice-route.md).
            
            4.  Click **OK**.
        
          - To edit a PSTN usage record that is already associated with this voice policy, do the following:
            
            1.  Highlight the PSTN usage record that you want to edit and click **Show details**.
            
            2.  Use any of the following methods to associate and configure routes for this PSTN usage record:
                
                  - To choose one or more routes from the list of all available routes in your Enterprise Voice deployment, click **Select**, highlight the routes you want to associate with this PSTN usage record, and then click **OK**.
                
                  - To remove a route from this PSTN usage record, highlight the route and click **Remove**.
                
                  - To define a new route and associate it with this PSTN usage record, click **New**. For details, see [Create a voice route in Lync Server 2013](lync-server-2013-create-a-voice-route.md).
                
                  - To edit a route that is already associated with this PSTN usage record, highlight the route and click **Show details**. For details, see [Modify a voice route in Lync Server 2013](lync-server-2013-modify-a-voice-route.md).
            
            3.  Click **OK**.

10. (Optional) Enter a number to test the voice policy and click **Go**. The test results are displayed under **Translated number to test**.
    
    <div>
    

    > [!NOTE]  
    > You can save a voice policy that does not yet pass the test and then reconfigure it later. For details, see <A href="lync-server-2013-test-voice-routing.md">Test voice routing in Lync Server 2013</A>.

    
    </div>

11. Click **OK**.

12. On the **Voice Policy** page, click **Commit**, and then click **Commit all**.
    
    <div>
    

    > [!NOTE]  
    > Whenever you create or modify a voice policy, you must run the <STRONG>Commit all</STRONG> command to publish the configuration change. For details, see <A href="lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md">Publish pending changes to the voice routing configuration in Lync Server 2013</A> in the Operations documentation.

    
    </div>

13. (Optional) Voicemail Escape detects that a call was immediately answered by the user’s mobile phone voice mail, and disconnects the call to the mobile phone voice mail. This allows the call to continue to ring on the user’s other endpoints giving the user the opportunity to answer the call. For details about how to configure a voice mail policy, see [Configuring voice mail escape in Lync Server 2013](lync-server-2013-configuring-voice-mail-escape.md).

</div>

<div>

## See Also


[Create a voice policy and configure PSTN usage records in Lync Server 2013](lync-server-2013-create-a-voice-policy-and-configure-pstn-usage-records.md)  
[View PSTN usage records in Lync Server 2013](lync-server-2013-view-pstn-usage-records.md)  
[Create a voice route in Lync Server 2013](lync-server-2013-create-a-voice-route.md)  
[Modify a voice route in Lync Server 2013](lync-server-2013-modify-a-voice-route.md)  
[Publish pending changes to the voice routing configuration in Lync Server 2013](lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md)  
[Configuring voice mail escape in Lync Server 2013](lync-server-2013-configuring-voice-mail-escape.md)  


[Test voice routing in Lync Server 2013](lync-server-2013-test-voice-routing.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

