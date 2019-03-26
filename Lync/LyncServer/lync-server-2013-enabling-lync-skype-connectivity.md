---
title: 'Lync Server 2013: Enabling Lync-Skype connectivity'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Enabling Lync-Skype connectivity
ms:assetid: 34c4db3e-582f-41fb-85c4-3438ae02f09f
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn440170(v=OCS.15)
ms:contentKeyID: 57793361
ms.date: 12/16/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Enabling Lync-Skype connectivity in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-12-16_

After you have submitted the provisioning request, you can focus on the Lync Server environment and administrative tasks required to configure Lync-Skype connectivity. In this section, we assume that the Lync Server administrator has deployed Lync Server and configured external access. For additional information on configuring external access for Lync Server, see [Planning for external user access in Lync Server 2013](lync-server-2013-planning-for-external-user-access.md) and [Deploying external user access in Lync Server 2013](lync-server-2013-deploying-external-user-access.md).

To prepare the Lync Server environment for Lync-Skype connectivity, the Lync Server administrator must complete the following three tasks:

<div>

## 1\. Configure Federation and PIC

Federation is required to enable Skype users to communicate with Lync users in your organization. Public Instant Messaging Connectivity (PIC) is a class of federation, and it must be configured to enable your Lync users to communicate with Skype users. Federation and PIC are configured by using the Lync Server Control Panel, shown below.

![Showing PIC](images/Dn440170.451b94e3-0b38-488c-835f-1f25690e8074(OCS.15).jpg "Showing PIC")

<div>


> [!IMPORTANT]  
> PIC federation is no longer supported by Live Communication Server 2005 SP1 or by Office Communications Server 2007. The supported platforms for PIC federation include Lync Server 2013, Lync Server 2010, and Office Communications Server 2007 R2.



</div>

</div>

<div>

## 2\. Configure at least one policy to support federated user access

Using the Lync Server Control Panel, an administrator must configure one or more external user access policies to control whether Skype users can collaborate with internal Lync Server users.

![Policies](images/Dn440170.8fd46ad1-9749-422c-8c47-c16ac9032cdb(OCS.15).jpg "Policies")

</div>

<div>

## 3\. Configure the Skype PIC provider setting for Lync

Using the Lync Server Management Shell, an administrator must configure the Lync client policy to display Skype as an additional PIC provider.

<div>


> [!NOTE]  
> Users of the Public Instant Messaging Connectivity (PIC) service providers can’t participate in IM or audio or video conferences in your organization until you also configure at least one policy (step 2, earlier in this procedure) to support public IM connectivity.



</div>

1.  To configure federation and PIC, see "Enable or Disable Federation and Public IM Connectivity" at [http://go.microsoft.com/fwlink/p/?LinkId=306063](http://go.microsoft.com/fwlink/p/?linkid=306063).

2.  To configure at least one policy to support federated user access, see "Configure Policies to Control Public User Access" at [http://go.microsoft.com/fwlink/p/?LinkId=306064](http://go.microsoft.com/fwlink/p/?linkid=306064).

**To edit an existing Messenger or Skype PIC provider and configure it for Skype**

1.  From a Lync Server Front End Server, open the Lync Server Management Shell.

2.  Run the following two commands:
    
    `Remove-CsPublicProvider -Identity <identity-name>`
    
    <div>
    

    > [!NOTE]  
    > If you do not already have a PIC provider in your environment and are creating a new PIC provider then you do not need to run the <STRONG>Remove-CsPublicProvider</STRONG> cmdlet.

    
    </div>
    
    `New-CsPublicProvider -ProxyFqdn federation.messenger.msn.com -Enabled 1 -Identity Skype  -VerificationLevel 2 -NameDecorationRoutingDomain msn.com -NameDecorationExcludedDomainList "msn.com,outlook.com,live.com,hotmail.com" -IconUrl "https://images.edge.messenger.live.com/Messenger_16x16.png"`
    
    <div>
    

    > [!NOTE]  
    > Added in Lync Server 2013 CU5 &amp; Lync desktop client in Office 2013 SP1, the NameDecorationRoutingDomain and NameDecorationExcludedDomainList improve the situation where Lync users adding Skype contacts needed to “decorate” non-Microsoft domains to identify and route them to Skype (the format of: user(contoso.com)@msn.com). These new settings will allow automatic formatting of the address user’s enter in the “Add Skype contact” dialog box with the NameDecorationRoutingDomain (which should be set to msn.com) if it does not contain the domains in the NameDecorationExcludedDomainList (we currently can support msn.com, live.com, Hotmail.com, outlook.com).

    
    </div>

3.  From a Lync client, you can now select Skype as the PIC provider, and add a Skype client by specifying their Microsoft account. In addition, a Skype user who has merged and logged in with their Microsoft account can send contact request to Lync users. For more information about Microsoft accounts, see [What is a Microsoft account?](https://support.skype.com/en/faq/fa12059/what-is-a-microsoft-account). For additional information on adding clients to Lync, see [Using Lync-Skype connectivity in Lync Server 2013 as an end user](lync-server-2013-using-lync-skype-connectivity-as-an-end-user.md).
    
    ![Add Skype Contact](images/Dn440170.df0e6ed9-2374-4dfa-a815-87281989487c(OCS.15).jpg "Add Skype Contact")

4.  For detailed information on modifying hosted providers, see "Create or Edit Hosted SIP Federated Providers" at [http://go.microsoft.com/fwlink/p/?LinkId=306065](http://go.microsoft.com/fwlink/p/?linkid=306065).

This completes the administrative tasks that must be performed on the server. You are now set up for Lync-Skype connectivity.

</div>

</div>

<span> </span>

</div>

</div>

</div>

