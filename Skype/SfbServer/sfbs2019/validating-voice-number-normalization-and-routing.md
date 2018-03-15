---
title: "Validating voice number normalization and routing in Lync Server 2013"
ms.author: jambirk
author: jambirk
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: a6a825c7-6928-4e80-b7e9-803b7f7ebd13
description: "Correct number normalization and routing is very important for functional Enterprise Voice environment. Especially during migrations from private branch exchange (PBX) to stand-alone Lync Server environment, one of the keys to successful migration is to reveal and document all existing dialing rules, and create appropriate normalization rules, voice policies, phone usages and routes."
---

# Validating voice number normalization and routing in Lync Server 2013
[]
Correct number normalization and routing is very important for functional Enterprise Voice environment. Especially during migrations from private branch exchange (PBX) to stand-alone Lync Server environment, one of the keys to successful migration is to reveal and document all existing dialing rules, and create appropriate normalization rules, voice policies, phone usages and routes.
  
Validating number normalization and routing is important not only during migrations but also during normal, stable operation of the system.
  
We recommend conducting this validation daily by using the Lync Server Control Panel, starting with developing a robust set of test cases against the current set of normalization rules that were published in the Lync Server global settings. These test cases should be run daily to highlight any unwanted changes that were made and committed to the dial plan.
  
Lync Server Control Panel also helps you visualize, test, change, archive, and share configuration information about voice routing and in changing Enterprise Voice number normalization rules, dial plans, voice policy, and routes. It has additional features for doing the following:
  
- Exporting and importing or backing up voice routing data between systems.
    
- Testing configuration changes before uploading them to a live system.
    
- Creating and running configuration test cases to help ensure the usability of routing data after you make changes to it, but before committing them the changes to a deployed system.
    
- Creating and changing number normalization rules, location profiles, voice policy, and routing data without writing the necessary regular expressions.
    
- Analyzing a location profile for compatibility with the Lync Server Phone Edition.
    
- More information about voice routing tests can be found at [Test voice routing in Lync Server 2013](test-voice-routing.md)
    
## See also

#### 

[Test voice routing in Lync Server 2013](test-voice-routing.md)

