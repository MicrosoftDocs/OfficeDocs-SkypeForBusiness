---
title: "Skype Room System manageability and tools"
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.reviewer: davgroom
ms.topic: quickstart
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: c336ee9a-1ed8-4f64-9f7f-89549ae24c40
description: "Read this topic to learn about management tools for Skype Room System."
---

# Skype Room System manageability and tools
 
Read this topic to learn about management tools for Skype Room System.
  
## Administrative Portal

For Skype for Business Server on-premises deployments, you can use the Skype Room System administrative portal to actively manage and monitor Skype Room System deployments within your organization.
  
See the following article for more details:
  
- [Deploy SRS v1 Administrative Web Portal in Skype for Business Server](../deploy-conferencing/room-system-v1-administrative-web-portal.md)
    
## System Center Operations Manager

Skype Room System can be monitored through the System Center Operations Manager (SCOM) by downloading the [Skype Room System Management Pack](https://www.microsoft.com/download/details.aspx?id=42320) and installing it on your SCOM server. You can use SCOM to set alerts, monitor the health of Skype Room System, generate uptime reports, and much more. Skype Room System comes with a pre-installed monitoring agent that can be configured to point to SCOM server. Refer to the installation guide provided by your Skype Room System manufacturer to know how to configure the monitoring agent on Skype Room System.
  
## Exchange Checklist

- Confirm Autodiscover is set up and an internal DNS A/CNAME RECORD is available for autodiscover.domain.com.
    
- Ping autodiscover (e.g., Ping Autodiscover.contoso.com).
    
- Test your Autodiscover service with the Microsoft Connectivity Analyzer Tool. Choose the first test, "I can't log on with Office Outlook."
    
- If the meeting room already has a resource mailbox, extend this account for the Skype Room System (example script at the bottom of the page).
    
## Skype for Business Checklist

- Run the following tools:
    
  - Skype for Business Best Practices Analyzer     
  - Skype for Business Health Analysis Tool (Excel)    
  - Skype for Business Connectivity Analyzer 32-Bit or 64-Bit
    
- Review [Useful new troubleshooting and analysis tools for Office 365](https://blogs.technet.microsoft.com/educloud/2013/08/13/useful-new-troubleshooting-and-analysis-tools-for-office-365/). Confirm you have a Skype for Business pool and an Office Web Apps server and can share a PowerPoint deck using the Skype for Business client.
    
- If the meeting room already has a resource mailbox, enable it for Skype for Business.
    
- If required, request a DID (phone number) for the Meeting Room System, and update the General Telephone field in the Active Directory tool.
    
## Network

- Make sure you have a wired network connection for the Skype Room System.
    
- Read the Network Planning Guide for Skype for Business.
    
- Request a Skype for Business network assessment from a Skype for Business partner.
    
- Read through the performance data captured in the Skype for Business Health Analysis Tool (Excel).
    
- Run the Network Analysis Tool.
    
- Run the Pre-Call Diagnostics Tool.
    
## Skype Room System Security

Skype Room System is an embedded system that can be fully integrated in a Windows deployment, using the Skype for Business security model, rights management, and management tools such as SCOM. Features include:
  
- A Write Filter to prevent disk writes in user mode 
    
- App Locker to prevent unauthorized apps from running. All USB ports are disabled in user mode.
    
  - No standard apps or viewers reside on the Skype Room System hardware. All content is rendered via HTTP or RDP protocols.
    
  - The appliance PC runs the Windows Embedded Standard 7 operating system. All hardware, including devices, is provided by OEM partners.
    
  - Optional Domain Join to Active Directory Domain Services (AD DS), enabling local security account management and control.
    
- You can also manage the local admin account using the Skype for Business admin center.
    
- Skype Room System is updated through standard Microsoft Update processes.
    
- Skype Room System connects with Skype for Business.
    
  - Skype for Business uses end-to-end encryption and authorization for all modes of communication
    
  - Skype Room System supports Skype for Business security and compliance standards. See [Plan for security in Skype For Business Server](../../plan-your-deployment/security/security.md) for more information.
    
## License

Verify that you use a KMS for activating software. If so, you might need to check or add the Skype for Business client KMS key to it. If you aren't using KMS, then request the volume licensing key for the Skype for Business client MAK.
  
## License keys

Skype Room System runs the Skype for Business desktop client in the background. If Skype Room System is a domain member, it will discover your KMS. (and if it has the Volume Licensing KMS Key it will activate automatically). Volume Licensing also provides a MAK, which you enter as it displays xxxxx-xxxxx-xxxxx-xxxxx. (You need Internet access to activate using MAK but not KMS). For more information, see Volume activation of Office 2013.
  
- To enter the MAK key, go to OEM Settings \> SRS Licensing Tool. Click Check Status. When the status says "product isn't activated," enter the key.
    
- If during activation you get an error that says, "'The Software Licensing Service reported that the product key is invalid," then verify that:
    
  - The key was entered correctly.
    
  - You entered the Skype for Business MAK key and not another key.
    
  - The system has Internet access.
    
- You can activate via telephone but must have attempted to activate using the SRS Licensing Tool first. To activate via telephone, start a test meeting (not a test call as that is too short). In the Office Activation Wizard, select Telephone Activation, call Microsoft, type the long number, and enter a response.
    
## Certificate Authority

Confirm the Certificate Authority used to issue the Office Web Apps Server 2013 certificate has an HTTP path included in the Certificate Revocation List property.
  
Import the Certificate file (.crt) to the Skype Room System if using Skype for Business Server. It's easily obtained from the CertEnroll share of the CA server, or in the Trusted Root folder of any domain joined PC.
  
## Certificates

Verify your Certificate Authority has an http path for the Certificate Revocation List. If not, update your CA to include one.
  
Install certificates in the admin setup of the Skype Room System under System Settings \> Certificate Manager. You need the Enterprise Root CA for your internal certificate.
  
One way to obtain the certificates you need is to discover the CA that issued your certificates. For Skype for Business Server, on a PC in Skype for Business, click Settings \> Tools \> Dial-in Conference Settings. This opens a web page secured by the CA that issued the internal certificates. Click the Lock icon on the browser address bar to display a security report. Click View Certificates and examine the CRL Distribution Point property. The second CN parameter should be the server name of the CA. Now open Windows Explorer for that address \\\< CA Server Name \>\CertEnroll. Copy the two .crl files and the .crt file to a flash drive and put it in the left hand side of the SMART board.
  
Import the .crt file to the Skype Room System under Trusted Room Certification Authority folder.
  
Import the .crl files on the Skype Room System under the Intermediate Certificate Authorities folder. (You need to change the file extension filter in Certificate Manager to .crl to see the files).
  
Note: The Office Web Apps 2013 server may share the same CA as Skype for Business. If it doesn't you won't be able to share PowerPoint in a meeting. Check with IT and obtain the CRT and CRL files off the CA network share CertEnroll as explained above. 
  
Domain membership can simplify some things because you can treat the Skype Room System as a Windows system and it can rely on Active Directory for some of the certificate aspects. However, it's best to manually manage this.
  

