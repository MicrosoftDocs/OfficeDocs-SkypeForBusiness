---
title: "Example XMPP configuration in Lync Server 2013 - XMPP federation with Google Talk"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 360a2f7b-015b-4e93-ac67-0f609c21f1a2
description: "An example configuration for deploying the XMPP Proxy defines a federation with Google Talk."
---

# Example XMPP configuration in Lync Server 2013 - XMPP federation with Google Talk
[]
An example configuration for deploying the XMPP Proxy defines a federation with Google Talk.
  
### Example XMPP configuration - XMPP federation with Google Talk

1. On the Front End Server, open the Lync Server Deployment Wizard. Click **Install** or **Update Lync Server System**, then click **Setup** or **Remove Lync Server Components**. Click **Run Again**.
    
2. At **Setup Lync Server components**, click **Next**. The summary screen will show actions as they are executed. After the deployment is complete, click **View Log** to view available log files. Click **Finish** to complete the deployment. 
    
3. On the Edge Server, open the Lync Server Deployment Wizard. Click **Install** or **Update Lync Server System**, then click **Setup** or **Remove Lync Server Components**. Click **Run Again**.
    
4. Add Google Talk as an XMPP allowed partner. Google Talk currently only supports unencrypted, TCP connections for server-to-server XMPP federation and only supports Server Dialback for identity verification. (See [https://xmpp.org/extensions/xep-0220.html](https://xmpp.org/extensions/xep-0220.mdl)).
    
  ```
  New-CsXmppAllowedPartner gmail.com -TlsNegotiation NotSupported -SaslNegotiation NotSupported -EnableKeepAlive $false -SupportDialbackNegotiation $true
  ```

5. To enable Edge Federation, type the following:
    
  ```
  Set-CsAccessEdgeConfiguration -AllowFederatedUsers $true
  ```

6. At **Setup Lync Server components**, click **Next**. The summary screen will show actions as they are executed. After the deployment is done, click **View Log** to view available log files. Click **Finish** to complete the deployment. 
    
7. On the Edge Server, in the Lync Server Deployment Wizard, next to **Step 3: Request, Install, or Assign Certificates**, click **Run again**.
    
    > [!TIP]
    > If you are deploying the Edge Server for the first time, you will see Run instead of Run Again. 
  
8. On the **Available Certificate Tasks** page, click **Create a new certificate request**.
    
9. On the **Certificate Request** page, click **External Edge Certificate**.
    
10. On the **Delayed or Immediate Request** page, select the **Prepare the request now, but send it later** check box. 
    
11. On the **Certificate Request File** page, type the full path and file name of the file to which the request is to be saved (for example, c:\cert_exernal_edge.cer). 
    
12. On the **Specify Alternate Certificate Template** page, to use a template other than the default WebServer template, select the **Use alternative certificate template for the selected certification authority** check box. 
    
13. On the **Name and Security Settings** page, do the following: 
    
1. In **Friendly name**, type a display name for the certificate
    
2. In **Bit length**, specify the bit length (typically, the default of **2048**)
    
3. Verify that the **Mark certificate private key as exportable** check box is selected 
    
14. On the **Organization Information** page, type the name for the organization and the organizational unit (for example, a division or department) 
    
15. On the **Geographical Information** page, specify the location information 
    
16. On the **Subject Name/Subject Alternate Names** page, the information to be automatically populated by the wizard is displayed. If additional subject alternative names are needed, you specify them in the next two steps 
    
17. On the **SIP Domain Setting on Subject Alternate Names (SANs)** page, select the domain check box to add a sip.  _\<sipdomain\>_ entry to the subject alternative names list. 
    
18. On the **Configure Additional Subject Alternate Names** page, specify any additional subject alternative names that are required. 
    
    > [!TIP]
    > If the XMPP proxy is installed, by default the domain name (such as contoso.com) is populated in the SAN entries. If you require more entries, add them in this step. 
  
19. On the **Request Summary** page, review the certificate information to be used to generate the request. 
    
20. After the commands finish running, you can **View Log**, or click **Next** to continue. 
    
21. On the **Certificate Request File** page, you can view the generated certificate signing request (CSR) file by clicking **View** or exit the Certificate Wizard by clicking **Finish**.
    
22. Copy the request file and submit to your public certification authority.
    
23. After receiving, importing and assigning the public certificate, you must stop and restart the Edge Server services. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.. In the Lync Server Management Shell, type:
    
  ```
  Stop-CsWindowsService
  ```

  ```
  Start-CsWindowsService
  ```

24. To configure DNS for XMPP federation, you add the following SRV record to external DNS:_xmpp-server._tcp. _\<domain name\>_ The SRV record will resolve to the access edge FQDN of the Edge server, with a port value of 5269 
    
25. Configure a new External Access Policy to enable all users by opening the Lync Server Management Shell on a Front End Server and typing:
    
  ```
  New-CsExternalAccessPolicy -Identity FedPic -EnableFederationAccess $true -EnablePublicCloudAccess $true
  Get-CsUser | Grant-CsExternalAccessPolicy -PolicyName FedPic
  ```


