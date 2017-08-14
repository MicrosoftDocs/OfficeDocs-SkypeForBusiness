---
title: Test-CsTrunkConfiguration
ms.prod: SKYPEFORBUSINESS
ms.assetid: 07f2ef04-49aa-4857-b213-fa98506c0427
---


# Test-CsTrunkConfiguration
[]
Validates a trunk configuration against a phone number. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Test-CsTrunkConfiguration -TrunkConfiguration <TrunkConfiguration> [-CallingNumber <PhoneNumber>] [-DialedNumber <PhoneNumber>]

```


## Examples


  
    
    

### EXAMPLE 1

This example runs a test against the trunk configuration defined for the Redmond site. The first line in this example calls the **Get-CsTrunkConfiguration** cmdlet to retrieve the configuration for the Redmond site (the configuration with the Identity site:Redmond). The trunk configuration object retrieved is assigned to the variable $tc.
  
    
    
In line 2 we call the **Test-CsTrunkConfiguration** cmdlet, passing the phone number to test to the DialedNumber parameter, and the trunk configuration we retrieved in line 1 (stored in $tc) to the TrunkConfiguration parameter.
  
    
    



```

$tc = Get-CsTrunkConfiguration -Identity Site:Redmond
Test-CsTrunkConfiguration -DialedNumber 4255551212 -TrunkConfiguration $tc
```


## Detailed Description

Use this cmdlet to verify that a trunking configuration performs as expected against a dialed phone number. Each configuration contains specific settings defining the relationship and capabilities between the Mediation Server and the public switched telephone network (PSTN) gateway, IP-public branch exchange (PBX), or Session Border Controller (SBC) at the service provider. These settings configure such things as whether media bypass is enabled on this trunk, whether real-time transport control protocol (RTCP) packets are sent under certain conditions, and whether to require secure real-time protocol (SRTP) encryption.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _TrunkConfiguration_ <br/> |Required  <br/> |Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.TrunkConfiguration  <br/> |A reference to a trunk configuration object against which to run the test. Trunk configuration objects can be retrieved by calling the **Get-CsTrunkConfiguration** cmdlet. <br/> |
| _CallingNumber_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Voice.PhoneNumber  <br/> |When specified, returns the matched outbound translation rules for the specified phone number. For example:  <br/>  `-CallingNumber "tel:+14255551219"` <br/> |
| _DialedNumber_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Voice.PhoneNumber  <br/> |The phone number against which to test the configuration.  <br/> |
   

## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.TrunkConfiguration object. Accepts pipelined input of a trunk configuration object.
  
    
    

## Return Types

Returns a value of type Microsoft.Rtc.Management.Voice.TrunkConfigurationTestResult.
  
    
    

## See also


#### 


  
    
    
 [New-CsTrunkConfiguration](new-cstrunkconfiguration.md)
  
    
    
 [Remove-CsTrunkConfiguration](remove-cstrunkconfiguration.md)
  
    
    
 [Set-CsTrunkConfiguration](set-cstrunkconfiguration.md)
  
    
    
 [Get-CsTrunkConfiguration](get-cstrunkconfiguration.md)
