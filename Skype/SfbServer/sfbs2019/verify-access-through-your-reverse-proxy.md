---
title: "Verify access through your reverse proxy in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3076a786-e022-4d41-91ec-1bf252b2a468
description: "Use the following procedure to verify that your users can access information on the reverse proxy. You might need to complete the firewall configuration and Domain Name System (DNS) configuration before access will work correctly."
---

# Verify access through your reverse proxy in Lync Server 2013
[]
Use the following procedure to verify that your users can access information on the reverse proxy. You might need to complete the firewall configuration and Domain Name System (DNS) configuration before access will work correctly.
  
### To verify that you can access the website through the Internet

- Open a web browser, type the URLs in the **Address** bar that clients use to access the Address Book files and the website for conferencing as follows: 
    
  - For Address Book Server, type a URL similar to the following: **https:// _externalwebfarmFQDN_/abs** where  _externalwebfarmFQDN_ is the external FQDN of the external web services that hosts Address Book services. The user should receive an HTTP challenge, because directory security on the Address Book Server folder is configured to Windows authentication by default. 
    
  - For conferencing, type a URL similar to the following: **https:// _externalwebfarmFQDN_/meet** where  _externalwebfarmFQDN_ is the external FQDN of the web farm that hosts meeting content. This URL should display the troubleshooting page for conferencing. Alternatively, confirm that your Simple URL for conferencing functions correctly. An example Simple URL for the conference join might be https://meet.contoso.com 
    
  - For distribution group expansion, type a URL similar to the following: **https:// _externalwebfarmFQDN_/GroupExpansion/service.svc**. The user should receive an HTTP challenge, because directory security on the distribution group expansion service is configured to Windows authentication by default.
    
  - For dial-in, type the simple URL similar to the following **https:// _externalwebfarmFQDN_/dialin** where  _externalwebfarmFQDN_ is the external FQDN of the web farm that hosts the dial-in page for dial-in conferencing. The user should be directed to the dial-in page. Alternatively, confirm that your Simple URL dial-in functions correctly. An example Simple URL for dial-in might be https://dialin.contoso.com 
    
  - To confirm that the autodiscover URL is working, type https://lyncdiscover.  _externaldomainFQDN_. The browser should prompt you to open a file. Select Notepad to open it. A typical response would be similar to:
    
  ```
  {"AccessLocation":"External","Root":{"Links":[{"href":"https:\/\/extweb.contoso.com\/Autodiscover\/AutodiscoverService.svc\/root\/domain","token":"Domain"},
  {"href":"https:\/\/extweb.contoso.com\/Autodiscover\/AutodiscoverService.svc\/root\/user","token":"User"},
  {"href":"https:\/\/lyncweb.contoso.com\/Autodiscover\/AutodiscoverService.svc\/root\/oauth\/user","token":"OAuth"}]}}
  
  ```


