---
title: "Deploy the SEFAUtil tool in Skype for Business"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom: 
ms.assetid: fb556e50-88dd-4404-a3d5-be36f5ba41e6
description: "Deploying the SEFAUtil tool in Skype for Business Server."
---

# Deploy the SEFAUtil tool in Skype for Business
 
Deploying the SEFAUtil tool in Skype for Business Server.
  
To deploy and manage Group Call Pickup, you need to use the Skype for Business Server version of the SEFAUtil tool. 
  
> [!IMPORTANT]
> Microsoft Unified Communications Managed API (UCMA) 5 Runtime must be installed on any computer where you plan to run the SEFAUtil tool. Download it here: [Unified Communications Managed API 5.0 Runtime](https://www.microsoft.com/en-us/download/details.aspx?id=47344). You can also download the UCMA 5 SDK, which includes the runtime, here: [UCMA 5.0 SDK](https://www.microsoft.com/en-us/download/details.aspx?id=47345).
  
You can run the SEFAUtil tool in any Front End pool in your deployment. 
To run the SEFAUtil tool you must run Steps 1, 2, and 3 from the Skype for Business Deployment Wizard on the Trusted Application Computer. 
SEFAUtil requires the local configuration store to be present, as well as a certificate.
  
> [!NOTE]
> For more details about running SEFAUtil, see the  blog article, "[How to get SEFAutil running?](https://go.microsoft.com/fwlink/?LinkId=278940)". 
  
### To deploy SEFAUtil

1. Log on to the computer where Skype for Business Server Management Shell is installed as a member of the RTCUniversalServerAdmins group or with the necessary user rights as described in **Delegate Setup Permissions**.
    
2. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.
    
3. The SEFAUtil tool can be run only on a computer that is part of a trusted application pool. If needed, define a trusted application pool for the Front End pool where you plan to run SEFAUtil. At the command line, run:
    
   ```
   New-CsTrustedApplicationPool -id <Pool FQDN> -Registrar <Pool Registrar FQDN> -site Site:<Pool Site>
   ```
    > [!NOTE]
    > Pool FQDN: The FQDN of the server or pool that will host the SEFAUtil application (usually a Skype for Business Front End server or pool).
    > Pool Registrar FQDN: The FQDN of the Skype for Business Front End server or pool associated with this application pool.
    > Pool Site: The Site ID of the site on which this pool is homed.

4. Define the SEFAUtil tool as a trusted application. At the command line, run:
    
   ```
   New-CsTrustedApplication -ApplicationId sefautil -TrustedApplicationPoolFqdn <Pool FQDN>  -Port 7489
   ```

    > [!NOTE]
    > You can use a different port if needed. 
  
5. Enable the topology with your changes. At the command line, run:
    
   ```
   Enable-CsTopology
   ```

6. If you haven't already, download the Skype for Business Server version of the SEFAUtil tool from [this location](https://www.microsoft.com/en-us/download/details.aspx?id=52631), and install it on the trusted application pool you created in step 3.
    
7. Verify that the SEFAUtil tool is running correctly, as follows: 
    
    a. Run the tool from the Windows command prompt with administrator privileges to display the call forwarding settings of a user in your deployment.
    
    b. Display the call forwarding settings of a user. At the command line, run:
    
   ```
   SEFAUtil.exe <user SIP address> /server:<Lync Server/Pool FQDN>
   ```

The call forwarding settings for the user will be displayed.
    

