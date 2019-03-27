---
title: 'Define and configure a Front End pool or Standard Edition server'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Define and configure a Front End pool or Standard Edition server
ms:assetid: 713fc263-23dd-414a-b001-82932e4fe966
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398538(v=OCS.15)
ms:contentKeyID: 48184457
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Define and configure a Front End pool or Standard Edition server in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-08_

This procedure does not require membership in a local administrator or privileged domain group. You should log on to a computer as a standard user.

If you are deploying an Enterprise server, a minimum number of Front End Servers in a pool must be running at all times. The following table summarizes these requirements.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Total number of Front End Servers in the pool</th>
<th>Number of servers that must be running for pool to be functional</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>1-2</p></td>
<td><p>1</p></td>
</tr>
<tr class="even">
<td><p>3-4</p></td>
<td><p>2</p></td>
</tr>
<tr class="odd">
<td><p>5-6</p></td>
<td><p>3</p></td>
</tr>
<tr class="even">
<td><p>7-8</p></td>
<td><p>4</p></td>
</tr>
<tr class="odd">
<td><p>9-10</p></td>
<td><p>5</p></td>
</tr>
<tr class="even">
<td><p>11-12</p></td>
<td><p>6</p></td>
</tr>
</tbody>
</table>


<div>


> [!NOTE]
> For Lync Server 2013, any time you add or remove a Front End Server from the pool, you must restart services. Removing and adding servers should be done as separate operations. For example, if you are going to add two Front End Servers and remove two Front End Servers, use the following process: 
> <OL>
> <LI>
> <P>Remove the two Front End Servers.</P>
> <LI>
> <P>Publish and re-activate the topology.</P>
> <LI>
> <P>Restart the services</P>
> <LI>
> <P>Add the two Front End Servers.</P>
> <LI>
> <P>Publish and re-activate the topology.</P>
> <LI>
> <P>Restart the services.</P></LI></OL>



</div>

After you have defined your topology, use the following procedure to define a Front End pool for your site. For details about defining the topology, see [Define and configure a topology in Topology Builder for Lync Server 2013](lync-server-2013-define-and-configure-a-topology-in-topology-builder.md).

<div>

## To define a Front End pool

1.  In the Define New Front End Pool Wizard, on the **Define the New Front End pool** page, click **Next**.

2.  On the **Define the Front End pool FQDN** page, enter a fully qualified domain name (FQDN) for the pool you are creating, click **Enterprise Edition Front End pool**, and then click **Next**.

3.  On the **Define the computers in this pool** page, enter a computer FQDN for the first Front End Server in the pool, and then click **Add**. Repeat this step for any additional computers (up to twelve) that you want to add to the pool, and then click **Next**.

4.  On the **Select features** page, select the check boxes for the features that you want on this Front End pool. For example, if you are deploying only instant messaging (IM) and presence features, you would select the **Conferencing** check box to allow multiparty IM but would not select the **Dial-in (PSTN) conferencing**, **Enterprise Voice**, or **Call Admission Control** check boxes, because they represent voice, video, and collaborative conferencing features.
    
      - **Conferencing**   This selection enables a rich set of features including:
        
          - IM with more than two parties in an IM session.
        
          - Conferencing, which includes document collaboration, application sharing, and desktop sharing.
        
          - A/V conferencing, which enables users to have real-time audio/video (A/V) conferences without the need for external services such as the Live Meeting service or a third-party audio bridge.
    
      - **Dial-in (PSTN) conferencing**   Allows users to join the audio portion of a Lync Server 2013 conference by using a public switched telephone network (PSTN) phone without requiring an audio conferencing provider.
    
      - **Enterprise Voice**   Enterprise Voice is the Voice over IP (VoIP) solution in Lync Server 2013 that allows users to make and receive phone calls. You would deploy this feature if you plan to use Lync Server 2013 for voice calls, voice mail, and other functions that use a hardware device or a software client.
    
      - **Call admission control (CAC)**   CAC determines, based on available network bandwidth, whether to allow real-time communications sessions such as voice or video calls to be established. If you have deployed only IM and presence, CAC is not needed because neither of these two features uses CAC.
    
      - **Archiving**   Archiving provides a way for you to archive IM content, conferencing (meeting) content, or both that is sent through Lync Server 2013.
    
      - **Monitoring**   Monitoring Server enables you to collect numerical data that describes the media quality on your network and endpoints, usage information related to VoIP calls, IM messages, A/V conversations, meetings, application sharing, and file transfers, and call error and troubleshooting information for failed calls.
    
    <div>
    

    > [!NOTE]
    > If you would like to enable CAC in your deployment, it is required that you enable CAC in exactly one pool per central site. CAC is recommended if you are deploying voice features or A/V conferencing.

    
    </div>
    
    The following table shows the available features (top) and the functions offered to users (left). The selections in the table are what you should select to enable those features for your organization.
    
    
    <table>
    <colgroup>
    <col style="width: 20%" />
    <col style="width: 20%" />
    <col style="width: 20%" />
    <col style="width: 20%" />
    <col style="width: 20%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th></th>
    <th>Conferencing</th>
    <th>Dial-In Conferencing</th>
    <th>Enterprise Voice</th>
    <th>Call Admission Control</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>Instant messaging and presence</p></td>
    <td><p>X</p></td>
    <td></td>
    <td></td>
    <td></td>
    </tr>
    <tr class="even">
    <td><p>Conferencing</p></td>
    <td><p>X</p></td>
    <td><p>X</p></td>
    <td></td>
    <td></td>
    </tr>
    <tr class="odd">
    <td><p>A/V conferencing</p></td>
    <td><p>X</p></td>
    <td><p>X</p></td>
    <td></td>
    <td><p>X</p></td>
    </tr>
    <tr class="even">
    <td><p>Enterprise Voice</p></td>
    <td></td>
    <td></td>
    <td><p>X</p></td>
    <td><p>X</p></td>
    </tr>
    </tbody>
    </table>


5.  On the **Select collocated server roles** page, you can to collocate the Mediation Server on the Front End Server or to deploy it as a stand-alone server.
    
    You can collocate the Mediation Server on the Front End pool.
    
      - If you intend to collocate the Mediation Server on the Enterprise Edition Front End pool, ensure the check box is selected. The server role will be deployed on the pool servers.
    
      - If you intend to deploy the Mediation Server as a stand-alone server, clear the appropriate check box. You will deploy Mediation Server in a separate deployment step after you completely deploy the Front End Server.
    
    <div>
    

    > [!NOTE]
    > We recommend that you collocate the Mediation Server if possible. For details about support for collocated or stand-alone Mediation Servers, see <A href="lync-server-2013-components-and-topologies-for-mediation-server.md">Components and topologies for Mediation Server in Lync Server 2013</A> in the Planning documentation.

    
    </div>

6.  The **Associate server roles with this Front End pool** page lets you define and associate server roles with the Front End pool. The following role is available:
    
    **Enable an Edge pool**   Defines and associates a single Edge Server or a pool of Edge Servers. An Edge Server facilitates communication and collaboration between users inside the organization and people outside the organization, including federated users.
    
    There are two possible scenarios that you can use to deploy and associate the server roles:
    
    For scenario one, you are defining a new topology for a new installation. You can approach the installation in one of two ways:
    
      - Leave the check box clear and proceed with defining the topology. After you have published, configured, and tested the Front End and Back End Server roles, you can run Topology Builder again to add the role servers to the topology. This strategy will enable you to test the Front End pool and the server running SQL Server without additional complications from additional roles. After you have completed your initial testing, you can run Topology Builder again to select the roles you need to deploy.
    
      - Select roles that you need to install, and then set up the hardware to accommodate the selected roles.
    
    For scenario two, you have an existing deployment and your infrastructure is ready for new roles or you need to associate existing roles with a new Front End Server:
    
      - In this case, you will select the roles that you intend to deploy or associate with the new Front End Server. In either case, you will proceed with the definition of the roles, set up any needed hardware, and proceed with the installation.

7.  On the **Define the SQL store** page, do one of the following:
    
      - To use an existing SQL Server store that has already been defined in your topology, select an instance from **SQL store**.
    
      - To define a new SQL Server instance to store pool information, click **New** and then specify the **SQL Server FQDN**in the **Define New SQL Store** dialog box.
    
      - To specify the name of a SQL Server instance, select **Named Instance**, and then specify the name of the instance.
    
      - To use the default instance, click **Default instance**.
    
      - To use SQL Mirroring, select **Enable SQL mirroring** and select an existing instance or create a new instance.

8.  On the **Define the file share** page, do one of the following:
    
      - To use a file share that has already been defined in your topology, select **Use a previously defined file share**.
    
      - To define a new file share, select **Define a new file share**, in the **File Server FQDN** box, enter the FQDN of the existing file server where the file share is to reside, and then enter a name for the file share in the **File Share** box.
    
    <div>
    

    > [!IMPORTANT]
    > The file share for Lync Server 2013 cannot be located on the Front End Server. Note that in this example, the file share has been located on the SQL Server-based Back End Server. This might not be an optimal location for your organization’s requirements, and a file server might be a better choice. You can define the file share without the file share having been created. You will need to create the file share in the location you define before you publish the topology.

    
    </div>

9.  On the **Specify the Web Services URL** page, do one or both of the following:
    
    <div>
    

    > [!IMPORTANT]
    > The base URL is the Web Services identity for the URL, minus the https://. For example, if the full URL for the Web Services of the pool is https://pool01.contoso.net, the base URL is pool01.contoso.net.

    
    </div>
    
    <div>
    

    > [!WARNING]
    > If you have more than one Front End pool or Front End Server, the external Web services FQDN must be unique. For example, if you define the external Web services FQDN of a Front End Server as <STRONG>pool01.contoso.com</STRONG>, you cannot use <STRONG>pool01.contoso.com</STRONG> for another Front End pool or Front End Server.

    
    </div>
    
    1.  If you are configuring DNS load balancing, select the **Override internal Web Services pool FQDN** check box, enter the internal base URL (which must be different from the pool FQDN and could be, for example, internal-\<your base URL\>) in **Internal Base URL**.
        
        <div>
        

        > [!WARNING]
        > If you decide to override the Internal web services with a self-defined FQDN, each FQDN must be unique from any other Front End pool, Director or a Director pool. <STRONG>Use only standard characters</STRONG> (including A–Z, a–z, 0–9, and hyphens) when defining URLs or fully qualified domain names. Do not use Unicode characters or underscores. Nonstandard characters in a URL or FQDN are often not supported by external DNS and public CAs (that is, when the URL or FQDN must be assigned to the subject name or subject alternative name in the certificate).

        
        </div>
    
    2.  Optionally enter the external base URL in **External Base URL**. You would enter the external base URL to differentiate it from your internal domain naming. For example, your internal domain is contoso.net, but your external domain name is contoso.com. You would define the URL using the contoso.com domain name. This is also important in the case of a reverse proxy. The external base URL domain name would be the same as the domain name of the FQDN of the reverse proxy. Instant messaging and presence does require HTTP access to the Front End pool.
    
    <div>
    

    > [!NOTE]
    > To use DNS load balancing, you must create the appropriate DNS records. For details, see <A href="lync-server-2013-configure-dns-for-load-balancing.md">Configure DNS for load balancing in Lync Server 2013</A>.

    
    </div>

10. If you selected **Conferencing** on the **Select Features** page, on the **Select an Office Web Apps Server** page select **Associate pool with an Office Web Apps Server** and then click **New** (or select an existing Office Web Apps Server from the drop-down list).

11. In the **Define New Office Web Apps Server** dialog box, type the fully qualified domain name (FQDN) of your Office Web Apps Server computer in the **Office Web Apps Server FQDN** box; when you do this, your Office Web Apps Server discovery URL should automatically be entered into the **Office Web Apps Server discovery URL** box.
    
    If the Office Web Apps Server is installed on-premises and in the same network zone as Lync Server 2013 then the option **Office Web Apps Server is deployed in an external network (that is, perimeter/Internet)** should not be selected.
    
    If the Office Web Apps Server is deployed outside your internal firewall, then select the option **Office Web Apps Server is deployed in an external network (that is, perimeter/Internet)**.
    
    <div>
    

    > [!NOTE]
    > For details, see <A href="lync-server-2013-enabling-office-web-apps-server-and-lync-server-2013.md">Configuring integration with Office Web Apps Server and Lync Server 2013</A>.

    
    </div>

12. On the **Define the Archiving SQL store** page, select an existing instance or SQL Server, or define a new instance to store the data associated with archiving data.

13. On the **Define the Monitoring SQL store** page, select an existing instance or SQL Server, or define a new instance to store the data associated with monitoring data.

14. Click **Next**. If you defined other role servers on the **Associate server roles with this Front End pool** page, separate role configuration wizard pages will open to let you configure the server roles. For details, see the following:
    
    [Deploying external user access in Lync Server 2013](lync-server-2013-deploying-external-user-access.md)

15. If you did not select additional server roles to configure and deploy, or when you have finished the configuration of the additional role servers, click **Finish**.

</div>

</div>

<span> </span>

</div>

</div>

</div>

