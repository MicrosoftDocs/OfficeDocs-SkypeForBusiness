---
title: PSTN calling known issues
ms.prod: SKYPEFORBUSINESS
ms.assetid: baa3645a-0518-472e-942e-971c63ba4ca0
---



# PSTN calling known issues

PSTN calling is a new feature found in Skype for Business Online. There are current issues that are being tracked, actively investigated and will be potentially resolved when the feature is updated in future builds in Office 365 and Skype for Business Online and are listed below.
  
    
    


## PSTN calling known issues



|**Known issue**|**Comments**|
|:-----|:-----|
|Transitioning from Tech Preview licenses to production licenses for PSTN calling doesn't automatically update the license.  <br/> |Purchase your new licenses first so they are ready to be assigned to your users. Remove the promo (Tech Preview) license from a user and then **IMMEDIATELY** assign the new Skype for Business Cloud PBX and Skype for Business PSTN Domestic Calling or PSTN Domestic and International Calling license to the user. <br/> If you are removing and adding licenses for multiple users, it is extremely important that you remove the licenses from all of the users using Windows PowerShell and then **IMMEDIATELY** assign the licenses for all of the users also using Windows PowerShell. Doing this will ensure there is no disruption service when handling large volumes of user license assignments. For sample PowerShell scripts, see [Assign Skype for Business licenses](assign-skype-for-business-licenses.md).  <br/> > [!CAUTION]> If you are using on-premises PSTN connectivity for hybrid users, you  *only*  need to assign a Skype for Business Cloud PBX license. You should **NOT** also assign a voice calling plan.> However, if you are enabling PSTN calling for users that are in Office 365, you need to still assign a voice calling plan license for those users. See  [Assign Skype for Business licenses](assign-skype-for-business-licenses.md).           |
   

  
    
    

## See also


#### Other Resources


  
    
    
 [Emergency calling terms and conditions](emergency-calling-terms-and-conditions.md)
  
    
    
 [Skype for Business Online PSTN services use terms](skype-for-business-online-pstn-services-use-terms.md)
