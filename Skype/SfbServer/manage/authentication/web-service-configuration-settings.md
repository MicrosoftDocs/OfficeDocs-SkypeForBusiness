---
title: "Manage Web Service configuration settings in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: f3f04d81-8a1f-427f-bd0f-fb659024e096
description: "Summary: Manage Web Service configuration settings in Skype for Business Server."
---

# Manage Web Service configuration settings in Skype for Business Server
 
**Summary:** Manage Web Service configuration settings in Skype for Business Server.
  
You can use the **Web Service** page to configure the authentication methods for accessing Skype for Business Server related web servers and Web Services.
  
Follow these steps to create a new Web Service policy.
  
### To create new web service configuration settings

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or assigned to the CsServerAdministrator or CsAdministrator role, log on to any computer that is in the network in which you deployed Skype for Business Server.
    
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel.  
    
3. In the left navigation bar, click **Security** and then click **Web Service**.
    
4. On the **Web Service** page, click **New**, and then do one of the following:
    
   - To configure the Web Service for a site, click **Site configuration**. In **Select a Site**, click the site to which the Web Service policy will be applied a site and click **OK**.
    
   - To configure the Web Service for a pool, click **Pool configuration**. In **Select a Service**, click the service to which the Web Service policy will be applied and click **OK**. 
    
5. In **New Web Service Setting**, in **Integrated Windows authentication**, select **Negotiate**, **Integrated Windows authentication**, or **None**.
    
6. Select one or more of the following depending on the capabilities of the clients and support in your environment:
    
   - **Enable PIN Authentication** to enable clients to be authenticated using PIN numbers.
    
   - **Enable certificate authentication** to have the servers in the pool issue certificates to clients.
    
   - **Enable certificate chain download** to have servers presented with an authentication certificate download the certificate chain for that certificate.
    
7. Click **Commit**.
    
## Modify existing Web Service configuration settings

You can use the **Web Service** page to configure the authentication methods for accessing Skype for Business Server related web servers and Web Services.
  
Follow these steps to modify an existing Web Service policy.
  
### To modify existing Web service configuration settings

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or assigned to the CsServerAdministrator or CsAdministrator role, log on to any computer that is in the network in which you deployed Skype for Business Server.
    
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel.  
    
3. In the left navigation bar, click **Security** and then click **Web Service**.
    
4. On the **Web Service** page, click a configuration, click **Edit**, and then click **Show details**.
    
5. In **Edit Web Service Setting**, in **Integrated Windows authentication**, select **Negotiate**, **Integrated Windows authentication**, or **None**.
    
6. Select one or more of the following depending on the capabilities of the clients and support in your environment:
    
   - **Enable PIN Authentication** to enable clients to be authenticated using PIN numbers.
    
   - **Enable certificate authentication** to have the servers in the pool issue certificates to clients.
    
   - **Enable certificate chain download** to have servers presented with an authentication certificate download the certificate chain for that certificate.
    
7. Click **Commit**.
    
## Delete existing Web Service configuration settings

Follow these steps to delete web service configuration settings.
  
### To delete web service configuration settings

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or assigned to the CsServerAdministrator or CsAdministrator role, log on to any computer that is in the network in which you deployed Skype for Business Server.
    
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel.  
    
3. In the left navigation bar, click **Security** and then click **Web Service**.
    
4. On the **Web Service** page, and in the search field, type all or part of the name of the policy you want to delete.
    
5. In the list of policies, click the policy that you want, click **Edit**, and then click **Delete**.
    
6. Click **OK**.
    
## Deleting Web Service Configuration Settings by Using Windows PowerShell Cmdlets

You can delete web service configuration settings by using Windows PowerShell and the **Remove-CsWebServiceConfiguration** cmdlet. You can run this cmdlet from the Skype for Business Server Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Skype for Business Server, see the blog article ["Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell"](https://go.microsoft.com/fwlink/p/?linkId=255876). The process is the same in Skype for Business Server.
  
### To delete a specific collection of web service configuration settings

- The following command removes the Web Service security settings applied to the Redmond site:
    
  ```
  Remove-CsWebServiceConfiguration -Identity "site:Redmond"
  ```

### To delete all of the web service configuration settings applied to the site scope

The following command removes all of the Web Service security settings applied to the service scope:
    
  ```
  Get-CsWebServiceConfiguration -Filter "service:*" | Remove-CsWebServiceConfiguration
  ```

### To delete all of the web service configuration settings that allow certificate authentication

The following command removes all the Web Service security settings that allow the use of certificate authentication:
    
  ```
  Get-CsWebServiceConfiguration | Where-Object {$_.UseCertificateAuth -eq $True} | Remove-CsWebServiceConfiguration
  ```

For details, see [Remove-CsWebServiceConfiguration](https://docs.microsoft.com/powershell/module/skype/remove-cswebserviceconfiguration?view=skype-ps).
  

