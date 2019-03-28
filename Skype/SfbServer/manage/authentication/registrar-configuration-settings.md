---
title: "Manage Registrar configuration settings in Skype for Business Server"
ms.reviewer: 
ms.author: heidip
author: microsoftheidi
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: eddfbdd2-cfd0-4c03-986e-443d6728db7d
description: "Summary: Manage Registrar configuration settings for Skype for Business Server."
---

# Manage Registrar configuration settings in Skype for Business Server
 
**Summary:** Manage Registrar configuration settings for Skype for Business Server.
  
You can use the Registrar to configure proxy server authentication methods. The authentication protocol you specify determines which type of challenges the servers in the pool issue to clients. The available protocols are:
  
- **Kerberos** This is the strongest password-based authentication scheme available to clients, but it is normally available only to enterprise clients because it requires client connection to a Key Distribution Center (Kerberos domain controller). This setting is appropriate if the server authenticates only enterprise clients.
    
- **NTLM** This is the password-based authentication available to clients that use a challenge-response hashing scheme on the password. This is the only form of authentication available to clients without connectivity to a Key Distribution Center (Kerberos domain controller), such as remote users. If a server authenticates only remote users, you should choose NTLM.
    
- **Certificate authentication** This is the new authentication method when the server needs to obtain certificates from Lync Phone Edition clients, common area phones, Skype for Business and the Lync Windows Store app. On Lync Phone Edition clients, after a user signs in and is successfully authenticated by providing a personal identification number (PIN), Skype for Business Server then provisions the SIP URI to the phone and provisions a Skype for Business Server signed certificate or a user certificate that identifies Joe (Ex: SN=joe@contoso.com ) to the phone. This certificate is used for authenticating with the Registrar and Web Services.
    
> [!NOTE]
> We recommend that you enable both Kerberos and NTLM when a server supports authentication for both remote and enterprise clients. The Edge Server and internal servers communicate to ensure that only NTLM authentication is offered to remote clients. If only Kerberos is enabled on these servers, they cannot authenticate remote users. If enterprise users also authenticate against the server, Kerberos is used. 
  
If you will use Lync Windows Store app clients, you must enable certificate authentication.
  
### To create new Registrar configuration settings

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or assigned to the CsServerAdministrator or CsAdministrator role, log on to any computer that is in the network in which you deployed Skype for Business Server.
    
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel.  
    
3. In the left navigation bar, click **Security** and then click **Registrar**.
    
4. On the **Registrar** page, click **New**
    
5. In **Select a Service**, click the service to which the Registrar is to be applied and then click **OK**.
    
6. In **New Registrar Setting**, select one or more of the following depending on the capabilities of the clients and support in your environment:
    
   - **Enable Kerberos authentication** to have the servers in the pool issue challenges using Kerberos authentication.
    
   - **Enable NTLM authentication** to have the servers in the pool issue challenges using NTLM.
    
   - **Enable certificate authentication** to have the servers in the pool issue certificates to clients.
    
7. Click **Commit**.
    
## Modify existing Registrar configuration settings

You can use the Registrar to configure proxy server authentication protocols. 
  
> [!NOTE]
> We recommend that you enable both Kerberos and NTLM when a server supports authentication for both remote and enterprise clients. The Edge Server and internal servers communicate to ensure that only NTLM authentication is offered to remote clients. If only Kerberos is enabled on these servers, they cannot authenticate remote users. If enterprise users also authenticate against the server, Kerberos is used. 
  
Follow these steps to modify an existing Registrar. 
  
### To modify existing registrar configuration settings

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or assigned to the CsServerAdministrator or CsAdministrator role, log on to any computer that is in the network in which you deployed Skype for Business Server.
    
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel.  
    
3. In the left navigation bar, click **Security** and then click **Registrar**.
    
4. On the **Registrar** page, click a service, click **Edit**, and then click **Show details**.
    
5. In **Edit Registrar Setting**, select one or more of the following depending on the capabilities of the clients and support in your environment:
    
   - **Enable Kerberos authentication** to have the servers in the pool issue challenges using Kerberos authentication.
    
   - **Enable NTLM authentication** to have the servers in the pool issue challenges using NTLM.
    
   - **Enable certificate authentication** to have the servers in the pool issue certificates to clients.
    
6. Click **Commit**.
    
### To delete Registrar configuration settings

1. From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or assigned to the CsServerAdministrator or CsAdministrator role, log on to any computer that is in the network in which you deployed Skype for Business Server.
    
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 
    
3. In the left navigation bar, click **Security** and then click **Registrar**.
    
4. On the **Registrar** page, and in the search field, type all or part of the name of the Registrar you want to delete.
    
5. In the list, click the Registrar that you want, click **Edit**, and then click **Delete**.
    
6. Click **OK**.
    
## Removing Registrar Configuration Settings by Using Windows PowerShell Cmdlets

You can delete the Registrar configuration settings by using Windows PowerShell and the **Remove-CsProxyConfiguration** cmdlet. You can run this cmdlet from the Skype for Business Server Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Skype for Business Server, see the blog article ["Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell"](https://go.microsoft.com/fwlink/p/?linkId=255876). The process is the same in Skype for Business Server.
  
### To remove a specific set of Registrar security settings

- The following command removes the Registrar security settings applied to the edge Server atl-edge-011.litwareinc.com:
    
  ```
  Remove-CsProxyConfiguration -Identity service:EdgeServer:atl-edge-011.litwareinc.com
  ```

### To remove all of the Registrar security settings applied to the site scope

- The following command removes all the Registrar security settings applied to the Registrar service:
    
  ```
  Get-CsProxyConfiguration -Filter "service:Registrar:*" | Remove-CsProxyConfiguration
  ```

### To remove all of the Registrar security settings that allow NTLM authentication

- The following command deletes all the Registrar security settings that allow the use of NTLM for client authentication:
    
  ```
  Get-CsProxyConfiguration | Where-Object {$_.UseNtlmForClientToProxyAuth -eq $True}| Remove-CsProxyConfiguration
  ```

For details, see [Remove-CsProxyConfiguration](https://docs.microsoft.com/powershell/module/skype/remove-csproxyconfiguration?view=skype-ps).
  

