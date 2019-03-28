---
title: 'Lync Server 2013: Setting up XMPP federation'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Setting up XMPP federation
ms:assetid: 5fda6cb7-8d4d-495d-90c7-601f1036e085
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204939(v=OCS.15)
ms:contentKeyID: 48184270
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Setting up XMPP federation in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-12-03_

To deploy the XMPP Proxy on the Edge Server, you must configure the Edge Server for XMPP federation. To do this, you do the following steps.

<div>

## Setting Up XMPP Federation

1.  Log on to the computer where the Lync Server Deployment Wizard is installed as a member of the Domain Admins group and the RTCUniversalServerAdmins group.

2.  On the Front End server, open the Lync Server Deployment wizard. Click Install or Update Lync Server System, then click Setup or Remove Lync Server Components. Click Run Again.

3.  At Setup Lync Server components, click Next. The summary screen will show actions as they are executed. Once the deployment is done, click View Log to view available log files. Click Finish to complete the deployment.

4.  On the Edge server, open the Lync Server Deployment wizard. Click Install or Update Lync Server System, then click Setup or Remove Lync Server Components. Click Run Again.

5.  At Setup Lync Server components, click Next. The summary screen will show actions as they are executed. Once the deployment is done, click View Log to view available log files. Click Finish to complete the deployment.

6.  On the Edge Server, in the Deployment Wizard, next to Step 3: Request, Install, or Assign Certificates, click Run again.
    
    <div class=" ">
    

    > [!TIP]  
    > If you are deploying the Edge Server for the first time, you will see Run instead of Run Again.

    
    </div>

7.  On the Available Certificate Tasks page, click Create a new certificate request.

8.  On the Certificate Request page, click External Edge Certificate.

9.  On the Delayed or Immediate Request page, select the Prepare the request now, but send it later check box.

10. On the Certificate Request File page, type the full path and file name of the file to which the request is to be saved (for example, c:\\cert\_exernal\_edge.cer).

11. On the Specify Alternate Certificate Template page, to use a template other than the default WebServer template, select the Use alternative certificate template for the selected certification authority check box.

12. On the Name and Security Settings page, do the following:
    
    1.  In Friendly name, type a display name for the certificate
    
    2.  In Bit length, specify the bit length (typically, the default of 2048)
    
    3.  Verify that the Mark certificate private key as exportable check box is selected

13. On the Organization Information page, type the name for the organization and the organizational unit (for example, a division or department)

14. On the Geographical Information page, specify the location information

15. On the Subject Name/Subject Alternate Names page, the information to be automatically populated by the wizard is displayed. If additional subject alternative names are needed, you specify them in the next two steps

16. On the SIP Domain Setting on Subject Alternate Names (SANs) page, select the domain check box to add a sip.\<sipdomain\> entry to the subject alternative names list.

17. On the Configure Additional Subject Alternate Names page, specify any additional subject alternative names that are required
    
    <div class=" ">
    

    > [!TIP]  
    > If the XMPP proxy is installed, by default the domain name (such as contoso.com) is populated in the SAN entries. If you require more entries, add them in this step.

    
    </div>

18. On the Request Summary page, review the certificate information to be used to generate the request.

19. After the commands finish running, you can View Log, or click Next to continue.

20. On the Certificate Request File page, you can view the generated certificate signing request (CSR) file by clicking View or exit the Certificate Wizard by clicking Finish.

21. Copy the request file and submit to your public certification authority.

22. After receiving, importing and assigning the public certificate, you must stop and restart the Edge Server services. You do this by typing in the Lync Server Management console:
    
       ```
        Stop-CsWindowsService
       ```
    
       ```
        Start-CsWindowsService
       ```

23. To configure DNS for XMPP federation, you add the following SRV record to external DNS:\_xmpp-server.\_tcp.\<domain name\> The SRV record will resolve to the access edge FQDN of the Edge server, with a port value of 5269. Additionally, you configure an ‘A’ host record (for example, xmpp.contoso.com) that points to the IP address of the Access Edge Server.
    
    <div class=" ">
    

    > [!IMPORTANT]  
    > If you have Edge pools in multiple sites, we recommend that you add multiple SRV records for XMPP federation. Add a SRV record for every Edge pool in your organization, and give each of those SRV records a different priority. When all Edge pools are running, XMPP requests will all be handled by the Edge pool with the first priority, but if that Edge pool goes down you won’t then have to add a new SRV record to regain XMPP federation functionality.

    
    </div>

24. Configure a new External Access Policy to enable all users by opening the Lync Server Management Shell on the Front End and typing:
    
       ```
        New-CsExternalAccessPolicy -Identity <name of policy to create.  If site scope, prepend with 'site:'> -EnableFederationAcces $true -EnablePublicCloudAccess $true
       ```
    
       ```
        New-CsExternalAccessPolicy -Identity FedPic -EnableFederationAcces $true -EnablePublicCloudAccess $true
       ```
    
       ```
        Get-CsUser | Grant-CsExternalAccessPolicy -PolicyName FedPic
       ```
    
    Enable XMPP Access for External Users by typing:
    
       ```
        Set-CsExternalAccessPolicy -Identity <name of the policy being used> EnableXmppAccess $true
       ```
    
       ```
        Set-CsExternalAccessPolicy -Identity FedPic -EnableXmppAccess $true
       ```

25. On the Edge Server where the XMPP Proxy is deployed, open a Command Prompt or a Windows PowerShell™ command-line interface and type the following:
    
       ```
        Netstat -ano | findstr 5269
       ```
    
       ```
        Netstat -ano | findstr 23456
       ```
    
    The command **netstat –ano** is a network statistics command, the parameters **–ano** request that netstat display all connections and listening ports, address and ports are displayed in a numerical form, and that the owning process ID is associated with each connection. The character **|** defines a pipe to the next command, **findstr**, or find string. The number 5269 and 23456 that is passed to findstr as a parameter instructs findstr to search the output of netstat for the strings 5269 and 23456. If XMPP is correctly configured, the result of the commands should result in listening and established connections, both on the external (port 5269) and the internal (port 23456) interfaces of the Edge Server.
    
    If the commands do not return established or listening ports on 5269 and 23456, check the following:

</div>

<div>

## Troubleshooting XMPP Federation

1.  To determine if the XMPP Proxy is running, do the following:

2.  Log on to the Edge server that is running the XMPP Proxy service as a member of the local administrator’s group.

3.  Click **Start**, click **All Programs**, click **Administrative Tools**, click **Services**

4.  In Services, locate Lync Server XMPP Translating Gateway Proxy. The service should be in the **Started** state. If it is not started, click the **Start** icon in the toolbar. The icon appears as a green, right-pointing arrow.

5.  Confirm that the service has changed to **Started**. If it has successfully started, close **Services** and continue.
    
    If ther service has not successfully started, from Administrative Tools, open Event Viewer and refer to the errors and warnings in the **Lync Server** portion under **Applications and Services Logs**.

6.  Once the **Lync Server XMPP Translating Gateway** service is running, recheck the netstat commands used previously. If you are not seeing established or listening sessions, check and ensure that the **XMPP Federation Route** is correctly configured in Topology Builder

7.  Log on to the computer where Topology Builder is installed as a member of the Domain Admins group and the RTCUniversalServerAdmins group.

8.  Start Topology Builder: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Topology Builder**.

9.  In Topology Builder, select the site for the XMPP federation route and review to confirm that the **Site federation route assignment** for **XMPP federation** shows your Edge Server or Edge pool as the selected XMPP federation route assignment.
    
    If the route assignment is incorrect or is not set, right-click the site, click **Edit Properties**. Select the XMPP federation check box and then select the correct Edge Server or Edge pool.

10. Publish the topology. For details, see [Publish your topology in Lync Server 2013](lync-server-2013-publish-your-topology.md)
    
    <div class=" ">
    

    > [!TIP]  
    > Though not required and typically not necessary, you may find that you will need to restart the Edge Servers

    
    </div>

11. Using the netstat process used previously, confirm that the Edge Server is now listening or has established sessions on port 5269 and port 23456.

12. If you still are not seeing the expected sessions, check the Event Viewer for possible contributing causes for the communication problem.

</div>

<div>

## See Also


[Example XMPP configuration in Lync Server 2013 – XMPP federation with Google Talk](lync-server-2013-example-xmpp-configuration-–-xmpp-federation-with-google-talk.md)  


[Manage XMPP federated partners in Lync Server 2013](lync-server-2013-manage-xmpp-federated-partners-for-your-organization.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

