---
title: "Validating the configuration of Office Web Apps Server in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f6e8ecbf-305d-4a13-92d0-b61dbd82b0ea
description: "After Office Web Apps Server has been added to the topology, and after that topology has been published, you should see two new event log events in the Lync Server event log. First, an LS Data MCU event (event ID 41034) should be added; this event will report that the Office Web Apps Server has been discovered:"
---

# Validating the configuration of Office Web Apps Server in Lync Server 2013
[]
After Office Web Apps Server has been added to the topology, and after that topology has been published, you should see two new event log events in the Lync Server event log. First, an LS Data MCU event (event ID 41034) should be added; this event will report that the Office Web Apps Server has been discovered:
  
 **Web Conferencing Server Office Web Apps Server is discovered, PowerPoint content is enabled.**
  
In addition to that you should see another LS Data MCU event (event ID 41032) that reports back Office Web Apps Server URLs. For example, you should see something similar to this:
  
 **Web Conferencing Server Office Web Apps Server discovery has succeeded.**
  
 **Office Web Apps Server internal presenter page: https://atl-officewebapps-001.litwareinc.com/m/Presenter.aspx?a=0&amp;embed=**
  
 **Office Web Apps Server internal attendee page: https://atl-officewebapps-001.litwareinc.com/m/ParticipantFrame.aspx?a=0&amp;embed=true&amp;=**
  
 **Office Web Apps Server external presenter page: https://atl-officewebapps-001.litwareinc.com/m/Presenter.aspx?a=0&amp;embed**
  
 **Office Web Apps Server internal attendee page: https://atl-officewebapps-001.litwareinc.com/m/ParticipantFrame.aspx?a=0&amp;embed=true&amp;**
  
If you see an LS Data MCU event with the event ID of 41033 that means that Office Web Apps Server discovery has failed. In that case, Microsoft Lync Server 2013 will try as many times as needed to discover the newly-configured Office Web Apps Server. If the discovery process fails repeatedly you should remove Office Web Apps Server from your topology document, publish the updated topology, and then try adding Office Web Apps Server back to the topology after the connectivity issues have been resolved.
  
If Office Web Apps Server appears to be configured correctly and has been recognized by the discovery process you can verify that Office Web Apps Server is working as expected by sharing a PowerPoint presentation between a pair of Microsoft Lync 2013 clients. If User A can load and display the PowerPoint presentation and if User B can then join the meeting and see that presentation then Office Web Apps Server is working.
  
Even if Office Web Apps Server appears to be configured correctly, you could potentially receive the error message "Some sharing features are unavailable due to server connectivity issues" when you try sharing a PowerPoint presentation. If you receive that error message you should restart the Front End server (or servers) associated with the new Office Web Apps Server.
  

