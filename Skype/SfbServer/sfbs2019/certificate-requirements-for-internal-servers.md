---
title: "Certificate requirements for internal servers in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 2/17/2017
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 0444cdbd-538c-43b1-b9a1-9d7d6cf818d6
description: "Internal servers that are running Lync Server and that require certificates include Standard Edition server, Enterprise Edition Front End Server, Mediation Server, and Director. The following table shows the certificate requirements for these servers. You can use the Lync Server certificate wizard to request these certificates."
---

# Certificate requirements for internal servers in Lync Server 2013
[]
Internal servers that are running Lync Server and that require certificates include Standard Edition server, Enterprise Edition Front End Server, Mediation Server, and Director. The following table shows the certificate requirements for these servers. You can use the Lync Server certificate wizard to request these certificates. 
  
> [!TIP]
> Wildcard certificates are supported for the subject alternative names associated with the simple URLs on the Front End pool, Front End Server, or Director. For details about wildcard certificate support, see [Wildcard certificate support in Lync Server 2013](wildcard-certificate-support.md). 
  
Although an internal enterprise certification authority (CA) is recommended for internal servers, you can also use a public CA. For a list of public CAs that provide certificates that comply with specific requirements for unified communications (UC) certificates and have partnered with Microsoft to ensure they work with the Lync Server Certificate Wizard, see article Microsoft Knowledge Base 929395, "Unified Communications Certificate Partners for Exchange Server and for Communications Server," at [https://go.microsoft.com/fwlink/p/?linkId=202834](https://go.microsoft.com/fwlink/p/?linkId=202834).
  
Communication with other applications and servers, such as Exchange 2013, requires a certificate that is supported by the other applications and products. For the 2013 release, Lync Server 2013 and other Microsoft server products, including Exchange 2013 and SharePoint Server, support the Open Authorization (OAuth) protocol for server-to-server authentication and authorization. For details, see [Managing server-to-server authentication (OAuth) and partner applications in Lync Server 2013](managing-server-to-server-authentication-oauth-and-partner-applications.md) in the Deployment documentation or the Operations documentation. 
  
For connections from clients running Windows 7 operating system, Windows Server 2008 operating system, Windows Server 2008 R2 operating system, Windows Vista operating system, and Microsoft Lync Phone Edition, Lync Server 2013 includes support for (but does not require) certificates signed using the SHA-256 cryptographic hash function. To support external access using SHA-256, the external certificate is issued by a public CA using SHA-256.
  
The following tables show certificate requirements by server role for Front End pools and Standard Edition servers. All these are standard web server certificates, private key, non-exportable.
  
Note that server enhanced key usage (EKU) is automatically configured when you use the certificate wizard to request certificates.
  
> [!NOTE]
> Each certificate Friendly Name must be unique in the computer store. 
  
> [!NOTE]
> If you have configured sipinternal.contoso.com or sipexternal.contoso.com in your DNS, you will need to add them in the certificate's Subject Alternative Name. 
  
**Certificates for Standard Edition Server**

|**Certificate**|**Subject name/  <br/> Common name**|**Subject alternative name**|**Example**|**Comments**|
|:-----|:-----|:-----|:-----|:-----|
|Default  <br/> |Fully qualified domain name (FQDN) of the pool  <br/> |FQDN of the pool and the FQDN of the server  <br/>  If you have multiple SIP domains and have enabled automatic client configuration, the certificate wizard detects and adds each supported SIP domain FQDNs.  <br/> If this pool is the auto-logon server for clients and strict Domain Name System (DNS) matching is required in group policy, you also need entries for sip.sipdomain (for each SIP domain you have).  <br/> |SN=se01.contoso.com; SAN=se01.contoso.com  <br/> If this pool is the auto-logon server for clients and strict DNS matching is required in group policy, you also need SAN=sip.contoso.com; SAN=sip.fabrikam.com  <br/> |On Standard Edition server, the server FQDN is the same as the pool FQDN.  <br/> The wizard detects any SIP domains you specified during setup and automatically adds them to the subject alternative name.  <br/> You can also use this certificate for Server-to-Server Authentication.  <br/> |
|Web internal  <br/> |FQDN of the server  <br/> | Each of the following:  <br/>  Internal web FQDN (which is the same as the FQDN of the server)  <br/>  Meet simple URLs  <br/>  Dial-in simple URL  <br/>  Admin simple URL  <br/>  Or, a wildcard entry for the simple URLs  <br/> |SN=se01.contoso.com; SAN=se01.contoso.com; SAN=meet.contoso.com; SAN=meet.fabrikam.com; SAN=dialin.contoso.com; SAN=admin.contoso.com  <br/> Using a wildcard certificate:  <br/> SN=se01.contoso.com; SAN=se01.contoso.com; SAN=\*.contoso.com  <br/> |You cannot override the Internal web FQDN in Topology Builder.  <br/> If you have multiple Meet simple URLs, you must include all of them as subject alternative names.  <br/> Wildcard entries are supported for the simple URL entries.  <br/> |
|Web external  <br/> |FQDN of the server  <br/> | Each of the following:  <br/>  External web FQDN  <br/>  Dial-in simple URL  <br/>  Meet simple URLs per SIP domain  <br/>  Or, a wildcard entry for the simple URLs  <br/> |SN=se01.contoso.com; SAN=webcon01.contoso.com; SAN=meet.contoso.com; SAN=meet.fabrikam.com; SAN=dialin.contoso.com  <br/> Using a wildcard certificate:  <br/> SN=se01.contoso.com; SAN=webcon01.contoso.com; SAN=\*.contoso.com  <br/> |If you have multiple Meet simple URLs, you must include all of them as subject alternative names.  <br/> Wildcard entries are supported for the simple URL entries.  <br/> |
   
**Certificates for Front End Server in a Front End Pool**

|**Certificate**|**Subject name/  <br/> Common name**|**Subject alternative name**|**Example**|**Comments**|
|:-----|:-----|:-----|:-----|:-----|
|Default  <br/> |FQDN of the pool  <br/> |FQDN of the pool and FQDN of the server.  <br/>  If you have multiple SIP domains and have enabled automatic client configuration, the certificate wizard detects and adds each supported SIP domain FQDNs.  <br/> If this pool is the auto-logon server for clients and strict DNS matching is required in group policy, you also need entries for sip.sipdomain (for each SIP domain you have).  <br/> |SN=eepool.contoso.com; SAN=eepool.contoso.com; SAN=ee01.contoso.com  <br/> If this pool is the auto-logon server for clients and strict DNS matching is required in group policy, you also need SAN=sip.contoso.com; SAN=sip.fabrikam.com  <br/> |The wizard detects any SIP domains you specified during setup and automatically adds them to the subject alternative name.  <br/> You can also use this certificate for Server-to-Server Authentication.  <br/> |
|Web Internal  <br/> |FQDN of the pool  <br/> | Each of the following:  <br/>  Internal web FQDN (which is NOT the same as the FQDN of the server)  <br/>  Server FQDN  <br/>  Lync pool FQDN  <br/>  Meet simple URLs  <br/>  Dial-in simple URL  <br/>  Admin simple URL  <br/>  Or, a wildcard entry for the simple URLs  <br/> |SN=ee01.contoso.com; SAN=ee01.contoso.com; SAN=meet.contoso.com; SAN=meet.fabrikam.com; SAN=dialin.contoso.com; SAN=admin.contoso.com  <br/> Using a wildcard certificate:  <br/> SN=ee01.contoso.com; SAN=ee01.contoso.com; SAN=\*.contoso.com  <br/> |If you have multiple Meet simple URLs, you must include all of them as subject alternative names.  <br/> Wildcard entries are supported for the simple URL entries.  <br/> |
|Web external  <br/> |FQDN of the pool  <br/> | Each of the following:  <br/>  External web FQDN  <br/>  Dial-in simple URL  <br/>  Admin simple URL  <br/>  Or, a wildcard entry for the simple URLs  <br/> |SN=ee01.contoso.com; SAN=webcon01.contoso.com; SAN=meet.contoso.com; SAN=meet.fabrikam.com; SAN=dialin.contoso.com  <br/> Using a wildcard certificate:  <br/> SN=ee01.contoso.com; SAN=webcon01.contoso.com; SAN=\*.contoso.com  <br/> |If you have multiple Meet simple URLs, you must include all of them as subject alternative names.  <br/> Wildcard entries are supported for the simple URL entries.  <br/> |
   
**Certificates for Director**

|**Certificate**|**Subject name/  <br/> Common name**|**Subject alternative name**|**Example**|
|:-----|:-----|:-----|:-----|
|Default  <br/> |FQDN of the Director pool  <br/> |FQDN of the Director, FQDN of the Director pool  <br/> If this pool is the auto-logon server for clients and strict DNS matching is required in group policy, you also need entries for sip.sipdomain (for each SIP domain you have).  <br/> |SN=dir-pool.contoso.com; SAN=dir-pool.contoso.com; SAN=dir01.contoso.com  <br/> If this Director pool is the auto-logon server for clients and strict DNS matching is required in group policy, you also need SAN=sip.contoso.com; SAN=sip.fabrikam.com  <br/> |
|Web Internal  <br/> |FQDN of the server  <br/> | Each of the following:  <br/>  Internal web FQDN (which is the same as the FQDN of the server)  <br/>  Server FQDN  <br/>  Lync pool FQDN  <br/>  Meet simple URLs  <br/>  Dial-in simple URL  <br/>  Admin simple URL  <br/>  Or, a wildcard entry for the simple URLs  <br/> |SN=dir01.contoso.com; SAN=dir01.contoso.com; SAN=meet.contoso.com; SAN=meet.fabrikam.com; SAN=dialin.contoso.com; SAN=admin.contoso.com  <br/> SN=dir01.contoso.com; SAN=dir01.contoso.com SAN=\*.contoso.com  <br/> |
|Web external  <br/> |FQDN of the server  <br/> | Each of the following:  <br/>  External web FQDN  <br/>  Dial-in simple URL  <br/>  Admin simple URL  <br/>  Or, a wildcard entry for the simple URLs  <br/> |The Director external web FQDN must be different from the Front End pool or Front End Server.  <br/> SN=dir01.contoso.com; SAN=directorwebcon01.contoso.com SAN=meet.contoso.com; SAN=meet.fabrikam.com; SAN=dialin.contoso.com  <br/> SN=dir01.contoso.com; SAN=directorwebcon01.contoso.com SAN=\*.contoso.com  <br/> |
   
If you have a stand-alone Mediation Server pool, the Mediation Servers in it each need the certificates listed in the following table. If you collocate Mediation Server with the Front End Servers, the certificates listed in the "Certificates for Front End Server in Front End Pool" table earlier in this topic are sufficient.
  
**Certificates for Stand-alone Mediation Server**

|**Certificate**|**Subject name/  <br/> Common name**|**Subject alternative name**|**Example**|
|:-----|:-----|:-----|:-----|
|Default  <br/> |FQDN of the pool  <br/> |FQDN of the pool  <br/> FQDN of pool member server  <br/> |SN=medsvr-pool.contoso.net; SAN=medsvr-pool.contoso.net; SAN=medsvr01.contoso.net  <br/> |
   
**Certificates for Survivable Branch Appliance**

|**Certificate**|**Subject name/  <br/> Common name**|**Subject alternative name**|**Example**|
|:-----|:-----|:-----|:-----|
|Default  <br/> |FQDN of the appliance  <br/> |SIP.\<sipdomain\> (need one entry per SIP domain)  <br/> |SN=sba01.contoso.net; SAN=sip.contoso.com; SAN=sip.fabrikam.com  <br/> |
   
## See also

#### 

[Wildcard certificate support in Lync Server 2013](wildcard-certificate-support.md)

