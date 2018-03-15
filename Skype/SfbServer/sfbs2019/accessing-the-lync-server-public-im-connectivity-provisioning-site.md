---
title: "Accessing the Lync Server public IM connectivity provisioning site from Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2017
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 77a08234-6bcf-4f59-b43b-ee5fc1926585

description: "The provisioning process for Lync-Skype connectivity has changed, as compared to previous PIC provisioning methods. This provisioning process can take up to thirty days to complete. We recommend that you start this process first, prior to completing the remaining steps in this document. After the Lync-Skype provisioning process is completed for your account, the account is activated and your eligible users are enabled for public IM connectivity."
---

# Accessing the Lync Server public IM connectivity provisioning site from Lync Server 2013
[]
The provisioning process for Lync-Skype connectivity has changed, as compared to previous PIC provisioning methods. This provisioning process can take up to thirty days to complete. We recommend that you start this process first, prior to completing the remaining steps in this document. After the Lync-Skype provisioning process is completed for your account, the account is activated and your eligible users are enabled for public IM connectivity. 
  
**To provision Lync-Skype connectivity, you need the following information:**

||
|:-----|
| Microsoft Agreement Number  <br/>  Access Edge service fully qualified domain name (FQDN)  <br/>  Session Initiation Protocol (SIP) domain(s)  <br/>  Any additional Access Edge service FQDNs  <br/>  Contact information  <br/> |
   
**To initiate the provisioning process for Lync-Skype connectivity:**

||
|:-----|
| Sign in to the website, **https://pic.lync.com**, using your Microsoft Windows Live ID.  <br/>  Select the Microsoft licensing agreement type.  <br/>  Select the check box, verifying that you have read and accept the Product Use Rights for Lync Server.  <br/>  On the **Initiate a Provisioning Request** page, click the appropriate link to initiate a provisioning request:  <br/>  On the **Specify Provisioning Information** page, enter the **Access Edge service FQDN**. For example, **sip.contoso.com**.  <br/> > [!IMPORTANT]>  After July 1st, 2017 Microsoft will additionally require customers have the Federation DNS SRV record deployed for Public IM connectivity to continue to work.            Enter at least one or more SIP domain names, and then click **Add**.  <br/> > [!IMPORTANT]>  At least one Access Edge server and one SIP domain are required to complete the provisioning process. The SIP domain and the Access Edge server must be active, functioning, and reachable on the network.            In the list of **Public IM Service providers**, select **Skype,** and click **Next** to add contact information, and submit the provisioning request.  <br/> |
   
After the provisioning request has been submitted, it can take up to 30 days for the account to activate and for users to be enabled for public IM connectivity.
  
## Enabling Federation and Public IM Connectivity (PIC)

After you have submitted the provisioning request, you can focus on the Lync Server environment and administrative tasks required to configure Lync-Skype connectivity. In this section, we assume that the Lync Server administrator has deployed Lync Server and configured external access. For additional information on configuring external access for Lync Server, see "Planning for External User Access" at [https://go.microsoft.com/fwlink/p/?LinkID=273772](https://go.microsoft.com/fwlink/p/?LinkID=273772) and "Deploying External User Access" at [https://go.microsoft.com/fwlink/p/?LinkID=27378](https://go.microsoft.com/fwlink/p/?LinkID=27378).
  
To prepare the Lync Server environment for Lync-Skype connectivity, the Lync Server administrator must complete the following three tasks: 
  
### 1. Configure Federation and PIC

Federation is required to enable Skype users to communicate with Lync users in your organization. Public Instant Messaging Connectivity (PIC) is a class of federation, and it must be configured to enable your Lync users to communicate with Skype users. Federation and PIC are configured by using the Lync Server Control Panel, shown below. 
  
> [!IMPORTANT]
> PIC federation is no longer supported by Live Communication Server 2005 SP1 or by Office Communications Server 2007. The supported platforms for PIC federation include Lync Server 2013, Lync Server 2010, and Office Communications Server 2007 R2. 
  
### 2. Configure at least one policy to support federated user access

Using the Lync Server Control Panel, an administrator must configure one or more external user access policies to control whether Skype users can collaborate with internal Lync Server users.
  
### 3. Configure the Skype PIC provider setting for Lync

Using the Lync Server Management Shell, an administrator must configure the Lync client policy to display Skype as an additional PIC provider. 
  
> [!NOTE]
> Users of the Public Instant Messaging Connectivity (PIC) service providers can't participate in IM or conferences in your organization until you also configure at least one policy (step 2, earlier in this procedure) to support public IM connectivity. > To configure federation and PIC, see "Enable or Disable Federation and Public IM Connectivity" at [https://go.microsoft.com/fwlink/p/?LinkId=306063](https://go.microsoft.com/fwlink/p/?LinkId=306063). > To configure at least one policy to support federated user access, see "Configure Policies to Control Public User Access" at [https://go.microsoft.com/fwlink/p/?LinkId=306064](https://go.microsoft.com/fwlink/p/?LinkId=306064). 
  
1. From a Lync Server Front End Server, open the Lync Server Management Shell.
    
2. Run the following two commands:
    
  -  `Remove-CsPublicProvider -Identity <identity-name>`
    
    > [!NOTE]
    > If you do not already have a PIC provider in your environment and are creating a new PIC provider then you do not need to run the **Remove-CsPublicProvider** cmdlet. 
  
  -  `New-CsPublicProvider -ProxyFqdn federation.messenger.msn.com -Enabled 1 -Identity Skype -VerificationLevel 2 -NameDecorationRoutingDomain msn.com -NameDecorationExcludedDomainList "msn.com,outlook.com,live.com,hotmail.com" -IconUrl "https://images.edge.messenger.live.com/Messenger_16x16.png"`
    
    > [!NOTE]
    > Added in Lync Server 2013 CU5 &amp; Lync desktop client in Office 2013 SP1, the NameDecorationRoutingDomain and NameDecorationExcludedDomainList improve the situation where Lync users adding Skype contacts needed to "decorate" non-Microsoft domains to identify and route them to Skype (the format of: user(contoso.com)@msn.com). These new settings will allow automatic formatting of the address user's enter in the "Add Skype contact" dialog box with the NameDecorationRoutingDomain (which should be set to msn.com) if it does not contain the domains in the NameDecorationExcludedDomainList (we currently can support msn.com, live.com, Hotmail.com, outlook.com). 
  
3. From a Lync client, you can now select Skype as the PIC provider, and add a Skype client by specifying their Microsoft account. In addition, a Skype user who has merged and logged in with their Microsoft account can send contact request to Lync users. For more information about Microsoft accounts, see [What is a Microsoft account?](https://support.skype.com/en/faq/FA12059/what-is-a-microsoft-account). For additional information on adding clients to Lync, see [Using Lync-Skype connectivity in Lync Server 2013 as an end user](using-lync-skype-connectivity-as-an-end-user.md).
    
4. For detailed information on modifying hosted providers, see "Create or Edit Hosted SIP Federated Providers" at [https://go.microsoft.com/fwlink/p/?LinkId=306065](https://go.microsoft.com/fwlink/p/?LinkId=306065).
    
This completes the administrative tasks that must be performed on the server. You are now set up for Lync-Skype connectivity.
  
## Additional Resources

[Using Lync-Skype connectivity in Lync Server 2013 as an end user](using-lync-skype-connectivity-as-an-end-user.md)
  
[Provisioning guide for Lync-Skype connectivity in Lync Server 2013](http://technet.microsoft.com/library/http://technet.microsoft.com/en-us/library/dn440173.aspx.aspx)
  

