---
title: Deploy Cloud PBX with on-premises PSTN connectivity in Skype for Business Server 2015 or Lync Server 2013
ms.prod: SKYPEFORBUSINESS
ms.assetid: 3cc3db88-0210-4804-b54e-ba4af1234884
---


# Deploy Cloud PBX with on-premises PSTN connectivity in Skype for Business Server 2015 or Lync Server 2013
[]
The following topics should be used to deploy Cloud PBX with on-premises PSTN connectivity. To learn about planning your deployment, see  [Plan Cloud PBX with on-premises PSTN connectivity in Skype for Business Server 2015 or Lync Server 2013](plan-cloud-pbx-with-on-premises-pstn-connectivity-in-skype-for-business-server-2.md).
  
    
    


## Moving users to Cloud PBX with on-premises PSTN connectivity

Before moving your users to Skype for Business Online it is recommended that you enable your users on-premises in Skype for Business Server or Lync Server 2013 and then move them online. If users are already in Skype for Business Online then you do not need to move them back, see the special considerations section of  [Enable the users for Enterprise Voice on-premises](enable-the-users-for-enterprise-voice-on-premises.md). To learn more about Cloud PBX including licensing and plans, see  [PSTN Calling plans for Skype for Business](https://support.office.com/article/PSTN-Calling-plans-for-Skype-for-Business-f47c6a97-bc8b-42e6-b5d4-ce6b41ed1918).
  
    
    
All users have to be created in Active Directory on-premises and synchronized to Office 365 using the supported version of Azure AD Connector. You cannot enable users for Cloud PBX that were created directly in Azure AD. If you want to enable Cloud PBX with on-premises PSTN connectivity for a user who was created in Azure AD, you'll need to create a new account for that user in your on-premises AD, configure the account on-premises, and then synchronize the account using a supported version of Azure AD Connector tool. See also,  [https://technet.microsoft.com/library/mt455217.aspx](https://technet.microsoft.com/library/mt455217.aspx).
  
    
    
Enabling a user for Cloud PBX with on-premises PSTN connectivity and then moving them to Skype for Business Online requires the following steps:
  
    
    

-  [Enable the users for Enterprise Voice on-premises](enable-the-users-for-enterprise-voice-on-premises.md) (performed while the users are homed on-premises).
    
  
-  [Assign a Voice Routing Policy](assign-a-voice-routing-policy.md) (performed while the users are homed on-premises).
    
  
-  [Synchronize users to the cloud and assign licenses](synchronize-users-to-the-cloud-and-assign-licenses.md) (performed using Office 365).
    
  
-  [Move Cloud PBX users to Skype for Business Online](move-cloud-pbx-users-to-skype-for-business-online.md) (performed using Windows PowerShell on-premises, but using your Office 365 administrator credentials).
    
  
-  [Enable users for Enterprise Voice online and Cloud PBX Voicemail](enable-users-for-enterprise-voice-online-and-cloud-pbx-voicemail.md) (performed using Remote PowerShell).
    
  

