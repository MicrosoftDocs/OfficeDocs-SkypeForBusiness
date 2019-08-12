---
title: 'Lync Server 2013: Moving users to Enterprise Voice'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Moving users to Enterprise Voice
ms:assetid: a2df6d51-5cf2-4d3e-8f97-496af5fd5e5e
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412758(v=OCS.15)
ms:contentKeyID: 48184958
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Moving users to Enterprise Voice in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-18_

If you are moving users from an existing PBX telephony infrastructure to Enterprise Voice, the deployment process includes some steps that are not part of the planning process already described in [Planning for Enterprise Voice in Lync Server 2013](lync-server-2013-planning-for-enterprise-voice.md). For information about migrating users from an earlier Enterprise Voice deployment, see the migration documents that were included with your installation media.

The process of moving users from an existing telephony infrastructure to Enterprise Voice consists of the following steps:

1.  Designate primary phone numbers.

2.  Enable users for Enterprise Voice.

3.  Prepare dial plans for users.

4.  Plan user voice policies.

5.  Plan call routes.

6.  Configure PBX or SIP Trunk to reroute calls for users enabled for Enterprise Voice.

7.  Move users to Exchange Unified Messaging (UM) (recommended).

This topic describes the planning that is necessary for each of these steps.

<div>

## Step 1. Designate primary phone numbers

Enterprise Voice integrates voice with other messaging media, such that when an incoming call arrives at the server, the server maps the number to the user’s SIP-URI and then forks the call to all the client endpoints associated with that SIP-URI. This process requires that each user be associated with a primary phone number.

A primary phone number must be:

  - Globally unique or, in the case of internal extensions, unique in the enterprise.

  - Owned by and routable in the enterprise. Personal numbers should not be used.

Enterprise users can have two or more telephone numbers listed for them in Active Directory Domain Services. All the telephone numbers associated with a particular user can be viewed or changed on the property sheet for that user in the Active Directory Users and Computers snap-in.

The **Telephone number** box on the **General** tab of the **User Properties** dialog box should contain the user’s main work number. This number will usually be designated as the user's Primary Phone Number.

Some users may have special requirements (for example, an executive who wants all incoming calls routed through an administrative assistant), but such exceptions should be limited only to those where the need is clear and critical.

After a primary number is chosen, it must be:

  - Normalized to E.164 format, wherever possible.

  - Copied to the Active Directory **msRTCSIP-line** attribute.
    
    <div>
    

    > [!NOTE]  
    > <STRONG>Coexisting with remote call control (RCC)</STRONG><BR>RCC is the ability to use Lync Server to monitor and control a desktop PBX phone. Control is routed through the server, which acts as a gateway to the PBX. Although you cannot configure a user for both RCC and Enterprise Voice, the Line URI setting designates a user’s primary phone number in either case.<BR>If you have an existing PBX infrastructure that you want selected users to continue using, you can introduce Enterprise Voice incrementally into your organization. For details about this deployment scenario, see <A href="lync-server-2013-direct-sip-deployment-options.md">Direct SIP deployment options in Lync Server 2013</A> in the Planning documentation.<BR>In previous releases, you could enable both RCC and Enterprise Voice for a user, but only if you also configured the user for dual forking, a feature in which an incoming call will ring a user’s PBX phone and Communicator simultaneously. In Lync Server 2010, dual-forking is not supported.

    
    </div>

There are three methods for populating the **msRTCSIP-line** attribute:

  - Microsoft Identity Integration Server (recommended)

  - The **Users** page in the Lync Server Control Panel

Where many phone numbers must be processed, a script custom developed by your organization is the better choice. Depending on how your organization represents telephone numbers in Active Directory Domain Services, the script may have to normalize primary phone numbers to E.164 format before copying them to the **msRTCSIP-line** attribute.

  - If your organization maintains all telephone numbers in Active Directory Domain Services in a single format, and if that format is E.164, your script only needs to write each Primary Telephone Number to the **msRTCSIP-line** attribute.

  - If your organization maintains all telephone numbers in Active Directory Domain Services in a single format, but that format is not E.164, your script should define an appropriate normalization rule to convert Primary Telephone Numbers from their existing format to E.164 before writing them to the **msRTCSIP-line** attribute.

  - If your organization does not enforce a standard format for telephone numbers in Active Directory Domain Services, your script should define appropriate normalization rules to convert Primary Phone Numbers from their various formats to E.164 compliance before writing the Primary Telephone Numbers to the **msRTCSIP-line** attribute.

Your script will also have to insert the prefix **Tel:** before each primary number before writing it to the **msRTCSIP-line** attribute.

The expected format of the number specified in this attribute is:

  - Tel:+14255550100;ext=50100.

  - Tel:5550100 (for unique enterprise wide extensions)
    
    <div>
    

    > [!IMPORTANT]  
    > The normalization performed by the Address Book Service (ABS) does not replace or otherwise eliminate the need to normalize each user's primary phone number in Active Directory Domain Services because ABS does not have access to Active Directory Domain Services and therefore cannot copy primary numbers to the <STRONG>msRTCSIP-line</STRONG> attribute.

    
    </div>

</div>

<div>

## Step 2. Enable users for Enterprise Voice

Other than identifying which users are to be enabled, no special planning is required to complete this step.

</div>

<div>

## Step 3. Prepare dial plans for users.

Users who are enabled for Enterprise Voice will not be able to make calls to the PSTN without dial plans in place. A dial plan is a named set of normalization rules that translates phone numbers for a named location, individual user, or contact object into a single standard (E.164) format for purposes of phone authorization and call routing. Normalization rules define how phone numbers expressed in various formats are to be routed for each specified location, user, or contact object.

For information about preparing dial plans, see [Dial plans and normalization rules in Lync Server 2013](lync-server-2013-dial-plans-and-normalization-rules.md).

</div>

<div>

## Step 4. Plan user voice policies

User class-of-service settings on a legacy PBX, such as the right to make long-distance or international calls from company phones, must be reconfigured as VoIP policies for users moved to Enterprise Voice. For details about planning and creating policies for Enterprise Voice, see [Voice policies in Lync Server 2013](lync-server-2013-voice-policies.md).

</div>

<div>

## Step 5. Plan outbound call routes

Call routes specify how Lync Server handles outbound calls placed by Enterprise Voice users. When a user dials a number, the server, if necessary, normalizes the dial string to E.164 format and attempts to match it to a SIP URI. If the server is unable to make the match, it applies outgoing call routing logic based on the number. The final step in defining that logic is creating a separate named call route for each set of destination phone numbers that are listed in each dial plan.

For details about planning call routes, see [Voice routes in Lync Server 2013](lync-server-2013-voice-routes.md).

</div>

<div>

## Step 6. Configure PBX or SIP Trunk to reroute calls for Enterprise Voice users

Users who formerly were hosted on a traditional PBX or on a SIP Trunk connection to an Internet Telephony Service Provider (ITSP) retain their phone numbers after the move. The only requirement is that after the move, the PBX or SIP Trunk must be reconfigured to route incoming calls for Enterprise Voice users to the Mediation Server.

</div>

<div>

## Step 7. Move users to Exchange Unified Messaging (recommended)

Moving users to Exchange Unified Messaging consists of the following tasks:

  - Configure Exchange Unified Messaging and Lync Server to work together.

  - Enable users for Exchange Unified Messaging call answering and Outlook Voice Access. This task is performed on the Exchange Unified Messaging server. For details, see the Exchange Server 2010 TechNet Library at [http://go.microsoft.com/fwlink/p/?linkID=139372](http://go.microsoft.com/fwlink/p/?linkid=139372).

</div>

</div>

<span> </span>

</div>

</div>

</div>

