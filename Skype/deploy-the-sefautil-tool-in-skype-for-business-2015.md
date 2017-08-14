---
title: Deploy the SEFAUtil tool in Skype for Business 2015
ms.prod: SKYPEFORBUSINESS
ms.assetid: fb556e50-88dd-4404-a3d5-be36f5ba41e6
---


# Deploy the SEFAUtil tool in Skype for Business 2015
[]Deploying the SEFAUtil tool in Skype for Business Server.
To deploy and manage Group Call Pickup, you need to use the Skype for Business Server version of the SEFAUtil tool. 
  
    
    


> [!IMPORTANT]
> Microsoft Unified Communications Managed API (UCMA) 3.0 Core SDK must be installed on any computer where you plan to run the SEFAUtil tool. 
  
    
    


You can run the SEFAUtil tool in any Front End pool in your deployment.
  
    
    


> [!NOTE]
> For more details about running SEFAUtil, see the Technet blog article, "How to get SEFAutil running?" at  [https://go.microsoft.com/fwlink/?LinkId=278940](https://go.microsoft.com/fwlink/?LinkId=278940). 
  
    
    


### To deploy SEFAUtil


1. Log on to the computer where Skype for Business Server Management Shell is installed as a member of the RTCUniversalServerAdmins group or with the necessary user rights as described in **Delegate Setup Permissions**.
    
  
2. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.
    
  
3. The SEFAUtil tool can be run only on a computer that is part of a trusted application pool. If needed, define a trusted application pool for the Front End pool where you plan to run SEFAUtil. At the command line, run:
    
  ```
  
New-CsTrustedApplicationPool -id <Pool FQDN> -Registrar <Pool Registrar FQDN> -site Site:<Pool Site>
  ```

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

6. If you haven't already, download the Skype for Business Server version of the SEFAUtil tool from  [this location](http://www.microsoft.com/en-us/download/details.aspx?id=47704), and install it on the trusted application pool you created in step 3.
    
    
    
  
7. Verify that the SEFAUtil tool is running correctly, as follows: 
    
1. Run the tool from the Windows command prompt with administrator privileges to display the call forwarding settings of a user in your deployment.
    
  
2. Display the call forwarding settings of a user. At the command line, run:
    
  ```
  SEFAUtil.exe <user SIP address> /server:<Lync Server/Pool FQDN>
  ```


    The call forwarding settings for the user will be displayed.
    
  

