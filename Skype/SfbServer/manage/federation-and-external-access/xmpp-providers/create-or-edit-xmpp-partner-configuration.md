---
title: 'Create or edit XMPP partner configuration'
ms:assetid: 362dbe5e-8ee9-4aba-8c26-5907312b4a60
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ552447(v=OCS.15)
ms:contentKeyID: 48679558
mtps_version: v=OCS.15
ms.author: jambirk
author: jambirk
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "To allow connections from other XMPP deployments, you must configure XMPP in the Skype for Business Server Control Panel."
---


# Create or edit XMPP partner configuration in Skype for Business Server


Skype for Business Server integrates an Extensible Messaging and Presence Protocol (XMPP) proxy on the Edge Server and an XMPP Gateway on the Front End Server or Front End pool. To allow connections from other XMPP deployments, you must configure XMPP in the Skype for Business Server Control Panel. You configure settings on an XMPP domain basis. To create a new partner association, you do the following.


## To create a new federated partner or edit an existing configuration

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel.

3.  In the left navigation bar, click **Federation and External Access**, and then click **XMPP Federated Partners**.

4.  To create a new configuration, click **New**

5.  To edit an existing configuration, select the configuration and click **Edit**

6.  To create or edit configurations for **XMPP Federated Partners**, you define the following settings:

7.  **Primary domain** (Required). The primary domain is the base domain of the XMPP partner. For example, you would enter **fabrikam.com** for the XMPP partner domain name. This is a required entry.

8.  **Description**. The description is for notes or other identifying information for this particular configuration. This entry is optional.

9.  **Additional domains**. Additional domains are domains that are a part of your XMPP partner’s domain that should be included as part of the allowed XMPP communication. For example, if the primary domain is **fabrikam.com**, then you would list all other domains that are under fabrikam.com that you will communicate with by way of XMPP. For example, you might enter **corp.fabrikam.com** and **it.fabrikam.com** for the Corporate XMPP domain and the Information Technologies XMPP domain under fabrikam.com’s main XMPP domain.

10. **Partner type**. The **Partner type** is a required setting and gives you a selection of three choices in a drop-down menu. You must choose one of the following to describe and enforce what contacts can be added. You can select from:
    
      - **Federated**. A **Federated** partner type is a trusted connection between a Skype for Business Server or Office Communications Server partner deployment.
    
      - **Public verified**. A **Public verified** partner is when contacts that are part of a deployment that are verified by the provider can be added to your user’s list of contacts. Invites can be sent from the Skype for Business user, or the Skype for Business  user can accept invites from the partner contact.
    
      - **Public unverified**. A **Public unverified** relationship implies that there is no established and verifiable status between the two deployments. A Skype for Business user must invite the unverified contact for that contact to be able to add the Skype for Business user to his contact list. For example, Google GTalk is not a public verified XMPP service as it relates to Skype for Business Server. A GTalk user will not be able to add the Skype for Business user as a contact unless there is an explicit invite sent from the Skype for Business user.

11. Notes on stream negotiation and the security methods Transport Layer Security (TLS) and Software Authentication and Security Layer (SASL):
    
    The **XMPP Standards Foundation** (XSF) and the **Internet Engineering Task Force** (IETF) define a set of rules and standards for using and managing TLS client certificates, TLS server certificates, and the SASL mechanism. Using TLS and SASL is the required process for securing the XMPP stream. From the XMPP Standards document **XEP-0178**, “specifies a recommended protocol flow for use of the SASL EXTERNAL mechanism with PKIX certificates, especially when an XMPP service indicates that TLS is mandatory-to-negotiate.” PKIX, as stated in the XSF documentation, refers to public key infrastructure, also known as PKI.
    
    Refer to the XSF document XEP-0178 for more details on the XMPP requirements. For details, refer to “XEP-0178: Best Practices for Use of SASL EXTERNAL with Certificates”. <http://xmpp.org/extensions/xep-0178.html>
    
    Refer to the IETF document “Extensible Messaging and Presence Protocol (XMPP): Core“, Section 5.0, STARTTLS Negotiation <http://tools.ietf.org/html/rfc6120>.
    
      - **TLS Negotiation**. Defines the TLS negotiation rules. An XMPP service can require TLS, can make TLS optional, or you define that TLS is not supported. Choosing Optional leaves the requirement up to the XMPP service for a mandatory-to-negotiate decision. To view all possible settings and details for SASL, TLS and Dialback negotiation –including not valid and known error configurations - see [Negotiation settings for XMPP federated partners](negotiation-settings-for-xmpp-federated-partners.md).
        
        - **Required**. The XMPP service requires TLS negotiation.

        - **Optional**. The XMPP service indicates that TLS is mandatory-to-negotiate.
 
        - **Not Supported**. The XMPP service does not support TLS.
    
      - **SASL negotiation**. Defines the SASL negotiation rules. An XMPP service can require SASL, can make SASL optional, or you define that SASL is not supported. Choosing Optional leaves the requirement up to the partner XMPP service for a mandatory-to-negotiate decision.

        > [!WARNING]  
        > SASL requires TLS. To use SASL, TLS must either be required or optional. Any configuration that defines SASL as either required or optional must have TLS support. When clicking <STRONG>Commit</STRONG> to save your changes, if you have not set TLS to required or optional, you will be warned that SASL must have TLS support and your changes are not saved. To resolve the error, set TLS to <STRONG>Required</STRONG> or <STRONG>Optional</STRONG>. If use of SASL is optional and TLS negotiation support is not possible, you must set SASL negotiation to <STRONG>Not Supported</STRONG>. Confirm with the XMPP service what the proper negotiation streams must be for TLS and SASL or service interruption will occur.

        - **Required**. The XMPP service requires SASL negotiation.    

        - **Optional**. The XMPP service indicates that SASL is mandatory-to-negotiate.

        - **Not Supported**. The XMPP service does not support SASL.
    
      - **Dialback negotiation**. Dialback negotiation is defined by the XSF in document **XEP-220 : Server Dialback** <http://xmpp.org/extensions/xep-0220.html>. The server dialback process uses the domain name system (DNS) and an authoritative server to verify that the request came from a valid XMPP partner. To do this, the originating server creates a message of a specific type with a generated dialback key and looks up the receiving server in DNS. The originating server sends the key in an XML stream to the resulting DNS lookup, presumably the receiving server. On receipt of the key over the XML stream, the receiving server does not respond to the originating server, but sends the key to a known authoritative server. The authoritative server verifies that the key is either valid or not valid. If not valid, the receiving server does not respond to the originating server. If the key is valid, the receiving server informs the originating server that the identity and key is valid and the conversation can commence.
        
        There are two valid states for **Dialback negotiation**:

        - **True**. The XMPP server is configured to use Dialback negotiation if a request should be received from an originating server

        - **False**. The XMPP server is not configured to use Dialback negotiation and if a request should be received from an originating server, it will be ignored


