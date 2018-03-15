---
title: "Configuring integration with Office Web Apps Server and Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3370ab55-9949-4f32-b88b-5cffed6aaad8
description: "Lync Server 2013 employs Office Web Apps Server to handle PowerPoint presentations. For information about the advantages to this approach, see Overview of web conferencing in Lync Server 2013."
---

# Configuring integration with Office Web Apps Server and Lync Server 2013
[]
Lync Server 2013 employs Office Web Apps Server to handle PowerPoint presentations. For information about the advantages to this approach, see [Overview of web conferencing in Lync Server 2013](web-conferencing-overview.md).
  
In order to use these new capabilities administrators must install Office Web Apps Server and they must configure Lync Server 2013 to communicate with Office Web Apps Server. This documentation provides information on how to configure Lync Server 2013 to work with Office Web Apps Server. What this documentation does not provide is information on how to install Office Web Apps Server itself; for that information, see the Microsoft Office Web Apps Deployment website at [https://go.microsoft.com/fwlink/p/?linkid=257525](https://go.microsoft.com/fwlink/p/?linkid=257525). That guide includes complete prerequisite information for Office Web Apps Server; note that Office Web Apps Server should be installed on a stand-alone computer that is not running Lync Server, Microsoft SQL Server, or any other server application. (You must not have any version of Microsoft Office installed on that computer.) Any computer used to run Office Web Apps Server must also have a specific set of software installed (including .NET Framework 4.5 and Windows PowerShell 3.0); these requirements, along with information on configuring certificates and Internet Information Services (IIS), are discussed in detail in the Microsoft Office Web Apps Deployment website at [https://go.microsoft.com/fwlink/p/?linkid=257525](https://go.microsoft.com/fwlink/p/?linkid=257525).
  
> [!NOTE]
> The latest iteration of Office Web Apps Server is named Office Online Server, which is supported by Lync Server 2013. For more detail, refer to the [Office Online Server documentation](https://technet.microsoft.com/en-us/library/jj219456%28v=office.16%29.aspx). 
  
This document covers the following topic areas:
  
- [Configuring Lync Server 2013 to work with Office Web Apps Server](configuring-lync-server-2013-to-work-with-office-web-apps-server.md)
    
- [Publishing Office Web Apps Server in Lync Server 2013 using a reverse proxy server](publishing-office-web-apps-server-using-a-reverse-proxy-server.md)
    
- [Validating the configuration of Office Web Apps Server in Lync Server 2013](validating-the-configuration-of-office-web-apps-server.md)
    
- [Configuring clients of Lync Server 2013 for use with Office Web Apps Server](configuring-clients-for-use-with-office-web-apps-server.md)
    

