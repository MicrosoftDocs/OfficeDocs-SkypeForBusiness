---
title: "Configure XMPP gateway"
ms.author: kenwith
author: kenwith
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "The final steps for migrating your XMPP Gateway are to configure certificates for the Skype for Business Server 2019 Edge Server, deploy the Skype for Business Server 2019 XMPP Gateway, and update the DNS records for the XMPP Gateway. These steps should be performed in parallel to minimize the down time of your XMPP Gateway. All users must be moved to your Microsoft Skype for Business Server 2019 deployment before performing these steps."
---

# Configure XMPP gateway on Skype for Business Server 2019

The final steps for migrating your XMPP Gateway are to configure certificates for the Skype for Business Server 2019 Edge Server, deploy the Skype for Business Server 2019 XMPP Gateway, and update the DNS records for the XMPP Gateway. These steps should be performed in parallel to minimize the down time of your XMPP Gateway. All users must be moved to your Microsoft Skype for Business Server 2019 deployment before performing these steps.
  
> [!IMPORTANT]
> XMPP federation is not supported for users who are homed on survivable branch appliances. This applies to both seeing presence information and exchanging IM messages. 
  
### Configure XMPP Gateway Certificates on the Skype for Business Server 2019 Edge Server

1. On the Edge Server, in the Deployment Wizard, next to **Step 3: Request, Install, or Assign Certificates**, click **Run again**.
    
    > [!TIP]
    > If you are deploying the Edge Server for the first time, you will see Run instead of Run Again. 
  
2. On the **Available Certificate Tasks** page, click **Create a new certificate request**.
    
3. On the **Certificate Request** page, click **External Edge Certificate**.
    
4. On the **Delayed or Immediate Request** page, select the **Prepare the request now, but send it later** check box. 
    
5. On the **Certificate Request File** page, type the full path and file name of the file to which the request is to be saved (for example, c:\cert_exernal_edge.cer). 
    
6. On the **Specify Alternate Certificate Template** page, to use a template other than the default WebServer template, select the **Use alternative certificate template for the selected certification authority** check box. 
    
7. On the **Name and Security Settings** page, do the following: 
    
    1. In **Friendly name**, type a display name for the certificate.
    
    2. In **Bit length**, specify the bit length (typically, the default of 2048).
    
    3. Verify that the **Mark certificate private key as exportable** check box is selected. 
    
8. On the **Organization Information** page, type the name for the organization and the organizational unit (for example, a division or department). 
    
9. On the **Geographical Information** page, specify the location information. 
    
10. On the **Subject Name/Subject Alternate Names** page, the information to be automatically populated by the wizard is displayed. If additional subject alternative names are needed, you specify them in the next two steps. 
    
11. On the **SIP Domain Setting on Subject Alternate Names (SANs)** page, select the domain check box to add a sip.<sipdomain> entry to the subject alternative names list. 
    
12. On the **Configure Additional Subject Alternate Names** page, specify any additional subject alternative names that are required. 
    
    > [!TIP]
    > If the XMPP proxy is installed, by default the domain name (such as contoso.com) is populated in the SAN entries. If you require more entries, add them in this step. 
  
13. On the **Request Summary** page, review the certificate information to be used to generate the request. 
    
14. After the commands finish running, you can **View Log**, or click Next to continue.
    
15. On the **Certificate Request File** page, you can view the generated certificate signing request (CSR) file by clicking **View** or exit the Certificate Wizard by clicking **Finish**.
    
16. Copy the request file and submit to your public certification authority.
    
17. After receiving, importing and assigning the public certificate, you must stop and restart the Edge Server services. You do this by typing in the Skype for Business Server Management console:
    
  ```
  Stop-CsWindowsService
  ```

  ```
  Start-CsWindowsService
  ```

### Configure a new Skype for Business Server 2019 XMPP Gateway

1. Open Skype for Business Server Control Panel.
    
2. In the left navigation bar, click **Federation and External Access** and then click **XMPP Federated Partners**.
    
3. To create a new configuration, click **New**.
    
4. Define the following settings:
    
5. **Primary domain** (Required). The primary domain is the base domain of the XMPP partner. For example, you would enter **fabrikam.com** for the XMPP partner domain name. This is a required entry. 
    
6. **Description** The description is for notes or other identifying information for this particular configuration. This entry is optional. 
    
7. **Additional domains** Additional domains are domains that are a part of your XMPP partner's domain that should be included as part of the allowed XMPP communication. For example, if the primary domain is **fabrikam.com**, then you would list all other domains that are under fabrikam.com that you will communicate with by way of XMPP.
    
8. **Partner type** The **Partner type** is a required setting. You must choose one of the following to describe and enforce what contacts can be added. You can select from: 
    
  - **Federated** A **Federated** partner type represents a high level of trust between the Skype for Business Server deployment and the XMPP partner. This partner type is recommended for federating with XMPP servers within the same enterprise or where there is an established business relationship. XMPP contacts in Federated partners can: 
    
    1. Add contacts and view their presence without express authorization from the user.
       
    2. Send instant messages to contacts whether or not the user has added them into their contact list.
    
    3. See a user's status notes.
    
  - **Public verified** A **Public verified** partner is a public XMPP provider that is trusted to verify the identity of its users. XMPP contacts in Public Verified networks can add Skype for Business Server contacts and view their presence and send instant messages to them without express authorization from the Skype for Business Server users. XMPP contacts in public verified networks never see a users' status notes. This setting is not recommended. 
    
  - **Public unverified** A **Public unverified** partner is a public XMPP provider that is not trusted to verify the identity of its users. XMPP users on Public Unverified networks cannot communicate with users unless the user has expressly authorized them by adding them to the contact list. XMPP users on public unverified networks never see users' status notes. This setting is recommended for any federation with public XMPP providers such as Google Talk. 
    
9. **Connection Type:** Defines the various rules and dialback settings. 
    
  - **TLS Negotiation** Defines the TLS negotiation rules. An XMPP service can require TLS, can make TLS optional, or you define that TLS is not supported. Choosing Optional leaves the requirement up to the XMPP service for a mandatory-to-negotiate decision. To view all possible settings and details for SASL, TLS and Dialback negotiation -including not valid and known error configurations - see **REPLACE OR REMOVE THIS LINK**
  [Negotiation settings for XMPP federated partners in Skype for Business Server 2019](../../operations/managing-federation-and-external-access-to-lync-server-2013/negotiation-settings-for-xmpp-federated-partners.md).
    
    > **Required** The XMPP service requires TLS negotiation. 
    
    > **Optional** The XMPP service indicates that TLS is mandatory-to-negotiate. 
    
    > **Not Supported** The XMPP service does not support TLS. 
    
  - **SASL negotiation** Defines the SASL negotiation rules. An XMPP service can require SASL, can make SASL optional, or you define that SASL is not supported. Choosing Optional leaves the requirement up to the partner XMPP service for a mandatory-to-negotiate decision. 
    
    > **Required** The XMPP service requires SASL negotiation. 
    
    > **Optional** The XMPP service indicates that SASL is mandatory-to-negotiate. 
    
    > **Not Supported** The XMPP service does not support SASL. 
    
  - **Support server dialback negotiation** The support server dialback negotiation process uses the domain name system (DNS) and an authoritative server to verify that the request came from a valid XMPP partner. To do this, the originating server creates a message of a specific type with a generated dialback key and looks up the receiving server in DNS. The originating server sends the key in an XML stream to the resulting DNS lookup, presumably the receiving server. On receipt of the key over the XML stream, the receiving server does not respond to the originating server, but sends the key to a known authoritative server. The authoritative server verifies that the key is either valid or not valid. If not valid, the receiving server does not respond to the originating server. If the key is valid, the receiving server informs the originating server that the identity and key is valid and the conversation can commence. 
    
    There are two valid states for **Dialback negotiation**:
    
    > **True** The XMPP server is configured to use Dialback negotiation if a request should be received from an originating server. 
    
    > **False** The XMPP server is not configured to use Dialback negotiation and if a request should be received from an originating server, it will be ignored. 
    
10. Click **Commit** to save your changes to the site or user policy. 
    
### Update DNS Records for Skype for Business Server 2019 XMPP Gateway

To configure DNS for XMPP federation, you add the following SRV record to your external DNS:_xmpp-server._tcp.\<domain name\> The SRV record will resolve to the Access Edge FQDN of the Edge server, with a port value of 5269.
    

