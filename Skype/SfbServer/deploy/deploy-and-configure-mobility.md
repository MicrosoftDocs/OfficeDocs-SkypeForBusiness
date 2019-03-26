---
title: "Deploy and Configure Mobility for Skype for Business Server"
ms.reviewer: 
ms.author: heidip
author: microsoftheidi
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 8ec6197a-3d1e-4b42-9465-564044cdab1a
description: "This article will walk you through the steps to configure an existing Skype for Business Server installation to use the Mobility service, allowing your mobile devices to be able to take advantage of Skype for Business Server Mobility features."
---

# Deploy and Configure Mobility for Skype for Business Server  
 
This article will walk you through the steps to configure an existing Skype for Business Server installation to use the Mobility service, allowing your mobile devices to be able to take advantage of Skype for Business Server Mobility features.
  
Having reviewed the [Plan for Mobility for Skype for Business Server](../plan-your-deployment/mobility.md) article, you should be ready to proceed with the steps below to deploy Mobility into your Skype for Business Server environment. The steps are as follows (and we're including in this table a permissions list):
  
|**Phase**|**Permissions**|
|:-----|:-----|
|[Create DNS records](deploy-and-configure-mobility.md#CreateDNSRec) <br/> |Domain Admins  <br/> DNSAdmins  <br/> |
|[Modify certificates](deploy-and-configure-mobility.md#ModCerts) <br/> |Local Administrator  <br/> |
|[Configure the reverse proxy](deploy-and-configure-mobility.md#ConfigRP) <br/> |Local Administrator  <br/> |
|[Configure Autodiscover for Mobility with hybrid deployments](deploy-and-configure-mobility.md#ConfigAutoD) <br/> |Domain Admins  <br/> |
|[Test your Mobility deployment](deploy-and-configure-mobility.md#TestMobility) <br/> |CsAdministrator  <br/> |
|[Configure for push notifications](deploy-and-configure-mobility.md#ConfigPush) <br/> |RtcUniversalServerAdmins  <br/> |
|[Configure Mobility policy](deploy-and-configure-mobility.md#ConfigMob) <br/> |CsAdministrator  <br/> |
   
All the following sections contain steps that assume you've read the Planning topic. If anything's confusing you, feel free to check out the information there.

> [!NOTE]
> MCX (Mobility Service) support for legacy mobile clients is no longer available in Skype for Business Server 2019. All current Skype for Business mobile clients already use Unified Communications Web API (UCWA) to support instant messaging (IM), presence, and contacts. Users with legacy clients using MCX will need to upgrade to a current client.
  
## Create DNS records
<a name="CreateDNSRec"> </a>

You may already have these as part of your Skype for Business Server environment, but you do need to create the following records for Autodiscovery to work:
  
- An internal DNS record to support mobile users who're connecting from within your organization's network.
    
- An external (or public) DNS record to support mobile users who're connecting from outside your organization's network.
    
These records can be either A (host) names or CNAME records (you don't have to make both, we're just including the steps for everything here).
  
### Create an internal DNS CNAME record

1. Log into a DNS server in your network that's either a member of the **Domain Admins** group or the **DnsAdmins** group.
    
2. Click **Start**, Choose **Administrative Tools** (you may need to **Search** for it if it's not an option off the Start menu), and then click **DNS** to open the DNS administrative snap-in.
    
3. In the left-hand pane of the console window, you'll need to go to the domain that's home to your Skype for Business Server's Front End Servers, and expand the **Forward Lookup Zones** there.
    
4. Take a moment to see which of the following you have:
    
   - Any host A or AAAA records for your Front End Server (Standard or Enterprise) or Front End pool(s).
    
   - Any host A or AAAA records for a Director or Director pool (an optional configuration you may have in your deployment).
    
5. Once you've noted this, right-click your SIP domain name, and then choose **New Alias (CNAME)** from the menu.
    
6. In the **Alias name** textbox, type lyncdiscoverinternal for your host name, for the internal Autodiscover service URL.
    
7. In the **Fully qualified domain name (FQDN for target host**, you'll need to type or browse to the internal Web Services FQDN for your Front End pool (or single Front End Server, or Director pool or Director), identified in step 4 above. Click OK when this is entered.
    
8. You'll need to create a new Autodiscover CNAME record in the forward lookup zone for each SIP domain supported in your Skype for Business Server environment.
    
### Create an external DNS CNAME record

1. These steps are generic, because we can't tell what public DNS provider you might be using, but we still want to help you out. Please log into your public DNS provider with an account that will be able to make new DNS records there.
    
2. At this point in time, a SIP domain should already exist there for Skype for Business Server. Expand the **Forward Lookup Zone** for this SIP domain, or otherwise open it up.
    
3. Take a moment to see which of the following you have:
    
   - Any host A or AAAA records for your Front End Server (Standard or Enterprise) or Front End pool(s).
    
   - Any host A or AAAA records for a Director or Director pool (an optional configuration you may have in your deployment).
    
4. Once you have that information, you should be able to select an option for creating a **New Alias (CNAME)**.
    
5. Now you should be able to enter an **Alias Name**, you need to enter lyncdiscover here for the external Autodiscover service URL.
    
6. Next there should be an area to enter in a **FQDN for target host**, this will need to be the FQDN for your Front End pool (or single Front End Server, or Director pool or Director), identified in step 3 above.
    
7. You may need to save here, or if you need to create additional CNAME records in the forward lookup zone of each SIP domain in your Skype for Business Server environment, you should do that, but once you're ready, save your work.
    
### Create an internal DNS A record

1. Log into a DNS server in your network that's either a member of the **Domain Admins** group or the **DnsAdmins** group.
    
2. Click **Start**, Choose **Administrative Tools** (you may need to **Search** for it if it's not an option off the Start menu), and then click **DNS** to open the DNS administrative snap-in.
    
3. In the left-hand pane of the console window, you'll need to go to the domain that's home to your Skype for Business Server's Front End Servers, and expand the **Forward Lookup Zones** there.
    
4. Take a moment to see which of the following you have:
    
   - Any host A or AAAA records for your Front End Server (Standard or Enterprise) or Front End pool(s).
    
   - Any host A or AAAA records for a Director or Director pool (an optional configuration you may have in your deployment).
    
5. Once you've noted this, right-click your SIP domain name, and then choose **New Host (A or AAAA)** from the menu.
    
6. In the **Name** textbox, type lyncdiscoverinternal for your host name, for the internal Autodiscover service URL.
    
7. In the **IP Address** textbox, type the internal Web Services IP address for your Front End pool (or single Front End Server, or Director pool or Director), identified in step 4 above.
    
8. When this is done, click **Add Host**, and then click **OK**.
    
9. You'll need to create a new Autodiscover A or AAAA records in the forward lookup zone for each SIP domain supported in your Skype for Business Server environment. To do this, repeat steps 6-8 as many times as needed.
    
10. When you're done, click **Done**.
    
### Create an external DNS A record

1. These steps are generic, because we can't tell what public DNS provider you might be using, but we still want to help you out. Please log into your public DNS provider with an account that will be able to make new DNS records there.
    
2. At this point in time, a SIP domain should already exist there for Skype for Business Server. Expand the **Forward Lookup Zone** for this SIP domain, or otherwise open it up.
    
3. Take a moment to see which of the following you have:
    
   - Any host A or AAAA records for your Front End Server (Standard or Enterprise) or Front End pool(s).
    
   - Any host A or AAAA records for a Director or Director pool (an optional configuration you may have in your deployment).
    
4. Once you have that information, you should be able to select an option for creating a **New Host A or AAAA**.
    
5. Now you should be able to enter a **Name**, you need to enter lyncdiscover here for the external Autodiscover service URL.
    
6. Next there should be an area to enter in a **IP Addresss**, this will need to be the IP for your Front End pool (or single Front End Server, or Director pool or Director), identified in step 3 above.
    
7. You may need to save here, or if you need to create additional A or AAAA records in the forward lookup zone of each SIP domain for your Skype for Business Server environment, you should do that, but once you're ready, save your work.
    
## Modify certificates
<a name="ModCerts"> </a>

If you have questions about Planning around certificates, we've documented that in our [Plan for Mobility for Skype for Business Server](../plan-your-deployment/mobility.md) article. Once you've reviewed that, we'll walk you through the following:
  
- Do I need new certificates?
    
- Requesting new certificates from your Certificate Authority (CA).
    
- Updating your in-place certificates with the replacements using PowerShell.
    
- Checking the certificates using the Certificates snapin in the Microsoft Management Console (MMC).
    
### Do I need new certificates?

1. First, you may need to check and see what certificates are in-place, and whether or not they have the entries you need. To do that, you'll need to log into your Skype for Business Server with an account that's a local Administrator. This account may also need to have rights to the issuing Certificate Authority (CA), for some of these steps.
    
2. Open the Skype for Business Server Management Shell (you can use Search to find it if you don't have it pinned to your Start menu or task bar).
    
3. It's going to be essential for you to know what certificates have been assigned before you try adding an updated certificate. So at the command, type:
    
   ```
   Get-CsCertificate
   ```

4. The information from Step 3 will be unique to you. You need to look it over to determine if you have a single certificate that's been assigned for multiple things, or whether you have a different certificate assigned for the different components that need them. The **Use** parameter will tell you how a certificate's being used, and the **Thumbprint** parameter will tell you if it's all the same certificate, or multiple certs.
    
5. If you have the SAN entries recommended in our Planning section, you're good. If not, you'll need to request a new certificate, or multiple certificates (depending on your configuration) from your Certificate Authority.
    
### Request a new certificate, or certificates, from your Certificate Authority (CA)

1. After you've checked to see what SAN entries you have, you know you have a **single certificate** (after checking via the steps above), and you learned you don't have all the entries you need. A new certificate request needs to be made to your CA. Open your Skype for Business Server PowerShell:
    
   - For a missing Autodiscover Service SAN (replacing the -Ca parameter with your own Certificate Authority path):
    
   ```
   Request-CsCertificate -New -Type Default,WebServicesInternal,WebServicesExternal -Ca dc\myca -AllSipDomain -verbose
   ```

   - Now, if you have multiple SIP domains, you can't use the AllSipDomain parameter as in the example above. You'll need to use the DomainName parameter instead. And when you use the DomainName parameter, you've got to define the FQDN for the lyncdiscoverinternal and lyncdiscover records. An example would be (replacing the -Ca parameter with your own Certificate Authority path):
    
   ```
   Request-CsCertificate -New -Type Default,WebServicesInternal,WebServicesExternal -Ca dc\myca -DomainName "LyncdiscoverInternal.contoso.com, LyncdiscoverInternal.contoso.net" -verbose
   ```

2. Or, after you've checked to see what SAN entries you have, you found you have **multiple certificates** that don't have all the entries you need. A new certificate request needs to be made to your CA. Open your Skype for Business Server PowerShell:
    
   - For a missing Autodiscover Service SAN (replacing the -Ca parameter with your own Certificate Authority path):
    
   ```
   Request-CsCertificate -New -Type WebServicesInternal -Ca dc\myca -AllSipDomain -verbose
   ```

   - Now, if you have multiple SIP domains, you can't use the AllSipDomain parameter as in the example above. You'll need to use the DomainName parameter instead. And when you use the DomainName parameter, you've got to define the FQDN for the lyncdiscoverinternal and lyncdiscover records. Examples would be (replacing the -Ca parameter with your own Certificate Authority path):
    
   ```
   Request-CsCertificate -New -Type WebServicesInternal -Ca dc\myca -DomainName "LyncdiscoverInternal.contoso.com, LyncdiscoverInternal.contoso.net" -verbose
   ```

   ```
   Request-CsCertificate -New -Type WebServicesExternal -Ca dc\myca -DomainName "Lyncdiscover.contoso.com, Lyncdiscover.contoso.net" -verbose
   ```

   - Once the new certificates have been generated by the CA, you're going to need to assign them.
    
### Assign certificates using Skype for Business Server Management Shell

- Depending on what you found in the Do I need new certifications section above, you need to run **one** of the following.
    
  - If you have a single certificate for everything (the thumbprints are identical) then you need to run this:
    
  ```
  Set-CsCertificate -Type <certificate(s) from the Use parameter> -Thumbprint <unique identifier>
  ```

  - If you've got different certificates for things (the thumbprints are all different), run this instead:
    
  ```
  Set-CsCertificate -Type Default -Thumbprint <certificate thumbprint>
  Set-CsCertificate -Type WebServicesInternal -Thumbprint <certificate thumbprint>
  Set-CsCertificate -Type WebServicesExternal -Thumbprint <certificate thumbprint>
  ```

### Viewing certificates in the Microsoft Management Console (MMC)

1. You have an option to look at your certificates using the Certificates snap-in for the MMC. Simply type MMC into search and it should pop up as an application option,.
    
2. To add the Certificates snap-in, you'll need to click **File**, and then **Add/Remove Snap-In...** (or keyboard shortcut **Ctrl+M** would also work). **Certificates** will be an option in the left-hand pane, select it and then **Computer Account** in the pop-up window, then **Next**.
    
3. Still in the pop-up window, in all likelihood you're doing this on the computer that's home to the certificates you need to look at, so leave the selection on **Local Computer** if that's so. If you're working on a remote machine, change the radio button to **Another Computer** and then either enter that computer's FQDN or use the **Browse** button to search for that computer through AD. After selecting the computer, you'll need to click **Finish** when ready, and then **OK** to add the snap-in to the MMC.
    
4. Expand the **Certificates** section in the MMC's left-hand pane. Expand the **Personal** folder as well, and then select **Certificates**. This lets you see the certificates in this store.
    
5. You need to locate the certificate you want to view, right-click on it, and choose **Open**.
    
    > [!NOTE]
    > How do you know what certificate this is? It should be either the single certificate assigned to everything for your farm, or you may have multiple certificates for different things, like Default, Internal Web Services, etc., in which case you may need to look at multiple certificates. Multiple certificates will have the same thumbprint. 
  
6. Once you've gotten to the **Certificate** view, choose **Details**. This will let you see the certificate subject name when you select **Subject**, and the assigned subject name and associated properties are shown.
    
7. You'll also need to check the **Subject Alternate Name** entries. You'll find one or more of the following:
    
   - The pool name for this pool, or the single server name if this isn't a pool.
    
   - The server name that the certificate is assigned to.
    
   - Simple URL records, typically meet and dialin.
    
   - Web Services internal and Web Services external names (for example, webpool01.contoso.net, webpool01.contoso.com), based on choices made in Topology Builder and over-ridden Web Services selections.
    
   - If already assigned, the lyncdiscover.\<sipdomain\> and lyncdiscoverinternal.\<sipdomain\> records.
    
     You'll need to check multiple certificates if you have more than one assigned (check the Note above).
    
8. So, if you find lyncdiscover.\<sipdomain\> and lyncdiscoverinternal.\<sipdomain\> records, you've got this configured already. You can close the MMC.
    
9. If they aren't assigned, you'll either need to make a new certificate request (outlined above) or you need to install them post-request (we recommend the following the PowerShell above for that).
    
## Configure the reverse proxy
<a name="ConfigRP"> </a>

The steps below are not meant to be followed exactly. That's because in previous versions of the product, we'd have walked you through, for example, configuring Threat Management Gateway (TMG) and if you weren't using that, you'd need to work out your own version from there.
  
TMG is no longer being offered by Microsoft as a product, and if you still need to configure it, you can look at the [Lync Server 2013 steps](https://technet.microsoft.com/en-us/library/hh690011%28v=ocs.15%29.aspx). But the following information's intended to be more generally helpful, even if there's no way we can provide specific walkthrough steps for every Reverse proxy out there.
  
We have two main things to consider:
  
- Are you going to be doing your initial Autodiscover request over HTTPS (which we recommend)?
    
  - If you have a web publishing rule, you need to modify it.
    
  - If you don't have a web publishing rule yet, you need to create it.
    
- If you're doing your initial Autodiscover request over HTTP, then you'll need to create or modify that rule as well.
    
> [!NOTE]
> **Important** A Proxy time-out value is a number that will vary from deployment to deployment. You should monitor your deployment and modify the value for the best experience for clients. You may be able to set the value as low as 200. If you are supporting Lync mobile clients in your environment, you should set the value to 960 to allow for push notification time-outs from Office 365, which have a time-out value of 900. It is very likely that you will have to increase the time-out value to avoid client disconnects when the value is too low, or decrease the number if connections through the proxy do not disconnect but clear long after the client has disconnected. Monitoring and baselining what is usual for your environment is the only accurate way to determine the appropriate setting for this value.
  
### Modify the existing web publishing rule for your external Autodiscover SAN and URL

1. Open your Reverse proxy interface.
    
2. You'll need to locate your web publishing rule, and choose the Edit option (it may be on a menu or tab, depending on your Reverse proxy configuration).
    
3. There should be an area that states what this web publishing rule is applied to. You need to modify this rule for incoming sites or requests for sites. You're going to **add** a new entry.
    
4. Type the name of your Autodiscover site (the example we'll use is lyncdiscover.contoso.com), and click **OK** or **Save**, depending on your Reverse proxy's format.
    
5. You may have a new certificate that has the Autodiscover SAN entry in it. That needs to be installed as well and configured for use according to your Reverse proxy's settings. Be sure to save everything when the configuration is completed.
    
6. If your Reverse proxy has a **Test** functionality, then please make use of it, to ensure everything's working properly.
    
7. Now, you may need to repeat these steps if you have a Director or Director pool in your environment (this would mean you have a second rule).
    
### Create a web publishing rule for the external Autodiscover URL

1. Open your Reverse proxy interface.
    
2. You'll need to locate where in the interface you create your web publishing rules, and choose the **New** or **Create** option (it may be on a menu or tab, depending on your Reverse proxy configuration). You are looking for the option to create a new web publishing rule.
    
3. Typically, you will need to enter the following information:
    
   - **Name**: the name for your rule
    
   - **Rule Action**: In this case it's an **Allow** rule, you're letting something pass through your Reverse proxy.
    
   - The **Publishing** rule or option you're choosing would be **single web site or load balancer**.
    
   - This needs to be **SSL** for external access, choose that option.
    
   - You're going to need to publish a path for **Internal Publishing**, and enter the FQDN for the external Web Services on your Front End pool's load balancer (or the FQDN of the Director pool's load balancer if you have one), an example would be sfb_pool01.contoso.local.
    
   - You should type **/\\*** as the path to be published, but you also need to **forward the original host header**.
    
   - There will be an option for **public or external name** details or information. This is the place where you'll be able to enter:
    
   - **Accept requests**, but it should be for the domain name.
    
   - For the **Name**, you should enter **lyncdiscover.** <sipdomain> (this is the external Autodiscover Service URL). Now, if you're creating a rule for the external Web Services URL on the Front End pool, you'll need to type the FQDN for the external Web Services on your Front End pool (for example, lyncwebextpool01.contoso.com).
    
   - There will be a **Path** option, and you'll need to enter **/\\*** here.
    
   - You'll need to select a **SSL Listener** with your up-to-date public certificate.
    
   - **Authentication Delegation** should be set to **No delegation**, but direct client authentication **should** be allowed.
    
   - The rule should be set to **All users**.
    
   - This should be all the information you need to create this rule and allow you to proceed.
    
4. You're going to need to ensure that the **original host header** is forwarded.
    
5. The **Web Server** ports will need to be set as well, you'll need to do the following:
    
   - **Redirect requests to HTTP port** and the port number should be **8080**.
    
   - **Redirect requests to SSL port** and the port number should be **4443**.
    
6. When everything's configured, you'll need to save or apply these, and then you'll want to test the rule.
    
### Create a web publishing rule for port 80 (Optional)

1. Open your Reverse proxy interface.
    
2. You'll need to locate where in the interface you create your web publishing rules, and choose the **New** or **Create** option (it may be on a menu or tab, depending on your Reverse proxy configuration). You are looking for the option to create a new web publishing rule.
    
3. Typically, you will need to enter the following information:
    
   - **Name**: the name for your rule
    
   - **Rule Action**: In this case it's an **Allow** rule, you're letting something pass through your Reverse proxy.
    
   - The **Publishing** rule or option you're choosing would be **single web site or load balancer**.
    
   - This needs to be a **non-secured connection to connect to the published Web server or farm**.
    
   - You're going to need to publish a path for **Internal Publishing**, and enter the FQDN for the **VIP address** of your Front End pool's load balancer, an example would be sfb_pool01.contoso.local.
    
   - You should type **/\\*** as the path to be published, but you also need to **forward the original host header**.
    
   - There will be an option for **public or external name** details or information. This is the place where you'll be able to enter:
    
   - **Accept requests**, but it should be for the domain name.
    
   - For the **Name**, you should enter **lyncdiscover.** <sipdomain> (this is the external Autodiscover Service URL).
    
   - There will be a **Path** option, and you'll need to enter **/\\*** here.
    
   - You'll need to select a web listener, or allow your Reverse proxy to create one for you.
    
   - **Authentication Delegation** should be set to **No delegation**, but direct client authentication **should not** be allowed.
    
   - The rule should be set to **All users**.
    
   - This should be all the information you need to create this rule and allow you to proceed.
    
4. The **Web Server** ports will need to be set, you'll need to do the following:
    
   - **Redirect requests to HTTP port** and the port number should be **8080**.
    
   - **Redirect requests to SSL port** and the port number should be **4443**.
    
5. When everything's configured, you'll need to save or apply these, and then you'll want to test the rule.
    
## Configure Autodiscover for Mobility with hybrid deployments
<a name="ConfigAutoD"> </a>

Hybrid environments in Skype for Business Server are environments that combine an on-premises and O365 environment. When you have Skype for Business Server working in a Hybrid environment, the Autodiscover service needs to be able to locate a user from either of these environments.
  
To let mobile clients discover where a user's located, the Autodiscover service needs to be configured with a new uniform resource locator (URL). The steps are:
  
1. Open Skype for Business Server Management Shell.
    
2. Run the following to get the value of the attribute **ProxyFQDN** for your Skype for Business Server environment:
    
   ```
   Get-CsHostingProvider
   ```

3. Then, still in the shell window, run:
    
   ```
   Set-CsHostingProvider -Identity [identity] -AutodiscoverUrl https://webdir.online.lync.com/autodiscover/autodiscoverservice.svc/root
   ```

    Where [identity] is replaced with the domain name of the shared SIP address space.
    
## Test your Mobility deployment
<a name="TestMobility"> </a>

Once you've deployed Skype for Business Server Mobility Service and Skype for Business Server Autodiscover Service, you'll want to run a test transaction, to make sure your deployment's working right. You can run **Test-CsUcwaConference** to test the ability of two users to create, join and communicate in a conference. You will need two users (real or test) and their full credentials to do this testing. This command will work for both Skype for Business clients as well as Lync Server 2013 clients.
  
For Lync Server 2010 clients on Skype for Business Server 2015, you'll need to run **Test-CsMcxP2PIM** to test. Your Lync Server 2010 users will still have to be actual users, or predefined test users, and you'll need their password credentials.

> [!NOTE]
> MCX (Mobility Service) support for legacy mobile clients is no longer available in Skype for Business Server 2019. All current Skype for Business mobile clients already use Unified Communications Web API (UCWA) to support instant messaging (IM), presence, and contacts. Users with legacy clients using MCX will need to upgrade to a current client.
  
### Test conferencing for Skype for Business and Lync 2013 mobile clients

1. Log on as a member of the **CsAdministrator** role on any computer where **Skype for Business Server Management Shell** and **Ocscore** are installed.
    
2. Start the **Skype for Business Server Management Shell** (you might type the name in search or go to **All Programs** and choose it).
    
3. At the command line, enter:
    
   ```
   Test-CsUcwaConference -TargetFqdn <FQDN of Front End pool> -Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID> -OrganizerSipAddress sip:<SIP address of test user 1> -OrganizerCredential <test user 1 credentials> -ParticipantSipAddress sip:<SIP address of test user 2> -ParticipantCredential <test user 2 credentials> -v
   ```

   It's also possible to set credentials in a script and pass them to the test cmdlet. We have an example of this below.
    
   ```
   $passwd1 = ConvertTo-SecureString "Password01" -AsPlainText -Force
   $passwd2 = ConvertTo-SecureString "Password02" -AsPlainText -Force
   $testuser1 = New-Object Management.Automation.PSCredential("contoso\UserName1", $passwd1)
   $testuser2 = New-Object Management.Automation.PSCredential("contoso\UserName2", $passwd2)
   Test-CsUcwaConference -TargetFqdn pool01.contoso.com -Authentication Negotiate -OrganizerSipAddress sip:UserName1@contoso.com -OrganizerCredential $testuser1 -ParticipantSipAddress sip:UserName2@contoso.com -ParticipantCredential $testuser2 -v
   ```

### Test conferencing for Lync 2010 mobile clients

> [!NOTE]
> MCX (Mobility Service) support for legacy mobile clients is no longer available in Skype for Business Server 2019. All current Skype for Business mobile clients already use Unified Communications Web API (UCWA) to support instant messaging (IM), presence, and contacts. Users with legacy clients using MCX will need to upgrade to a current client.

1. Log on as a member of the **CsAdministrator** role on any computer where **Skype for Business Server Management Shell** and **Ocscore** are installed.
    
2. Start the **Skype for Business Server Management Shell** (you might type the name in search or go to **All Programs** and choose it).
    
3. At the command line, enter:
    
   ```
   Test-CsMcxP2PIM -TargetFqdn <FQDN of Front End pool> -Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID> -SenderSipAddress sip:<SIP address of test user 1> -SenderCredential <test user 1 credentials> -ReceiverSipAddress sip:<SIP address of test user 2> -ReceiverCredential <test user 2 credentials> -v
   ```

   It's also possible to set credentials in a script and pass them to the test cmdlet. We have an example of this below.
    
   ```
   $passwd1 = ConvertTo-SecureString "Password01" -AsPlainText -Force
   $passwd2 = ConvertTo-SecureString "Password02" -AsPlainText -Force
   $tuc1 = New-Object Management.Automation.PSCredential("contoso\UserName1", $passwd1)
   $tuc2 = New-Object Management.Automation.PSCredential("contoso\UserName2", $passwd2)
   Test-CsMcxP2PIM -TargetFqdn pool01.contoso.com -Authentication Negotiate -SenderSipAddress sip:UserName1@contoso.com -SenderCredential $tuc1 -ReceiverSipAddress sip:UserName2@contoso.com -ReceiverCredential $tuc2 -v
   ```

To review the command procedures further, you can check out [Test-CsUcwaConference](https://docs.microsoft.com/powershell/module/skype/test-csucwaconference?view=skype-ps) and [Test-CsMcxP2PIM](https://docs.microsoft.com/powershell/module/skype/test-csmcxp2pim?view=skype-ps).
  
## Configure for push notifications
<a name="ConfigPush"> </a>

Push notifications, in the form of badges, icons, or alerts, can be sent to a mobile device even when the Skype or Lync app is inactive. But what are push notifications? They are event alerts, like a new or missed IM invitation, or for a received voicemail. The Skype for Business Server Mobility service sends these notifications to the cloud-based Skype for Business Server Push Notification Service, which then sends the notifications to the Microsoft Push Notification Service (MSNS) for Windows Phone users.
  
This functionality is unchanged from Lync Server 2013, but if you have a Skype for Business Server, you'll want to do the following:
  
- For a Skype for Business Server Edge Server, add a new hosting provider, Microsoft Skype for Business Online, and then set up hosting provider federation between your organization and Skype for Business Online.
    
- Enable push notifications by running the **Set-CsPushNotificationConfiguration** cmdlet. By default, push notifications are turned off.
    
- Test your federation configuration and push notifications.
    
### Configure your Skype for Business Edge Server for push notifications

1. Log on, with an account that's a member of the **CsAdministrator** role, to a computer where **Skype for Business Server Management Shell** and **Ocscore** are installed.
    
2. Start the **Skype for Business Server Management Shell**.
    
3. Add a Skype for Business Server online hosting provider.
    
   ```
   New-CsHostingProvider -Identity <unique identifier for hosting provider> -Enabled $True -ProxyFQDN <FQDN for the Access Server used by the hosting provider> -VerificationLevel UseSourceVerification
   ```

   As an example:
    
   ```
   New-CsHostingProvider -Identity "SkypeOnline" -Enabled $True -ProxyFQDN "sipfed.online.lync.com" -VerificationLevel UseSourceVerification
   ```

    > [!NOTE]
    > You can't have more than one federation relationship with a single hosting provider. So, if you've already set up a hosting provider that has a federation relationship with sipfed.online.lync.com, don't add another hosting provider for it, even if the identity of the hosting provider is something other than SkypeOnline. 
  
4. Set up the hosting provider federation between your organization and the Push Notification Service at Skype for Business Online. At the command line, you'll need to type:
    
   ```
    New-CsAllowedDomain -Identity "push.lync.com"
   ```

### Enable push notifications

1. Log on, with an account that's a member of the **CsAdministrator** role, to a computer where **Skype for Business Server Management Shell** and **Ocscore** are installed.
    
2. Start the **Skype for Business Server Management Shell**.
    
3. Enable push notifications:
    
   ```
   Set-CsPushNotificationConfiguration -EnableMicrosoftPushNotificationService $True
   ```

4. Enable Federation:
     
   ```
   Set-CsAccessEdgeConfiguration -AllowFederatedUsers $True
   ```

### Test federation and push notifications

1. Log on, with an account that's a member of the **CsAdministrator** role, to a computer where **Skype for Business Server Management Shell** and **Ocscore** are installed.
    
2. Start the **Skype for Business Server Management Shell**.
    
3. Test the federation configuration:
    
   ```
   Test-CsFederatedPartner -TargetFqdn <FQDN of Access Edge server used for federated SIP traffic> -Domain <FQDN of federated domain> -ProxyFqdn <FQDN of the Access Edge server used by the federated organization>
   ```

    As an example:
    
   ```
   Test-CsFederatedPartner -TargetFqdn accessproxy.contoso.com -Domain push.lync.com -ProxyFqdn sipfed.online.lync.com
   ```

4. Test your push notifications:
    
   ```
   Test-CsMcxPushNotification -AccessEdgeFqdn <Access Edge service FQDN>
   ```

    As an example:
    
   ```
   Test-CsMcxPushNotification -AccessEdgeFqdn accessproxy.contoso.com
   ```

## Configure Mobility policy
<a name="ConfigMob"> </a>

You have the ability with Skype for Business Server to determine who can use your Mobility service, Call via Work, voice over IP (VoIP), or video, as well as whether WiFi will be required for VoIP or video. Call via Work lets a mobile user use their work phone number, instead of their mobile phone number, when placing and receiving calls. The person on the other end of the line won't see that mobile user's cell phone number, and it lets that mobile user avoid outgoing call charges. When VoIP and video are set up, users can take and make VoIP calls and video. The settings for WiFi usage determine whether a user's mobile device will be required to use a WiFi network over a cellular data network.
  
Mobility, Call via Work, and the VoIP and video features are all enabled by default. The setting to require WiFi for VoIP and video are disabled. An Admin has the ability to change this, either globally, by site, or by user.
  
To be able to use Mobility features and Call via Work, users need to be:
  
- Enabled for Skype for Business Server
    
- Enabled for Enterprise Voice.
    
- Assigned a Mobility policy that has the **EnableMobility** option set to **True**.
    
For users to be able to use Call via Work, they'll also need to be:
  
- Assigned a voice policy that has the **Enable simultaneous ringing of phones** option selected.
    
- Assigned a Mobility policy that has the **EnableOutsideVoice** set to **True**.
    
> [!NOTE]
> Users who aren't enabled for Enterprise Voice can use their mobile devices to make Skype to Skype VoIP calls or can join conferences by using the Click to Join link while on their mobile devices, if the appropriate options are set for the Voice policy they're associated with. There's more detail in the PLANNING topic. 
  
### Modify global Mobility policy

1. Log on, with an account that's a member of the **CsAdministrator** role, to a computer where **Skype for Business Server Management Shell** and **Ocscore** are installed.
    
2. Start the **Skype for Business Server Management Shell**.
    
3. Turn off access to Mobility and Call via Work globally by typing:
    
   ```
   Set-CsMobilityPolicy -EnableMobility $False -EnableOutsideVoice $False
   ```

    > [!NOTE]
    > You can turn off Call via Work without turning off access to Mobility. But you can't turn off Mobility without also turning off Call via Work. 
  
    For more info, check out [Set-CsMobilityPolicy](https://docs.microsoft.com/powershell/module/skype/set-csmobilitypolicy?view=skype-ps).
    
### Modify Mobility policy by site

1. Log on, with an account that's a member of the **CsAdministrator** role, to a computer where **Skype for Business Server Management Shell** and **Ocscore** are installed.
    
2. Start the **Skype for Business Server Management Shell**.
    
3. You can create a site-level policy, turn off VoIP and video, enable Require WiFi for IP Audio, and Require WiFi for IP Video by site. Type:
    
   ```
   New-CsMobilityPolicy -Identity site:<site identifier> -EnableIPAudioVideo $false -RequireWiFiForIPAudio $True -RequireWiFiforIPVideo $True
   ```

    Learn more at [New-CsMobilityPolicy](https://docs.microsoft.com/powershell/module/skype/new-csmobilitypolicy?view=skype-ps).
    
### Modify Mobility policy by user

1. Log on, with an account that's a member of the **CsAdministrator** role, to a computer where **Skype for Business Server Management Shell** and **Ocscore** are installed.
    
2. Start the **Skype for Business Server Management Shell**.
    
3. Create user level Mobility policies and turn off Mobility and Call via Work by user. Type:
    
   ```
   New-CsMobilityPolicy -Identity <policy name> -EnableMobility $False -EnableOutsideVoice $False
   Grant-CsMobilityPolicy -Identity <user identifier> -PolicyName <policy name>
   ```

    A further example with sample data:
    
   ```
   New-CsMobilityPolicy "tag:disableOutsideVoice" -EnableOutsideVoice $False
   Grant-CsMobilityPolicy -Identity MobileUser1@contoso.com -PolicyName tag:disableOutsideVoice
   ```

    > [!NOTE]
    > You can turn off Call via Work without turning off access to Mobility. But you can't turn off Mobility without also turning off Call via Work. 
  

