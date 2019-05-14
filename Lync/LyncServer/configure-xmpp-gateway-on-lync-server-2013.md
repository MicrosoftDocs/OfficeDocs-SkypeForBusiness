---
title: Configure XMPP gateway on Lync Server 2013
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Configure XMPP gateway on Lync Server 2013
ms:assetid: c70282e0-b502-47e2-a0be-a32eb1faf99d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ721881(v=OCS.15)
ms:contentKeyID: 49733816
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configure XMPP gateway on Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-10-28_

The final steps for migrating your XMPP Gateway are to configure certificates for the Lync Server 2013 Edge Server, deploy the Lync Server 2013 XMPP Gateway, and update the DNS records for the XMPP Gateway. These steps should be performed in parallel to minimize the down time of your XMPP Gateway. All users must be moved to your Microsoft Lync Server 2013 deployment before performing these steps.

<div class=" ">


> [!IMPORTANT]  
> XMPP federation is not supported for users who are homed on survivable branch appliances. This applies to both seeing presence information and exchanging IM messages.



</div>

<div>

## Configure XMPP Gateway Certificates on the Lync Server 2013 Edge Server

1.  On the Edge Server, in the Deployment Wizard, next to **Step 3: Request, Install, or Assign Certificates**, click **Run again**.
    
    <div class=" ">
    

    > [!TIP]  
    > If you are deploying the Edge Server for the first time, you will see Run instead of Run Again.

    
    </div>

2.  On the **Available Certificate Tasks** page, click **Create a new certificate request**.

3.  On the **Certificate Request** page, click **External Edge Certificate**.

4.  On the **Delayed or Immediate Request** page, select the **Prepare the request now, but send it later** check box.

5.  On the **Certificate Request File** page, type the full path and file name of the file to which the request is to be saved (for example, c:\\cert\_exernal\_edge.cer).

6.  On the **Specify Alternate Certificate Template** page, to use a template other than the default WebServer template, select the **Use alternative certificate template for the selected certification authority** check box.

7.  On the **Name and Security Settings** page, do the following:
    
    1.  In **Friendly name**, type a display name for the certificate.
    
    2.  In **Bit length**, specify the bit length (typically, the default of 2048).
    
    3.  Verify that the **Mark certificate private key as exportable** check box is selected.

8.  On the **Organization Information** page, type the name for the organization and the organizational unit (for example, a division or department).

9.  On the **Geographical Information** page, specify the location information.

10. On the **Subject Name/Subject Alternate Names** page, the information to be automatically populated by the wizard is displayed. If additional subject alternative names are needed, you specify them in the next two steps.

11. On the **SIP Domain Setting on Subject Alternate Names (SANs)** page, select the domain check box to add a sip.\<sipdomain\> entry to the subject alternative names list.

12. On the **Configure Additional Subject Alternate Names** page, specify any additional subject alternative names that are required.
    
    <div class=" ">
    

    > [!TIP]  
    > If the XMPP proxy is installed, by default the domain name (such as contoso.com) is populated in the SAN entries. If you require more entries, add them in this step.

    
    </div>

13. On the **Request Summary** page, review the certificate information to be used to generate the request.

14. After the commands finish running, you can **View Log**, or click Next to continue.

15. On the **Certificate Request File** page, you can view the generated certificate signing request (CSR) file by clicking **View** or exit the Certificate Wizard by clicking **Finish**.

16. Copy the request file and submit to your public certification authority.

17. After receiving, importing and assigning the public certificate, you must stop and restart the Edge Server services. You do this by typing in the Lync Server Management console:
    
        Stop-CsWindowsService

      &nbsp;
    
        Start-CsWindowsService

</div>

<div>

## Configure a new Lync Server 2013 XMPP Gateway

1.  Open Lync Server Control Panel.

2.  In the left navigation bar, click **Federation and External Access** and then click **XMPP Federated Partners**.

3.  To create a new configuration, click **New**.

4.  Define the following settings:

5.  **Primary domain**    (Required). The primary domain is the base domain of the XMPP partner. For example, you would enter **fabrikam.com** for the XMPP partner domain name. This is a required entry.

6.  **Description**   The description is for notes or other identifying information for this particular configuration. This entry is optional.

7.  **Additional domains**   Additional domains are domains that are a part of your XMPP partner’s domain that should be included as part of the allowed XMPP communication. For example, if the primary domain is **fabrikam.com**, then you would list all other domains that are under fabrikam.com that you will communicate with by way of XMPP.

8.  **Partner type**   The **Partner type** is a required setting. You must choose one of the following to describe and enforce what contacts can be added. You can select from:
    
      - **Federated**   A **Federated** partner type represents a high level of trust between the Lync Server deployment and the XMPP partner.  This partner type is recommended for federating with XMPP servers within the same enterprise or where there is an established business relationship.  XMPP contacts in Federated partners can:
        
        1.  Add Lync contacts and view their presence without express authorization from the Lync user.
        
        2.  Send instant messages to Lync contacts whether or not the Lync user has added them into their contact list.
        
        3.  See a Lync user’s status notes.
    
      - **Public verified**   A **Public verified** partner is a public XMPP provider that is trusted to verify the identity of its users.  XMPP contacts in Public Verified networks can add Lync contacts and view their presence and send instant messages to them without express authorization from the Lync users.  XMPP contacts in public verified networks never see a Lync users’ status notes.  This setting is not recommended.
    
      - **Public unverified**   A **Public unverified** partner is a public XMPP provider that is not trusted to verify the identity of its users.  XMPP users on Public Unverified networks cannot communicate with Lync users unless the Lync user has expressly authorized them by adding them to the contact list.  XMPP users on public unverified networks never see Lync users’ status notes.  This setting is recommended for any federation with public XMPP providers such as Google Talk.

9.  **Connection Type:** Defines the various rules and dialback settings.
    
      - **TLS Negotiation**   Defines the TLS negotiation rules. An XMPP service can require TLS, can make TLS optional, or you define that TLS is not supported. Choosing Optional leaves the requirement up to the XMPP service for a mandatory-to-negotiate decision. To view all possible settings and details for SASL, TLS and Dialback negotiation –including not valid and known error configurations - see [Negotiation settings for XMPP federated partners in Lync Server 2013](lync-server-2013-negotiation-settings-for-xmpp-federated-partners.md).
        
          - <span></span>  
            **Required**   The XMPP service requires TLS negotiation.
        
          - <span></span>  
            **Optional**   The XMPP service indicates that TLS is mandatory-to-negotiate.
        
          - <span></span>  
            **Not Supported**   The XMPP service does not support TLS.
    
      - **SASL negotiation**   Defines the SASL negotiation rules. An XMPP service can require SASL, can make SASL optional, or you define that SASL is not supported. Choosing Optional leaves the requirement up to the partner XMPP service for a mandatory-to-negotiate decision.
        
          - <span></span>  
            **Required**   The XMPP service requires SASL negotiation.
        
          - <span></span>  
            **Optional**   The XMPP service indicates that SASL is mandatory-to-negotiate.
        
          - <span></span>  
            **Not Supported**   The XMPP service does not support SASL.
    
      - **Support server dialback negotiation** The support server dialback negotiation process uses the domain name system (DNS) and an authoritative server to verify that the request came from a valid XMPP partner. To do this, the originating server creates a message of a specific type with a generated dialback key and looks up the receiving server in DNS. The originating server sends the key in an XML stream to the resulting DNS lookup, presumably the receiving server. On receipt of the key over the XML stream, the receiving server does not respond to the originating server, but sends the key to a known authoritative server. The authoritative server verifies that the key is either valid or not valid. If not valid, the receiving server does not respond to the originating server. If the key is valid, the receiving server informs the originating server that the identity and key is valid and the conversation can commence.
        
        There are two valid states for **Dialback negotiation**:
        
          - <span></span>  
            **True**   The XMPP server is configured to use Dialback negotiation if a request should be received from an originating server.
        
          - <span></span>  
            **False**   The XMPP server is not configured to use Dialback negotiation and if a request should be received from an originating server, it will be ignored.

10. Click **Commit** to save your changes to the site or user policy.

</div>

<div>

## Update DNS Records for Lync Server 2013 XMPP Gateway

1.  To configure DNS for XMPP federation, you add the following SRV record to your external DNS:\_xmpp-server.\_tcp.\<domain name\> The SRV record will resolve to the Access Edge FQDN of the Edge server, with a port value of 5269.

</div>

</div>

<span> </span>

</div>

</div>

</div>

