---
title: 'Lync Server 2013: Migrating Lync Online users to Lync on-premises'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Migrating Lync Online users to Lync on-premises
ms:assetid: 0e29605b-db2d-4cbf-b6a9-15db6b9fdabc
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn689115(v=OCS.15)
ms:contentKeyID: 62258120
ms.date: 11/13/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Migrating Lync Online users to Lync on-premises in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2015-11-13_

<div class="">


> [!IMPORTANT]  
> These steps are necessary only for migrating user accounts that were originally enabled for Lync in Lync Online, before you deployed Lync on-premises. To move users who were originally enabled for Lync on-premises, then later moved to Lync Online, see <A href="lync-server-2013-administering-users-in-a-hybrid-deployment.md">Administering users in a hybrid Lync Server 2013 deployment</A>.<BR>Additionally, all users being moved must have accounts in the on-premises Active Directory.



</div>

<div>

## Migrating User Accounts Originally Enabled in Lync Online to Lync On-Premises

1.  First, make sure that your organization is configured for hybrid.
    
      - Install the Azure Active Directory Sync Tool. For more information, see <http://social.technet.microsoft.com/wiki/contents/articles/19098.howto-install-the-windows-azure-active-directory-sync-tool.aspx>.
    
      - To enable your users to use single sign-on for Lync Online, install Active Directory Federation Services <http://social.technet.microsoft.com/wiki/contents/articles/1011.active-directory-federation-services-ad-fs-overview.aspx>.
    
      - On your on-premises deployment, in Lync Server Management Shell, type the following cmdlets to create the hosting provider for Lync Online:
        
           ```
           Set-CsAccessEdgeConfiguration -AllowOutsideUsers 1 -AllowFederatedUsers 1 -UseDnsSrvRouting -EnablePartnerDiscovery $true
           ```
        
           ```
            New-CsHostingProvider -Identity LyncOnline -ProxyFqdn "sipfed.online.lync.com" -Enabled $true -EnabledSharedAddressSpace $true -HostsOCSUsers $true -VerificationLevel UseSourceVerification -IsLocal $false -AutodiscoverUrl https://webdir.online.lync.com/Autodiscover/AutodiscoverService.svc/root
           ```

2.  Confirm that on your on-premises Edge Servers, you have the certificate chain that enables connection to Lync Online, as shown in the following table. You can download this chain here: [https://corp.sts.microsoft.com/Onboard/ADFS\_Onboarding\_Pack/corp\_sts\_certs.zip](https://corp.sts.microsoft.com/onboard/adfs_onboarding_pack/corp_sts_certs.zip) .
    
    
    <table>
    <colgroup>
    <col style="width: 50%" />
    <col style="width: 50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Certificate</th>
    <th>Certificate Store</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>Baltimore CyberTrust Root</p></td>
    <td><p>Trusted Root CA</p></td>
    </tr>
    <tr class="even">
    <td><p>Microsoft Internet Authority (New CA certificate)</p></td>
    <td><p>Intermediate CA</p></td>
    </tr>
    <tr class="odd">
    <td><p>MSIT Machine Auth CA2 (New Issuing CA2)</p></td>
    <td><p>Intermediate CA</p></td>
    </tr>
    </tbody>
    </table>


3.  In your on-premises Active Directory, enable the affected user accounts for Lync on-premises. You can do this for an individual user by typing the following cmdlet:
    
        Enable-CsUser
        -Identity "username" 
        -SipAddress "sip: username@contoso.com"
        -HostingProviderProxyFqdn "sipfed.online.lync.com"
    
    Or you can create a script that reads user names from a file and provides them as input to the Enable-CsUser cmdlet:
    
        Enable-CsUser
        -Identity $Identity 
        -SipAddress $SipAddress 
        -HostingProviderProxyFqdn "sipfed.online.lync.com"

4.  Run DirSync to sync the Lync Online users with the updated Lync on-premises users.

5.  Update some DNS records to direct all SIP traffic to Lync on-premises:
    
      - Update the **lyncdiscover.contoso.com** A record to point to the FQDN of the on-premises reverse proxy server.
    
      - Update the ***\_sip*.\_tls.contoso.com** SRV record to resolve to the public IP or VIP address of the Access Edge service of Lync on-premises.
    
      - Update the ***\_sipfederationtls*.\_tcp.contoso.com** SRV record to resolve to the public IP or VIP address of the Access Edge service of Lync on-premises.
    
      - If your organization uses split DNS (sometimes called “split-brain DNS”), make sure that users resolving names through the internal DNS zone are directed to the Front End Pool.

6.  Type the `Get-CsUser` cmdlet to check some properties about the users you’ll be moving. You want to make sure that the HostingProviderProxyFQDN is set to `"sipfed.online.lync.com"` and that the SIP addresses are set correctly.

7.  Move Lync Online users to Lync on-premises.
    
    To move a single user, type this:
    
       ```
       $cred = Get-Credential
       ```
    
       ```
       Move-CsUser -Identity <username>@contoso.com -Target "<fe-pool>.contoso.com" -Credential $cred -HostedMigrationOverrideURL <URL>
       ```
    
    You can move multiple users by using the **Get-CsUSer** cmdlet with the –Filter parameter to select the users with a specific property. For example, you could select all Lync Online users by filtering for {Hosting Provider –eq “sipfed.online.lync.om”}. You can then pipe the returned users to the **Move-CsUSer** cmdlet, as shown below.
    
        Get-CsUser -Filter {Hosting Provider -eq "sipfed.online.lync.com"} | Move-CsUser -Target "<fe-pool>.contoso.com" -Credential $creds -HostedMigrationOverrideURL <URL>
    
    The format of the URL specified for the **HostedMigrationOverrideUrl** parameter must be the URL to the pool where the Hosted Migration service is running, in the following format: *Https://\<Pool FQDN\>/HostedMigration/hostedmigrationService.svc*.
    
    You can determine the URL to the Hosted Migration Service by viewing the URL for the Lync Online Control Panel for your Office 365 tenant account.
    
    <div>
    
    ## To determine the Hosted Migration Service URL for your Office 365 tenant
    
    1.  Login to your Office 365 tenant as an administrator.
    
    2.  Open the **Lync admin center**.
    
    3.  With the **Lync admin center** displayed, select and copy the URL in the address bar up to **lync.com**. An example URL looks similar to the following:
        
        `https://webdir0a.online.lync.com/lscp/?language=en-US&tenantID=`
    
    4.  Replace **webdir** in the URL with **admin**, resulting in the following:
        
        `https://admin0a.online.lync.com`
    
    5.  Append the following string to the URL: **/HostedMigration/hostedmigrationservice.svc**.
        
        The resulting URL, which is the value of the **HostedMigrationOverrideUrl**, should look like the following:
        
        `https://admin0a.online.lync.com/HostedMigration/hostedmigrationservice.svc`
    
    </div>
    
    <div class="">
    

    > [!NOTE]  
    > The default maximum size for transaction log files of the rtcxds database is 16 GB. This might not be big enough if you’re moving a large number of users at once, especially if you have mirroring enabled. To get around this you can increase the file size or back up the log files regularly. For more information, see <A class=uri href="http://support.microsoft.com/kb/2756725">http://support.microsoft.com/kb/2756725</A>.

    
    </div>

8.  This is an optional step. If you need to integrate with Exchange 2013 Online, you need to use an additional hosting provider. For details, see [Configuring on-premises Lync Server 2013 integration with Exchange Online](lync-server-2013-configuring-on-premises-lync-server-integration-with-exchange-online.md).

9.  The users are now moved. To check that a user has correct values for the attributes shown in the following table, type this cmdlet:
    
        Get-CsUser | fl DisplayName,HostingProvider,SipAddress,Enabled
    
    
    <table>
    <colgroup>
    <col style="width: 25%" />
    <col style="width: 25%" />
    <col style="width: 25%" />
    <col style="width: 25%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Active Directory attribute</th>
    <th>Attribute name</th>
    <th>Correct value for Lync Online user</th>
    <th>Correct value for Lync on–premises users</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>msRTCSIP-DeploymentLocator</p></td>
    <td><p>HostingProvider</p></td>
    <td><p>sipfed.online.lync.com</p></td>
    <td><p>SRV:</p></td>
    </tr>
    <tr class="even">
    <td><p>msRTCSIP-PrimaryUserAddress</p></td>
    <td><p>SIPAddress</p></td>
    <td><p>sip:userName@contoso.com</p></td>
    <td><p>sip:userName@contoso.com</p></td>
    </tr>
    <tr class="odd">
    <td><p>sRTCSIP-UserEnabled</p></td>
    <td><p>Enabled</p></td>
    <td><p>True</p></td>
    <td><p>True</p></td>
    </tr>
    </tbody>
    </table>


10. Each user who has been moved will need to log out of Lync, then log back in. When they log in they should verify their contact lists, and add contacts if needed.
    
    Note that scheduled meetings are not migrated from Lync Online to Lync on-premises. Users will need to reschedule these meetings after being moved.
    
    After the DNS records are updated and all users are directed to On premise, the HostingProvider attribute directs the Lync user to either use SRV records or direct them to the Online provider “sipfed.online.lync.com.”

</div>

</div>

<span> </span>

</div>

</div>

</div>

