---
title: 'Accessing the Lync Server public IM connectivity provisioning site'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Accessing the Lync Server public IM connectivity provisioning site
ms:assetid: 77a08234-6bcf-4f59-b43b-ee5fc1926585
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn440174(v=OCS.15)
ms:contentKeyID: 57793364
ms.date: 03/09/2017
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Accessing the Lync Server public IM connectivity provisioning site from Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2019-03-22_

The provisioning process for Lync-Skype connectivity has changed, as compared to previous PIC provisioning methods. This provisioning process can take up to thirty days to complete. We recommend that you start this process first, prior to completing the remaining steps in this document. After the Lync-Skype provisioning process is completed for your account, the account is activated and your eligible users are enabled for public IM connectivity.

### To provision Lync-Skype connectivity, you need the following information:

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><ol>
<li><p>Microsoft Agreement Number</p></li>
<li><p>Access Edge service fully qualified domain name (FQDN)</p></li>
<li><p>Session Initiation Protocol (SIP) domain(s)</p></li>
<li><p>Any additional Access Edge service FQDNs</p></li>
<li><p>Contact information</p></li>
</ol></td>
</tr>
</tbody>
</table>

Beginning in April 2019, we will stop the collection and retention of contact information for customers who are provisioned for Skype Federation via the pic.lync.com website. This change is being made to ensure that the pic.lync.com provisioning system adheres to Microsoft privacy policies. 

Once this change goes live, we will no longer be able to provide email updates on pending provisioning changes. PIC provisioning changes typically complete within 24-48 hours after being entered. If you are still experiencing Skype Federation issues 48 hours after submitting a provisioning request, please engage Microsoft Technical Support to investigate further.

> [!IMPORTANT]
> As part of this change, all previously entered contact information will be purged from our system by the end of April, 2019.

### To initiate the provisioning process for Lync-Skype connectivity:

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><ol>
<li><p>Sign in to the website, <strong>https://pic.lync.com</strong>, using your Microsoft Windows Live ID.</p></li>
<li><p>Select the Microsoft licensing agreement type.</p></li>
<li><p>Select the check box, verifying that you have read and accept the Product Use Rights for Lync Server.</p></li>
<li><p>On the <strong>Initiate a Provisioning Request</strong> page, click the appropriate link to initiate a provisioning request:</p></li>
<li><p>On the <strong>Specify Provisioning Information</strong> page, enter the <strong>Access Edge service FQDN</strong>. For example, <strong>sip.contoso.com</strong>.</p>



> [!IMPORTANT]
> After July 1st, 2017 Microsoft will additionally require customers have the Federation DNS SRV record deployed for Public IM connectivity to continue to work.

</li>
<li><p>Enter at least one or more SIP domain names, and then click <strong>Add</strong>.</p>



> [!IMPORTANT]
> At least one Access Edge server and one SIP domain are required to complete the provisioning process. The SIP domain and the Access Edge server must be active, functioning, and reachable on the network.

</li>
<li><p>In the list of <strong>Public IM Service providers</strong>, select <strong>Skype,</strong> and click <strong>Next</strong> to add contact information, and submit the provisioning request.</p></li>
</ol></td>
</tr>
</tbody>
</table>


After the provisioning request has been submitted, it can take up to 30 days for the account to activate and for users to be enabled for public IM connectivity.

<div>

## Enabling Federation and Public IM Connectivity (PIC)

After you have submitted the provisioning request, you can focus on the Lync Server environment and administrative tasks required to configure Lync-Skype connectivity. In this section, we assume that the Lync Server administrator has deployed Lync Server and configured external access. For additional information on configuring external access for Lync Server, see "Planning for External User Access" at [https://go.microsoft.com/fwlink/p/?LinkID=273772](https://go.microsoft.com/fwlink/p/?linkid=273772) and "Deploying External User Access" at [https://go.microsoft.com/fwlink/p/?LinkID=27378](https://go.microsoft.com/fwlink/p/?linkid=27378).

To prepare the Lync Server environment for Lync-Skype connectivity, the Lync Server administrator must complete the following three tasks:

<div>

## 1\. Configure Federation and PIC

Federation is required to enable Skype users to communicate with Lync users in your organization. Public Instant Messaging Connectivity (PIC) is a class of federation, and it must be configured to enable your Lync users to communicate with Skype users. Federation and PIC are configured by using the Lync Server Control Panel, shown below.

<div>


> [!IMPORTANT]
> PIC federation is no longer supported by Live Communication Server 2005 SP1 or by Office Communications Server 2007. The supported platforms for PIC federation include Lync Server 2013, Lync Server 2010, and Office Communications Server 2007 R2.



</div>

</div>

<div>

## 2\. Configure at least one policy to support federated user access

Using the Lync Server Control Panel, an administrator must configure one or more external user access policies to control whether Skype users can collaborate with internal Lync Server users.

</div>

<div>

## 3\. Configure the Skype PIC provider setting for Lync

Using the Lync Server Management Shell, an administrator must configure the Lync client policy to display Skype as an additional PIC provider.

<div>


> [!NOTE]
> Users of the Public Instant Messaging Connectivity (PIC) service providers can’t participate in IM or conferences in your organization until you also configure at least one policy (step 2, earlier in this procedure) to support public IM connectivity.<BR>To configure federation and PIC, see "Enable or Disable Federation and Public IM Connectivity" at <A href="https://go.microsoft.com/fwlink/p/?linkid=306063">https://go.microsoft.com/fwlink/p/?LinkId=306063</A>.<BR>To configure at least one policy to support federated user access, see "Configure Policies to Control Public User Access" at <A href="https://go.microsoft.com/fwlink/p/?linkid=306064">https://go.microsoft.com/fwlink/p/?LinkId=306064</A>.



</div>

1.  From a Lync Server Front End Server, open the Lync Server Management Shell.

2.  Run the following two commands:
    
      - `Remove-CsPublicProvider -Identity <identity-name>`
        
        <div>
        

        > [!NOTE]
        > If you do not already have a PIC provider in your environment and are creating a new PIC provider then you do not need to run the <STRONG>Remove-CsPublicProvider</STRONG> cmdlet.

        
        </div>
    
      - `New-CsPublicProvider -ProxyFqdn federation.messenger.msn.com -Enabled 1 -Identity Skype  -VerificationLevel 2 -NameDecorationRoutingDomain msn.com -NameDecorationExcludedDomainList "msn.com,outlook.com,live.com,hotmail.com" -IconUrl "https://images.edge.messenger.live.com/Messenger_16x16.png"`
        
        <div>
        

        > [!NOTE]
        > Added in Lync Server 2013 CU5 &amp; Lync desktop client in Office 2013 SP1, the NameDecorationRoutingDomain and NameDecorationExcludedDomainList improve the situation where Lync users adding Skype contacts needed to “decorate” non-Microsoft domains to identify and route them to Skype (the format of: user(contoso.com)@msn.com). These new settings will allow automatic formatting of the address user’s enter in the “Add Skype contact” dialog box with the NameDecorationRoutingDomain (which should be set to msn.com) if it does not contain the domains in the NameDecorationExcludedDomainList (we currently can support msn.com, live.com, Hotmail.com, outlook.com).

        
        </div>

3.  From a Lync client, you can now select Skype as the PIC provider, and add a Skype client by specifying their Microsoft account. In addition, a Skype user who has merged and logged in with their Microsoft account can send contact request to Lync users. For more information about Microsoft accounts, see [What is a Microsoft account?](https://support.skype.com/en/faq/fa12059/what-is-a-microsoft-account). For additional information on adding clients to Lync, see [Using Lync-Skype connectivity in Lync Server 2013 as an end user](lync-server-2013-using-lync-skype-connectivity-as-an-end-user.md).

4.  For detailed information on modifying hosted providers, see "Create or Edit Hosted SIP Federated Providers" at [https://go.microsoft.com/fwlink/p/?LinkId=306065](https://go.microsoft.com/fwlink/p/?linkid=306065).

This completes the administrative tasks that must be performed on the server. You are now set up for Lync-Skype connectivity.

</div>

</div>

<div>

## Additional Resources

[Using Lync-Skype connectivity in Lync Server 2013 as an end user](lync-server-2013-using-lync-skype-connectivity-as-an-end-user.md)

[Provisioning guide for Lync-Skype connectivity in Lync Server 2013](lync-server-2013-provisioning-guide-for-lync-skype-connectivity.md)

</div>

</div>

<span> </span>

</div>

</div>

</div>

