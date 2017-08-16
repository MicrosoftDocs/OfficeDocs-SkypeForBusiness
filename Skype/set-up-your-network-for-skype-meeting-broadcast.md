---
title: Set up your network for Skype Meeting Broadcast
ms.prod: OFFICE365
ms.assetid: dfa736b9-4920-4f48-b8c0-b5487ec6086f
---


# Set up your network for Skype Meeting Broadcast

After you  [Enable Skype Meeting Broadcast](enable-skype-meeting-broadcast.md) Skype Meeting Broadcast, you need to configure your network. Do this step if you want to hold webinars and other broadcasts for people outside of your business.
  
    
    

If you aren't experienced with configuring your firewall, consider hiring a  [Microsoft partner](https://go.microsoft.com/fwlink/?linkid=391089) to do this step for you.
To skip this step and instead add another business to your federation so you can invite them to broadcasts, follow the steps in  [Allow users to contact external Skype for Business users](allow-users-to-contact-external-skype-for-business-users.md). 
  
    
    


## Step 1: Set up allowed domains

Use one of the following methods to set up allowed domains: 
  
    
    

### Method 1: Use the Office 365 admin center


1. Go to the **Office 365 admin center** and then in the left nav, click **Settings** > **Services &amp; add-ins** then **Skype for Business**.
    
  
2.  On the **External sharing** page under **Domain exceptions**, click **All domains are blocked except**, enter the following domains but separate them with a comma (,):
    
  - noammeetings.lync.com
    
  
  - emeameetings.lync.com
    
  
  - apacmeetings.lync.com
    
  
  - resources.lync.com
    
  
3. Click **Save**.
    
  

### Method 2: Use Windows PowerShell


- From the **Start Menu** > **Windows PowerShell** > right click and ** Run as administrator**. In the **Windows PowerShell** window, type each line and press Enter.
    
    
    


  ```
  
$r = New-CsEdgeDomainPattern -Domain "noammeetings.lync.com"
  ```


    
    


  ```
  $s = New-CsEdgeDomainPattern -Domain "emeameetings.lync.com"
  ```


    
    


  ```
  $t = New-CsEdgeDomainPattern -Domain "apacmeetings.lync.com"
  ```


    
    


  ```
  $n = New-CsEdgeDomainPattern -Domain "resources.lync.com"
  ```


    
    


  ```
  $newAllowList = New-CsEdgeAllowList -AllowedDomain $r,$s,$t,$n
  ```


    
    


  ```
  Set-CsTenantFederationConfiguration -AllowedDomains $newAllowList
  ```


## Step 2: Add Skype Meeting Broadcast domains, URLs and IP addresses

The second step in the setup process is for you to first add domains that are needed and then add IP addresses and URLs that are required for Skype Meeting Broadcast to work.
  
    
    

- **Add the required domain endpoints:**
    
    To use Skype Meeting Broadcast, the following endpoints need to be accessible to client computers.
    
|
|
|**Row**|**Purpose**|**Source |Credentials**|**Destination**|**CDN**|**ExpressRoute for Office 365**|**Destination IP**|**Destination Port**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|1  <br/> |**Required:** Skype for Business endpoints. <br/> |See  [Skype for Business Online](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO) and ensure all entries labeled "required" are accessible. <br/> |||
|2  <br/> |**Required:** [Skype Meeting Broadcast](https://support.office.com/article/What-is-a-Skype-Meeting-Broadcast-c472c76b-21f1-4e4b-ab58-329a6c33757d) presenter and attendee <br/> |Client computer / logged on user  <br/> |broadcast.skype.com  <br/> *.broadcast.skype.com1 <br/> browser.pipe.aria.microsoft.com  <br/> |No  <br/> |Yes  <br/> | [](8548a211-3fe7-47cb-abb1-355ea5aa88a2.md#BKMK_SfB_IP).  <br/> |TCP 443  <br/> |
|aka.ms  <br/> amp.azure.net  <br/> |No  <br/> |No  <br/> |N/A  <br/> |TCP 443  <br/> |
|3  <br/> |**Required:** [Skype Meeting Broadcast](https://support.office.com/article/What-is-a-Skype-Meeting-Broadcast-c472c76b-21f1-4e4b-ab58-329a6c33757d) presenter and attendee <br/> |Client computer / logged on user  <br/> |mlccdn.blob.core.windows.net  <br/> ajax.aspnetcdn.com  <br/> *.msecnd.net2 <br/> *.streaming.mediaservices.windows.net3 <br/> *.keydelivery.mediaservices.windows.net3 <br/> |Yes  <br/> |No  <br/> |N/A  <br/> |TCP 443  <br/> |
   

    1 The wildcard for lync.com and broadcast.skype.com represents a long list of nodes that are exclusively used for Office 365.
    
    2 The wildcard for msecnd.net represents a dynamically generated endpoint within the CDN that join page libraries are pulled from.
    
    3 The wildcards for mediaservices.windows.net represents a list of media services endpoints associated with Azure Media Services where video content is pulled from. These endpoints are available via the internet and Azure Public peering.
    
  
- **Add the required Skype for Business Online endpoint URLs and IP addresses by seeing which ones are required** [here](https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US#bkmk_lyo).
    
  

## Set up Skype Meeting Broadcast in Hybrid deployments and organizations

If you have a Skype for Business Online organization and an on-premises deployments of Lync Server 2010, Microsoft Lync Server 2013, and Skype for Business Server 2015 and have users both online and on-premises, there are other set up steps that you will need to do in addition to the ones above to enable your on-premises organization to communicate with Skype for Business Online and allow all of your users to be able to create and join a Skype Meeting Broadcast. To see what those requirements are, see  [Configure your on-premises deployment for Skype Meeting Broadcast](https://go.microsoft.com/fwlink/?LinkId=617070).
  
    
    

## See also


#### Other Resources


  
    
    
 [Enable Skype Meeting Broadcast](enable-skype-meeting-broadcast.md)
  
    
    
 [Office 365 URLs and IP address ranges](http://technet.microsoft.com/library/8548a211-3fe7-47cb-abb1-355ea5aa88a2%28Office.14%29.aspx)
  
    
    
 [Set up Skype for Business Online](set-up-skype-for-business-online.md)
