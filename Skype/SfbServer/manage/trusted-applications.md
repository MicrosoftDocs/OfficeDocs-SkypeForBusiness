---
title: "Manage trusted applications"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "A trusted application is an application based on Microsoft Unified Communications Managed API (UCMA) 3.0 Core SDK that is trusted by Skype for Business Server."
---

# Manage trusted applications in Skype for Business Server

A *trusted application* is an application based on Microsoft Unified Communications Managed API (UCMA) 3.0 Core SDK that is trusted by Skype for Business Server. For details about UCMA applications, see “Unified Communications Managed API 3.0 Core SDK Documentation” at http://go.microsoft.com/fwlink/p/?linkId=210320.

To successfully publish, enable, or disable a topology when adding or removing a server role, you should be logged on as a user who is a member of the RTCUniversalServerAdmins and Domain Admins groups. 

Use this article to learn how to configure a new trusted application server, view a list of trusted applications, and view trusted application information. 

## Configure a new trusted application server

1.  Log on to the computer where Topology Builder is installed as a member of the Domain Admins group and the RTCUniversalServerAdmins group.

2.  Start Topology Builder: Click **Start**, click **All Programs**, click **Skype for Business Server**, and then click **Skype for Business Server Topology Builder**.

3.  Select **Download topology from existing deployment**, and then click **OK**.

4.  In the **Save Topology As** dialog box, click the Topology Builder file you want to use, and then click **Save**.

5.  In the left pane, right-click **Trusted application servers**, and then click **New Trusted Application Pool**.

6.  Enter the **Pool FQDN** of the trusted application pool, select whether it will be a single-server or multiple-server, and then click **Next**.

7.  On the **Select the next hop** page, from the list, select the Skype for Business Server Front End pool.

8.  Click **Finish**.

9.  Select the top node **Skype for Business Server**, and then, from the **Actions** menu, click **Publish Topology**.
    
    The **Trusted Application Pool** should have been created successfully and associated with the correct Front End pool.


## View a list of trusted applications

You can use the Skype for Business Server Control Panel to view a list of the trusted applications that you have deployed in your Skype for Business Server environment. A trusted application is an application based on Microsoft Unified Communications Managed API (UCMA) 3.0 Core SDK that is trusted by Skype for Business Server. This trust relationship is summarized in the following list:

  - Trusted applications are not challenged for authentication by Skype for Business Server.

  - Trusted applications are not throttled by Skype for Business Server for SIP transactions, connections or outgoing Voice over Internet Protocol (VoIP) calls.

  - Trusted applications can impersonate any user and can join conferences without appearing in rosters.

  - Trusted applications are highly available and resilient.

In the Skype for Business Server Control Panel, you can see the name of the applications, the pool where they run, and the port they use.


### To view a list of trusted applications

1.  From a user account that is assigned to the CsServerAdministrator, CsAdministrator, CsHelpDesk, or CsViewOnlyAdministrator role, log on to any computer in your internal deployment. For details about the predefined administrative roles available in Skype for Business Server, see [Role-based access control (RBAC)](../plan-your-deployment/security/role-based-access-control-rbac.md).

2.  Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel.

3.  In the left navigation bar, click **Topology**, and then click **Trusted Application**.

4.  On the **Trusted Application** page, click a column heading to sort the applications, if needed.


## View trusted application information

You can view information about your trusted applications by using Windows PowerShell and the **Get-CsTrustedApplication** cmdlet. This cmdlet can be run either from the Skype for Business Server Management Shell or from a remote session of Windows PowerShell. 


### To view trusted applications

To view all of your trusted applications, type the following command in the Skype for Business Server Management Shell, and then press ENTER:
    
        Get-CsConferenceDisclaimer
    
   This command returns information similar to the following for each trusted application:
    
        Identity               : CN={5dedf4b0-a590-49b3-80cf-f16f914bbef9},CN=Application Contacts,CN=RTC
                                 Service,CN=Services,CN=Configuration,DC=litware,DC=com
        RegistrarPool          : 487279971
        HomeServer             : CN=Lc Services,CN=Microsoft,CN=co1:2,CN=Pools,CN=RTC
                                 Service,CN=Services,CN=Configuration,DC=litware,DC=com
        OwnerUrn               : urn:application:helpdesk
        SipAddress             : sip:RtcApplication-dbf5142f-2bb2-4c4f-9531-b7fea45c5000@litware.com
        DisplayName            :
        DisplayNumber          :
        LineURI                :
        PrimaryLanguage        : 0
        SecondaryLanguages     : {}
        EnterpriseVoiceEnabled : True
        ExUmEnabled            : False
        Enabled                : True
    
   For details, see [Get-CsTrustedApplication](https://docs.microsoft.com/powershell/module/skype/Get-CsTrustedApplication).
