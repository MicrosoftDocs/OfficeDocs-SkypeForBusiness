---
title: "Deploy a resource forest topology"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- Hybrid 
- M365-voice
- M365-collaboration
- Teams_ITAdmin_Help
- Adm_Skype4B_Online
ms.custom: 
description: "The following sections provide guidance on how to configure an environment that has multiple forests in a resource/user forest model to provide Skype for Business functionality in a hybrid scenario."
---

# Deploy a resource forest topology
 
The following sections provide guidance on how to configure an environment that has multiple forests in a resource/user forest model to provide Skype for Business functionality in a hybrid scenario. 
  
![Multi-Forest Environment for Hybrid](../../sfbserver/media/5f079435-b252-4a6a-9638-3577d55b2873.png)
  
## Topology requirements

Multiple user forests are supported. Keep the following in mind: 
    
- For supported versions of Lync Server and Skype for Business Server in a hybrid configuration, see [Server version requirements](plan-hybrid-connectivity.md#server-version-requirements) in [Plan hybrid connectivity between Skype for Business Server and Office 365](plan-hybrid-connectivity.md).
    
- Exchange Server can be deployed in one or more forests, which may or may not include the forest containing Skype for Business Server. Make sure you have applied the latest Cumulative Update.
    
- For details on co-existence with Exchange Server, including support criteria and limitations in various combinations of on-premises and online, see [Feature support](../../sfbserver/plan-your-deployment/integrate-with-exchange/integrate-with-exchange.md#feature_support) in [Plan to integrate Skype for Business and Exchange](../../sfbserver/plan-your-deployment/integrate-with-exchange/integrate-with-exchange.md).
    
  
## User homing considerations

Skype for Business users homed on premises can have Exchange homed on premises or online. Skype for Business Online users should use Exchange Online for an optimal experience; however, this is not required. Exchange on premises is not required to implement Skype for Business in either case.
  
## Configure forest trusts

In a resource forest topology, the resource forests hosting Skype for Business Server must trust each account forest that contains users' accounts that will access it. If you have multiple user forests, to enable cross-forest authentication it is important that Name Suffix Routing is enabled for each of these forest trusts. For instructions, see [Managing Forest Trusts](https://technet.microsoft.com/en-us/library/cc772440.aspx). If you have Exchange Server deployed in an another forest and it provides functionality for Skype for Business users, the forest hosting Exchange must trust the forest hosting Skype for Business Server. For example, if Exchange were deployed in the account forest, this would effectively mean a two-way trust between account and Skype for Business forests is required in that configuration.
  
## Synchronize accounts into the forest hosting Skype for Business

When Skype for Business Server is deployed in one forest (a resource forest), but provides functionality to users in one or more other forests (account forests), users in the other forests must be represented as disabled user objects in the forest where Skype for Business Server is deployed. An identity management product, such as Microsoft Identity Manager, needs to be deployed and configured to provision and synchronize the users from the account forests into the forest where Skype for Business Server is deployed. Users must be synchronized into the forest hosting Skype for Business Server as disabled user objects. Users cannot be synchronized as Active Directory contact objects, because Azure Active Directory Connect will not properly synchronize contacts into Azure AD for use with Skype.
  
Regardless of any multi-forest configuration, the forest hosting Skype for Business Server can also provide functionality for any enabled users that exist in the same forest.
  
To get proper identity synchronization, the following attributes need to be synchronized: 
  
|**User forests**|**Resource forests**|
|:-----|:-----|
|chosen account link attribute  <br/> |chosen account link attribute  <br/> |
|mail  <br/> |mail  <br/> |
|ProxyAddresses  <br/> |ProxyAddresses  <br/> |
|ObjectSID  <br/> |msRTCSIP-OriginatorSID  <br/> |
   
The [chosen account link attribute](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-design-concepts/) will be used as the Source Anchor. If you have a different and immutable attribute that you would prefer to use, you may do so; just be sure to edit the AD FS claims rule and select the attribute during the AAD Connect configuration.
  
Do not sync the UPNs between the forests. We found during testing that we needed to use a unique UPN for each user forest, as you cannot use the same UPN across multiple forests. As a result, we were presented with two possibilities, to synchronize the UPN or to not synchronize. 
  
- If the unique UPN from each user forest was not synchronized to the associated disabled object in the resource forest, single sign-on (SSO) would be broken for at least the initial sign-in attempt (assuming the user selected the option to save password). In the Skype for Business client, we assume that the SIP/UPN values are the same. Since the SIP address in this scenario is user@company.com, but the UPN of the enabled object in the user forest is in fact user@contoso.company.com, the initial login attempt would fail and the user would be prompted to enter credentials. Upon entering their correct/actual UPN, the authentication request would be completed against the domain controllers in the user forest, and sign-in would be successful.
    
- If the unique UPN from each user forest was synchronized to the associated disabled object in the resource forest, AD FS authentication would fail. The matching rule would find the UPN on the object in the resource forest, which was disabled and could not be used for authentication. 
    
## Create an Office 365 tenant

You will next need to provision an Office 365 tenant to use with your deployment. For more information, please see [Subscriptions, licenses, accounts, and tenants for Microsoft's cloud offerings](https://docs.microsoft.com/office365/enterprise/subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings). 
  
## Configure Active Directory Federation Services

Once you have a tenant, you will need to configure Active Directory Federation Services (AD FS) in each of the user forests. This assumes you have a unique SIP and SMTP address and User Principal Name (UPN) for each forest. AD FS is optional and is used here to get single sign-on (SSO). DirSync with Password Sync is also supported and can also be used in place of AD FS. 
  
Only deployments with matching SIP/SMTP and UPNs were tested. Not having matching SIP/SMTP/UPNs may result in reduced functionality, such as problems with Exchange integration and SSO. 
  
Unless you use a unique SIP/SMTP/UPN for users from each forest, you can still run into SSO problems, regardless of where AD FS is deployed: 
  
- One-way or two-way trusts between resource/user forests with AD FS farm deployed in each user forest, all users share common SIP/SMTP domain but unique UPN for each user forest. 
    
- Two-way trusts between resource/user forests with AD FS farm deployed only in resource forest, all users share common SIP/SMTP domain but unique UPN for each user forest. 
    
By placing an AD FS farm in each user forest and using a unique SIP/SMTP/UPN for each forest, we resolve both issues. Only the accounts in that specific user forest would be searched and matched during authentication attempts. This will help provide a more seamless authentication process. 
  
This will be a standard deployment of the Windows Server 2012 R2 AD FS and should be working before continuing. For instructions, see [How To Install AD FS 2012 R2 For Office 365](https://blogs.technet.com/b/rmilne/archive/2014/04/28/how-to-install-adfs-2012-r2-for-office-365.aspx). 
  
Once deployed, you then have to edit the claims rule to match the Source Anchor selected earlier. In the AD FS MMC, under Relying Party Trusts, right-click **Microsoft Office 365 Identity Platform**, and then click **Edit Claim Rules**. Edit the first rule, and change ObjectSID to **employeeNumber**. 
  
![Multi-forest Edit Rules Screen](../../sfbserver/media/f5d485bd-52cc-437f-ba71-217f8902056c.png)
  
## Configure AAD Connect

In resource forest topologies, it’s required that user attributes from both the resource forest and any account forests(s) are synchronized into Azure AD. The simplest and recommended way to do this is to have Azure AD Connect synchronize and merge user identities from *all* forests that have enabled user accounts and the forest that contains Skype for Business. For details see, [Configure Azure AD Connect for Skype for Business and Teams](configure-azure-ad-connect.md).

Note that AAD Connect does not provide synchronization on premises between the account and resource forests. That must be separately configured using Microsoft Identity Manager or similar product, as described earlier.
  
When finished and AAD Connect is merging, if you look at an object in the metaverse, you should see something similar to this: 
  
![Multi-forest Metaverse Object Screen](../../sfbserver/media/16379880-2de3-4c43-b219-1551f5dec5f6.png)
  
The green highlighted attributes were merged from Office 365, the yellow are from the user forest, and the blue are from the resource forest. 
  
This is a test user, and you can see that AAD Connect has identified the sourceAnchor and the cloudSourceAnchor from the user and the resource forest objects from Office 365, in our case 1101, which is the employeeNumber selected earlier. It then was able to merge this object into what you see above. 
  
For more information, see [Integrate your on-premises directories with Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/). 
  
AAD Connect should be installed using the defaults, except for the following: 
  
1. Single sign-in - with AD FS already deployed and working: Select **Do not configure**.
    
2. Connect your directories: Add all of the domains.
    
3. Identify users in on-premises directories: Select **User identities exist across multiple directories**, and select the **ObjectSID** and **msExchangeMasterAccountSID** attributes.
    
4. Identify users in Azure AD: Source Anchor: Select the attribute you've chosen after reading [Selecting a good sourceAnchor attribute](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-design-concepts/), User Principal Name - **userPrincipalName**.
    
5.  Optional features: Select whether you have Exchange hybrid deployed.
    
    > [!NOTE]
    >  If you have only Exchange Online, there could be an issue with OAuth failures during autodiscover because of CNAME redirection. To correct this, you will need to set the Exchange Autodiscover URL by running the following cmdlet from the Skype for Business Server Management Shell:
  
    Set-CsOAuthConfiguration -ExchangeAutoDiscoverURL https://<span>autodiscover-s.outlook.com/autodiscover/autodiscover.svc 
    
6.  AD FS Farm: Select **Use an existing Windows Server 2012 R2 AD FS farm** and enter the name of the AD FS server.
    
7.  Finish the wizard and perform the necessary validations.
    
## Configure hybrid connectivity for Skype for Business Server

Follow the best practices for configuring Skype for Business hybrid. For more information information, see [Plan hybrid connectivity](plan-hybrid-connectivity.md) and [Configure hybrid connectivity](configure-hybrid-connectivity.md). 
  
## Configure hybrid connectivity for Exchange Server

If necessary, follow the best practices for configuring Exchange hybrid. For more information, see [Exchange Server Hybrid Deployments](https://docs.microsoft.com/en-us/exchange/exchange-hybrid). 
  

