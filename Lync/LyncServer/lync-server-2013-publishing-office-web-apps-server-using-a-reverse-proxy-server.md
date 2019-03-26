---
title: 'Publishing Office Web Apps Server using a reverse proxy server'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Publishing Office Web Apps Server using a reverse proxy server
ms:assetid: 0babe39f-c4b9-46f0-995a-33dc99c2be03
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204665(v=OCS.15)
ms:contentKeyID: 48183384
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Publishing Office Web Apps Server in Lync Server 2013 using a reverse proxy server

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-25_

If you want external users (that is, users logging on from outside your organization’s firewall) to have access to Office Web Apps Server PowerPoint presentations then you will need to use Office Web Apps Server and a reverse proxy server such as Microsoft Forefront Threat Management Gateway. That also means that you will need to create and configure a website publishing rule; that rule will help ensure that users are able to connect to the server. If you do not need to provide access to external users then you do not need to configure a website publishing rule.

To configure a website publishing rule in Forefront Threat Management Gateway complete the following procedure:

1.  Click **Start**, click **All Programs**, click **Microsoft Forefront TMG**, and then click **Forefront TMG Management**.

2.  In Forefront TMG, right-click **Firewall Policy**, point to **New**, and then click **Web Site Publishing Rule**.

3.  In the New Web Publishing Rule Wizard, on the **Welcome to the New Web Publishing Rule Wizard** page, type a name for your new rule in the **Web publishing rule name** box (for example, **Office Web Apps Server Rule**) and then click **Next**.

4.  On the **Specify Rule Action** page, select **Allow** and then click **Next**.

5.  On the **Publishing Type** page, select **Publish a single Web site or load balancer** and then click **Next**.

6.  On the **Server Connection Security** page, select **Use SSL to connect to the published Web server or server farm** and then click **Next**.

7.  On the **Internal Publishing Details** page, type the FQDN of your Office Web Apps server (for example, **officewebapps01.contoso.com**) in the **Internal site name** box and then click **Next**. The name entered in the **Internal site name** box must appear in the Subject field or the Subject Alternative Name field of the certificate you have assigned to Office Web Apps Server.

8.  On the **Internal Publishing Details** page, type **/\*** in the **Path (optional)** box and then click **Next**. The /\* syntax will help ensure that all the folders and subfolders for the site are published.

9.  On the **Public Name Details** page, select **This domain name (type below)** from the **Accept requests for** drop-down list and then type the fully qualified for your Office Web Apps Server in the Public name box. This name should be the name used to access your website. For example, if your site is accessed using the URL http://officewebapps01.contoso.com then you should enter **officewebapps01.contoso.com** in the **Public name** box.

10. Click **Next**.

11. On the **Select Web Listener** page, click **New**.

12. In the New Web Listener Definition Wizard, type a name for the new Web listener (for example, **SSL**) in the **Web listener name** box and then click **Next**.

13. On the **Client Connection Security** page, select **Require SSL secured connections with clients** and then click **Next**.

14. On the **Web Listener IP Addresses** page, select **External**, select **Internal**, and then click **Next**.

15. On the **Listener SSL Certificates** page, select **Use a single certificate for this Web Listener** and then click **Select Certificate**.

16. In the **Select Certificate** dialog box, select the certificate to be used for this Web Listener and then click **Select**.

17. On the **Listener SSL Certificates** page, click **Next**.

18. On the **Authentication Settings** page, select **No Authentication** from the **Select how clients will provide credentials to Forefront TMG** drop-down list, and then click **Next**.

19. On the **Single Sign On Settings** page, click **Next**.

20. On the **Completing the New Web Listener Wizard** page, review the summary of the configuration choices you have made. When ready, click **Finish**.

21. On the **Select Web Listener** page, click **Next**.

22. On the **Authentication Delegation** page, select **No delegation, but client may authenticate directly** from the **Select the method used by Forefront TMG to authenticate to the published Web server** drop-down list and then click **Next**.

23. On the **User Sets** page, confirm that the appropriate user sets are listed. By default, this is the **All Users** user set. Click **Add** to add other user sets you may have defined. When complete, click **Next**.

24. On the **Completing the New Web Publishing Rule Wizard** page, click **Finish**.

Note that clicking **Finish** does not mean that you completed the process; that is, this does not automatically apply and enable the new rule. Instead, you will need to click the **Apply** button that will appear in the Forefront TMG user interface. When you click **Apply** the **Configuration Change Description** dialog box will appear. Click **Apply** in that dialog box to enable the new publishing rule.

After your new rule has been applied, you will then need to make some minor modifications to the rule to make sure that users can use the new PowerPoint presentation capabilities. To do that, complete the following procedure:

1.  In Forefront TMG, right-click the name of the new publishing rule and then click **Properties**.

2.  In the **Properties** dialog box, on the **To** tab, select the option **Forward the original host header instead of the actual one**.

3.  On the **Traffic** tab, click **Filtering** and then click **Configure HTTP**.

4.  In the **Configuring HTTP policy for rule** dialog box, clear the **Verify normalization** check box and then click **OK**.

5.  In the **Properties** dialog box, click **OK**.

6.  In Forefront TMG, click **Apply** to enable the changes. When the **Configuration Change Description** dialog box appears, click **Apply**.

After completing the installation you can test your Office Web Apps Server using the procedures in the topic [Validating the configuration of Office Web Apps Server in Lync Server 2013](lync-server-2013-validating-the-configuration-of-office-web-apps-server.md).

</div>

<span> </span>

</div>

</div>

</div>

