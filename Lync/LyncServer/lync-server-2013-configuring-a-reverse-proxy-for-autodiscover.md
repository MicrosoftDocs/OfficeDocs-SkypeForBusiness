﻿---
title: 'Lync Server 2013: Configuring a reverse proxy for Autodiscover'
TOCTitle: Configuring a reverse proxy for Autodiscover
ms:assetid: 1e3c3cc2-fe55-408b-99c4-c6e0a9252689
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ945619(v=OCS.15)
ms:contentKeyID: 51541456
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuring a reverse proxy for Autodiscover in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-12-12_

Autodiscover and the support of clients using autodiscover requires modification of an existing web publishing rule or creating a new web publishing rule for the reverse proxy. The modification or creation of a new publishing rule is not dependent on the decision to update or not update the subject alternative name lists on the reverse proxy certificates.

If you decide to use HTTPS for initial Lync Server 2013 Autodiscover Service requests and update the subject alternative names lists on the reverse proxy certificates, you need to assign the updated public certificate to the Secure Sockets Layer (SSL) Listener on your reverse proxy. The required update to the external (public) certificate will include the subject alternate name (SAN) entry for lyncdiscover.\<domain name\>. You then need to modify the existing listener for the external web services or create a new web publishing rule for the external Autodiscover Service URL, for example **lyncdiscover.contoso.com**. If you do not already have a web publishing rule for the external Lync Server 2013 Web Services URL for your Front End pool and Director pool (if you have deployed Directors), you also need to publish a rule for that.

<div>


> [!NOTE]  
> The reverse proxy publishing rule and listener can service both the external web services and the Autodiscover Service, as long as the certificate assigned to the listener contains the necessary subject name and subject alternative names for both. For details on the default configuration of the web listener and publishing rule, see <A href="lync-server-2013-setting-up-reverse-proxy-servers.md">Setting up reverse proxy servers for Lync Server 2013</A> for more details.



</div>

If you decide to use HTTP for initial Autodiscover Service requests so that you do not need to update subject alternative names for the reverse proxy, you need to create or modify a web publishing rule for port 80.

The procedures in this section describe how to create or modify the web publishing rules in Microsoft Forefront Threat Management Gateway 2010 for automatic discovery.

<div>


> [!NOTE]  
> These procedures assume that you have installed the Standard Edition of Forefront Threat Management Gateway (TMG) 2010. If you are using another reverse proxy, the procedures are similar, but will need to be mapped to the documentation for the third-party product.



</div>

<div>

## To create a web publishing rule for the external Autodiscover URL

1.  Click **Start**, point to **Programs**, point to **Microsoft Forefront TMG**, and then click **Forefront TMG Management**.

2.  In the left pane, expand **ServerName**, right-click **Firewall Policy**, point to **New**, and then click **Web Site Publishing Rule**.

3.  On the **Welcome to the New Web Publishing Rule** page, type a display name for the new publishing rule (for example, LyncDiscoveryURL).

4.  On the **Select Rule Action** page, select **Allow**.

5.  On the **Publishing Type** page, select **Publish a single Web site or load balancer**.

6.  On the **Server Connection Security** page, select **Use SSL to connect to the published Web server or server farm**.

7.  On the **Internal Publishing Details** page, in **Internal Site name**, type the fully qualified domain name (FQDN) of your Director pool (for example, lyncdir01.contoso.local). If you are creating a rule for the external Web Services URL on the Front End pool, type the FQDN of the Front End pool (for example, lyncpool01.contoso.local).

8.  On the **Internal Publishing Details** page, in **Path (optional)**, type **/\*** as the path of the folder to be published, and then select **Forward the original host header**.

9.  On the **Public Name Details** page, do the following:
    
      - Under **Accept Requests for**, select **This domain name**.
    
      - In **Public Name**, type **lyncdiscover.**\<sipdomain\> (the external Autodiscover Service URL). If you are creating a rule for the external Web Services URL on the Front End pool, type the FQDN for the external Web Services on your Front End pool (for example, lyncwebextpool01.contoso.com).
    
      - In **Path**, type **/\***.

10. On **Select Web Listener** page, in **Web Listener**, select your existing SSL Listener with the updated public certificate.

11. On the **Authentication Delegation** page, select **No delegation, but client may authenticate directly**.

12. On the **User Set** page, select **All Users**.

13. On the **Completing the New Web Publishing Rule Wizard** page, verify that the web publishing rule settings are correct, and then click **Finish**.

14. In the Forefront TMG list of web publishing rules, double-click the new rule you just added to open **Properties**.

15. On the **To** tab, do the following:
    
      - Select **Forward the original host header instead of the actual one**.
    
      - Select **Requests appear to come from the Forefront TMG computer**.

16. On the **Bridging** tab, configure the following:
    
      - Select **Web server**.
    
      - Select **Redirect requests to HTTP port**, and type **8080** for the port number.
    
      - Select **Redirect requests to SSL port**, and type **4443** for the port number.

17. Click **OK**.

18. Click **Apply** in the details pane to save the changes and update the configuration.

19. Click **Test Rule** to verify that your new rule is set up correctly.

</div>

<div>

## To modify an existing web publishing rule to add the external Autodiscover SAN and URL

1.  Click **Start**, point to **Programs**, point to **Microsoft Forefront TMG**, and then click **Forefront TMG Management**.
    
    <div>
    

    > [!IMPORTANT]  
    > You will repeat the modification for each publishing rule and listener that you have. Typically, this will be one rule and listener for the Front End pools and one for the optional Directors or Director pools, if you have deployed them.

    
    </div>

2.  In the left pane, expand **ServerName**, right-click **Firewall Policy**, click the applicable rule. On the **Tasks** tab, click **Edit Selected rule**.

3.  On the **Public Name** tab, in **This rule applies to**, select **Requests for the following Web sites**.

4.  Click **Add**, type the name of the new Autodiscover site (for example, “lyncdiscover.contoso.com”), and then click **OK**.

5.  On the **Listener** tab, click **Select Certificate** and assign the new certificate with the added Autodiscover SAN entries. Close the Listener and Web Publishing properties.

6.  Click **Apply** in the details pane to save the changes and update the configuration.

7.  Click **Test Rule** to verify that your new rule is set up correctly.

</div>

<div>

## To create a web publishing rule for port 80

1.  Click **Start**, point to **Programs**, point to **Microsoft Forefront TMG**, and then click **Forefront TMG Management**.

2.  In the left pane, expand **ServerName**, right-click **Firewall Policy**, point to **New**, and then click **Web Site Publishing Rule**.

3.  On the **Welcome to the New Web Publishing Rule** page, type a display name for the new publishing rule (for example, Lync Autodiscover (HTTP)).

4.  On the **Select Rule Action** page, select **Allow**.

5.  On the **Publishing Type** page, select **Publish a single Web site or load balancer**.

6.  On the **Server Connection Security** page, select **Use non-secured connections to connect to the published Web server or server farm**.

7.  On the **Internal Publishing Details** page, in **Internal Site name**, type the internal Web Services FQDN for your Front End pool (for example, lyncpool01.contoso.local).

8.  On the **Internal Publishing Details** page, in **Path (optional)**, type **/\*** as the path of the folder to be published, and then select **Forward the original host header instead of the one specified in the Internal site name field**.

9.  On the **Public Name Details** page, do the following:
    
      - Under **Accept Requests for**, select **This domain name**.
    
      - In **Public Name**, type **lyncdiscover.**\<sipdomain\> (the external Autodiscover Service URL).
    
      - In **Path**, type **/\***.

10. On **Select Web Listener** page, in **Web Listener**, select a Web Listener or use the New Web Listener Definition Wizard to create a new one.

11. On the **Authentication Delegation** page, select **No delegation, and client cannot authenticate directly**.

12. On the **User Set** page, select **All Users**.

13. On the **Completing the New Web Publishing Rule Wizard** page, verify that the web publishing rule settings are correct, and then click **Finish**.

14. In the Forefront TMG list of web publishing rules, double-click the new rule you just added to open **Properties**.

15. On the **Bridging** tab, configure the following:
    
      - Select **Web server**.
    
      - Select **Redirect requests to HTTP port**, and type **8080** for the port number.
    
      - Verify that **Redirect requests to SSL port** is not selected.

16. Click **OK**.

17. Click **Apply** in the details pane to save the changes and update the configuration.

18. Click **Test Rule** to verify that your new rule is set up correctly.

19. Verify that the external Autodiscover Service URL is not defined on any other web publishing rule.

</div>

<div>

## See Also


[Setting up reverse proxy servers for Lync Server 2013](lync-server-2013-setting-up-reverse-proxy-servers.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

