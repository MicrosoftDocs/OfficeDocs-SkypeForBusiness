---
title: Migrate online users to on-premises in Skype for Business Server
ms.prod: SKYPEFORBUSINESS
ms.assetid: 0e29605b-db2d-4cbf-b6a9-15db6b9fdabc
---


# Migrate online users to on-premises in Skype for Business Server
[] **Summary:** Learn how to migrate user accounts that were originally enabled for Lync or Skype for Business Online to on-premises Skype for Business.
> [!IMPORTANT]
> These steps are necessary only for migrating user accounts that were originally enabled for Lync or Skype for Business Online before you deployed Lync or Skype for Business on-premises. To move users who were originally enabled for an on-premises deployment, then later moved to online, see  [Manage users in a Skype for Business Server 2015 hybrid deployment](manage-users-in-a-skype-for-business-server-2015-hybrid-deployment.md). > Additionally, all users being moved must have accounts in the on-premises Active Directory. 
  
    
    


### Migrating user accounts originally enabled online to an on-premises deployment


1. First, make sure that your organization is configured for hybrid, including Azure Active Directory Connect and sync tools. For more information, see  [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online](plan-hybrid-connectivity-between-skype-for-business-server-and-skype-for-busines.md).
    
  - On your on-premises deployment, in the Skype for Business Server Management Shell, type the following cmdlets to create the hosting provider for Skype for Business Online. You can use whatever value you want for the Identity and Name parameters.
    
  ```
  
Set-CsAccessEdgeConfiguration -AllowOutsideUsers 1 -AllowFederatedUsers 1 -UseDnsSrvRouting -EnablePartnerDiscovery $true
  ```


  ```
  New-CsHostingProvider -Identity SkypeforBusinessOnline -ProxyFqdn "sipfed.online.lync.com" -Enabled $true -EnabledSharedAddressSpace $true -HostsOCSUsers $true -VerificationLevel UseSourceVerification -IsLocal $false -AutodiscoverUrl https://webdir.online.lync.com/Autodiscover/AutodiscoverService.svc/root
  ```

2. Confirm that on your on-premises Edge Servers, you have the certificate chain that enables connection to Skype for Business Online, as shown in the following table. You can download this chain here:  [https://corp.sts.microsoft.com/Onboard/ADFS_Onboarding_Pack/corp_sts_certs.zip](https://corp.sts.microsoft.com/Onboard/ADFS_Onboarding_Pack/corp_sts_certs.zip) .
    

|**Certificate**|**Certificate Store**|
|:-----|:-----|
|Baltimore CyberTrust Root  <br/> |Trusted Root CA  <br/> |
|Microsoft Internet Authority (New CA certificate)  <br/> |Intermediate CA  <br/> |
|MSIT Machine Auth CA2 (New Issuing CA2)  <br/> |Intermediate CA  <br/> |
   
3. In your on-premises Active Directory, enable the affected user accounts for Skype for Business Server 2015 on-premises. You can do this for an individual user by typing the following cmdlet: 
    
  ```
  Enable-CsUser
-Identity "username " 
-SipAddress "sip: username @contoso.com"
-HostingProviderProxyFqdn "sipfed.online.lync.com"
  ```


    Or you can create a script that reads user names from a file and provides them as input to the Enable-CsUser cmdlet:
    


  ```
  
Enable-CsUser
-Identity $Identity 
-SipAddress $SipAddress 
-HostingProviderProxyFqdn "sipfed.online.lync.com"
  ```

4. Synchronize the Online users with the updated on-premises users. For more information, see  [Directory Integration Tools](https://go.microsoft.com/fwlink/p/?LinkId=530320).
    
  
5. Update some DNS records to direct all SIP traffic to your on-premises deployment:
    
  - Update the **lyncdiscover.contoso.com** A record to point to the FQDN of the on-premises reverse proxy server.
    
  
  - Update the ** *_sip*  ._tls.contoso.com** SRV record to resolve to the public IP or VIP address of the Access Edge service of Lync on-premises.
    
  
  - Update the ** *_sipfederationtls*  ._tcp.contoso.com** SRV record to resolve to the public IP or VIP address of the Access Edge service of Skype for Business Server 2015 on-premises.
    
  
  - If your organization uses split DNS (sometimes called "split-brain DNS"), make sure that users resolving names through the internal DNS zone are directed to the Front End Pool.
    
  
6. Type the  `Get-CsUser` cmdlet to check some properties about the users you'll be moving. You want to make sure that the HostingProviderProxyFQDN is set to `"sipfed.online.lync.com"` and that the SIP addresses are set correctly.
    
  
7. Move Online users to on-premises.
    
    To move a single user, type this:
    


  ```
  
$cred = Get-Credential
  ```




  ```
  Move-CsUser -Identity <username>@contoso.com  -Target "<fe-pool>.contoso.com " -Credential $cred -HostedMigrationOverrideURL <URL>
  ```


    You can move multiple users by using the **Get-CsUSer** cmdlet with the -Filter parameter to select the users with a specific property. For example, you could select all Online users by filtering for {Hosting Provider -eq "sipfed.online.lync.om"}. You can then pipe the returned users to the **Move-CsUSer** cmdlet, as shown below.
    


  ```
  Get-CsUser -Filter {Hosting Provider -eq "sipfed.online.lync.com"} | Move-CsUser -Target "<fe-pool>.contoso.com " -Credential $creds -HostedMigrationOverrideURL <URL>
  ```


    The format of the URL specified for the **HostedMigrationOverrideUrl** parameter must be the URL to the pool where the Hosted Migration service is running, in the following format: _Https://<Pool FQDN>/HostedMigration/hostedmigrationService.svc_.
    
    You can determine the URL to the Hosted Migration Service by viewing the URL for the Lync Online Control Panel for your Office 365 tenant account.
    
### To determine the Hosted Migration Service URL for your Office 365 tenant


1. Login to your Office 365 tenant as an administrator.
    
  
2. Open the **Skype for Business admin center**.
    
  
3. With the **Skype for Business admin center** displayed, select and copy the URL in the address bar up to **lync.com**. An example URL looks similar to the following:
    
     `https://webdir0a.online.lync.com/lscp/?language=en-US&amp;tenantID=`
    
  
4. Replace **webdir** in the URL with **admin**, resulting in the following: 
    
     `https://admin0a.online.lync.com`
    
  
5. Append the following string to the URL: **/HostedMigration/hostedmigrationservice.svc**.
    
    The resulting URL, which is the value of the **HostedMigrationOverrideUrl**, should look like the following:
    
     `https://admin0a.online.lync.com/HostedMigration/hostedmigrationservice.svc`
    
  

    > [!NOTE]
      > The default maximum size for transaction log files of the rtcxds database is 16 GB. This might not be big enough if you're moving a large number of users at once, especially if you have mirroring enabled. To get around this you can increase the file size or back up the log files regularly. For more information, see  [https://support.microsoft.com/kb/2756725](https://support.microsoft.com/kb/2756725). 
8. This is an optional step. If you need to integrate with Exchange 2013 Online, you need to use an additional hosting provider. For details, see  [Configure integration between on-premises Skype for Business Server 2015 and Outlook Web App](configure-integration-between-on-premises-skype-for-business-server-2015-and-out.md).
    
  
9. The users are now moved. To check that a user has correct values for the attributes shown in the following table, type this cmdlet: 
    
  ```
  Get-CsUser | fl DisplayName,HostingProvider,SipAddress,Enabled
  ```



|**Active Directory attribute**|**Attribute name**|**Correct value for Online user**|**Correct value for on-premises users**|
|:-----|:-----|:-----|:-----|
|msRTCSIP-DeploymentLocator  <br/> |HostingProvider  <br/> |sipfed.online.lync.com  <br/> |SRV:  <br/> |
|msRTCSIP-PrimaryUserAddress  <br/> |SIPAddress  <br/> |sip:userName@contoso.com  <br/> |sip:userName@contoso.com  <br/> |
|sRTCSIP-UserEnabled  <br/> |Enabled  <br/> |True  <br/> |True  <br/> |
   
10. Each user who has been moved will need to log out, then log back in. When they log in they should verify their contact lists, and add contacts if needed.
    
    Note that scheduled meetings are not migrated from online to on-premises. Users will need to reschedule these meetings after being moved.
    
    After the DNS records are updated and all users are directed to On-premises, the HostingProvider attribute directs the user to either use SRV records or direct them to the Online provider "sipfed.online.lync.com."
    
  

