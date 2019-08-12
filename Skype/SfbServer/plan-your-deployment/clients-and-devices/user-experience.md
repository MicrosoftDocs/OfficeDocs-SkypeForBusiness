---
title: "Plan the Skype for Business 2015 client experience for your users"
ms.author: v-lanac
author: lanachin
ms.reviewer: PhillipGarding
manager: serdars
ms.date: 12/20/2018
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom: 
ms.assetid: 0df4fd9e-370b-4b9d-a595-f1199fbc9f81
description: "Summary: Learn about the new Skype for Business and the steps you can take to prepare your environment and your users for the update, whether you're using Skype for Business Online, Skype for Business Server 2019, Skype for Business Server 2015, Lync Server 2013, or Lync Server 2010."
---

# Plan the Skype for Business 2015 client experience for your users
 
**Summary:** Learn about the new Skype for Business and the steps you can take to prepare your environment and your users for the update, whether you're using Skype for Business Online, Skype for Business Server 2019, Skype for Business Server 2015, Lync Server 2013, or Lync Server 2010.
  
The April 14th, 2015 Office Update for Lync 2013 includes the new Skype for Business user interface. This update enables administrators to control the look and feel of the client and choose whether to retain the Lync 2013 client experience or use the improved Skype for Business client experience. The Skype for Business client effectively replaced the Lync 2013 client, and added the ability for administrators to choose between the existing Lync client experience and the new Skype for Business client experience. For information about this update, see [April 14, 2015 update for Lync 2013 (Skype for Business) (KB2889923)](https://support.microsoft.com/en-us/kb/2889923/).
  
On May 12th, 2015 there will be another monthly update from Office that includes the updated Skype for Business client. Many customers that did not apply the April update will pick up the May 12th update for Office 2013. The information in this topic will help you prepare your organization, your environment, and your users for the client update. To make the transition easy for your users and support teams, use the information in this topic to help you decide which client experience you want for your users and then make the changes to your environment before deploying the client update in your organization.
  
- [What client experience do you want for your users?](user-experience.md#clientexperience)
    
- [Prepare your environment for the Skype for Business client](user-experience.md#usinglync)
    
- [Resources to help you prepare your support teams and your end users for the update](user-experience.md#support)
    
> [!NOTE]
> The Lync 2013 client experience is not an option for Skype for Business 2016 client versions. Before you attempt to configure your client environment to use the Lync 2013 client, please check the client version to ensure it does not start with the number 16; for example: 16.x.x.x. 
  
## What client experience do you want for your users?
<a name="clientexperience"> </a>

With the new Skype for Business client, you can control which client experience your users get, either Lync or Skype for Business. The default client experience depends on whether you are using Lync or Skype for Business on-premises or online. If you are using Skype for Business Online (Lync Online) today with Office 365 ProPlus, Office 365 Business Premium or Office 2013, the updated Skype for Business client experience—inspired by the look and feel of Skype—will be the default user experience. If you are using Lync Server on-premises today, the Lync client experience will be the default.
  
You can configure which client experience your users get by using client policies. A client policy is a set of configuration settings that are applied to users when they login to Lync or Skype for Business.
  
### Skype for Business client experience

In addition to all the features of Lync, Skype for Business provides new features with simplified controls and familiar icons from Skype. Some new features in Skype for Business are available only with the new Skype for Business client experience. To learn more about the new features in Skype for Business, see [Discover Skype for Business](https://go.microsoft.com/fwlink/p/?LinkId=528686).
  
### Lync client experience

The Lync client experience is very similar to the Lync 2013 client experience that your users are already familiar with, but there are a few changes that you'll want to let your users know about. To see what's different between the Lync client experience and the Lync 2013 client, see [Why do I see Skype for Business when I'm using Lync?](https://go.microsoft.com/fwlink/p/?LinkId=544712) and the additional links later in this topic.
  
## Prepare your environment for the Skype for Business client
<a name="usinglync"> </a>

There are a few things you'll need to do to get your environment ready for the client update. Before you start making any changes to configure the client experience, you first need to make sure that you are using a version of Skype for Business Server or Lync Server that supports the client policy settings.
  
Once you've confirmed that you're using a version of Skype for Business Server or Lync Server that supports the policy settings to control the client experience, you'll need to configure the policy settings in your environment. The specific steps you need to follow depend on the version of Skype for Business Server or Lync Server that you are using, and whether your users are on-premises or online. 
  
You'll want to make these changes before the client update is delivered to your users so that you can control the client experience from the first time they start the Skype for Business client. The following tables points you to the steps you need to take to configure your environment for the desired client experience for your users.
  
|**Deployment**|**Skype for Business client experience**|**Lync client experience**|
|:-----|:-----|:-----|
|Skype for Business Online  <br/> |There are no additional steps other than to deploy client build 4711.1002 (April, 2015) or later.  <br/> |[Use the Lync client experience with Skype for Business Online](user-experience.md#LyncwithSfBO) <br/> |
|Skype for Business Server 2015  <br/> |There are no additional steps other than to deploy client build 4711.1002 (April, 2015) or later.  <br/> |[Use the Lync client experience with Skype for Business Server on-premises](user-experience.md#LyncwithSfBServer) <br/> |
|Lync Server 2013 and Lync Server 2010  <br/> |[Use the Skype client experience with Lync Server 2013 or Lync Server 2010 on-premises](user-experience.md#SkypewithLynconprem) <br/> |[Use the Lync client experience with Lync Server 2013 or Lync Server 2010 on-premises](user-experience.md#LyncwithLynconprem) <br/> |
   
## Use the Skype client experience with Lync Server 2013 or Lync Server 2010 on-premises
<a name="SkypewithLynconprem"> </a>

Follow the steps in this section if you want to configure the Skype client experience in an on-premises deployment. The default experience for on-premises
  
 **Step 1:** First, make sure you are running a version of Lync Server that supports the client policy settings.
  
- **Lync Server 2013** - You must be running the December 2014 Cumulative Update (5.0.8308.857) for Lync Server 2013 or a later update. For information, see [Updates for Lync Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=532772).
    
- **Lync Server 2010** - You must be running the February 2015 Cumulative Update (4.0.7577.710) for Lync Server 2010 or a later update. For information, see [Updates for Lync Server 2010](https://go.microsoft.com/fwlink/p/?LinkId=532771).
    
  **Step 2:** Next, use a client policy to set the Skype client experience with the Skype for Business client. There are **3 options** for using a client policy to set the client experience.
  
  **Option 1:** Set the Skype client experience by using a Global policy. Note that the Global policy applies to all of the users in your deployment, but user and site level policies take precedence over the Global policy:
  
```
Set-CsClientPolicy -Identity Global -EnableSkypeUI $True
```

 **Option 2:** Modify an existing client policy that you are using in your environment to include the setting to enable the Skype client experience. This lets you assign the Skype client experience only to those users that have the existing policy assigned:
  
```
Set-CsClientPolicy -Identity ExistingClientPolicyName -EnableSkypeUI $True
```

 **Option 3:** Create a new policy to assign to users that includes the setting for the Skype client experience. First, create the new client policy and provide the name of the policy as the value of the **Identity** parameter:
  
```
New-CsClientPolicy -Identity UseSkypeUI -EnableSkypeUI $True
```

Then assign the policy to users, using the name of the policy (the value you used for the **Identity** parameter) as the value of the **PolicyName** parameter:
  
```
Grant-CsClientPolicy username@contoso.com -PolicyName UseSkypeUI
```

 **Step 3:** After you've configured your client policies, deploy the Skype for Business client, build 4711.1002 (April, 2015) or later.
  
## Use the Lync client experience with Lync Server 2013 or Lync Server 2010 on-premises
<a name="LyncwithLynconprem"> </a>

This is the default experience when the Skype for Business client is deployed in an on-premises Lync Server deployment. You don't need to configure any client policies to use the Lync client experience, but you may want to control the first run behavior for the client. By default, the first time users start the Skype for Business client, the Skype client experience is used and a notification is displayed to users that requests that they restart the client to get the Lync client experience. You can configure your environment so that the Lync client experience is displayed the first time users start the client, as well as turn off the client tutorial by modifying the system registry on client computers. For the steps you need to perform before you deploy the Skype for Business client, see one of the following topics:
  
- **Lync Server 2013**, see [Configure the client experience with Skype for Business in Lync Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=532732)
    
- **Lync Server 2010** see [Configure the client experience with Skype for Business in Lync Server 2010](https://go.microsoft.com/fwlink/p/?LinkId=532733)
    
## Use the Lync client experience with Skype for Business Server on-premises
<a name="LyncwithSfBServer"> </a>

Follow the steps in this section if you want to configure the Lync client experience in an on-premises Skype for Business Server deployment.
  
Follow the steps in this section if you want to configure the Skype client experience in an on-premises deployment. The default experience for on-premises
  
 **Step 1:** First, deploy Skype for Business Server.
  
 **Step 2:** Next, use a client policy to set the Lync client experience with the Skype for Business client. There are **3 options** for using a client policy to set the client experience.
  
 **Option 1:** Set the Lync client experience by using a Global policy. Note that the Global policy applies to all of the users in your deployment, but user and site level policies take precedence over the Global policy:
  
```
Set-CsClientPolicy -Identity Global -EnableSkypeUI $False
```

 **Option 2:** Modify an existing client policy that you are using in your environment to include the setting to enable the Lync client experience. This lets you assign the Lync client experience only to those users that have the existing policy assigned:
  
```
Set-CsClientPolicy -Identity ExistingClientPolicyName -EnableSkypeUI $False
```

 **Option 3:** Create a new policy to assign to users that includes the setting for the Lync client experience. First, create the new client policy and provide the name of the policy as the value of the **Identity** parameter:
  
```
New-CsClientPolicy -Identity UseLyncUI -EnableSkypeUI $False
```

Then assign the policy to users, using the name of the policy (the value you used for the **Identity** parameter) as the value of the **PolicyName** parameter:
  
```
Grant-CsClientPolicy username@contoso.com -PolicyName UseLyncUI
```

 **Step 3: Optional** - By default, the first time users start the Skype for Business client, the Skype client experience is used and a notification is displayed to users asking them to restart the client to get the Lync client experience. You can configure your environment so that the Lync client experience is displayed the first time users start the client, as well as turn off the client tutorial, by modifying the system registry on client computers. For the steps you need to perform before you deploy the Skype for Business client see [Configure the client experience with Skype for Business](../../deploy/deploy-clients/configure-the-client-experience.md).
  
 **Step 4:** After you've configured your client policies, deploy the Skype for Business client, build 4711.1002 (April, 2015) or later.
  
## Use the Lync client experience with Skype for Business Online
<a name="LyncwithSfBO"> </a>

Follow the steps in this section if you want to configure the Lync client experience and you using Skype for Business Online.
  
If you are using Skype for Business Online, you can still use the Lync client experience with the Skype for Business client in your organization by using Remote PowerShell to configure client policies. There are **3 options** for using a client policy to set the client experience. Note that the policy and parameter names are different than the settings you use to configure the client experience when you are using Skype for Business or Lync Server on-premises.
  
 **Option 1:** Set the Lync client experience by using a Global policy. Note that client and site policies applied to users will take precedence over a Global policy.
  
```
Grant-CsClientPolicy -PolicyName ClientPolicyDisableSkypeUI
```

 **Option 2:** Modify an existing client policy that you are using in your environment to include the setting to enable the Lync client experience. This lets you assign the Lync client experience only to those users that have the existing policy assigned:
  
```
Grant-CsClientPolicy -PolicyName ClientPolicyDisableSkypeUI
```

 **Option 3:** Use a custom policy instance that includes the setting for the Lync client experience.
  
```
Grant-CsClientPolicy username@contoso.com -PolicyName ClientPolicyNoIMURLDisableSkypeUI
```

After you've configured your client policies, deploy the Skype for Business client, build 4711.1002 (April, 2015) or later.
  
For detailed information about how to configure the client experience with Skype for Business Online, including steps about how to control the first run experience and PowerShell scripts you can use to configure your environment, see [Switching between the Skype for Business and the Lync client user interfaces](https://aka.ms/SfBOUI).
  
## Resources to help you prepare your support teams and your end users for the update
<a name="support"> </a>

To make it easier for you and your organization prepare for the transition, we have many additional resources available to help you plan, educate and engage end-users.
  
- [Video: Introducing Skype for Business](https://go.microsoft.com/fwlink/p/?LinkId=544819)
    
- [Skype for Business Quick Start Guides (Download)](https://go.microsoft.com/fwlink/p/?LinkId=544818)
    
- [Lync is now Skype for Business — see what's new](https://go.microsoft.com/fwlink/p/?LinkID=529224)
    
- [Skype for Business: Step-by-step guide for new users](https://go.microsoft.com/fwlink/p/?LinkId=544815)
    
- [Why do I see Skype for Business when I'm using Lync?](https://go.microsoft.com/fwlink/p/?LinkID=544712)
    

