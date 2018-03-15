---
title: "Overview of web conferencing in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 40616dc4-f705-4890-85bf-79f76a033a9b
description: "In this articleWhiteboard and AnnotationsPollingApplication Sharing and Desktop SharingPowerPoint Sharing"
---

# Overview of web conferencing in Lync Server 2013
[]
 **In this article**
  
[Whiteboard and Annotations](#sectionSection0)
  
[Polling](#sectionSection1)
  
[Application Sharing and Desktop Sharing](#sectionSection2)
  
[PowerPoint Sharing](#sectionSection3)
  
With web conferencing, users can share and collaborate on documents, such as PowerPoint presentations, during their conferences. Additionally, users can share all or part of their desktops with each other in real time, making it seem as though the people in the conference were gathered around the same table in the meeting.
  
## Whiteboard and Annotations
<a name="sectionSection0"> </a>

A whiteboard is a blank canvas that can be used for collaboration, with text, ink, drawings and images. Annotations made on whiteboards can be seen by all meeting participants. The whiteboard feature enhances collaboration by enabling meeting participants to discuss ideas, brainstorm, take notes, and so on.
  
## Polling
<a name="sectionSection1"> </a>

The polling feature enhances collaboration by enabling presenters to quickly determine participants' preferences. During online meetings and conversations, presenters can use polling to gather anonymous responses from participants. All presenters can see the results and can either hide the results or show them to all attendees. 
  
## Application Sharing and Desktop Sharing
<a name="sectionSection2"> </a>

During a conference you can share your entire desktop, an individual application, or individual monitors in a multi-monitor environment. Aside from just viewing the content, other participants in the conference can also request control of your screen and, with the permission, interact with the content (including scrolling and editing). 
  
> [!NOTE]
> Participants who are viewing the conference can also take over and start sharing content during the meeting 
  
## PowerPoint Sharing
<a name="sectionSection3"> </a>

In Lync 2010 PowerPoint presentations were viewed in one of two ways. For users running Lync 2010, PowerPoint presentations were displayed using the PowerPoint 97-2003 format and were viewed using an embedded copy of the PowerPoint viewer. For users running Lync Web App, PowerPoint presentations were converted to dynamic HTML files then viewed using a combination of those customized DHTML files and Silverlight. Although generally effective, this approach did have some limitations:
  
- The embedded PowerPoint Viewer (which provided the optimal viewing experience) is only available on the Windows platform.
    
- Many mobile devices (including some of the more popular mobile phones) do not support Silverlight.
    
- The PowerPoint Viewer and the DHTML/Silverlight approach do not support all of the features (such slide transitions and embedded video) that are found in the more recent editions of PowerPoint.
    
To help address these issues, and to improve the overall experience of users presenting or viewing PowerPoint presentations, Lync Server 2013 employs Office Web Apps and the Office Web Apps Server to handle PowerPoint presentations. Among other advantages, this new approach enables:
  
- Higher-resolution displays and better support for PowerPoint capabilities, such as animations, slide transitions, and embedded video.
    
- Additional mobile devices to access these presentations. That's because Lync Server 2013 uses standard DHTML and JavaScript to broadcast PowerPoint presentations instead of customized DHTML and Silverlight.
    
- Users with the appropriate privileges to scroll through a PowerPoint presentation independent of the presentation itself. For example, while Ken Myer is presenting his slide show, Pilar Ackerman can look at any slide she wants to, and without affecting Ken's presentation.
    

