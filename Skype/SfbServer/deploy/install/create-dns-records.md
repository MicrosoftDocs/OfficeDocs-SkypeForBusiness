---
title: "Create DNS records for Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 2/15/2018
audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom: 
ms.assetid: 798a663c-0b63-4f75-b0a3-9c553cef8c5f
description: "Summary: Learn how to configure DNS and create DNS records for an installation of Skype for Business Server. Download a free trial of Skype for Business Server from the Microsoft Evaluation center at:  https://www.microsoft.com/evalcenter/evaluate-skype-for-business-server."
---

# Create DNS records for Skype for Business Server
 
**Summary:** Learn how to configure DNS and create DNS records for an installation of Skype for Business Server. Download a free trial of Skype for Business Server from the Microsoft Evaluation center at: [https://www.microsoft.com/evalcenter/evaluate-skype-for-business-server](https://www.microsoft.com/evalcenter/evaluate-skype-for-business-server).
  
For Skype for Business Server to work properly, a number of Domain Name System (DNS) settings must be in place. This is so that clients know how to access the services and that the servers know about each other. These settings need to be completed only once per deployment because once you assign a DNS entry, it is available throughout the domain. You can do steps 1 through 5 in any order. However, you must do steps 6, 7, and 8 in order, and after steps 1 through 5, as outlined in the diagram. Creating DNS records comprises step 5 of 8. For more information about planning DNS, see [Environmental requirements for Skype for Business Server](../../plan-your-deployment/requirements-for-your-environment/environmental-requirements.md) or [Server requirements for Skype for Business Server 2019](../../../SfBServer2019/plan/system-requirements.md).
  
> [!IMPORTANT]
> It is important to note that this is just an example of how to create DNS records in a Windows Server DNS environment. There are many other DNS entries that are required for Skype for Business Server, and the procedure for creating DNS records depends on the system you are using to manage DNS in your organization. For a complete list of requirements for DNS, see [DNS requirements for Skype for Business Server](../../plan-your-deployment/network-requirements/dns.md). 
  
![Overview diagram](../../media/d2fc733c-6a80-4d17-a02f-93b8c4bfb999.png)
  
## Configure DNS

DNS records are required for Skype for Business Server to work properly and be accessible by users.
  
This example is using a DNS load balanced FQDN named pool.contoso.local. This pool consists of three servers running Skype for Business Server Enterprise Edition. A Standard Edition front-end server can only contain a single server. By using Standard Edition, you would only use the fully qualified domain name (FQDN) of the single Standard Edition server when referencing the front-end role instead of creating a DNS load balanced pool of servers, as this example shows. This simple example that uses only the front-end role includes the DNS entries in the following table. To plan your specific DNS requirements, see [DNS requirements for Skype for Business Server](../../plan-your-deployment/network-requirements/dns.md). 
  
 
|**Description**|**Record type**|**Name**|**Resolves to**|**Load balancing type**|
|:-----|:-----|:-----|:-----|:-----|
|Internal Web Services FQDN  <br/> |A  <br/> |webint.contoso.local  <br/> |VIP for Internal Web Services  <br/> |Supported software and hardware  <br/> |
|Pool FQDN  <br/> |A  <br/> |pool.contoso.local  <br/> |IP address of server SFB01  <br/> |DNS  <br/> |
|SFB01 FQDN  <br/> |A  <br/> |SFB01.contoso.local  <br/> |IP address of server SFB01  <br/> |DNS  <br/> |
|Pool FQDN  <br/> |A  <br/> |pool.contoso.local  <br/> |IP address of server SFB02  <br/> |DNS  <br/> |
|SFB02 FQDN  <br/> |A  <br/> |SFB02.contoso.local  <br/> |IP address of server SFB02  <br/> |DNS  <br/> |
|Pool FQDN  <br/> |A  <br/> |pool.contoso.local  <br/> |IP address of server SFB03  <br/> |DNS  <br/> |
|SFB03 FQDN  <br/> |A  <br/> |SFB03.contoso.local  <br/> |IP address of server SFB03  <br/> |DNS  <br/> |
|Skype for Business Auto Discover  <br/> |A  <br/> |lyncdiscoverinternal.contoso.local  <br/> |VIP for Internal Web Services  <br/> |Supported software and hardware  <br/> |
|Meeting Simple URL  <br/> |A  <br/> |meet.contoso.local  <br/> |VIP for Internal Web Services  <br/> |Supported software and hardware  <br/> |
|Dial-in Simple URL  <br/> |A  <br/> |dialin.contoso.local  <br/> |VIP for Internal Web Services  <br/> |Supported software and hardware  <br/> |
|Web Scheduler Simple URL  <br/> |A  <br/> |scheduler.contoso.local  <br/> |VIP for Internal Web Services  <br/> |Supported software and hardware  <br/> |
|Administration Simple URL  <br/> |A  <br/> |admin.contoso.local  <br/> |VIP for Internal Web Services  <br/> |Supported software and hardware  <br/> |
|Legacy Discovery  <br/> |SRV  <br/> |_sipinternaltls._tcp.contoso.local  <br/> |Pool FQDN (port 5061)  <br/> |N/A  <br/> |
   
### Create DNS records

1. Log on to the DNS server, and open **Server Manager**.
    
2. Click the **Tools** drop-down menu, and click **DNS**.
    
3. In the console tree for your SIP domain, expand **Forward Lookup Zones**, and then expand the SIP domain in which Skype for Business Server will be installed.
    
4. Right-click the SIP domain, and select **New Host (A or AAAA)**, as shown in the figure.
    
     ![selecting new A record](../../media/f89c5c1f-b5b7-428c-a6e3-2bcd12e878c3.png)
  
5. In the **Name** box, type the name of the host record (the domain name will be automatically appended).
    
6. In the **IP Address box**, type the IP address of the individual front-end server, and then select **Create associated pointer (PTR) record** or **Allow any authenticated user to update DNS records with the same owner name**, if applicable. Note that this assumes that DNS is used to load balance all traffic with the exception of web services. In this example, we have three front-end servers as shown in the table.
    
   |**Server Name**|**Type**|**Data**|
   |:-----|:-----|:-----|
   |SFB01  <br/> |Host (A)  <br/> |10.0.0.5  <br/> |
   |SFB02  <br/> |Host (A)  <br/> |10.0.0.6  <br/> |
   |SFB03  <br/> |Host (A)  <br/> |10.0.0.7  <br/> |
   
7. Next, create the DNS load balancing entries for the pool. DNS load balancing allows DNS to send requests to the individual servers in the pool while using the same DNS pool name. For more information about DNS and load balancing, see [DNS requirements for Skype for Business Server](../../plan-your-deployment/network-requirements/dns.md). 
    
    > [!NOTE]
    > Pooling multiple servers together is available only in Enterprise Edition deployments. If you are deploying a single Enterprise Server or Standard Edition server, you need to create only an A record for the single server. 
  
    For example, if you had a pool named pool.contoso.local and three front-end servers, you would create the following DNS entries:
    
   |**FQDN**|**Type**|**Data**|
   |:-----|:-----|:-----|
   |pool.contoso.local  <br/> |Host (A)  <br/> |10.0.0.5  <br/> |
   |pool.contoso.local  <br/> |Host (A)  <br/> |10.0.0.6  <br/> |
   |pool.contoso.local  <br/> |Host (A)  <br/> |10.0.0.7  <br/> |
   
8. Continue creating A records for all servers in the planned deployment. 
    
9. To create the service record (SRV) record for legacy discovery, right-click the SIP domain, and select **Other New Records**.
    
10. In **Select a resource record type**, click **Service Location (SRV)**, and then click **Create Record**.
    
11. Click **Service**, and then type **_sipinternaltls**.
    
12. Click **Protocol**, and then type **_tcp**.
    
13. Click **Port Number**, and then type **5061**.
    
14. Click **Host offering this service**, and then type the FQDN of the pool or Standard Edition server.
    
     ![Screenshot of the new resource record dialog.](../../media/54b1aac5-a2ec-41fe-90c0-02eaeaa9d1b4.png)
  
15. Click **OK**, and then click **Done**.
    
### Verify DNS records

1. Log on to a client computer in the domain with an account that is a member of the Authenticated Users group or has equivalent permissions.
    
2. Click **Start**, and then type **cmd**, and press Enter.
    
3. Type **nslookup \<FQDN of the Front End pool\>** or **\<FQDN of the Standard Edition server or single Enterprise Edition server\>**, and press Enter.
    
4. Continue to verify the rest of the A records for your deployment.
    
5. If you are supporting legacy clients and created the SRV record, verify it by typing **set type=srv** at the **nslookup** prompt, and then press Enter.
    
6. Type **_sipinternaltls._tcp. *domain*** (for example, _sipinternaltls._tcp.contoso.local), and then press Enter.
    
7. The expected output should be similar to that shown in the figure. Note that not all DNS records are shown in the sample output, but all records should be verified. 
    
     ![Verify the dns settings.](../../media/4fcaa70f-7717-4939-9652-d2048d6293cc.png)
  

