---
title: "Move users from Skype for Business Online to on premises"
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 12/19/2017
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection:
- Ent_O365_Hybrid
- IT_Skype16
- IT_Skype4B_Hybrid
- Strat_SB_Hybrid
ms.custom:
ms.assetid: 55733bb5-6742-4daf-8db5-1c5df86f4cea
description: "Summary: Learn how to move user accounts from online to on premises in Skype for Business Server."
---

# Move users from Skype for Business Online to on premises

**Summary:** Learn how to move user accounts from online to on premises in Skype for Business Server.

You might need to move user accounts from online to on premises to ensure that users homed online and on premises are discoverable to one another. To be discoverable to one another, all users must have a presence in the on-premises Active Directory. For more information, see [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online](../../skype-for-business-hybrid-solutions/plan-hybrid-connectivity.md). You might want to move online users to on premises, for example, if:

- You have new users who need to be created on premises and then moved to the cloud.

- Your organization deployed Skype for Business Online before it deployed Skype for Business Server. Therefore, you have users who were created in the cloud first, and now need to be moved to on premises before they are move to Skype for Business Online.

This topic describes two scenarios:

- [Move online users—who were originally online—to on premises](move-users-from-skype-for-business-online-to-on-premises.md#BKMK_originallyonline)

- [Move online users (who were originally on premises) to on premises](move-users-from-skype-for-business-online-to-on-premises.md#BKMK_originallyonprem)

## Move online users—who were originally online—to on premises
<a name="BKMK_originallyonline"> </a>

This section applies only to users who were created and enabled online, but who do not have an account in the on premises Active Directory.

Before you start moving online users to your on-premises environment, check that all of the following are true:

- Your on-premises environment must be fully deployed and validated. For more information, see [Deploying Lync Server 2013](https://technet.microsoft.com/library/b76795a4-4e71-4c70-a5c0-d1197fa8028c.aspx) or [Deploy Skype for Business Server 2015](../../deploy/deploy.md), depending on which version you are using on premises.

- Your online tenant must be configured for remote PowerShell access.

    To do this, first install the Skype for Business Online connector module for Windows PowerShell, which you can get here: [https://go.microsoft.com/fwlink/p/?LinkId=391911](https://go.microsoft.com/fwlink/p/?LinkId=391911).

    After you install the module, you can establish a remote session by typing the following cmdlets in the Skype for Business Server Management Shell:

  ```
  Import-Module SkypeOnlineConnector
  ```

  ```
  $cred = Get-Credential
  ```

  ```
  $CSSession = New-CsOnlineSession -Credential $cred
  ```

  ```
  Import-PSSession $CSSession -AllowClobber
  ```

    For more information about using PowerShell with Skype for Business Online, see [Set up your computer for Windows PowerShell](../../../SfbOnline/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell.md)

- Your online tenant must be configured for a shared SIP address space. To do this, first start a remote Powershell session with Skype for Business Online. Then run the following cmdlet:

  ```
  Set-CsTenantFederationConfiguration -SharedSipAddressSpace $True
  ```

    > [!NOTE]
    > The SharedSipAddressSpace attribute needs to remain "True" until moving to online is final, and no users remain on premises.

After you've finished these steps, you can migrate user accounts as described in the following procedure:

### Move user accounts originally enabled online to an on-premises deployment

1. First, make sure that your organization is configured for hybrid, including Azure Active Directory Connect and sync tools. For more information, see [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online](../../skype-for-business-hybrid-solutions/plan-hybrid-connectivity.md).

   - On your on-premises deployment, in the Skype for Business Server Management Shell, type the following cmdlets to create the hosting provider for Skype for Business Online. You can use whatever value you want for the Identity and Name parameters.

   ```
   Set-CsAccessEdgeConfiguration -AllowOutsideUsers 1 -AllowFederatedUsers 1 -UseDnsSrvRouting -EnablePartnerDiscovery $true
   ```

   ```
   New-CsHostingProvider -Identity SkypeforBusinessOnline -ProxyFqdn "sipfed.online.lync.com" -Enabled $true -EnabledSharedAddressSpace $true -HostsOCSUsers $true -VerificationLevel UseSourceVerification -IsLocal $false -AutodiscoverUrl https://webdir.online.lync.com/Autodiscover/AutodiscoverService.svc/root
   ```

2. Confirm that on your on-premises Edge Servers, you have the certificate chain that enables connection to Skype for Business Online, as shown in the following table. You can download this chain here: [https://corp.sts.microsoft.com/Onboard/ADFS_Onboarding_Pack/corp_sts_certs.zip](https://corp.sts.microsoft.com/Onboard/ADFS_Onboarding_Pack/corp_sts_certs.zip).

|**Certificate**|**Certificate Store**|
|:-----|:-----|
|Baltimore CyberTrust Root  <br/> |Trusted Root CA  <br/> |
|Microsoft Internet Authority (New CA certificate)  <br/> |Intermediate CA  <br/> |
|MSIT Machine Auth CA2 (New Issuing CA2)  <br/> |Intermediate CA  <br/> |

3. In your on-premises Active Directory, enable the affected user accounts for Skype for Business Server 2015 on premises. You can do this for an individual user by typing the following cmdlet:

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

4. Synchronize the online users with the updated on-premises users. For more information, see [Directory Integration Tools](https://go.microsoft.com/fwlink/p/?LinkId=530320).

5. Update the following DNS records to direct all SIP traffic to your on-premises deployment:

   - Update the **lyncdiscover.contoso.com** A record to point to the FQDN of the on-premises reverse proxy server.

   - Update the ***_sip*  ._tls.contoso.com** SRV record to resolve to the public IP or VIP address of the Access Edge service of Lync on-premises.

   - Update the ***_sipfederationtls*  ._tcp.contoso.com** SRV record to resolve to the public IP or VIP address of the Access Edge service of Skype for Business Server 2015 on-premises.

   - If your organization uses split DNS (sometimes called "split-brain DNS"), make sure that users resolving names through the internal DNS zone are directed to the Front End Pool.

6. Type the  `Get-CsUser` cmdlet to check some properties about the users you'll be moving. You want to make sure that the HostingProviderProxyFQDN is set to `"sipfed.online.lync.com"` and that the SIP addresses are set correctly.

7. Move online users to on premises.

    To move a single user, type this:

   ```
   $cred = Get-Credential
   Move-CsUser -Identity <username>@contoso.com  -Target "<fe-pool>.contoso.com " -Credential $cred -HostedMigrationOverrideURL <URL>
   ```

    You can move multiple users by using the **Get-CsUSer** cmdlet with the -Filter parameter to select the users with a specific property. For example, you could select all Online users by filtering for {Hosting Provider -eq "sipfed.online.lync.om"}. You can then pipe the returned users to the **Move-CsUSer** cmdlet, as shown below.

   ```
   Get-CsUser -Filter {Hosting Provider -eq "sipfed.online.lync.com"} | Move-CsUser -Target "<fe-pool>.contoso.com " -Credential $creds -HostedMigrationOverrideURL <URL>
   ```

    The format of the URL specified for the **HostedMigrationOverrideUrl** parameter must be the URL to the pool where the Hosted Migration service is running, in the following format: _Https://\<Pool FQDN\>/HostedMigration/hostedmigrationService.svc_.

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
    > The default maximum size for transaction log files of the rtcxds database is 16 GB. This might not be big enough if you're moving a large number of users at once, especially if you have mirroring enabled. To get around this you can increase the file size or back up the log files regularly. For more information, see [https://support.microsoft.com/kb/2756725](https://support.microsoft.com/kb/2756725).

6. This is an optional step. If you need to integrate with Exchange 2013 Online, you need to use an additional hosting provider. For details, see [Configure integration between on-premises Skype for Business Server 2015 and Outlook Web App](../../deploy/integrate-with-exchange-server/outlook-web-app.md).

7. The users are now moved. To check that a user has correct values for the attributes shown in the following table, type this cmdlet:

   ```
   Get-CsUser | fl DisplayName,HostingProvider,SipAddress,Enabled
   ```

| **Active Directory attribute**     | **Attribute name**     | **Correct value for Online user** | **Correct value for on-premises users** |
|:-----------------------------------|:-----------------------|:----------------------------------|:----------------------------------------|
| msRTCSIP-DeploymentLocator  <br/>  | HostingProvider  <br/> | sipfed.online.lync.com  <br/>     | SRV:  <br/>                             |
| msRTCSIP-PrimaryUserAddress  <br/> | SIPAddress  <br/>      | sip:userName@contoso.com  <br/>   | sip:userName@contoso.com  <br/>         |
| msRTCSIP-UserEnabled  <br/>        | Enabled  <br/>         | True  <br/>                       | True  <br/>                             |

10. Each user who has been moved will need to log out, then log back in. When they log in they should verify their contact lists, and add contacts if needed.

    Note that scheduled meetings are not migrated from online to on-premises. Users will need to reschedule these meetings after being moved.

    After the DNS records are updated and all users are directed to On-premises, the HostingProvider attribute directs the user to either use SRV records or direct them to the Online provider "sipfed.online.lync.com."

## Move online users (who were originally on premises) to on premises
<a name="BKMK_originallyonprem"> </a>

This section applies only to users who were created and enabled for an on-premises deployment and then moved from an on-premises deployment to online.

- Run the following cmdlets to move a user from Skype for Business Online back to on-premises, replacing the value for the **Identity** and **Target** parameters to correct values for your environment:

  ```
  $cred=Get-Credential
  ```

  ```
  Move-CsUser -Identity username@contoso.com -Target localpool.contoso.com -Credential $cred -HostedMigrationOverrideUrl <URL>
  ```

The format of the URL specified for the **HostedMigrationOverrideUrl** parameter must be the URL to the pool where the Hosted Migration service is running, in the following format:

 _Https://\<Pool FQDN\>/HostedMigration/hostedmigrationService.svc_. You can determine the URL to the Hosted Migration Service by viewing the URL for the Lync Online Control Panel for your Office 365 tenant account.

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


