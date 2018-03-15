---
title: "Configure dial-in conferencing access numbers in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d8a18030-f318-43dd-834d-70e5014b5e8a
description: "When you deploy dial-in conferencing, you need to set up phone numbers that users can dial from the public switched telephone network (PSTN) to join the audio portion of conferences. These dial-in access numbers appear in meeting invitations and on the Dial-in Conferencing Settings webpage."
---

# Configure dial-in conferencing access numbers in Lync Server 2013
[]
When you deploy dial-in conferencing, you need to set up phone numbers that users can dial from the public switched telephone network (PSTN) to join the audio portion of conferences. These dial-in access numbers appear in meeting invitations and on the Dial-in Conferencing Settings webpage.
  
Before you can create dial-in access numbers, you must first plan your dial-in conferencing regions and then configure dial plans with the regions. For details about regions, see [Dial-in conferencing requirements in Lync Server 2013](dial-in-conferencing-requirements.md) in the Planning documentation. For details about configuring dial plans for dial-in conferencing, see [Configure dial plans for dial-in conferencing in Lync Server 2013](configure-dial-plans-for-dial-in-conferencing.md).
  
> [!NOTE]
> You cannot use a new dial-in access number until Active Directory Domain Services (AD DS) replication of that access number is complete. Replication can take several hours to complete. 
  
> [!NOTE]
> After you create dial-in access numbers, you can modify the display name for the Active Directory contact objects so that users can more easily identify the correct access number. Use the **Set-CsDialInConferencingAccessNumber** cmdlet to modify the display name. You should not modify Active Directory objects manually. For details about modifying an access number, see Lync Server Management Shell documentation for the **Set-CsDialInConferencingAccessNumber** cmdlet. 
  
## In this section

[Create or modify a dial-in conferencing access number in Lync Server 2013](create-or-modify-a-dial-in-conferencing-access-number.md)
  
## See also

#### 

[Dial-in conferencing requirements in Lync Server 2013](dial-in-conferencing-requirements.md)
#### 

[Configure dial plans for dial-in conferencing in Lync Server 2013](configure-dial-plans-for-dial-in-conferencing.md)

