---
title: "Associate a subnet with a network site in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: aa69e3ac-542a-4ba1-9582-2e6bee29f633
description: "Every subnet in your network must be associated with a specific network site, because subnet information is used to determine the network site on which an endpoint is located while a new session is initiated. When the location of each party in a session is known, advanced Enterprise Voice features can apply that information to determine how to handle the call setup or routing."
---

# Associate a subnet with a network site in Lync Server 2013
[]
Every subnet in your network must be associated with a specific network site, because subnet information is used to determine the network site on which an endpoint is located while a new session is initiated. When the location of each party in a session is known, advanced Enterprise Voice features can apply that information to determine how to handle the call setup or routing.
  
> [!IMPORTANT]
> All configured public IP addresses of the Audio/Video Edge Servers in your deployment must be added to your network configuration settings. These IP addresses are added as subnets with a mask of 32. The associated network site should correspond to the appropriate configured network site. For example, the public IP address that corresponds to the A/V Edge Server in central site Chicago would be NetworkSiteID Chicago. For details about public IP addresses, see [Determine external A/V firewall and port requirements for Lync Server 2013](determine-external-a-v-firewall-and-port-requirements.md) in the Planning documentation. 
  
> [!NOTE]
>  A Key Health Indicator (KHI) alert is raised, specifying a list of IP addresses that are present in your network but are either not associated with a subnet, or the subnet that includes the IP addresses is not associated with a network site. This alert will not be raised more than once within an 8-hour period. The relevant alert information and an example are as follows: > **Source**: CS Bandwidth Policy Service (Core) > **Event number**: 36034 > **Level**: 2 > **Description**: The subnets for the following IP addresses: \<List of IP Addresses\> are either not configured or the subnets are not associated to a Network Site. > **Cause**: The subnets for the corresponding IP addresses are missing from the network configuration settings or the subnets are not associated to a network site. > **Resolution**: Add subnets corresponding to the list of IP addresses into the network configuration settings and associate every subnet to a network site. >  For example, if the IP address list in the alert specifies 10.121.248.226 and 10.121.249.20, either these IP addresses are not associated with a subnet or the subnet they are associated with does not belong to a network site. If 10.121.248.0/24 and 10.121.249.0/24 are the corresponding subnets for these addresses, you can resolve this issue as follows: >  Be sure that IP address 10.121.248.226 is associated with the 10.121.248.0/24 subnet and IP address 10.121.249.20 is associated with the 10.121.249.0/24 subnet. >  Be sure that the 10.121.248.0/24 and 10.121.249.0/24 subnets are each associated with a network site. 
  
For details about working with network subnets, see the Lync Server Management Shell documentation for the following cmdlets:
  
- [New-CsNetworkSubnet](new-csnetworksubnet.md)
    
- [Get-CsNetworkSubnet](get-csnetworksubnet.md)
    
- [Set-CsNetworkSubnet](set-csnetworksubnet.md)
    
- [Remove-CsNetworkSubnet](remove-csnetworksubnet.md)
    
> [!TIP]
> If you are working with a large number of subnets, we recommend using a comma-separated values (CSV) file to associate the subnets to sites. The CSV file must have the following four columns: **IPAddress**, **mask**, **description**, **NetworkSiteID**. 
  
### To associate a subnet with a network site by using Management Shell

1. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
2. Run the **New-CsNetworkSubnet** cmdlet to associate a subnet with a network site: 
    
  ```
  New-CsNetworkSubnet -SubnetID <String> -MaskBits <Int32> -NetworkSiteID <String>
  ```

    For example:
    
  ```
  New-CsNetworkSubnet -SubnetID 172.11.12.13 - MaskBits 20 -NetworkSiteID Chicago
  ```

    In this example, you created an association between the subnet 172.11.12.13 and the network site "Chicago".
    
3. Repeat step 2 for all subnets in your topology.
    
### To associate subnets with network sites by importing a CSV file

1. Create a CSV file that includes all of the subnets you want to add. For example, create a file named **subnet.csv** with the following content: 
    
     `IPAddress, mask, description, NetworkSiteID`
    
     `172.11.12.0, 24, "NA:Subnet in Portland", Portland`
    
     `172.11.13.0, 24, "NA:Subnet in Reno", Reno`
    
     `172.11.14.0, 25, "EMEA:Subnet in Warsaw", Warsaw`
    
     `172.11.15.0, 31, "EMEA:Subnet in Paris", Paris`
    
2. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
3. Run the following cmdlet to import **subnet.csv**, and then store its contents in the Lync Server management store:
    
  ```
  import-csv subnet.csv | foreach {New-CsNetworkSubnet $_IPAddress -MaskBits $_.mask -Description $_.description -NetworkSiteID $_.NetworkSiteID}
  ```

### To associate a subnet with a network site by using Lync Server Control Panel

1.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
2. In the left navigation bar, click **Network Configuration**.
    
3. Click the **Subnet** navigation button. 
    
4. Click **New**.
    
5. On the **New Subnet** page, click **Subnet ID**, and then type the first address in the IP address range defined by the subnet you want to associate with a network site.
    
6. Click **Mask**, and then type the bitmask to apply to the subnet.
    
7. Click **Network site ID**, and then select the site ID of the site to which you are adding this subnet.
    
    > [!NOTE]
    > If you have not yet created network sites, this list will be empty. For details about the procedure, see [Create or modify a network site in Lync Server 2013](create-or-modify-a-network-site.md). You can also retrieve site IDs for your deployment by running the **Get-CsNetworkSite** cmdlet. For details, see the Lync Server Management Shell documentation. 
  
8. Optionally, click **Description**, and then type additional information to describe this subnet.
    
9. Click **Commit**.
    
Repeat these steps to add other subnets to a network site.

