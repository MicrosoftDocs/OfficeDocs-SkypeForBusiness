---
title: "Test dial-in conferencing in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: f4ccbfd4-6075-466f-b459-20561318803d
description: "Summary: Learn how to test dial-in conferencing in Skype for Business Server."
---

# Test dial-in conferencing in Skype for Business Server
 
**Summary:** Learn how to test dial-in conferencing in Skype for Business Server.
  
As final verification of your dial-in conferencing configuration, you can search for dial plans that have a dial-in conferencing region that is not used by any access number and for access numbers that have not specified a dial-in conferencing region. You should also verify that the Dial-in Conferencing Settings webpage and the dial-in access numbers work correctly.
  
## Find dial plans with a dial-in conferencing region that is not used by an access number

1. Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the Cs-ServerAdministrator or CsAdministrator role.
    
2. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.
    
3. Run the following at the command prompt:
    
   ```
   Get-CsDialinConferencingAccessNumber -EmptyRegion
   ```

    This cmdlet returns all of the dial plans that have a dial-in conferencing region that is not used by an access number.
    
For more information, see [Get-CsDialInConferencingAccessNumber](https://docs.microsoft.com/powershell/module/skype/get-csdialinconferencingaccessnumber?view=skype-ps).
  
## Find access numbers without assigned regions

1. Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the Cs-ServerAdministrator or CsAdministrator role.
    
2. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.
    
3. Run the following at the command prompt:
    
   ```
   Get-CsDialinConferencingAccessNumber -Region NULL
   ```

    This cmdlet returns all the dial-in conferencing access numbers that are not associated with a region.
    
For more information, see [Get-CsDialInConferencingAccessNumber](https://docs.microsoft.com/powershell/module/skype/get-csdialinconferencingaccessnumber?view=skype-ps).
  
## Test webpage and access numbers

To verify that the Dial-in Conferencing Settings webpage and the dial-in access numbers work correctly, you need to do the following:
  
- Test the Dial-in Conferencing Settings webpage by signing in to the simple URL.
    
- Test that access numbers work correctly for a specific pool by running the script later in this topic. This script simulates calls to access numbers. You need the SIP address and credentials of one unified communications (UC) client that is hosted on the specific pool to use this script.
    
### To test access numbers for a specific pool

1. Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the Cs-ServerAdministrator or CsAdministrator role.
    
2. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.
    
3. Run the following at the command prompt:
    
   ```
   $credentials = Get-Credential
   User name:  testuser1@contoso.com
   Password:  ********
   Test-CsDialInConferencing -UserSipAddress sip:testuser1@contoso.com -UserCredential $credentials -TargetFqdn <serverName>.<domainName>.com -Verbose
   ```

    The resulting report shows either Success or Failure, along with specific diagnostic information. The -Verbose flag provides more detailed information about how many access numbers were found and details about them.
    
For more information, see [Test-CsDialInConferencing](https://docs.microsoft.com/powershell/module/skype/test-csdialinconferencing?view=skype-ps).
  

