---
title: "Configure dial plans for dial-in conferencing in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: a3e0958e-384f-43e5-b4c9-686b6ecac7ed
description: "When you deploy dial-in conferencing, you need to create or modify one or more dial plans for routing dial-in access phone numbers. Make sure that at least one normalization rule in each dial plan converts telephone extensions into complete phone numbers in E.164 format. Users of dial-in conferencing join conferences as authenticated enterprise users by entering their personal identification number (PIN) and their phone number. You need a normalization rule to convert extensions into complete phone numbers so that users can be authenticated when they enter just a telephone extension."
---

# Configure dial plans for dial-in conferencing in Lync Server 2013
[]
When you deploy dial-in conferencing, you need to create or modify one or more dial plans for routing dial-in access phone numbers. Make sure that at least one normalization rule in each dial plan converts telephone extensions into complete phone numbers in E.164 format. Users of dial-in conferencing join conferences as authenticated enterprise users by entering their personal identification number (PIN) and their phone number. You need a normalization rule to convert extensions into complete phone numbers so that users can be authenticated when they enter just a telephone extension.
  
To set up dial plans for dial-in conferencing, do the following:
  
- Whether or not you deploy Enterprise Voice, modify the global dial plan to add a dial-in conferencing region and to make sure that a normalization rule accurately converts your dial-in access numbers. For detailed instructions, see [Modify a dial plan in Lync Server 2013](modify-a-dial-plan.md).
    
- If you did not deploy Enterprise Voice, create dial plans for your dial-in conferencing access numbers. Be sure to include a dial-in conferencing region. For detailed instructions, see [Create a dial plan in Lync Server 2013](create-a-dial-plan.md).
    
- If you deployed Enterprise Voice, modify Enterprise Voice dial plans as necessary to include regions and use appropriate normalization rules for dial-in access numbers. For detailed instructions, see [Modify a dial plan in Lync Server 2013](modify-a-dial-plan.md). You can also create dedicated dial plans that are used only for dial-in access numbers. For detailed instructions, see [Create a dial plan in Lync Server 2013](create-a-dial-plan.md).
    
For details about planning regions, see [Dial-in conferencing requirements in Lync Server 2013](dial-in-conferencing-requirements.md) in the Planning documentation. 
  
## In this section

- [View dial plan information in Lync Server 2013](view-dial-plan-information.md)
    
- [Create a dial plan in Lync Server 2013](create-a-dial-plan.md)
    
- [Modify a dial plan in Lync Server 2013](modify-a-dial-plan.md)
    
- [Defining normalization rules in Lync Server 2013](defining-normalization-rules.md)
    

