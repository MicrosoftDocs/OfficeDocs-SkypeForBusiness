---
title: "Enabling Lync-Skype connectivity in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 34c4db3e-582f-41fb-85c4-3438ae02f09f
description: "In this article1. Configure Federation and PIC2. Configure at least one policy to support federated user access3. Configure the Skype PIC provider setting for Lync"
---

# Enabling Lync-Skype connectivity in Lync Server 2013
[]
 **In this article**
  
[1. Configure Federation and PIC](#sectionSection0)
  
[2. Configure at least one policy to support federated user access](#sectionSection1)
  
[3. Configure the Skype PIC provider setting for Lync](#sectionSection2)
  
After you have submitted the provisioning request, you can focus on the Lync Server environment and administrative tasks required to configure Lync-Skype connectivity. In this section, we assume that the Lync Server administrator has deployed Lync Server and configured external access. For additional information on configuring external access for Lync Server, see [Planning for external user access in Lync Server 2013](planning-for-external-user-access.md) and [Deploying external user access in Lync Server 2013](deploying-external-user-access.md).
  
To prepare the Lync Server environment for Lync-Skype connectivity, the Lync Server administrator must complete the following three tasks: 
  
## 1. Configure Federation and PIC
<a name="sectionSection0"> </a>

Federation is required to enable Skype users to communicate with Lync users in your organization. Public Instant Messaging Connectivity (PIC) is a class of federation, and it must be configured to enable your Lync users to communicate with Skype users. Federation and PIC are configured by using the Lync Server Control Panel, shown below. 
  
![Showing PIC](media/ProvisioningGuideforLyncSkype_01ShowingPIC.jpg)
  
> [!IMPORTANT]
> PIC federation is no longer supported by Live Communication Server 2005 SP1 or by Office Communications Server 2007. The supported platforms for PIC federation include Lync Server 2013, Lync Server 2010, and Office Communications Server 2007 R2. 
  
## 2. Configure at least one policy to support federated user access
<a name="sectionSection1"> </a>

Using the Lync Server Control Panel, an administrator must configure one or more external user access policies to control whether Skype users can collaborate with internal Lync Server users.
  
![Policies](media/ProvisioningGuideforLyncSkype_02Policies.jpg)
  
## 3. Configure the Skype PIC provider setting for Lync
<a name="sectionSection2"> </a>

Using the Lync Server Management Shell, an administrator must configure the Lync client policy to display Skype as an additional PIC provider. 
  
> [!NOTE]
> Users of the Public Instant Messaging Connectivity (PIC) service providers can't participate in IM or audio or video conferences in your organization until you also configure at least one policy (step 2, earlier in this procedure) to support public IM connectivity. 
  
1. To configure federation and PIC, see "Enable or Disable Federation and Public IM Connectivity" at [https://go.microsoft.com/fwlink/p/?LinkId=306063](https://go.microsoft.com/fwlink/p/?LinkId=306063).
    
2. To configure at least one policy to support federated user access, see "Configure Policies to Control Public User Access" at [https://go.microsoft.com/fwlink/p/?LinkId=306064](https://go.microsoft.com/fwlink/p/?LinkId=306064).
    
### To edit an existing Messenger or Skype PIC provider and configure it for Skype

1. From a Lync Server Front End Server, open the Lync Server Management Shell.
    
2. Run the following two commands:
    
     `Remove-CsPublicProvider -Identity <identity-name>`
    
    > [!NOTE]
    > If you do not already have a PIC provider in your environment and are creating a new PIC provider then you do not need to run the **Remove-CsPublicProvider** cmdlet. 
  
     `New-CsPublicProvider -ProxyFqdn federation.messenger.msn.com -Enabled 1 -Identity Skype -VerificationLevel 2 -NameDecorationRoutingDomain msn.com -NameDecorationExcludedDomainList "msn.com,outlook.com,live.com,hotmail.com" -IconUrl "https://images.edge.messenger.live.com/Messenger_16x16.png"`
    
    > [!NOTE]
    > Added in Lync Server 2013 CU5 &amp; Lync desktop client in Office 2013 SP1, the NameDecorationRoutingDomain and NameDecorationExcludedDomainList improve the situation where Lync users adding Skype contacts needed to "decorate" non-Microsoft domains to identify and route them to Skype (the format of: user(contoso.com)@msn.com). These new settings will allow automatic formatting of the address user's enter in the "Add Skype contact" dialog box with the NameDecorationRoutingDomain (which should be set to msn.com) if it does not contain the domains in the NameDecorationExcludedDomainList (we currently can support msn.com, live.com, Hotmail.com, outlook.com). 
  
3. From a Lync client, you can now select Skype as the PIC provider, and add a Skype client by specifying their Microsoft account. In addition, a Skype user who has merged and logged in with their Microsoft account can send contact request to Lync users. For more information about Microsoft accounts, see [What is a Microsoft account?](https://support.skype.com/en/faq/FA12059/what-is-a-microsoft-account). For additional information on adding clients to Lync, see [Using Lync-Skype connectivity in Lync Server 2013 as an end user](using-lync-skype-connectivity-as-an-end-user.md).
    
     ![Add Skype Contact](media/ProvisioningGuideforLyncSkype_03AddSkypeContact.jpg)
  
4. For detailed information on modifying hosted providers, see "Create or Edit Hosted SIP Federated Providers" at [https://go.microsoft.com/fwlink/p/?LinkId=306065](https://go.microsoft.com/fwlink/p/?LinkId=306065).
    
This completes the administrative tasks that must be performed on the server. You are now set up for Lync-Skype connectivity.
  

