---
title: Configure User Profile
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Configure User Profile
ms:assetid: 52713245-e502-4539-a238-66ff1aca26b1
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ945594(v=OCS.15)
ms:contentKeyID: 51541419
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configure User Profile

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2018-10-11_

The tools included in the Lync Server 2013 Stress and Performance Tool package enable you to create and configure test user accounts that you can use to run load simulations. Use the Lync Server 2013 User Creation Tool to create the users. (For details, see [Create Users and Contacts](create-users-and-contacts.md).) After users are created, configure the user profiles by using the Lync Server 2013 Load Configuration Tool.

<div>

## Running the Lync Server 2013 Load Configuration Tool

To configure user profiles, run the Lync Server 2013 Load Configuration Tool (UserProfileGenerator.exe) and fill out each of the tabs. UserProfileGenerator.exe generates a directory for each of the client computers that you need to run the simulation. Each client directory also comes with a script to start all the instances of the Lync Server 2013 Stress and Performance Tool (LyncPerfTool.exe).

<div>


> [!IMPORTANT]  
> The user-specific values specified in UserProfileGenerator must match the values specified in the Lync Server 2013 User Creation Tool (UserProvisioningTool) for the pool.



</div>

Fill in the fields on each tab of the Lync Server 2013 Load Configuration Tool, as described in the following sections.

<div>

## Common Configuration

The **Common Configuration** tab of the Lync Server 2013 Load Configuration Tool is shown in the following figure. Fill in the fields of the **Common Configuration** tab, as described in the following steps.

![Common Configuration tab.](images/JJ945594.c68dcc8f-10f2-499e-95a2-fccbcc206c2f(OCS.15).jpg "Common Configuration tab.")

1.  In **Number of Available Machines**, type or click the number of computers that you want to use to run LyncPerfTool.exe. We recommend that you have one computer for every 4,500 users that you will be simulating. That number may vary if you reduce the load level or if you use only a subset of the available features. (Load levels are set on the **General Scenarios** tab.)

2.  In **Prefix for User Names**, type the prefix for the user name of the users. To log in, the Uniform Resource Identifier (URI) will be: UserPrefix\[User Start Index…(Number Of Users-1)\]@User Domain.

3.  In **Password for All Users**, enter the password that was used for creating the users. If you leave this field empty, the username will be used as the password.

4.  In **User Start Index**, click or type the index of the first user to be configured. You can configure different ranges for different types or levels of load, but you must run UserProfileGenerator.exe once per the range that you want to configure.

5.  In **Number of Users**, click or type the total number of users you are going to configure.

6.  In **User Domain**, type the domain used for the SIP URI. This is used to construct the SIP URI of each user to log on to the Lync Server 2013 Front End Server or Standard Edition server. It can be different from the account domain.

7.  In **Account Domain**, type the Active Directory Domain Services domain logon.

8.  Enter the maximum number of concurrent endpoints in **Sign In Per Second (per instance)** for which you want the tool to log in all the endpoints/users. The recommended rate is \<=2 per second/standard SKU FE.

9.  In **Access Proxy or Pool FQDN**, type the fully qualified domain name (FQDN) of the server that you want the clients to connect to. If the users are logging on externally, specify the access proxy. If the users are internal, specify the FQDN of their pool or Standard Edition server.

10. In **Port**, click or type the port that you want users to use for SIP (the default is 5061).

For External Network Server Settings, specify the **Access Proxy or Pool FQDN** and the **Port**. These settings are used only for External endpoints load simulation.

</div>

<div>

## General Scenarios

The **General Scenarios** tab of the Lync Server 2013 Load Configuration Tool is shown in the following figure.

Configure the load levels and parameters for each of the general scenarios that you want to run, or leave disabled.

![General Scenarios tab.](images/JJ945594.4f046d39-b532-4baf-99a6-c89d1d6d1fcc(OCS.15).jpg "General Scenarios tab.")

1.  In **Instant Messaging**, which includes peer-to-peer and conferencing, specify the appropriate value for the Load Level.
    
    <div>
    

    > [!NOTE]  
    > Load level values for all fields (except Location Information Services) are <STRONG>Disabled</STRONG>, <STRONG>Low</STRONG>, <STRONG>Medium</STRONG>, <STRONG>High</STRONG>, and <STRONG>Custom</STRONG>. When Low, Medium, High, or Custom is selected, configurations will be generated for each modality and client. High will result in the maximum supported load to be generated for the server, Medium corresponds to 60 percent of the load, and Low corresponds to 30 percent of the load.

    
    </div>

2.  In **Audio Conferencing**, which is audio conferencing only, specify the appropriate value for Load Level. Peer-to-peer calls are covered in the Voice Scenarios section later in this topic. To enable MultiView, open the **Advanced** tab for that modality.

3.  In **Application Sharing**, specify the appropriate value for Load Level.

4.  In **Data Collaboration**, which includes data conferencing, specify the appropriate value for Load Level.

5.  In **Distribution List Expansion**, specify the appropriate value for Load Level. You must also click the **Advanced** button, and then fill in the fields with the same values that you configured on the **Distribution List** tab of the Lync Server User Creation Tool (UserProvisioningTool.exe). For details about these fields, see [Create Users and Contacts](create-users-and-contacts.md)

6.  In **Address Book Web Query**, which is the address book lookup service (not the address book file download), specify the appropriate value for Load Level. To enable address book downloads, click the corresponding **Advanced** button, and then set **EnableABSDownload** to true.

7.  In **Response Group Service**, specify the appropriate value for Load Level. You must also click the corresponding **Advanced** button, and then specify the URIs of the response groups you have already created when provisioning Response Group Service agents. You must specify at least one response group. Use semicolons to separate multiple response groups. Update RGSUriSuffixStartIndex and RGSUriSuffixEndIndex to the actual values.

8.  In **Location Information Services**, select the appropriate value for Load Level. The load level for Location Information Services must be **Enabled** or **Disabled**.

<div>


> [!NOTE]  
> Each of the scenarios has an <STRONG>Advanced</STRONG> button located next to it, and a set of check boxes that enable variations of the scenarios. <STRONG>Ad-hoc</STRONG> means to generate simulation of conferences that will be created throughout the hour. <STRONG>Large Conf</STRONG> means that Large Conference Scenario will be simulated. <STRONG>External</STRONG> means to also simulate external users.<BR>These buttons and check boxes allow access to values specific to each scenario that will change the behavior of the Lync Server 2013 Stress and Performance Tool (LyncPerfTool) and make customization possible. For each scenario on the <STRONG>General Scenarios</STRONG> tab (except for Location Information Services), if the value of Load Level is <STRONG>Custom</STRONG>, then the conversation rate will be calculated using the corresponding field in the <STRONG>Advanced</STRONG> dialog box. The field name differs, depending on the scenario, but the field description will state, "NOTE: This number will only be used if Custom is selected from the drop-down menu." In general, the values <STRONG>High</STRONG>, <STRONG>Medium</STRONG>, and <STRONG>Low</STRONG> will alter the conversation rates per modality in line with the User Model that is a balance of all the scenarios. If there is a need to change the load level per modality due to a difference in expected usage, we recommend using a <STRONG>Custom</STRONG> conversation rate.<BR>



</div>

</div>

<div>

## Voice Scenarios

The **Voice Scenarios** tab of the Lync Server 2013 Load Configuration Tool is shown in the following figure.

Use the **Voice Scenarios** tab to configure all of the voice-related scenarios.

![Voice Scenarios tab.](images/JJ945594.28edf664-da59-40b0-9a0e-196f01e9ca86(OCS.15).jpg "Voice Scenarios tab.")

1.  In **VoIP**, click the **Advanced** button, and then provide values for the **PhoneAreaCode** and **LocationProfile** (dial plan) fields. You must also specify a value for **Load Level**. If Load Level for **VoIP** and **UC/PSTN Gateway** is Enabled, then a public switched telephone network (PSTN) to unified communications (UC) configuration file will always be generated that will simulate external calls.

2.  In **UC/PSTN Gateway**, specify a value for Load Level. If you select a load level other than **Disabled**, you must supply a value for **PSTN Area Code** by clicking the **Add** button under Mediation Server and PSTN. Verify that you have a route configured for that area code.
    
    <div>
    

    > [!NOTE]  
    > You can use either the Lync Server Control Panel or the Lync Server Management Shell to verify voice route configuration.

    
    </div>

3.  In **Conferencing Attendant**, specify a value for Load Level. Selecting a load level (other than **Disabled**) will enable the **Telephone Number** field. Enter the telephone number of the Auto Attendant that you want to use. Also, click the **Advanced** button, and then specify a value for the **LocationProfile** field.

4.  In **Call Park Service**, specify the appropriate value for **Load Level**.

5.  In **Mediation Server and PSTN**, for each Mediation Server that you want to use, you must have a separate PSTN simulator. After you have determined which client you are going to use as the simulator, you need to configure your Mediation Server to route calls to that computer on the PSTN Simulator port that you configured. Click **Add** to configure the value for the Mediation Server.

<div>


> [!NOTE]  
> Each of the scenarios has an <STRONG>Advanced</STRONG> button located next to it. These buttons allow access to values specific to each scenario that will change the behavior of the Lync Server 2013 Stress and Performance Tool (LyncPerfTool) and enable customization. For each scenario on the <STRONG>Voice Scenarios</STRONG> tab, if the value of <STRONG>Load Level</STRONG> is <STRONG>Custom</STRONG>, then the conversation rate will be calculated by using the corresponding field in the <STRONG>Advanced</STRONG> dialog box. The field name differs, depending on the scenario, but the field description will state, "NOTE: This number will only be used if Custom is selected from the drop-down menu."



</div>

</div>

<div>

## Reach

Reach is a new experience in Lync Server 2013 that supports conferencing scenarios through the Unified Communications Web API (UCWA) server that is installed on the Front-End server. The **Reach** tab of the Lync Server 2013 Load Configuration Tool is shown in the following figure.

Use the **Reach** tab to configure all the reach-related scenarios.

![Reach tab.](images/JJ945594.65ccf6de-0e8d-47ba-93f3-9dcb39d3fd62(OCS.15).jpg "Reach tab.")

1.  Click the **Advanced** button next to **General Reach Settings**. Set the field **UcwaTargetServerUrl** to the Director pool virtual IP (VIP) or the Front End pool VIP.

2.  In **Application Sharing**, **Data Collaboration**, and **IM**, select the appropriate value for **Load Level**.

<div>


> [!NOTE]  
> Each of the scenarios has an <STRONG>Advanced</STRONG> button located next to it. These buttons allow access to values specific to each scenario that will change the behavior of the Lync Server 2013 Stress and Performance Tool (LyncPerfTool) and enable customization. For each of the Reach scenarios, if the <STRONG>Load Level</STRONG> is <STRONG>Custom</STRONG>, then the value specified in the <STRONG>ConversationsPerHour</STRONG> field is used instead of the default



</div>

Use the **Mobility** tab to configure all of the mobility-related scenarios.

![Mobility tab.](images/JJ945594.4dd8f3e0-921c-48a5-8b23-2a0330d3c334(OCS.15).jpg "Mobility tab.")

1.  Click the **Advanced** button next to **Mobility (UCWA)**. Set the field **UcwaTargetServerUrl** to the Director pool virtual IP (VIP) or the Front End pool VIP.

2.  In **Presence and P2P Instant Messaging\\Audio**, select the appropriate value for **Load Level** to enable Mobility Scenario simulation.

<div>


> [!NOTE]  
> Each of the scenarios has an <STRONG>Advanced</STRONG> button located next to it. These buttons allow access to values specific to each scenario that will change the behavior of the Lync Server 2013 Stress and Performance Tool (LyncPerfTool) and enable customization. For each of the Reach scenarios, if the <STRONG>Load Level</STRONG> is <STRONG>Custom</STRONG>, then the value specified in the <STRONG>ConversationsPerHour</STRONG> field is used instead of the default.



</div>

</div>

<div>

## Summary

The **Summary** tab of the Lync Server 2013 Load Configuration Tool is shown in the following figure.

![Summary tab.](images/JJ945594.c675e869-8ded-4195-8c2a-68d844fc96ad(OCS.15).jpg "Summary tab.")

The **Summary** tab indicates which users to use for each of the scenarios. It is possible to manually configure user number ranges by selecting the **Enable Custom User Range Generation** check box, and then double-clicking the scenario in the table that has the **User Range** that you want to customize. Check (RunClient.bat) Add sign-in delay when starting, in order to include delays in the generated batch files to correspond with the sign-in rate. This is useful to prevent server overload when signing in a large number of users. Click **Generate Files**, and select the folder where you want to generate the configuration. A dialog box similar to the following figure will appear when your files have been successfully created.

![Acknowledgement that files have been created.](images/JJ945594.00dc1e92-bfba-48e7-9568-b97ad864491e(OCS.15).jpg "Acknowledgement that files have been created.")

</div>

</div>

<div>

## See Also


[Create Users and Contacts](create-users-and-contacts.md)  
</div>
</div>
<span></span>
</div>
</div>
</div>
