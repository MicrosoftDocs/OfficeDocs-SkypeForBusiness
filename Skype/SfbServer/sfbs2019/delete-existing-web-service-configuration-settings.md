---
title: "Delete existing Web Service configuration settings in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c2b96f4c-4b07-48e6-9ca6-55bc0e0cf5a1
description: "Follow these steps to delete web service configuration settings."
---

# Delete existing Web Service configuration settings in Lync Server 2013
[]
Follow these steps to delete web service configuration settings.
  
### To delete web service configuration settings

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or assigned to the CsServerAdministrator or CsAdministrator role, log on to any computer that is in the network in which you deployed Lync Server 2013. 
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Security** and then click **Web Service**.
    
4. On the **Web Service** page, and in the search field, type all or part of the name of the policy you want to delete. 
    
5. In the list of policies, click the policy that you want, click **Edit**, and then click **Delete**.
    
6. Click **OK**.
    
## Deleting Web Service Configuration Settings by Using Windows PowerShell Cmdlets

You can delete web service configuration settings by using Windows PowerShell and the **Remove-CsWebServiceConfiguration** cmdlet. You can run this cmdlet from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876).
  
### To delete a specific collection of web service configuration settings

- The following command removes the Web Service security settings applied to the Redmond site:
    
  ```
  Remove-CsWebServiceConfiguration -Identity "site:Redmond"
  ```

### To delete all of the web service configuration settings applied to the site scope

- The following command removes all of the Web Service security settings applied to the service scope:
    
  ```
  Get-CsWebServiceConfiguration -Filter "service:*" | Remove-CsWebServiceConfiguration
  ```

### To delete all of the web service configuration settings that allow certificate authentication

- The following command removes all the Web Service security settings that allow the use of certificate authentication:
    
  ```
  Get-CsWebServiceConfiguration | Where-Object {$_.UseCertificateAuth -eq $True} | Remove-CsWebServiceConfiguration
  ```

For details, see [Remove-CsWebServiceConfiguration](remove-cswebserviceconfiguration.md).
  
## See also

#### 

[Configuring authentication in the Lync Server 2013 Control Panel](configuring-authentication-in-the-lync-server-control-panel.md)

