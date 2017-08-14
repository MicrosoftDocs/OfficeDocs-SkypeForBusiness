---
title: Configure a secondary Location Information service in Skype for Business Server 2015
ms.prod: SKYPEFORBUSINESS
ms.assetid: 083ffbc6-7c18-4141-85f9-8825b62c3d10
---


# Configure a secondary Location Information service in Skype for Business Server 2015
[]Configure a secondary location source (SLS) database for E9-1-1 in Skype for Business Server Enterprise Voice. 
Skype for Business Server provides a web service interface that you can use to point the Location Information service to a Secondary Location Source (SLS) database. The web service interface that connects to the SLS database must conform to Location Information service WSDL. If both a location database and secondary location database are configured, the Location Information service first queries the location database, and if no match is found, sends the location request from the client to the SLS database. If the location exists in the SLS, the Location Information service then sends the location back to the client. 
  
    
    


### To configure a Secondary Location database


1. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.
    
  
2. Run the following cmdlet to configure the URL for the location of the secondary location database. 
    
  ```
  
Set-CsWebServiceConfiguration -SecondaryLocationSourceURL "<web service url>" 
  ```


## See also


#### 


  
    
    
 [Set-CsWebServiceConfiguration](set-cswebserviceconfiguration.md)
