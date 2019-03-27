---
title: 'Lync Server 2013: Configure web publishing rules for a single internal pool'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Configure web publishing rules for a single internal pool
ms:assetid: 86ff4b2a-1ba9-46a2-a175-8b19e00a49dd
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg429712(v=OCS.15)
ms:contentKeyID: 48184725
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configure web publishing rules for a single internal pool in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-07-07_

Microsoft Forefront Threat Management Gateway 2010 and Internet Information Server Application Request Routing (IIS ARR) uses web publishing rules to publish internal resources, such as a meeting URL, to users on the Internet.

In addition to the Web Services URLs for the virtual directories, you must also create publishing rules for simple URLs, the LyncDiscover URL, and the Office Web Apps Server. For each simple URL, you must create an individual rule on the reverse proxy that points to that simple URL.

If you are deploying mobility and using automatic discovery, you need to create a publishing rule for the external Autodiscover Service URL. Automatic discovery also requires publishing rules for the external Lync Server Web Services URL for your Director pool and Front End pool. For details about creating the web publishing rules for automatic discovery, see [Configuring the reverse proxy for mobility in Lync Server 2013](lync-server-2013-configuring-the-reverse-proxy-for-mobility.md).

Use the following procedures to create web publishing rules.

<div>


> [!NOTE]  
> These procedures assume that you have installed the Standard Edition of Forefront Threat Management Gateway (TMG) 2010 or have installed and configured Internet Information Server with the Application request Routing (IIS ARR) extension. You use either TMG or IIS ARR.



</div>

<div>

## To create a web server publishing rule on the computer running TMG 2010

1.  Click **Start**, select **Programs**, select **Microsoft Forefront TMG**, and then click **Forefront TMG Management**.

2.  In the left pane, expand **ServerName**, right-click **Firewall Policy**, select **New**, and then click **Web Site Publishing Rule**.

3.  On the **Welcome to the New Web Publishing Rule** page, type a display name for the publishing rule (for example, LyncServerWebDownloadsRule).

4.  On the **Select Rule Action** page, select **Allow**.

5.  On the **Publishing Type** page, select **Publish a single Web site or load balancer**.

6.  On the **Server Connection Security** page, select **Use SSL to connect to the published Web server or server farm**.

7.  On the **Internal Publishing Details** page, type the fully qualified domain name (FQDN) of the internal web farm that hosts your meeting content and Address Book content in the **Internal Site name** box.
    
    <div>
    

    > [!NOTE]  
    > If your internal server is a Standard Edition server, this FQDN is the Standard Edition server FQDN. If your internal server is a Front End pool, this FQDN is a hardware load balancer virtual IP (VIP) that load balances the internal web farm servers. The TMG server must be able to resolve the FQDN to the IP address of the internal web server. If the TMG server is not able to resolve the FQDN to the proper IP address, you can select <STRONG>Use a computer name or IP address to connect to the published server</STRONG>, and then in the <STRONG>Computer name or</STRONG> <STRONG>IP address</STRONG> box, type the IP address of the internal web server. If you do this, you must ensure that port 53 is open on the TMG server and that it can reach a DNS server that resides in the perimeter network. You can also use entries in the local hosts file to provide name resolution.

    
    </div>

8.  On the **Internal Publishing Details** page, in the **Path (optional)** box, type **/\*** as the path of the folder to be published.
    
    <div>
    

    > [!NOTE]  
    > In the website publishing wizard you can only specify one path. Additional paths can be added by modifying the properties of the rule.

    
    </div>

9.  On the **Public Name Details** page, confirm that **This domain name** is selected under **Accept Requests for**, type the external Web Services FQDN, in the **Public Name** box.

10. On **Select Web Listener** page, click **New** to open the New Web Listener Definition Wizard.

11. On the **Welcome to the New Web Listener Wizard** page, type a name for the web listener in the **Web listener name** box (for example, LyncServerWebServers).

12. On the **Client Connection Security** page, select **Require SSL secured connections with clients**.

13. On the **Web Listener IP Address** page, select **External**, and then click **Select IP Addresses**.

14. On the **External Listener IP selection** page, select **Specified IP address on the Forefront TMG computer in the selected network**, select the appropriate IP address, click **Add**.

15. On the **Listener SSL Certificates** page, select **Assign a certificate for each IP address**, select the IP address that is associated with the external web FQDN, and then click **Select Certificate**.

16. On the **Select Certificate** page, select the certificate that matches the public names specified in step 9, click **Select**.

17. On the **Authentication Setting** page, select **No Authentication**.

18. On the **Single Sign On Setting** page, click **Next**.

19. On the **Completing the Web Listener Wizard** page, verify that the **Web listener** settings are correct, and then click **Finish**.

20. On the **Authentication Delegation** page, select **No delegation, but client may authenticate directly**.

21. On the **User Set** page, click **Next**.

22. On the **Completing the New Web Publishing Rule Wizard** page, verify that the web publishing rule settings are correct, and then click **Finish**.

23. Click **Apply** in the details pane to save the changes and update the configuration.

</div>

<div>

## To create a web server publishing rule on the computer running IIS ARR

1.  Bind the certificate that you will use for the reverse proxy to the HTTPS protocol. Click **Start**, select **Programs**, select **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.
    
    <div>
    

    > [!NOTE]  
    > Additional help, screen shots and guidance on deploying and configuring IIS ARR can be found in the NextHop article <A href="http://go.microsoft.com/fwlink/?linkid=293391">Using IIS ARR as a Reverse Proxy for Lync Server 2013</A>.

    
    </div>

2.  If you have not already done so, import the certificate that you will use for the reverse proxy. In **Internet Information Services (IIS) Manager**, click the reverse proxy server name on the left-hand size of the console. In the middle of the console under **IIS** locate **Server Certificates**. Right-click **Server Certificates** and select **Open feature**.

3.  On the right hand side of the console, click **Import…**. Type the path and filename of the certificate with the extension, or click **…** to browse for the certificate. Select the certificate and click **Open**. Supply the password used to protect the private key (if you assigned a password when exporting the certificate and private key). Click **OK**. If the certificate import was successful, the certificate will appear as an entry in the middle of the console as an entry in **Server Certificates**.

4.  Assign the certificate for use by HTTPS. On the left-hand side of the console, select the **Default Web Site** of the IIS server. On the right-hand side, click **Bindings…**. In the **Site Bindings** dialog, click **Add…**. On the **Add Site Binding** dialog under **Type:**, select **https**. Selecting https will allow you to select the certificate to use for https. Under **SSL certificate:**, select the certificate that you imported for the reverse proxy. Click **OK**. Then, click **Close**. The certificate is now bound to the reverse proxy for secure socket layer (SSL) and transport layer security (TLS).
    
    <div>
    

    > [!IMPORTANT]  
    > If you receive a warning when closing the Bindings dialogs that intermediate certificates are missing, you need to locate and import the public CA root authority certificate and any intermediate CA certificates. Consult the instructions at the public CA that you requested your certificate from and follow the instructions to request and import a certificate chain. If you exported the certificate from your Edge Server, you can export the root CA certificate and any intermediate CA certificates associated with the Edge Server. Import the root CA certificate into the Computer’s (not to be confused with the User store) Trusted Root Certification Authorities store and intermediate certificates into the Computer’s Intermediate Certification Authorities store.

    
    </div>

5.  On the left-hand side of the console below the IIS server name, right-click **Server Farms** then click **Create Server Farm…**.
    
    <div>
    

    > [!NOTE]  
    > If you do not see the <STRONG>Server Farms</STRONG> node, you need to install Application Request Routing. For details, see <A href="lync-server-2013-setting-up-reverse-proxy-servers.md">Setting up reverse proxy servers for Lync Server 2013</A>.

    
    </div>
    
    On the **Create Server Farm** dialog in **Server farm name**, type the a name (this can be a friendly name for identification purposes) for the first URL. Click **Next**.

6.  On the **Add Server** dialog in **Server Address**, type the fully qualified domain name (FQDN) of the external web services on your Front End Server. The names that will be used here for example purposes are the same that are used in the Planning section for the reverse proxy, [Certificate summary - Reverse proxy in Lync Server 2013](lync-server-2013-certificate-summary-reverse-proxy.md). Referring to the reverse proxy planning, we type the FQDN `webext.contoso.com`. Confirm that the checkbox next to **Online** is selected. Click **Add** to add the server to the pool of web servers for this configuration.
    
    <div>
    

    > [!WARNING]  
    > Lync Server uses hardware load balancers to pool Director and Front End Servers for HTTP and HTTPS traffic. You will only supply one FQDN when adding a server to the IIS ARR Server Farm. The FQDN will be the Front End Server or Director in non-pooled server configurations, or the FQDN of the configured hardware load balancer for server pools. The only supported method to load balance HTTP and HTTPS traffic is by using hardware load balancers.

    
    </div>

7.  On the **Add Server** dialog, click **Advanced settings…**. This opens a dialog to define application request routing for requests to the configured FQDN. The purpose is to redefine what port is used when the request is processed by IIS ARR.
    
    By default, the destination HTTP port must be defined as 8080. Click next to the current **httpPort 80** and set the value to **8080**. Click next to the current **httpsPort 443** and set the value to **4443**. Leave the **weight** parameter at 100. If needed, you can redefine weights for a given rule once you have baseline statistics. Click **Finish** to complete this part of the rule configuration.

8.  You may see a dialog Rewrite Rules that informs you that IIS Manager can create a URL rewrite rule to route all incoming requests to the server farm automatically. Click **Yes**. You will adjust the rules manually, but selecting Yes sets the initial configuration..

9.  Click the name of the server farm that you have just created. Under **Server Farm** in IIS Manager Features View, you double-click **Caching**. Deselect **Enable disk cache**. Click **Apply** on the right-hand side.

10. Click the name of the server farm. Under **Server Farm** in IIS Manager Features View, you double-click **Proxy**. On the Proxy settings page change the value for **Time-out (seconds)** to a value appropriate for your deployment. Click **Apply** to save the change.
    
    <div>
    

    > [!IMPORTANT]  
    > The Proxy Time-out value is a number that will vary from deployment to deployment. You should monitor your deployment and modify the value for the best experience for clients. You may be able to set the value as low as 200. If you are supporting Lync mobile clients in your environment, you should set the value to 960 to allow for push notifications timeout from Office 365 which have a time-out value of 900. It is very likely that you will need to increase the time-out value to avoid client disconnects when the value is too low or decrease the number if connections through the proxy do not disconnect and clear long after the client has disconnected. Monitoring and base-lining what is normal for your environment is the only accurate means to determine where the right setting is for this value.

    
    </div>

11. Click the name of the server farm. Under **Server Farm** in IIS Manager Features View, you double-click **Routing Rules**. On the Routing Rules dialog under Routing, clear the checkbox next to Enable SSL offloading. If the ability to clear the checkbox is not available, select the checkbox for **Use URL Rewrite to inspect incoming requests**. Click **Apply** to save your changes.
    
    <div>
    

    > [!WARNING]  
    > SSL Offloading by the reverse proxy is not supported.

    
    </div>

12. Repeat Steps 5-11 for each URL that must pass through the reverse proxy. A common list would be the following:
    
      - Front End Server Web services external: webext.contoso.com (already configured by initial walk through)
    
      - Director Web services external for Director: webdirext.contoso.com (Optional if a Director is deployed)
    
      - Simple URL meet: meet.contoso.com
    
      - Simple URL dialin: dialin.contoso.com
    
      - Lync Autodiscover URL: lyncdiscover.contoso.com
    
      - Office Web Apps Server URL: officewebapps01.contoso.com
        
        <div>
        

        > [!IMPORTANT]  
        > The URL for the Office Web Apps Server will use a different httpsPort address. In step 7, you define the <STRONG>httpsPort</STRONG> as <STRONG>443</STRONG> and the <STRONG>httpPort</STRONG> as port <STRONG>80</STRONG>. All other configuration settings are the same.

        
        </div>

13. On the left-hand side of the console, click the IIS server name. In the middle of the console, locate **URL Rewrite** under **IIS**. Double-click URL Rewrite to open the URL Rewrite rules configuration. You should see rules for each Server Farm that you created in the previous steps. If you do not, confirm that you clicked on the **IIS Server** name immediately below the **Start Page** node in the Internet Information Server Manager console.

14. In the **URL Rewrite** dialog, using webext.contoso.com as an example, the full name of the rule as displayed is **ARR\_webext.contoso.com\_loadbalance\_SSL**.
    
      - Double-click the rule to open the **Edit Inbound Rule** dialog.
    
      - Click **Add…** on the **Conditions** dialog.
    
      - On the **Add Condition** in **Condition input:** type **{HTTP\_HOST}**. (As you type, a dialog appears that will let you select the condition). under **Check if input string:** select **Matches the Pattern**. In the **Pattern input** type **\***. **Ignore case** should be selected. Click **OK**.
    
      - Scroll down in the **Edit Inbound Rule** dialog to locate the **Action** dialog. **Action Type:** should be set to **Route to Server Farm**, **Scheme:** set to **https://**, **Server farm:** set to the URL that this rule applies to. For this example, this should be set to **webext.contoso.com**. **Path:** is set to **/{R:0}**
    
      - Click **Apply** to save your changes. Click **Back to Rules** to return to the URL Rewrite rules.

15. Repeat the procedure defined in Step 14 for each of the SSL rewrite rules that you have defined, one per Server Farm URL.
    
    <div>
    

    > [!WARNING]  
    > By default, HTTP rules are created as well and are denoted by the similar naming to the SSL rules. For our current example, the HTTP rule would be named <STRONG>ARR_webext.contoso.com_loadbalance</STRONG>. No modifications are needed to these rules and they can be safely ignored.

    
    </div>

</div>

<div>

## To modify the properties of the web publishing rule in TMG 2010

1.  Click **Start**, point to **Programs**, select **Microsoft Forefront TMG**, and then click **Forefront TMG Management**.

2.  In the left pane, expand **ServerName**, and then click **Firewall Policy**.

3.  In the details pane, right-click the web server publishing rule that you created in the previous procedure (for example, LyncServerExternalRule), and then click **Properties**.

4.  On the **Properties** page, on the **From** tab, do the following:
    
      - In the **This rule applies to traffic from these sources** list, click **Anywhere**, and then click **Remove**.
    
      - Click **Add**.
    
      - In **Add Network Entities**, expand **Networks**, click **External**, click **Add**, and then click **Close**.

5.  On the **To** tab, ensure that the **Forward the original host header instead of the actual one** check box is selected.

6.  On the **Bridging** tab, select the **Redirect request to SSL port** check box, and then specify port **4443**.

7.  On the **Public Name** tab, add the simple URLs (for example, meet.contoso.com and dialin.contoso.com).

8.  Click **Apply** to save changes, and then click **OK**.

9.  Click **Apply** in the details pane to save the changes and update the configuration.

</div>

<div>

## To modify the properties of the web publishing rule in IIS ARR

1.  Click **Start**, select **Programs**, select **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.

2.  On the left-hand side of the console, click the IIS server name.

3.  In the middle of the console, locate **URL Rewrite** under **IIS**. Double-click URL Rewrite to open the URL Rewrite rules configuration.

4.  Double-click the rule that you need to modify. Make your modifications, as needed, in **Match URL**, **Conditions**, **Server Variables** or **Action**.

5.  Click **Apply** to commit your changes. Click **Back to Rules** to modify other rules, or close the **IIS Manager** console if you are done with your changes.

</div>

</div>

<span> </span>

</div>

</div>

</div>

