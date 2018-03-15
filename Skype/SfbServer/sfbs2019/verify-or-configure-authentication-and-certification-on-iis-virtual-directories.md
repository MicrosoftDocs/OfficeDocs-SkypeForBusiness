---
title: "Verify or configure authentication and certification on IIS virtual directories in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3ca90be0-1d64-447c-807a-3a2ee3bf625e
description: "Use the following procedure to configure the certificate on your Internet Information Services (IIS) virtual directories or verify that the certificate is configured correctly. Perform the following procedure on each server running IIS in your internal Lync Server pool and the optional Director.or Director pool servers."
---

# Verify or configure authentication and certification on IIS virtual directories in Lync Server 2013
[]
Use the following procedure to configure the certificate on your Internet Information Services (IIS) virtual directories or verify that the certificate is configured correctly. Perform the following procedure on each server running IIS in your internal Lync Server pool and the optional Director.or Director pool servers.
  
> [!NOTE]
> The following procedure defines a procedure to request a combined certificate that is used for all purposes Lync Server, Internal Web Site and External Web Site in IIS. Lync Server 2010 introduced a set of Lync Server Management Shell Windows PowerShell cmdlets for the express purpose of managing certificate request, import, and assignment. The procedure assumes that there is an internally deployed certification authority (CA) that can process the request. If you use public certificates for your Lync Server purposes, or your CA requires an offline request, see the detailed syntax in this topic for information on the -Output parameter. [Request-CsCertificate](request-cscertificate.md)
  
### To configure authentication and certificates on IIS virtual directories

1. To successfully complete the following, you must be logged on to the computer (Front End Server or Director) where the web services are installed and be a local administrator. You must have the **read** and **enroll** permissions on the certification authority that you will be requesting certificates from, if the certification authority is your organization's certification authority. You do not need permissions to the certification authority if you will configure and send an offline certificate request. 
    
2. Click **Start**, select **All Programs**, select **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.
    
3. In **Internet Information Services (IIS) Manager**, select **ServerName**. In **Features View**, select **Server Certificates**, right-click and select **Open Feature**.
    
    > [!TIP]
    > In the Server Certificates Feature View, if there are certificates assigned to the server, they will appear here. If there is a certificate that matches the requirements for the External Web Site in IIS, you can re-use that certificate. To view a certificate, right-click the certificate and select **View…**
  
4. On the Front End Server or Director that you are requesting the certificate for, click **Start**, select **All Programs**, select **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
5. In the Lync Server Management Shell, type the following:
    
  ```
  Get-CsCertificate
  
  ```

    The output is a list of the certificates that are currently on the server in the Computer Personal certificate store. Note that in the combined certificate (that is, where the default, web services internal and web services external are using the same certificate) you will see that the Use property will be populated with Default, WebServicesInternal and WebServicesExternal. Also, the Thumbprint property will be the same for each of the Use types. An example output of Get-CsCertificate is shown in this example: 
    
    ![Get-CsCertificate info on current scert status](media/IIS_Certificate_Config_Initial_PS_Out.jpg)
  
6. In the Lync Server Management Shell, type the following:
    
  ```
  Request-CsCertificate -New -Type Default,WebServicesInternal,WebServicesExternal -CA <CA Server FQDN\CA Instance> -Verbose -DomainName "<FQDN entries to be added to the Subject Alternative Name>"
  
  ```

    Where the full command would appear like following example:
    
  ```
  Request-CsCertificate -New -Type Default,WebServicesInternal,WebServicesExternal -CA dc01.contoso.net\contoso-DC01-CA -Verbose -DomainName "LyncdiscoverInternal.Contoso.com,Lyncdiscover.Contoso.com"
  
  ```

    > [!TIP]
    > By default, Request-CsCertificate will populate the subject name with the server or pool name and populate entries in the subject alternative name with the server FQDN, pool FQDN, Simple URL FQDNs, and internal and external web services FQDNs. It does this by referencing to the topology document in your deployment. If there is a missing value and you have specified the -Verbose parameter, you will be notified that the computed and actual values for alternative names are different, but it does not inform you which values are missing. It does supply you with the entire computed value that the cmdlet references. Use the computed alternative names string in the output to re-request a new certificate that will include all values. 
  
    ![Output from cert request using Request-CsCertifica](media/IIS_Certificate_Config_Request_PS_Out.jpg)
  
7. In the Lync Server Management Shell, type the following:
    
  ```
  Set-CsCertificate -Type Default,WebServicesInternal,WebServicesExternal -Thumbprint <Thumbprint of certificate to use>
  
  ```

    Where the full command would appear like following example:
    
  ```
  Set-CsCertificate -Type Default,WebServicesInternal,WebServicesExternal -Thumbprint 466D9BB0E8B928B65AF38FA2D9F41E1B301ECE9D
  
  ```

    The output from the Set-CsCertificate cmdlet will show that the same certificate (identified by the thumbprint of the certificate) is assigned for the Default, WebServicesExternal and WebServicesInternal usage.
    
    ![Output from Set-CsCertificate on IIS WebExt](media/IIS_Certificate_Config_Set_PS_Out.jpg)
  
### To verify or configure authentication and certificates on IIS virtual directories

1. Click **Start**, select **All Programs**, select **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.
    
2. In **Internet Information Services (IIS) Manager**, expand **ServerName**, and then expand ** Sites **.
    
3. Right-click **Lync Server External Web Site**, and then click **Edit Bindings**
    
4. Verify that https is associated with port 4443, and then click **https**.
    
5. Select the HTTPS entry, click **Edit**, and then verify that Lync Server WebServicesExternalCertificate is bound to this protocol. Compare the thumbprint from the Set-CsCertificate cmdlet to ensure that the expected certificate is correctly associated with the HTTPS binding.
    
## See also

#### 

[Get-CsCertificate](get-cscertificate.md)
  
[Set-CsCertificate](set-cscertificate.md)

