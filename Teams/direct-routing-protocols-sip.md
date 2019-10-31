---
title:  Phone System Direct Routing
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.date: 01/28/2019
ms.topic: article
ms.service: msteams
audience: admin
ms.collection:  
- Teams_ITAdmin_Help
- M365-voice
ms.reviewer: nmurav
search.appverid: MET150
description: Direct Routing protocols
appliesto:
- Microsoft Teams
---

# Direct Routing - SIP protocol

This article describes how Direct Routing implements the Session Initiation Protocol (SIP). To properly route traffic between a Session Border Controller (SBC) and the SIP proxy, some SIP parameters MUST have specific values. This article is intended for voice administrators who are responsible for configuring the connection between the on-premises SBC and the SIP proxy service.

## Processing the incoming request: finding the tenant and user

On an incoming call, the SIP proxy needs to find the tenant to which the call is destined and to the specific user within this tenant (the callee). The tenant administrators might configure non-DID numbers, for example +1001, in multiple tenants. It is important to find the specific tenant where to perform lookup of the number as the non-DID numbers might be the same in multiple Office 365 tenants.   **NEED TO CLARIFY WHAT THE LAST SENTENCE MEANS.  DO WE MEAN THE FOLLOWING?**

It is important to find the specific tenant on which to perform number lookup because the non-DID numbers might be the same in multiple Office 365 tenants.

The section below describes how the SIP proxy finds the tenant, finds the user, and performs authentication of the SBC on the incoming connection.
The following is an example of the SIP Invite message on an incoming call:

| Parameter name | Example of the value | 
| :---------------------  |:---------------------- |
| Request-URI | INVITE sip:+18338006777@sip.pstnhub.microsoft.com SIP /2.0 |
| Via Header | Via: SIP/2.0/TLS sbc1.adatum.biz:5058;alias;branch=z9hG4bKac2121518978 | 
| Max-Forwards header | Max-Forwards:68 |
| From Header | From Header From: <sip:7168712781@sbc1.adatum.biz;transport=udp;tag=1c747237679 |
| To Header | To: sip:+183338006777@sbc1.adatum.biz | 
| CSeq header | CSeq: 1 INVITE | 
| Contact Header | Contact: <sip: 68712781@sbc1.adatum.biz;transport=tls> | 

On receiving the invite, the SIP proxy performs the following steps:

1. Check the certificate. On the initial connection, the Direct Routing **service** takes the FQDN name presented in the Contact header and matches it to the Common Name or Subject Alternative name of the presented certificate. The SBC name MUST match one of the following options:

   - Option 1. The full FQDN name presented in the Contact header must match the Common Name/Subject Alternative name of the presented certificate.  OR

   - Option 2. The domain portion of the FQDN name presented in the Contact header (for example adatum.biz of the FQDN name sbc1.adatum.biz) must matche the wildcard value in Common Name/Subject Alternative Name (for example *.adatum.biz).

2. Try to find a tenant using the full FQDN name presented in Contact.  

   Check if the FQDN name from the Contact header (sbc1.adatum.biz) is registered as a DNS name in any Office 365 tenant. If found, the lookup of the user is performed in the tenant that has the SBC FQDN registered as a Domain name. If not found, Step 3 applies.   **NEED TO CLARIFY MEANING**

3. Only applies if Step 2 failed. Remove the host portion from the FQDN, presented in the Contact header (FQDN: sbc12.adatum.biz, after removing the host portion: adatum.biz) and check if this name is registered as a DNS name in any Office 365 tenant. If found, the user lookup is performed in this tenant. If not found, the call fails.

4. Using the phone number presented in the Request-URI, perform the reverse number lookup within the tenant found in Step 2 or 3. Match the presented phone number to a user SIP URI within the tenant found on the previous step.

5. Apply trunk settings. Find the parameters set by the tenant admin for this SBC.

   It is not supported to have a 3rd party SIP Proxy or User Agent Server between the **Microsoft SIP Hub**  **IS THIS ANOTHER NAME FOR DIRECT ROUTING SERVICE** and the paired SBC, which might modify the Request URI, created by the paired SBC.

   The requirements for the two lookups (Step 2 and 3) needed for the scenario where one SBC is interconnected to many tenants (carrier scenario) and covered later in the document.

### 3.2.1   Detailed requirements for Contact Header and Request-URI

#### Contact header

For all incoming calls to Microsoft SIP Hub  **SAME QUESTION: IS THIS ANOTHER NAME FOR DIRECT ROUTING SERVICE**, the Contact Header MUST have the paired SBC FQDN in URI hostname:

Syntax: Contact:  <sip:phone or sip address@FQDN of the SBC;transport=tls> 

This name MUST also be in Common Name or Subject Alternative name field(s) of the presented certificate.  It is supported using wildcard values of the name(s) in the Common Name or Subject Alternative Name fields of the certificate.   **NEED CLARIFICATION**

The support for wildcards is described in [RFC 2818, section 3.1](https://tools.ietf.org/html/rfc2818#section-3.1), specifically:

"Names may contain the wildcard character * which is considered to match any single domain name component or component fragment. E.g., *.a.com matches foo.a.com but not bar.foo.a.com. f*.com matches foo.com but not bar.com."

If more than one value in the Contact header presented in a SIP message sent by SBC, only the FQDN portion of the first value of the Contact header used.

#### Request-URI (might be removed after delivering trunk normalization rules in SIP Proxy)

For all incoming calls, the Request-URI used to match the phone number to a user.   **NEED CLARIFICATION**

The phone number MUST contain a plus sign (+) as shown in the following example. (Note there is work ongoing to add trunk normalization rules in SIP Proxy, so this rule might be lifted).  **LEAVE PARENTHETICAL REFERENCE OUT? USE CURRENTLY INSTEAD**  

```
INVITE sip:+18338006777@sip.pstnhub.microsoft.com SIP /2.0
```

## 3.3  Contact and Record-Route headers considerations

The SIP Hub needs to calculate the next hop FQDN in new in-dialog client transactions (for example Bye or Re-Invite), and when replying to SIP Options. Either Contact or Record-Route used. 

According to the RFC 3261 is it mandatory to use Contact header in any request which can result in the establishing a new dialog. The Record-Route only required if a proxy wants to stay on the path of future requests in a dialog. 

Microsoft recommends using only Contact header and do not present Record-Route to SIP Hub for the following reasons:

- Per RFC 3261, the Record -Route is used if a proxy wants to stay on the path of future requests in a dialog, which is not essential as all traffic goes between the Microsoft SIP Hub and the paired SBC. There is no need for an intermediate proxy server between the SBC and Microsoft SIP Hub.

- The other factor, the Microsoft SIP Hub uses only Contact header (and not Record-Route) to determine the next hop when sending outbound ping Options (and not Record-Route). Configuring only one parameter (Contact) instead of two (Contact and Record-Route) simplifies the administration.

To calculate the next hop the SIP Hub uses:

- Priority 1. Top-level Record-Route. If the top-level Record-Route contains the FQDN name or IP, the FQDN name or IP used to make outbound in-dialog connection;

- Priority 2. Contact header. If Record-Route does not exist, the SIP hub will look up the value of the Contact header to make the outbound connection (recommended configuration)

If both Contact and Record-Route used the SBC administrator must keep their values identical which can be an administrative overhead. 

### Use of FQDN Name in Contact or Record-Route

Use of IP address is not supported in either Record-Route or Contact. The only supported option is an FQDN, which also MUST match either Common Name or Subject Alternative Name of the SBC certificate (wildcard values in the certificate supported).

If an IP address presented in the Record-route or Contact, the certificate check fails and calling experience breaks.

If FQDN does not match the value of the Common or Subject Alternative Name in the presented certificate, the call also fails. 

## Inbound call: SIP dialog description

The call flow is slightly different between the non-bypass and bypass modes. The table below summarizeS the main difference and similarities between the two modes:

| Parameter name | Non-bypass mode | Bypass mode
| :---------------------  |:---------------------- |:----------------|
| Media candidates in 183 and 200 messages coming from | Media processors | Clients | 
| Number of 183 messages SBC can receive | One per session | Multiple | 
| Call can be with provisional answer (183) | Yes | Yes |
| Call can be without provisional answer (183) | Yes | Yes |

### 3.4.1   Non-Media Bypass flow

Teams user might have multiple endpoints logged in at the same time. For example, Teams for Windows client, Teams for iPhone client, and Teams Phone (which is Teams Android client). Each endpoint might signal in HTTP rest:

-   Call progress – converted by SIP Proxy to the 180 SIP message. On receiving of 180 the SBC must generate the local ringing

-   Media Answer – converted by SIP Proxy to 183 with media candidates in SDP. On receiving of which the SBC expected to connect to the media candidates received in the SDP message. Note in some cases the Media Answer might not be generated, the end point might answer with “Call Accepted” message

-   Call accepted – converted by the SIP Proxy to 200 SIP messages with SDP. On receiving of 200 SIP message the SBC is expected to send and receive media to and from the provided SDP candidates.

#### 3.4.1.1    Multiple endpoints ringing with provisional answer

1.  On receiving the first Invite from the SBC, the SIP Proxy sends "SIP SIP/2.0 100 Trying" immediately and notifies the all end user endpoints about incoming call. 

2.  Each endpoint upon notification from SIP Proxy will start ringing and sending Call progress” to SIP Proxy. As Teams user can have multiple end points SIP proxy might receive multiple Call Progress messages

3.  On receiving every Call Progress message SIP Proxy converts the call progress, received from the clients to a SIP message "SIP SIP/2.0 180 Trying". The 180 Trying will be sent as many times as SIP Proxy received call progress notification from clients. Interval of sending such messages defined by interval of receiving the messages from Call Controller. On the picture below there are two 180 messages generated by the SIP Proxy, meaning that user logged into three Teams clients and each client send the call progress. Every message will be a separate session (parameter “tag” in “To” field is different)

4.  Once an endpoint generates media answer with IP addresses of end point’s media candidates, the Sip Proxy converts the message received from the client to a "SIP 183 Session Progress" SIP message with SDP from the client replaced by the SDP from the Media Processor. On the picture below the end point from Fork 2 answered the call. If trunk is non-Bypassed the 183 SIP message generated only once (either Ring Bot or Client End Point). The 183 might came on existing fork or start a new one

5.  Call Acceptance message with the final candidates of the endpoint which accepted the call. “Call Acceptance” message is converted to 200 SIP message. 


INSERT GRAPHIC HERE

#### 3.4.1.2    Multiple endpoints ringing without provisional answer

1.  On receiving the first Invite from the SBC, the SIP Proxy sends "SIP SIP/2.0 100 Trying" immediately and notifies the all end user endpoints about incoming call. 

2.  Each endpoint upon notification from SIP Proxy will start ringing and sending Call progress” to SIP Proxy. As Teams user can have multiple end points SIP proxy might receive multiple Call Progress messages

3.  On receiving every Call Progress message SIP Proxy converts the call progress, received from the clients to a SIP message "SIP SIP/2.0 180 Trying". The 180 Trying will be sent as many times as SIP Proxy received call progress notification from clients. Interval of sending such messages defined by interval of receiving the messages from Call Controller. On the picture below there are two 180 messages generated by the SIP Proxy, meaning that user logged into three Teams clients and each client send the call progress. Every message will be a separate session (parameter “tag” in “To” field is different)

4.  Call Acceptance message with the final candidates of the endpoint which accepted the call. “Call Acceptance” message is converted to 200 SIP message.

INSERT GRAPHIC HERE

### Media bypass flow

The same messages (100 Trying, 180, 183) are used in the media bypass scenario. 

The schema below shows an example of the bypass call flow. Note that the media candidates can come from different endpoints. 

INSERT GRAPHIC HERE

## Replaces option

The SBC must support Invite with Replaces

## Size fo SDP considerations

The Direct Routing interface might send a SIP message exceeding 1,500 bytes.  The size of SDP primarily causes this. However, if there is a UDP trunk behind the SBC, it might reject such message if forwarded from Microsoft SIP Hub to the Trunk unmodified. We do recommend stripping some values in SDP on SBC when sending the message to the UDP trunks. For example, the ICE candidates or unused codecs can be removed.

## 3.7  Call transfer

Direct Routing supports two methods for call transfer:

- Option 1. SIP Proxy processes Refer from the client locally and acts as a Referee as described in section 7.1 of RFC 3892

- Option 2. SIP Proxy sends the Refer to the SBC and acts as a Transferor as describing in Section 6 of RFC 5589

High-level difference: in the first case the SIP Proxy terminates the transfer and adds a new Invite, In the second case the SIP proxy sends a Refer to the SBC and expect SBC to handle the Transfer fully.

SIP proxy selects the method, based on capabilities reported by the SBC. 

If the SBC indicates in SIP messages that it supports method “Refer”, the SIP proxy will use Option 2 and for call transfers.

Example of SBC sending the indication of Refer method being supported:

```
ALLOW: INVITE, OPTIONS, INFO, BYE, CANCEL, ACK, PRACK, UPDATE, REFER, SUBSCRIBE, NOTIFY
```

If the SBC doesn’t include the Refer as a supported method, Direct Routing will use Option 1 (SIP Proxy acts as a Referee) . The SBC also must signal supporting of the Notify method  
Example of SBC indicating that Refer method is not supported:

```
ALLOW: INVITE, ACK, CANCEL, BYE, INFO, NOTIFY, PRACK, UPDATE, OPTIONS
```

### SIP proxy processes Refer from the client locally and acts as a Referee

If the SBC indicated that the Refer method is not supported, the SIP proxy acts as a Referee. 

The Refer request that comes from the client will be terminated on the SIP Proxy (Refer request from the client is shown as “Call transfer to Dave” on the picture below), 
description in 7.1 of https://www.ietf.org/rfc/rfc3892.txt 

INSERT GRAPHIC HERE

## SIP proxy send the refer to the SBC and acts as a transferor

This is the preferred method for call transfers, and it is mandatory for devices seeking Media Bypass certification. Call Transfer without the SBC being able to handle Refer is not supported in Media Bypass mode. 

The standard explained in the Section 6 of RFC 5589. THe base RFCs are:

- [Session Initiation Protocol (SIP) Call Control - Transfer](https://tools.ietf.org/html/rfc5589)

- [Session Initiation Protocol (SIP) "Replaces" Header](https://tools.ietf.org/html/rfc3891)

- [Session Initiation Protocol (SIP) "Referred-By" mechanism](https://tools.ietf.org/html/rfc3892)

The option assumes that the SIP proxy acts as a Transferor and sends a REFER **WHY ALL CAPS HERE AND NOT ELSEWHERE** message to SBC. SBC acts as a Transferee and handles the REFER to generate new offer for transfer. There are two possible cases:

- Call transferred to an external PSTN participant. 
- Call transferred goes from one Teams User to another Teams user in the same tenant via the SBC. 

If the call is transferred from a Teams user to another Teams user via SBC, the SBC is expected on receiving the Refer, issue a new invite (start a new dialog) for Transfer Target (which is a Teams User) towards the SIP Proxy, using the information, received in the Refer message. 

To properly populate To/Transferor fields for transaction of the request internally (second case), SIP proxy needs to convey this information in a special manner inside REFER-TO/REFERRED-BY headers. 

SIP proxy will form the REFER-TO as SIP URI comprising of SIP Proxy FQDN in the hostname and a) E.164 phone number in the username part of URI in case transfer target is a phone number or b) x-m and x-t parameters encoding full transfer target MRI and tenant id respectively. 

REFERRED-BY header is a SIP URI with transferor MRI encoded in it as well as transferor tenant Id and other transfer context parameters.

| Parameter | Value | Description |  
|:---------------------  |:---------------------- |:---------------------- |
| x-m | MRI | Full MRI of transferor/transfer target as populated by CC |
| x-t | Tenant ID | x-t Tenant ID Optional Tenant Id as populated by CC |
| x-ti | Transferor Correlation Id | Correlation Id of the call to the transferor |
| x-tt | Transfer target call URI | Encoded call replacement URI |

The size of the Refer Header can be up to 400 symbols in this case. The SBC must support handling Refer messages with size up to 400 symbols.

INSERT GRAPHIC HERE

## Session timer

The SIP Proxy supports (always offers) the Session Timer on non-bypass calls and never offers it of the bypass calls. Use of the Session Timer by the SBC is not mandatory.

##  Use of Request-Uri parameter user=phone

The SIP Proxy analyses the Request-URI and if the parameter user=phone is present the service will handle the Request-URI as a phone number, perming the matching of the number to a user. If parameter is not present the SIP proxy applies heuristics to determine if the Request-URI user type (phone number or a SIP address).

It is recommended to always apply the user=phone to simplify the call setup process.

### History-Info Header

History-Info. The History-Info header is used for retargeting SIP requests and “provide(s) a standard mechanism for capturing the request history information to enable a wide variety of services for networks and end-users” (RFC 4244 – Section 1.1, http://www.ietf.org/rfc/rfc4244.txt). For the Microsoft Phone System this is used in Simulring and Call Forwarding scenarios.  

If sending the History-Info is enabled:
-   The SIP Proxy will insert a parameter containing the associated phone number in individual History-Info entries that comprise the History-Info header sent to the PSTN Controller.  Using only entries that have the phone number parameter, the PSTN Controller will rebuild a new History-Info header, and pass it on to the SIP trunk provider via SIP Proxy

-   History-Info header will be added for simultaneous ring and call forwarding cases

-   History-Info header will not be added for call transfer cases

-   Note that an individual history entry in the reconstructed History-Info header will have the phone number parameter provided combined with the Direct Routing FQDN (sip.pstnhub.microsoft.com) set as the host part of the URI; a parameter of ‘user=phone’ will be added as part of the SIP URI.  Any other parameters associated with the original History-Info header, except for phone context parameters, will be passed thru in the re-constructed History-Info header.  Note that entries that are private (as determined via the mechanisms defined in Section 3.3 of RFC 4244) will be forwarded as-is since the SIP trunk provider is a trusted peer

-   Inbound History-Info is ignored

Format of History-info header sent by SIP Proxy:

```
sip.pstnhub.microsoft.com?Privacy=history&Reason=SIP%3B\cause%3D486>;index=1.2,
```

If call was redirected several times, information about every redirect included with appropriate reason in chronological order.


Header Example:

History-info: 
<sip:+14257123456@sip.pstnhub.microsoft.com;user=phone?Reason=SIP;cause=302;text=”Move Temporarily”>;index=1
<sip:+14257123457@sip.pstnhub.microsoft.com;user=phone?Reason=SIP;cause=496;text=”User Busy”>;index=1.1

The History-Info is protected by mandatory TLS mechanism. 

## SBC connection to Direct Routing and Failover mechanism

Please refer to  Failover mechanism for SIP Signaling

## Retry-After

In cases if a Direct Routing datacenter is busy, the interface can send to the SBC Retry-After message with interval 1 second. 
When the SBC receives a 503 with a Retry-After header in response to an INVITE the SBC must terminate that connection and try next available Microsoft datacenter. 

## ICE Restart: Media Bypass call transferred to an endpoint which does not support Media Bypass

SBC MUST support ICE restart as described in https://tools.ietf.org/html/rfc5245#section-9.1.1.1 
The restart in Direct Routing implemented according to this paragraph of RFC:

*To restart ICE, an agent MUST change both the ice-pwd and the ice-ufrag for the media stream in an offer.  Note that it is permissible to use a session-level attribute in one offer, but to provide the same ice-pwd or ice-ufrag as a media-level attribute in a subsequent offer.  This is not a change in password, just a change in its representation, and does not cause an ICE restart.*

*An agent sets the rest of the fields in the SDP for this media stream as it would in an initial offer of this media stream (see
Section 4.3).  Consequently, the set of candidates MAY include some, none, or all of the previous candidates for that stream and MAY include a totally new set of candidates gathered as described in Section 4.1.1.*

In case if call initially was established with Media Bypass and the call transferred to a SfB client Direct Routing need to insert a Media Processor as it is not supported to use Direct Routing with SfB client with Media Bypass. Direct Routing starts ICE restart process by  changing the ice-pwd and ice-ufrag and offering new media candidates in a reinvite. 


