---
title: 'Lync Server 2013: Using Lync Connectivity Analyzer'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Using Lync Connectivity Analyzer
ms:assetid: 954953fb-0c7a-4fd5-8acd-68ecb59b20af
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ907302(v=OCS.15)
ms:contentKeyID: 50639759
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Using Lync Connectivity Analyzer in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-02-11_

Microsoft Lync Connectivity Analyzer helps Lync administrators determine whether the deployment and configuration of their Office 365 or on-premises Lync Server environment meets the requirements to support connections from Lync Windows Store app and Lync apps on mobile devices.

Lync Connectivity Analyzer attempts to connect to Lync Server on-premises or Lync Online by using the same services and protocols that are used by Lync Windows Store app and Lync mobile apps. You can perform the connection tests over your internal network or over an external network that connects to Lync Server or Lync Online. Lync Connectivity Analyzer provides a report with detailed information about each connection step to help you validate your configuration and troubleshoot connection problems.

Lync Connectivity Analyzer tests the following Lync Server components:

  - Autodiscover service

  - Authentication Broker (Reach) service

  - Mobility (MCX) service

  - Mobility (UCWA) service

  - WebTicket service

Lync Connectivity Analyzer tests the configuration of the following other components:

  - Publication of DNS records for Autodiscover URLs

  - Certificates

  - Proxy servers

You can download Lync Connectivity Analyzer from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkId=277056](http://go.microsoft.com/fwlink/?linkid=277056).

<div>

## To Analyze Your Connectivity

1.  Enter the credentials for a valid Lync account (either an on-premises Lync account or an Office 365 Lync account) that will be used by the tool to test the connection:
    
      - In **Lync Account Type**, select **Office 365** or **On-Premises**.
    
      - In **SIP URI**, enter the SIP sign-in address for the Lync connection in the format <strong>user@domain.com</strong>.
    
      - In **Password**, enter the password associated with this account.
    
      - In **User name (optional)**, enter a user name if applicable. The user name is also known as the User Principal Name (UPN). If the user name and the SIP URI are the same, you do not need to enter a user name. If they are not the same, enter the user name in the format <strong>user@domain.com</strong> or **domain\\user**, as appropriate.
    
      - **Network access**, choose **From inside my organization** if you are running Lync Connectivity Analyzer from a computer connected to your internal network. Otherwise, choose **External (Internet)**. Lync Connectivity Analyzer always performs both internal and external tests, but specifying whether you are inside or outside of your own network helps the tool interpret whether certain failures are expected.
    
      - In **Client**, select whether to perform connectivity tests for the **Lync Windows Store App**, **Lync Mobile 2010 App**, or **Lync Mobile 2013 App**.
    
      - Under **Server Discovery**, select the type of test to perform:
        
          - If you want the tool to discover the Lync server automatically, select **Automatic**.
        
          - If you want the tool to bypass the autodiscover test, or if you know the name of the server you would like to connect to, select **Manual using address:** and specify the fully qualified domain name (FQDN) of the Lync server—for example, **lync.company.com**.

2.  (Optional) Under **Log File**, select the checkbox if you would like to create a log file at the specified path. If logging is enabled, click **Clear** to clear the log file, click **Open** to open and view the log file, click **Email** to open an email message to send the results to your support team (you must manually attach the log file from the path specified).

3.  Click **Start**.

The following figure shows sample results from Lync Connectivity Analyzer.

**Lync Connectivity Analyzer**

![Screenshot of the Lync Connectivity Analyzer](images/JJ907302.a7cc0abe-fac2-4691-a7d8-9ffef59cdee5(OCS.15).png "Screenshot of the Lync Connectivity Analyzer")

</div>

<div>

## Components Tested by Lync Connectivity Analyzer

Lync Connectivity Analyzer attempts to discover the Lync server and establish a connection by using the same steps used by Lync Windows Store app and Lync mobile apps. It performs the tests as described in this section.

If **Automatic discovery** is selected, Lync Connectivity Analyzer does the following:

  - Queries Domain Name Service (DNS) for autodiscover URLs.

  - Attempts discovery by using the secured internal channel. For example, **HTTPS://lyncdiscoverinternal.company.com/**.

  - Attempts discovery by using the unsecured internal channel. For example, **HTTP://lyncdiscoverinternal.company.com/**.

  - Attempts discovery by using the secured external channel. For example, **HTTPS://lyncdiscover.company.com**.

  - Attempts discovery by using the unsecured external channel. For example, **HTTP://lyncdiscover.company.com**.

If **Use the following server discovery address** is selected, Lync Connectivity Analyzer does the following:

  - Queries DNS for the server’s FQDN.

  - Attempts discovery by using the secured channel. For example, **HTTPS://serverFQDN/**.

  - Attempts discovery by using the unsecured channel. For example, **HTTP://serverFQDN/**.

If **Lync Windows Store app** is selected under **Test the requirements for**, Lync Connectivity Analyzer does the following:

  - Verifies that the WebTicket service is available and tests authentication of the Lync account credentials.

  - Verifies that the Authentication Broker (Reach) service is available.

If **Lync Mobile 2010 App** is selected under **Client**, Lync Connectivity Analyzer does the following:

  - Verifies that the WebTicket service is available and tests authentication of the Lync account credentials.

  - Verifies that the Mobility (MCX) service is available.

If **Lync Mobile 2013 App** is selected under **Client**, Lync Connectivity Analyzer does the following:

  - Verifies that the WebTicket service is available and tests authentication of the Lync account credentials.

  - Verifies that the Mobility (UCWA) service is available.

While performing these tests, Lync Connectivity Analyzer validates the certificates installed on Lync Server, hardware load balancers, proxy servers, and the computer on which you are running the tests.

</div>

<div>

## Other Resources

Microsoft also provides Microsoft Remote Connectivity Analyzer, a web-based connectivity test tool, which is available at <https://testconnectivity.microsoft.com/>. Lync Connectivity Analyzer and Remote Connectivity Analyzer differ in the following ways:

  - Remote Connectivity Analyzer can test connectivity for Microsoft Exchange and Outlook, in addition to Microsoft Lync.

  - Remote Connectivity Analyzer completes the SIP sign-in, whereas Lync Connectivity Analyzer only validates the account credentials, without signing in.

  - Remote Connectivity Analyzer tests connections only from outside of your organization’s network because it runs from a public web server.

  - Remote Connectivity Analyzer does not test the availability of Authentication Broker (Reach), Mobility (MCX), and WebTicket services.

  - Lync Connectivity Analyzer tests the Autodiscover service.

  - Remote Connectivity Analyzer can connect to any version of Lync Server, whereas Lync Connectivity Analyzer can connect successfully only to Lync Server 2010 with Cumulative Updates for Lync Server 2010: February 2012 (at a minimum), or the latest version of Lync Server.

The following documentation describes the requirements and procedures for deploying and configuring Lync Server to support Lync Windows Store app and Lync mobile clients:

  - [Deploying clients and devices in Lync Server 2013](lync-server-2013-deploying-clients-and-devices.md)

  - [Planning for mobility in Lync Server 2013](lync-server-2013-planning-for-mobility.md)

  - [Deploying mobility in Lync Server 2013](lync-server-2013-deploying-mobility.md)

</div>

</div>

<span> </span>

</div>

</div>

</div>

