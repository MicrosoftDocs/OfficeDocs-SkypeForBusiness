---
title: 'Lync Server 2013: Using Lync-Skype connectivity as an end user'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Using Lync-Skype connectivity as an end user
ms:assetid: ad22f731-118c-4349-8790-b1a72941cbdd
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn440175(v=OCS.15)
ms:contentKeyID: 57793365
ms.date: 12/29/2016
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Using Lync-Skype connectivity in Lync Server 2013 as an end user

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2016-12-27_

Lync-Skype Connectivity enables Skype users and Lync users to add each other as contacts, exchange instant messages and make audio and video calls. When a Skype user adds a Lync user, a Skype user will create a contact in Skype containing the session initiation protocol (SIP) uniform resource identifier (URI) of the Lync user. Conversely, when a Lync user adds a Skype contact, the Lync user will create a contact in Lync that will contain the Microsoft Account (MSA) of the Skype user, and not the Skype user name.

**What is an MSA?** Skype users must sign in to Skype with a Microsoft account (previously called Windows Live ID) in order to communicate with Lync contacts. A Microsoft account consists of the combination of an email address and a password, which you can also use to sign in to services such as Microsoft OneDrive storage technology, Windows Phone, Microsoft Xbox LIVE online game service, and Microsoft Outlook messaging and collaboration client (and, previously, Microsoft Hotmail web-based e-mail service or Windows Live Messenger). If you use an email address and a password to sign in to these or other services, you already have a Microsoft account. For details about creating a Microsoft Account, see the Microsoft account sign-up page at [https://go.microsoft.com/fwlink/p/?LinkId=306061](https://go.microsoft.com/fwlink/p/?linkid=306061). You can merge your existing Skype account with your Microsoft account for single sign-on, across a variety of applications and services. Once the account is merged a Skype user can send a contact request to Lync users.

<div>


> [!IMPORTANT]  
> In order for Lync and Skype users to fully communicate with each other, the following requirements must be met: 
> <UL>
> <LI>
> <P>Skype users must be logged into their Skype client with a Microsoft Account (MSA).</P>
> <LI>
> <P>Lync users must be enabled for public IM connectivity by their Lync administrator.</P>
> <LI>
> <P>When a Skype user adds a Lync contact, verify that the word Lync appears below the contact’s name. This indicates that a Lync URI has been found.</P>
> <LI>
> <P>When a Skype user adds a Lync contact and zero search results are returned for that Lync domain, the PIC provisioning process may not have completed, or the Lync domain has not yet been set up.</P>
> <LI>
> <P>Depending on the privacy settings of the Lync and Skype users, IM, video, and presence may not work until the new contacts are accepted by each user.</P></LI></UL>



</div>

**To add a Skype contact to Lync 2013**

1.  From Lync, click **Add a Contact, Add a Contact Not in My Organization**.

2.  From the list of available contact providers, select **Skype**.

3.  In the **IM Address** field, enter the Microsoft Account (MSA) of the Skype user.

4.  In the **Add to contact group** dropdown box, select a contact group to add the user to.

5.  In the **Set privacy relationship** dropdown box, select the appropriate contact setting and then click **OK**.

6.  The user will now appear as a contact in Lync. Select the user, right-click the user name, and click **See Contact Card** to view the user properties. You can now establish an audio or video call with the newly added Skype user.

For additional information on support for contacts, see [Add a contact in Lync](https://support.office.com/en-us/article/add-a-contact-ae55b88d-b9af-48da-bffe-7cc720a5059a).

When a Skype user’s Microsoft account uses a custom domain name, such as <strong>bob@contoso.com</strong> , a Lync user can add that Microsoft account to Lync in two ways:

1.  Use the **Add a Contact** icon, or

2.  Use the **Find someone or a room, or a dial a number** field.

In each instance, the Lync user must enter the Skype user’s email in the following format: <strong>user(domain name)@msn.com</strong> .

<div>


> [!IMPORTANT]  
> This step is not required for Microsoft accounts that use the following domain names: <STRONG>@live.com, @hotmail.com or @outlook.com</STRONG>. For more information on supported custom domain names, see <A href="https://support.microsoft.com/kb/897567">Supported public IM domains</A>.



</div>

**To add a Skype contact to Lync when using a custom domain name**

1.  From Lync, click **Add a Contact, Add a Contact Not in My Organization**.

2.  From the list of available contact providers, select **Skype**.

3.  In the **IM Address** field, enter the Microsoft Account (MSA) of the Skype user in the format <strong>user(domain name)@msn.com</strong>. So for user bob@contoso.com, the entry would be <strong>bob(contoso.com)@msn.com<strong> .

4.  In the **Add to contact group** drop-down list box, select a contact group to add the user to.

5.  In the **Set privacy relationship** drop-down list box, select the appropriate contact setting and then click **OK**.

6.  A Lync user can also use the **Find someone or a room, or dial a number** field in Lync, and add an address that resembles the following <strong>user(domain name)@msn.com</strong> . So for the bob@contoso.com Microsoft account, the entry would be <strong>bob(contoso.com)@msn.com</strong> .

7.  Follow steps 4 and 5 earlier in this procedure to add the contact to a contact group and to select the appropriate privacy relationship.

**To add a Lync contact to Skype**

1.  Sign in to Skype. The Skype user must be logged into their Skype client with a Microsoft Account (MSA).

2.  Select the Add Contacts icon.

3.  Enter the SIP URI of the Lync user. For example, bob@contoso.com.

4.  When Skype finds the match in the search results, look for the word **Lync** below the Lync user’s name. This indicates Skype successfully located the Lync client’s SIP URI. Click the name.

5.  In the top right corner of the window, click Add to Contacts.

6.  The new contact is now added to your contact list, but you’ll see a question mark instead of their status icon until they accept your request. When your new contact accepts your request, you will be able to see when they are online, initiate IM conversations, and make audio and video calls.
    
    <div>
    

    > [!IMPORTANT]  
    > The Lync Server administrator must configure the Lync user’s policy settings to allow incoming requests. If not, the Lync user will not receive contact requests from the Skype user. Depending on the configuration of the Lync user’s policy settings, the request to add the Skype user will appear on the Lync client’s <STRONG>New</STRONG> tab. To begin communicating with the Skype user, the Lync user must add the Skype user to either the Favorites list or a contact list. The image below shows the location of the <STRONG>New</STRONG> tab in the Lync client.

    
    </div>

A Lync user must configure Lync alerts to ensure that requests sent from a Skype user appear and are discoverable by the Lync user. To configure Lync alerts, complete the procedure that follows.

**To configure Lync Alerts**

1.  From the Lync client, click the **Options** icon.

2.  Select **Alerts**.

3.  Under **General alerts**, check **Tell me when someone adds me to his or her contact list**.

4.  Under **Contacts not using Lync**, select **Allow invites but block all other communications**.

5.  Click **OK** to close the Options window.

</div>

<span> </span>

</div>

</div>

</div>

