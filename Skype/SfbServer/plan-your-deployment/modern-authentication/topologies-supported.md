---
title: "Skype for Business topologies supported with Modern Authentication"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.custom: tracyp
ms.assetid: 258430b0-574a-47fb-90b7-54ee8996b2ec

description: "This article lists what online and on-premises topologies are supported with Modern Authentication in Skype for Business, as well as security features that apply to each topology."
---

# Skype for Business topologies supported with Modern Authentication
 
This article lists what online and on-premises topologies are supported with Modern Authentication in Skype for Business, as well as security features that apply to each topology.
  
## Modern Authentication in Skype for Business

Skype for Business can leverage security advantages of Modern Authentication. Because Skype for Business works closely with Exchange, the login behaviour Skype for Business client users will see will also be effected by the MA status of Exchange. This will also apply if you have a Skype for Business split-domain hybrid. That's a lot of moving parts, but the aim here is an easy to visualize list of supported topologies.
  
Given Skype for Business, Skype for Business online, Exchange Server, and Exchange online, what topologies are supported with MA?
  
<!--  > [!TIP] > Not sure what Modern Authentication even is? No worries.  This Skype for Business article  4e6a99cd-7859-4062-8a30-5ac79ba36b52  explains it in the first paragraphs. --> 
  
### Supported MA topologies in Skype for Business

There are potentially two server applications, and two Office 365 workloads, involved with Skype for Business topologies used by MA.
  
- Skype for Business server (CU 5) on-premises
    
- Skype for Business online (SFBO)
    
- Exchange server on-premises
    
- Exchange server online (EXO)
    
Another important part of MA is knowing where the authentication (authN) and authorization (authZ) of users will take place. The two options are:
  
- Azure AD, online in the Microsoft Cloud
    
- Active Directory Federation Server (ADFS) on-premises
    
So it looks a bit like this, with EXO and SFBO in the Cloud with Azure AD, and Exchange Server (EXCH) and Skype for Business server (SFB) on-prem.
  
![An example of all the applications (Exchange and Skype for Business) and workloads (EXO and SFBO), and both of the authorization servers (ADFS and evoSTS) that can be involved when turning on MA.](../../media/18a3b451-1e64-40fc-b47f-7ce9587814bb.PNG)
  
Here are the supported topologies. Please note the key for the graphics:
  
- If the icon is dimmed or grey, it is not used in the scenario.
    
- EXO is Exchange Online.
    
- SFBO is Skype for Business Online.
    
- EXCH is Exchange on-premises.
    
- SFB is Skype for Business on-premises.
    
- Authorizing servers are represented by triangles, for example, the Azure AD is a triangle with a cloud behind it.
    
- Arrows point at the authorizing server that will be used when clients try to reach the specified server resource.
    
First, let's cover MA with Skype for Business in both On-premises-only or Cloud-only topologies.
  
> [!IMPORTANT]
> Are you ready to set up Modern Authentication in Skype for Business Online? The steps to enable this feature are right [here](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx). 
  
|Topology name  <br/> |Example  <br/> |Description  <br/> |Supported  <br/> |
|:-----|:-----|:-----|:-----|
|Cloud only  <br/> |![Supported SFB with MA topology, Cloud only.](../../media/4d19b47f-8257-4a6f-9dab-0755206f7c52.PNG)Users homed/mailboxes located: Online  <br/> |MA is on for both EXO and SFBO.  <br/> Therefore, the authorization server is Azure AD.  <br/> |Multi-factor authentication (MFA), Client-certificate based authentication (CBA), Conditional Access (CA)/Mobile Application Management (MAM) with Intune. \*  <br/> |
|On-prem only  <br/> |![Supported SFB with MA topology, on-premises only.](../../media/9773e9a5-7cd6-41ef-940b-c4386c9fce20.PNG)Users homed/mailboxes located: On-premises  <br/> |MA is on for SFB on-premises.  <br/> Therefore, the authorization server is ADFS.  <br/> For configuration details, please see [this article.](https://technet.microsoft.com/en-us/library/mt710548.aspx) <br/> |MFA (Windows Desktop only - mobile clients are not supported). No Exchange integration features.  <br/> |
   
> [!IMPORTANT]
> It's recommended that the MA state be the same across Skype for Business and Exchange (and their online counterparts) to reduce the number of prompts. 
  
Mixed topologies involve combinations of SFB split-domain hybrids. These are the Mixed topologies currently supported:
  
|Topology name  <br/> |Example  <br/> |Description  <br/> |Supported  <br/> |
|:-----|:-----|:-----|:-----|
|Mixed 1  <br/> |![Supported SFB with MA topology, Mixed 1 (EXO + SFB).](../../media/7b2e607a-c83a-4bb3-9b48-a43566516129.PNG)           <br/> Users homed/mailboxes located: EXO and SFB  <br/> |MA is not enabled for SFB; no SFB MA features available in this topology.  <br/> |No MA features for SFB.  <br/> |
|Mixed 2  <br/> |![Supported MA with S4B Mixed topology 2, SFBO plus MA working with EXCH on-prem.](../../media/247a985d-39cd-4c16-a19e-b8b65207d82e.PNG)           <br/> Users homed/mailboxes located: EXCH and SFBO  <br/> |MA is on for SFBO only. The authorization server is Azure AD for users homed in SFBO, but AD for EXCH on-premises.  <br/> |MFA, CBA, CA/MAM with Intune.\*  <br/> |
|Mixed 3  <br/> |![Supported MA with SFB, EXO with MA on, plus EXCH and SFB on premises.](../../media/772dc261-c041-4a96-90d0-fd0b5124decf.PNG)           <br/> Users homed/mailboxes located: EXO + SFB, or EXCH + SFB  <br/> |No SFB MA features available in this topology  <br/> |No MA features for SFB.  <br/> |
|Mixed 4  <br/> |![Supported MA with SFB, SFBO with MA on, plus EXCH and SFB.](../../media/8971bfaf-961f-476c-b16e-5418d1fa0a6d.PNG)           <br/> Users homed/mailboxes located: EXCH +SFBO or EXCH + SFB  <br/> |MA is on for SFBO, therefore the authorization server is Azure AD for users homed in SFBO. On-prem users in SFB and EXO use AD.  <br/> |MFA, CBA, CA/MAM with Intune for online users only.\*  <br/> |
|Mixed 5  <br/> |![Supported MA in SFB, EXO with MA, and SFBO with MA, and EXCH and SFB on premises.](../../media/ecc366cf-1a7b-4ad1-bf8e-57111b8ad94f.PNG)           <br/> Users homed/mailboxes located: EXO + SFBO, EXO + SFB, EXCH + SFBO, or EXCH + SFB  <br/> |MA is on in both EXO and SFBO, therefore the authorization server is Azure AD for users homed in SFBO; on-prem users in EXCH and SFB use AD.  <br/> |MFA, CBA, CA/MAM with Intune for online users only.\*  <br/> |
|Mixed 6  <br/> |![In a Mixed 6 topology, Modern Authentication is on in all four possibile locations - the ideal situtation when it comes to Modern Auth.](../../media/8de21756-9152-466d-a706-58b258e2271c.png)           <br/> Users homed/mailboxes located: EXO + SFBO, EXO + SFB, EXCH + SFBO, or EXCH + SFB  <br/> |MA is on everywhere, therefore the authorization server is Azure AD for all users. (online and on-premises)  <br/>  Please see [https://aka.ms/ModernAuthOverview](https://aka.ms/ModernAuthOverview) for deployment steps. <br/> |MFA, CBA and CA/MAM (via Intune) for all users.  <br/> |
   
\* - MFA includes Windows Desktop, MAC, iOS, Android devices, and Windows Phones; CBA includes Windows Desktop, iOS and Android devices; CA/MAM with Intune, includes Android and iOS devices. 
  
> [!IMPORTANT]
> It's very important to note that users may see **multiple prompts** in some cases, notably where the MA state is not the same across all the server resources that clients may need and request, as is the case with all versions of the Mixed topologies.

> [!IMPORTANT]
> Also note that in some cases (Mixed 1, 3, and 5 specifically) an [AllowADALForNonLynIndependentOfLync](https://support.microsoft.com/en-us/help/3082803/info-about-the-allowadalfornonlyncindependentoflync-setting-in-skype-for-business,-lync-2013,-and-exchange-online) registry key must be set for proper configuration for Windows Desktop Clients.
  

