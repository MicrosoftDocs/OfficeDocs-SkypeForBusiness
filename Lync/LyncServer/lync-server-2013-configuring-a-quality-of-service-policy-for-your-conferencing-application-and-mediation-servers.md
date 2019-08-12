---
title: 'Lync Server 2013: Configuring a Quality of Service policy for your Conferencing, Application, and Mediation servers'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Configuring a Quality of Service policy for your Conferencing, Application, and Mediation servers
ms:assetid: 8adcbbc5-c9f5-476d-ab7f-72e61859cacf
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205076(v=OCS.15)
ms:contentKeyID: 48184769
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuring a Quality of Service policy in Lync Server 2013 for your Conferencing, Application, and Mediation servers

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-06-23_

Configuring port ranges facilitates the use of Quality of Service by ensuring that all traffic of a specified type (for example, all audio traffic) travels through the same set of ports. This makes it easy for the system to identify and mark a given packet: if port 49152 is reserved for audio traffic, then any packet traveling through port 49152 can be marked with a DSCP code that indicates that this is an audio packet. In turn, this enables routers to identify the packet as an audio packet, and give it higher priority than unmarked packets (such as packets used to copy a file from one server to another).

However, simply restricting a set of ports to a specific type of traffic does not result in packets traveling through those ports being marked with the appropriate DSCP code. In addition to defining port ranges you must also create Quality of Service policies that specify the DSCP code to be associated with each port range. For Microsoft Lync Server 2013 that typically means creating two policies: one for audio and one for video.

Quality of Service policies are most-easily created, and managed, by using Group Policy. (These same policies can also be created by using local security policies. However, that requires you to repeat the same procedure on each and every computer.) Your initial set of QoS policies (one for audio and one for video) should be applied only to Lync Server computers running the Conferencing server, Application server, and/or Mediation server services. If all of these computers are located in the same Active Directory OU then you can simply assign the new Group Policy object (GPO) to that OU. Alternatively, you can take other steps to target the new policy to the specified computers; for example, you can place the appropriate computers in a security group, then use Group Policy security filtering to apply the GPO just to that security group.

In order to create a Quality of Service policy for managing audio, log on to a computer where Group Policy Management has been installed. Open Group Policy Management (click **Start**, point to **Administrative Tools**, and then click **Group Policy Management**) and then complete the following procedure:

1.  In Group Policy Management, locate the container where the new policy should be created. For example, if all your Lync Server computers are located in an OU named Lync Server then the new policy should be created in the Lync Server OU.

2.  Right-click the appropriate container and then click **Create a GPO in this domain, and Link it here**.

3.  In the **New GPO** dialog box, type a name for the new Group Policy object in the **Name** box (for example, **Lync Server QoS**) and then click **OK**.

4.  Right-click the newly-created policy and then click **Edit**.

5.  In the Group Policy Management Editor, expand **Computer Configuration**, expand **Policies**, expand **Windows Settings**, right-click **Policy-based QoS**, and then click **Create new policy**.

6.  In the **Policy-based QoS** dialog box, on the opening page, type a name for the new policy (e.g., **Lync Server QoS**) in the **Name** box. Select **Specify DSCP Value** and set the value to **46**. Leave **Specify Outbound Throttle Rate** unselected, and then click **Next**.

7.  On the next page, make sure that **All applications** is selected and then click **Next**. This simply ensures that all applications will match packets from the specified port range with the specified DSCP code.

8.  On the third page, make sure that both **Any source IP address and Any destination IP address** are selected and then click **Next**. These two settings ensure that packets will be managed regardless of which computer (IP address) sent those packets and which computer (IP address) will receive those packets.

9.  On page four, select **TCP and UDP** from the **Select the protocol this QoS policy applies to** dropdown list. TCP (Transmission Control Protocol) and UDP (User Datagram Protocol) are the two networking protocols most-commonly used by Lync Server and its client applications.

10. Under the heading **Specify the source port number**, select **From this source port or range**. In the accompanying text box, type the port range reserved for audio transmissions. For example, if you reserved ports 49152 through ports 57500 for audio traffic enter the port range using this format: **49152:57500**. Click **Finish**.

<div>


> [!NOTE]  
> The DSCP value of 46 is somewhat arbitrary: although DSCP 46 is often used for marking audio packets, you do not have to use DSCP 46 for audio communications. If you have already implemented QoS and you are using a different DSCP code for audio (for example, DSCP 40) then you should configure your Quality of Service policy to use that same code (i.e., 40 for audio). If you are just now implementing Quality of Service, then it is recommended that you use DSCP 46 for audio, simply because that value is commonly used to mark audio packets.



</div>

After you have created the QoS policy for audio traffic you should then create a second policy for video traffic (and, optionally, a third policy for managing application sharing traffic). To create a policy for video, follow the same basic procedure you followed when creating the audio policy, making these substitutions:

  - Use a different (and unique) policy name (for example, **Lync Server Video**).

  - Set the DSCP value to **34** instead of 46. (Note that you do not have to use a DSCP value of 34. The only requirement is that you use a different DSCP value for video than you used for audio.)

  - Use the previously-configured port range for video traffic. For example, if you have reserved ports 57501 through 65535 for video, then set the port range to this: **57501:65535**.

If you decide to create a policy for managing application sharing traffic you must create a third policy, making the following substitutions:

  - Use a different (and unique) policy name (for example, **Lync Server Application Sharing**).

  - Set the DSCP value to **24** instead of 46. (Again, you do not have to use a DSCP value of 24. The only requirement is that you use a different DSCP value for application sharing than you used for audio or for video.)

  - Use the previously-configured port range for video traffic. For example, if you have reserved ports 40803 through 49151 for application sharing, then set the port range to this: **40803:49151**.

The new policies you have created will not take effect until Group Policy has been refreshed on your Lync Server computers. Although Group Policy periodically refreshes on its own, you can force an immediate refresh by running the following command on each computer where Group Policy needs to be refreshed:

    Gpupdate.exe /force

This command can be run from within the Lync Server Management Shell or from any command window that is running under administrator credentials. To run a command window under administrator credentials, click **Start**, right-click **Command Prompt**, and then click **Run as administrator**.

To verify that the new QoS policies have been applied, do the following:

1.  On a Lync Server computer, click **Start** and then click **Run**.

2.  In the **Run** dialog box, type **regedit** and then press ENTER.

3.  In Registry Editor, expand **Computer**, expand **HKEY\_LOCAL\_MACHINE**, expand **SOFTWARE**, expand **Policies**, expand **Microsoft**, expand **Windows**, and then click **QoS**. Under **QoS** you should see registry keys for each of the QoS policies you just created. For example, if you created two new policies (one named Lync Server Audio QoS and the other named Lync Server Video QoS) you should registry entries for Lync Server Audio QoS and Lync Server Video QoS.

To help ensure that network packets are marked with the appropriate DSCP value, you should also create a new registry entry on each computer by completing the following procedure:

1.  Click **Start** and then click **Run**.

2.  In the **Run** dialog box, type **regedit** and then press ENTER.

3.  In the Registry Editor, expand **HKEY\_LOCAL\_MACHINE**, expand **SYSTEM**, expand **CurrentControlSet**, expand **services**, and then expand **Tcpip**.

4.  Right-click **Tcpip**, point to **New**, and then click **Key**. After the new registry key is created, type **QoS** and then press ENTER to rename the key.

5.  Right-click **QoS**, point to **New**, and then click **String Value**. After the new registry value is created, type **Do not use NLA** and then press ENTER to rename the value.

6.  Double-click **Do not use NLA**. In the **Edit String** dialog box, type **1** in the **Value data** box and then click **OK**.

7.  Close the Registry Editor and then reboot your computer.

</div>

<span> </span>

</div>

</div>

</div>

