---
title: "(Optional) Verify dial-in conferencing in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3e2b4220-8fb3-442f-98b1-78447adb321f
description: "To verify that the Dial-in Conferencing Settings webpage and the dial-in access numbers work correctly, you need to do the following:"
---

# (Optional) Verify dial-in conferencing in Lync Server 2013
[]
To verify that the Dial-in Conferencing Settings webpage and the dial-in access numbers work correctly, you need to do the following:
  
- Test the Dial-in Conferencing Settings webpage by signing in to the simple URL.
    
- Test that access numbers work correctly for a specific pool by running the script later in this topic. This script simulates calls to access numbers. You need the SIP address and credentials of one unified communications (UC) client that is hosted on the specific pool to use this script.
    
This step is optional.
  
### To test access numbers for a specific pool

1. Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the **Cs-ServerAdministrator** or **CsAdministrator** role. 
    
2. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
3. Run the following at the command prompt:
    
  ```
  $credentials = Get-Credential
     User name:  testuser1@contoso.com
     Password:  ********
  Test-CsDialInConferencing -UserSipAddress sip:testuser1@contoso.com -UserCredential $credentials -TargetFqdn <serverName>.<domainName>.com -Verbose
  
  ```

    The resulting report shows either Success or Failure, along with specific diagnostic information. The -Verbose flag provides more detailed information about how many access numbers were found and details about them.
    

