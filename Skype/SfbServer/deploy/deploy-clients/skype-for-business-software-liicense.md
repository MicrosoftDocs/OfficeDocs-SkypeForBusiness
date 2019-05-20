---
title: "Skype Room System Skype for Business software license"
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.reviewer: davgroom
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 78a664ba-fefc-4423-ac8f-b58e6fbc2e55
description: "Read this topic to learn how to check whether you have a Skype for Business software volume license."
---

# Skype Room System: Skype for Business software license
 
Read this topic to learn how to check whether you have a Skype for Business software volume license. 
  
Skype Room System uses an installed Skype for Business client, which requires a software volume license. Before deploying the first Skype Room System, find out the volume license state of the deployment - using Key Management Servers (KMS) or Multiple Activation Keys (MAK).
  
## Key Management Servers (KMS)

If KMS are in place and will distribute Skype for Business Volume License activations, the Skype Room System will automatically activate the Skype for Business client. To find out if KMS are in place:
  
From a command prompt, run:  `nslookup -type=srv _vlmcs._tcp >%temp%\kms.txt`
  
For more information, see [How to discover Office and Windows KMS hosts via DNS and remove unauthorized instances](https://blogs.technet.com/b/odsupport/archive/2011/11/14/how-to-discover-kms-hosts-via-a-dns-query-and-remove-them-if-need-be.aspx). 
  
To set up a KMS, see [KMS activation of Office 2013](https://technet.microsoft.com/library/ee624357.aspx) and [GVLKs for KMS and Active Directory activation of Office 2013](https://technet.microsoft.com/library/dn385360.aspx)
  
Office 2013 Generic Volume License Key for Lync: 2MG3G-3BNTT-3MFW9-KDQW3-TCK7R (This key causes the Skype Room System to look for a KMS on the network.)
  
## Multiple Activation Keys (MAK) from the Volume License Service Center (VLSC)

If the customer uses any other volume license software, the IT department will manage the software activations and Volume License Agreement (VLA) using the VLSC. This will also enable the company to purchase Skype for Business VL activations, after which the company can obtain a MAK for input in the Skype Room System Admin Console.
  
A customer with a VLA must know their VLSC credentials, which will be used to administer the agreement and obtain MAK. If uncertain, the customer's finance department should be able to confirm if the customer has paid for a VLA.
  
To obtain a MAK, access the Volume Licensing Service Center to view agreements and download product keys (MAK). For more information, go to the [Volume Licensing Service Center](https://www.microsoft.com/Licensing/servicecenter/default.aspx). 
  
## MAK for Office 365 without VLSC access

If the customer doesn't have a Volume License Agreement, Skype for Business activations will be much more difficult to manage. However, Office 365 customers without VLSC access can obtain a promotional MAK by providing the following information to the OEM selling the Skype Room System:
  
- Company name
    
- Deployment contact name, email, and phone number
    
- Number of systems deployed
    
- Deployment date
    
- If the customer has a Microsoft Technical Account Manager, the TAM's name and contact information
    

