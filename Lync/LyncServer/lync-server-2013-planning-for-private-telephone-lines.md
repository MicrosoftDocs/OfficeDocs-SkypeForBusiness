---
title: 'Lync Server 2013: Planning for private telephone lines'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Planning for private telephone lines
ms:assetid: 9cc4f9e1-7b7a-4699-bd05-f16669ef2d21
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412728(v=OCS.15)
ms:contentKeyID: 48184909
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Planning for private telephone lines with Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-11_

Lync Server 2013 introduces the ability to give users a second, private telephone line in addition to their primary telephone line. Private telephone lines are often assigned to executives and others who want an unlisted telephone number at which they can be reached directly.

Private telephone lines can only be configured with the Lync Server Management Shell. You cannot configure private telephone lines with the Lync Server Control Panel. Private telephone lines should be configured only in deployments of Lync Server and not in mixed deployments.

<div>

## Characteristics of Private Telephone Lines

Although the concept of a second, private telephone line is fundamentally simple, it is important to understand the characteristics of private lines and the ways in which they are similar to and different from users’ primary telephone lines.

<div>

## General Characteristics of Private Telephone Lines

  - A user can have only one private telephone line.

  - A user with a private telephone line has only one voice mailbox and receives missed call notifications at a single email address.

  - A user with a private telephone line does not have a second SIP address, and a second, private telephone line does not give a user a second presence on the network (such as a second instant messaging identity).

  - Private telephone lines are available for on-premises deployments only. They are not available with hosted deployments of Lync Server.

</div>

<div>

## How Private Telephone Lines Differ from Primary Telephone Lines

  - The telephone numbers for private telephone lines do not appear in the telephone directories or Contacts lists that are derived from Active Directory Domain Services.

  - None of the following features are available with a private telephone line: call forwarding, team call, delegation, team ring, Group Call Pickup, and Response Group application.

  - Calls to a private telephone line have a special ring, and the system notification for the call tells the user that the incoming call is on his or her private line.

  - Calls to the private telephone line always ring through. They do not follow "do not disturb" rules.

  - Private telephone lines are inbound only and cannot be used to make outgoing calls. When a user with a private telephone line makes a call, the call originates from the user’s primary telephone line and does not hide the user’s name or the user’s primary telephone number from the person called.

</div>

<div>

## How Private Telephone Lines Are Similar to Primary Telephone Lines

  - Unanswered calls to a private telephone line are routed to the same voice mail inbox as for the primary telephone line (if voice mail is enabled).

  - Call park and call pickup work with private telephone lines in exactly the same manner as they do with the user’s primary telephone line.

  - When simultaneous ringing is enabled on a user’s primary telephone line, it is also enabled on the private telephone line.

  - The telephone number for a private telephone line is recorded in the call detail record in the same manner as the telephone number for a user’s primary telephone line, but with an indication that it is a private telephone number.

  - After a user answers a call on a private telephone line, the call is treated the same as a call on the user’s primary telephone line. For example, if a user who receives a call on a private telephone line forwards the call or invites others to a conference call, the user’s name appears in Lync 2013, and the telephone number for the user’s primary telephone line appears in caller ID.

  - A user can deflect a call (redirect the call to another destination, such as a mobile phone or home phone, before answering) from the private telephone line in the same manner as with a primary telephone line.
    
    <div>
    

    > [!NOTE]  
    > When a call to a private line is routed to an alternate telephone number, the telephone number for the private telephone line is made available to the alternate telephone number and can be displayed in the logs for that number.

    
    </div>
    
    <div>
    

    > [!NOTE]  
    > Calls from a conference to the private telephone line will not have a <EM>private-line</EM> indication in the incoming system notification.

    
    </div>

</div>

</div>

<div>

## Administering Private Telephone Lines

In addition to the technical aspects of creating and managing private telephone lines, you will need to establish administrative procedures for them. This includes determining policies for who in the organization is eligible for a private line, creating and maintaining lists of people and their telephone lines, possibly creating a private telephone directory for executives, arranging for user training, and related tasks.

<div>


> [!NOTE]  
> The private telephone line is stored in Active Directory as an msRTCSIP-PrivateLine attribute on the user object. By default any member of the Authenticated Users group has read access to this attribute.



</div>

<div>

## Assigning Telephone Numbers

Accounts for new users who need private telephone lines are created in the same manner as accounts without private telephone lines, using Lync Server Control Panel or Lync Server Management Shell.

Use the **Set-CsUser** cmdlet in the Lync Server Management Shell to assign a telephone number to a private telephone line for a user, for example, **Set-CsUser -Identity "sip:joe@contoso.com" -PrivateLine "Tel:+14255551212"**.

Telephone numbers for private telephone lines can be between 3 and 15 numbers in length and must be preceded with the "TEL:" prefix. They can have any area code and any country/region code as long as your organization has direct inward dialing for that area code and country/region code.

For details about cmdlets and Lync Server Management Shell, see the [Lync Server 2013 Management Shell](lync-server-2013-lync-server-management-shell.md) documentation.

</div>

<div>

## Private Telephone Lines in Mixed Deployments

Private telephone lines should be configured only for deployments of Lync Server. In a deployment in which there are both Lync Server and Office Communications Server 2007 or Office Communications Server 2007 R2 servers, when a user on earlier version attempts to call a private telephone line, routing of the call fails because the server cannot perform a reverse number lookup on a private telephone line.

</div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

