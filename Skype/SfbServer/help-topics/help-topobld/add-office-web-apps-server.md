---
title: "Add Office Web Apps Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 2/8/2018
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.tb.AddOfficeWebAppsServerPage
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 8825dfb1-4b3d-4e01-ba4a-2bd800c6de3b
description: "The Define New Office Web Apps Server wizard defines a new Office Web Apps Server in your deployment. You fill in the following information:"
---

# Add Office Web Apps Server

The **Define New Office Web Apps Server** wizard defines a new Office Web Apps Server in your deployment. You fill in the following information:

 **Office Web Apps Server FQDN**: Type the fully qualified domain name of the server that will host the Office Web Apps Server

 **Office Web Apps Server discovery URL**: Type the full uniform resource locator (URL) of the Office Web Apps Server

> [!TIP]
> The default behavior of the **Office Web Apps Server discovery URL** is to create the URL based on the FQDN of the Office Web Apps Server in the format: `https://<FQDN of the Office Web Apps Server/hosting/discovery` . In most cases you will not need to change the default format. You may need to change the default format in the event that the Office Web Apps Server and the Office Web Apps Server discovery URL must be different. For example, your Office Web Apps Server is placed in the perimeter network and will have a different URL based on the location.

 **Office Web Apps Server is deployed in an external network (that is, perimeter/Internet)**: Select the check box if your Office Web Apps Server is placed outside of your internal firewall, such as the perimeter network, external network, or other network zone that is not the same as your internal network.

## See also

[Components and Topologies for Conferencing](https://technet.microsoft.com/library/eb83052a-3360-4ba1-a6a0-6ee419942809.aspx)
