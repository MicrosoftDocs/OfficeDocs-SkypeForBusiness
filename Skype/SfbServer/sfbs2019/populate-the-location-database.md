---
title: "Populate the location database in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: fb84f5b6-c991-4893-bdbf-f195b4b7d28e
description: "To automatically locate clients within a network, you first need to populate the location database with a network wiremap, which maps network elements to civic (that is, street) addresses. You can use subnets, wireless access points, switches, and ports to define the wiremap."
---

# Populate the location database in Lync Server 2013
[]
To automatically locate clients within a network, you first need to populate the location database with a network wiremap, which maps network elements to civic (that is, street) addresses. You can use subnets, wireless access points, switches, and ports to define the wiremap.
  
You can add addresses to the location database individually, or in bulk by using a CSV file that contains the column formats described in the following table.
  
If you use an Emergency Location Identification Number (ELIN) gateway, include the ELIN in the **CompanyName** field for each location. You can include multiple ELINs for each location, each separated by a semicolon. 
  
|**Network Element**|**Required Columns**|
|:-----|:-----|
|**Wireless access point** <br/> |\<BSSID\>,\<Description\>,\<Location\>,\<CompanyName\>,\<HouseNumber\>,\<HouseNumberSuffix\>,\<PreDirectional\>,…  <br/> …\<StreetName\>,\<StreetSuffix\>,\<PostDirectional\>,\<City\>,\<State\>,\<PostalCode\>,\<Country\>  <br/> |
|**Subnet** <br/> |\<Subnet\>,\<Description\>,\<Location\>,\<CompanyName\>,\<HouseNumber\>,\<HouseNumberSuffix\>,\<PreDirectional\>,…  <br/> …\<StreetName\>,\<StreetSuffix\>,\<PostDirectional\>,\<City\>,\<State\>,\<PostalCode\>,\<Country\>  <br/> |
|**Port** <br/> |\<ChassisID\>,\<PortIDSubType\>,\<PortID\>,\<Description\>,\<Location\>,\<CompanyName\>,\<HouseNumber\>,\<HouseNumberSuffix\>,…  <br/> …\<PreDirectional\>,\<StreetName\>,\<StreetSuffix\>,\<PostDirectional\>,\<City\>,\<State\>,\<PostalCode\>,\<Country\>  <br/> |
|**Switch** <br/> |\<ChassisID\>,\<Description\>,\<Location\>,\<CompanyName\>,\<HouseNumber\>,\<HouseNumberSuffix\>,\<PreDirectional\>,…  <br/> …\<StreetName\>,\<StreetSuffix\>,\<PostDirectional\>,\<City\>,\<State\>,\<PostalCode\>,\<Country\>  <br/> |
   
If you do not populate the location database, and the **Location Required** in the Location Policy is set to **Yes** or **Disclaimer**, the client will prompt the user to enter a location manually.
  
For details about populating the location database, see the Lync Server Management Shell documentation for the following cmdlets:
  
- **Get-CsLisSubnet**
    
- **Set-CsLisSubnet**
    
- Remove-CsLisSubnet
    
- **Get-CsLisWirelessAccessPoint**
    
- **Set-CsLisWirelessAccessPoint**
    
- **Remove-CsLisWirelessAccessPoint**
    
- **Get-CsLisSwitch**
    
- **Set-CsLisSwitch**
    
- **Remove-CsLisSwitch**
    
- **Get-CsLisPort**
    
- **Set-CsLisPort**
    
- **Remove-CsLisPort**
    
### To add network elements to the location database

1. Run the following cmdlet to add a subnet location to the location database.
    
  ```
  Set-CsLisSubnet -Subnet 157.56.66.0 -Description "Subnet 1" -Location Location1 -CompanyName "Litware" -HouseNumber 1234 -HouseNumberSuffix "" -PreDirectional "" -StreetName 163rd -StreetSuffix Ave -PostDirectional NE -City Redmond -State WA -PostalCode 99123 -Country US
  ```

    For ELIN gateways, put the ELIN in the CompanyName field. You can include more than one ELIN. For example:
    
  ```
  Set-CsLisSubnet -Subnet 157.56.66.0 -Description "Subnet 1" -Location Location1 -CompanyName 425-555-0100; 425-555-0200; 425-555-0300 -HouseNumber 1234 -HouseNumberSuffix "" -PreDirectional "" -StreetName 163rd -StreetSuffix Ave -PostDirectional NE -City Redmond -State WA -PostalCode 99123 -Country US
  ```

    Alternately, you can run the following cmdlets and use a file named "subnets.csv" to bulk update subnet locations.
    
  ```
  $g = Import-Csv subnets.csv
  $g | Set-CsLisSubnet
  
  ```

2. Run the following cmdlet to add wireless locations to the location database.
    
  ```
  Set-CsLisWirelessAccessPoint -BSSID 0A-23-CD-16-AA-2E -Description "Wireless1" -Location Location2 -CompanyName "Litware" -HouseNumber 2345 -HouseNumberSuffix "" -PreDirectional "" -StreetName 163rd -StreetSuffix Ave -PostDirectional NE -City Bellevue -State WA -PostalCode 99234 -Country US
  ```

    Alternately, you can run the following cmdlets and use a file named "waps.csv" to bulk update wireless locations.
    
  ```
  $g = Import-Csv waps.csv
  $g | Set-CsLisWirelessAccessPoint
  ```

3. Run the following cmdlet to add switch locations to the location database.
    
  ```
  Set-CsLisSwitch-ChassisID 0B-23-CD-16-AA-BB -Description "Switch1" -Location Location1 -CompanyName "Litware" -HouseNumber 1234 -HouseNumberSuffix "" -PreDirectional "" -StreetName 163rd -StreetSuffix Ave -PostDirectional NE -City Redmond -State WA -PostalCode 99123 -Country US
  ```

    Alternately, you can run the following cmdlets and use a file named "switches.csv" to bulk update switch locations.
    
  ```
  $g = Import-Csv switches.csv
  $g | Set-CsLisSwitch
  ```

4. Run the following cmdlet to add port locations to the location database
    
  ```
  Set-CsLisPort -ChassisID 0C-23-CD-16-AA-CC -PortID 0A-abcd -Description "Port1" -Location Location2 -CompanyName "Litware" -HouseNumber 2345 -HouseNumberSuffix "" -PreDirectional "" -StreetName 163rd -StreetSuffix Ave -PostDirectional NE -City Bellevue -State WA -PostalCode 99234 -Country US
  ```

    The default for PortIDSubType is LocallyAssigned. You can also set it to InterfaceAlias or InterfaceName
    
    Alternately, you can run the following cmdlets and use a file named "ports.csv" to bulk update port locations.
    
  ```
  $g = Import-Csv ports.csv
  $g | Set-CsLisPort
  ```


