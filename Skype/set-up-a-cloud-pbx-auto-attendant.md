---
title: Set up a Cloud PBX auto attendant
ms.assetid: 6fc2687c-0abf-43b8-aa54-7c3b2a84b67c
---



# Set up a Cloud PBX auto attendant

Auto attendants are very useful and let people that call into your organization navigate a menu system to get them to the right department, call queue, a person or the operator. You can create an auto attendant for your organization using the Skype for Business admin center. To create a new auto attendant, go to **Call routing** in the left navigation, and then select **Auto attendants** > **Add new**.
  
    
    

If you want to learn more about auto attendants, see  [What are Cloud PBX auto attendants?](what-are-cloud-pbx-auto-attendants.md).
## Step 1 - Getting started


- Before you can create and set up your auto attendants, you will need to get or transfer your existing toll or toll-free service numbers. Once you get the toll or toll-free service numbers, they will show up in the ** Skype for Business admin center** > **Voice** > **Phone numbers** tab and the **Number type** listed will be listed as **Service - Toll-Free**. To get your service numbers, see  [Getting Skype for Business service phone numbers](getting-skype-for-business-service-phone-numbers.md) or if you want to transfer and existing service number, see [Transfer phone numbers to Skype for Business Online](transfer-phone-numbers-to-skype-for-business-online.md). **User (subscriber)** numbers can't be assigned to auto attendants. If you are outside the U.S., you can't use the Skype for Business admin center to get service numbers. Go [Get phone numbers for Skype for Business Online](get-phone-numbers-for-skype-for-business-online.md) instead to see how to do it from the outside of the U.S.
    
    > [!CAUTION]
      > To get and use toll-free phone numbers, you need to set up PSTN Consumption Billing. To do this see  [What is PSTN Consumption billing?](what-is-pstn-consumption-billing.md) and [Set up PSTN Consumption billing](set-up-pstn-consumption-billing.md). 
- Your organization must have (at a minimum) an Enterprise E3 plus Skype for Business Cloud PBX license or an Enterprise E5 license. The number of Skype for Business Cloud PBX user licenses that are assigned impacts the number of service numbers that are available to be used for auto attendants. The numbers of auto attendants you can have is dependent on the number Skype for Business Cloud PBX and PSTN Conferencing licenses that are assigned in your organization. To learn more about licensing, go  [Skype for Business add-on licensing](skype-for-business-add-on-licensing.md).
    
    > [!TIP]
      > To redirect calls to an operator or a menu option that is an Online user with a Skype for Business Cloud PBX license, you will need to enable them for Enterprise Voice or assign a PSTN Calling plan to them. See  [Assign Skype for Business licenses](assign-skype-for-business-licenses.md). You can also use Windows PowerShell. For example run:  `Set-CsUser -identity "Amos Marble" -EnterpriseVoiceEnabled $true`

## Step 2 - Create a new auto attendant

In the **Skype for Business admin center**, click **Call routing** > **Auto attendants**, then click **Add new**:
  
    
    

### Edit general info page

On the Edit general info page, put in or choose:
  
    
    

  
    
    
![New auto attendant page 1.](images/edacec94-9384-4a87-be0a-5c49a151287e.png)
  
    
    

  
    
    

|||
|:-----|:-----|
|**1** <br/> |**Name** Put in a descriptive display name for your auto attendant. The name is required and can contain up to 64 characters, including spaces. It will be listed in the **Name** column on the **Auto attendants** tab. <br/> |
|**2** <br/> |**Phone number** Select a phone number for your auto attendant. A phone number is required and you can pick any available service toll or toll-free phone number that you have for your organization. If there are no phone numbers listed, you will need to get a service toll or toll-free phone number. Go [Getting Skype for Business service phone numbers](getting-skype-for-business-service-phone-numbers.md) to get them. <br/> > [!NOTE]> **User (subscriber)** numbers can't be assigned to auto attendants.          |
|**3** <br/> |**Time zone** You must set the time zone for your auto attendant, but it doesn't need to correspond to the time zone of the main address listed for your organization. Each auto attendant can have a different time zone, and the business hours set for the auto attendant will be set based on the time zone that you select here. <br/> |
|**4** <br/> |**Language** Select the language that you want to use for your auto attendant from any of the available languages listed. The language you set here is the language that the auto attendant will use to interact with people that call into this auto attendant and all the system prompts will be played in this language. <br/> |
|**5** <br/> |**Speech recognition** Speech recognition is available and if this option is checked, people that call in can use voice input in the language you set. You can disable speech recognition by unchecking it if you want to only let people use their phone keypad. <br/> |
|**6** <br/> |**Operator** This is optional and doesn't need to be set for the auto attendant. However, you can set **Operator** option for people that call in to be able to break out of the menus to speak to a person to help them. <br/>  The key 0 is automatically assigned to Operator. <br/>  If you set this up, you will also need to tell people that call in that this is an available option in the **Edit menu options** on the **Business hours call handling** page. If you set an operator on your auto attendant, you will need to put in the corresponding prompt text in the **Callers will hear** box or change your audio file to include this option. For example, "For the Operator, press zero." <br/>  You can set one of the following as Operator: <br/>  A **Person in your company** that is an Online user with a Skype for Business Cloud PBX license that is enabled for Enterprise Voice or assigned a PSTN Calling plan. <br/> > [!NOTE]>  Users hosted on-premises using Skype for Business Server 2015 or Lync Server 2013 and 2010 aren't supported.           A **Call Queue** that you have set up. <br/>  You can set it up so the person calling will be sent to voicemail. To do this, select a **Person in your company** and set this person's calls to be forwarded directly to voicemail. <br/> |
   

### Select hours of operation page

By default, business hours are set to 24 hours a day - 7 days a week, so all hours are considered business hours. All of the hours that aren't included in business hours are considered after business hours. If you select the **Custom** option and set your business hours, then a new page called **After hours call handling** will be added and you will have to configure the call handling for after business hours for the auto attendant.
  
    
    

  
    
    
![New auto attendant Hours of operation.](images/61769547-cdb4-45c0-af5a-3d6e0731fbc6.png)
  
    
    

  
    
    

|||
|:-----|:-----|
|**1** <br/> |Select the **Custom** option to select specific business hours in the calendar. When you select **Custom**, business hours will be set to Monday to Friday, 9:00 am-5:00 pm by default.  <br/> |
|**2** <br/> |To change business hours, highlight the business hours you want to set using the calendar. The calendar allows you to select business hours in 30 minute intervals, and the business hours you select here will be set based on the time zone that you set on the **General info** page. To set up a break (a lunch break, for example), deselect or drag to deselect the time on the calendar. You can also have multiple breaks that you can set within business hours. <br/> |
   

### Business hours call handling page


> [!TIP]
> If you use a custom business hours schedule, you will also need to set up call handing for after business hours. An **After hours call handling** page will be added so you can configure those options, and it will give you the same options as **Business hours call handling**. 
  
    
    

You can set up greetings, prompts and menus for people who call into your organization's auto attendant phone number will hear during the business hours.
  
    
    

  
    
    
![Business hours call handling.](images/2a33b1f7-d362-47a7-bf32-ef702bc878e8.png)
  
    
    

  
    
    

|||
|:-----|:-----|
|**1**|**Company greeting** Business hours greeting is optional and can be set to **None**. In this case, the caller will hear no message or greeting before the call is handled by one of the options you select. You can also upload an audio file (in .wav, mp3 or .wma formats), or create a custom greeting using Text-to-Speech. **None** No greeting will be played when people call into the auto attendant phone number. **Create a custom greeting** If you chose this, you should enter the text you want the system to read (up to 1000 characters). For example, you would enter "Welcome to Contoso. Your call is important to us." in the **Callers will hear** text box. **Upload an audio file** If you chose this, you will need to record the greeting and then upload your audio file (in a .wav, .mp3 or .wma format).|
|**2**| You can select what happens to the calls that arrive during business hours. You can chose from the following options: **Disconnect** If you select it, the person calling in will be disconnected after hearing a business hours greeting. **Redirect call** This can be used to automatically send the call to: **Person in your company** that is an Online user with a Skype for Business Cloud PBX license that is enabled for Enterprise Voice or assigned a PSTN Calling plan. You can set it up so the person calling in can be sent to voicemail. To do this, select a **Person in your company** and this person will have their calls forwarded directly to voicemail.> [!NOTE]>  Users hosted on-premises using Skype for Business Server 2015 or Lync Server 2013 and 2010 aren't supported.           A **Call Queue** Using a Call Queue allows the call to be transferred to an existing Call Queue that you have set up Another **Auto attendant** You can use an existing auto attendant to create a second level of menu options containing a submenu. These are called nested auto attendants. **Play menu options prompt** These can also be used to let you set up a prompt you want played.|
|**3**|**Menu prompt** To create main menu prompt, you can either use Text-to-Speech or upload an audio file (.wav, .mp3 or .wma). You can type the prompt in the **Callers will hear** box or record an audio file and say, for example: "For Sales, say or press or say 1. For Services, press or say 2. For Customer Support, press or say 3. For the operator, press or say 0. To hear this menu again, press the star key or say repeat." **Create a custom prompt** If you chose this, you should enter the text you want the system to read (up to 1000 characters). **Upload an audio file** If you chose this, you will need to record the greeting and then upload your audio file (in a .wav, mp3 or .wma format).|
|**4**|**Dial by Name** If you choose this option, this will enable people who call in to search for people in your organization using Directory Search. You can select which people will be listed as available or not available for Dial by Name by setting up those options on the **Dial scope** page. Any online user with Skype for Business Cloud PBX license can be found by Dial by Name.> [!CAUTION]> Users hosted on-premises using Skype for Business Server 2015 or Lync Server 2013 and 2010 **can't be reached** with Dial by Name.          |
|**5**|**Edit menu options** Menu options can be added or removed by using key buttons on the keypad. To add a menu option, press the corresponding key on the keypad. The keys in use will change in color and the corresponding row of options will appear below. To delete a Menu Option, simply click on the corresponding key on the keypad control to unselect this key. The key mapping row will be removed.> [!TIP]> You will have update menu prompts text or re-record the audio separately when adding to removing options because it won't be automatically done for the existing menu prompt.           Any menu option can be added and removed in any order and the key mappings don't have to be continuous. It is possible, for example, to create a menu with keys 0, 1 and 3 mapped to options, while the keys 2 isn't used.> [!NOTE]> The keys * (Repeat) and # (Back) are reserved by the system and can't be reassigned. If speech recognition is enabled, pressing * will correspond to "Repeat" and # will correspond to the "Back" voice commands.           |
|**6**| To set up your menu options, after you select the key(s), you will need to: **Enter the Name of the option** This can be up to 64 characters long, and can contain multiple words like "Customer Service" or "Operations and Grounds". If speech recognition is enabled, the name will automatically be recognized , and the person calling in will be able to either press 3, say "three" or say "Customer Service" to select option mapped to key 3. The next step is to select where the call is to be sent if the corresponding key is pressed, or the option is selected using speech recognition. The call can be sent to: **Operator** If operator is already setup, it is automatically mapped to key 0 but it can also be deleted or reassigned to a different key. If operator isn't set to any key, then the voice command "Operator" will be disabled too. A **Person in your company** that is an Online user with a Skype for Business Cloud PBX license that is enabled for Enterprise Voice or assigned a PSTN Calling plan. You can set it up so the person calling in can be sent to voicemail. To do this, select a **Person in your company** and this person will have their calls forwarded directly to voicemail.> [!NOTE]>  Users hosted on-premises using Skype for Business Server 2015 or Lync Server 2013 and 2010 aren't supported.          **Call Queue** Using a Call Queue option allows the call to be transferred to an existing Call Queue that you have set up. **Auto Attendant** You can use an existing auto attendant to create a second level of menu options containing a submenu. These are called nested auto attendants.> [!NOTE]>  The **Business Hours** of nested (or second level) auto attendants will also be used including for the calls sent from other auto attendant that has been set up.          |
   

### Select dial scope page

On this page, you can set up what users in your organization will be listed in your directory and available for Dial by Name when a person that calls into your organization.
  
    
    

  
    
    
![Dial scope for searching with dial by name.](images/1bcb185c-00db-43a7-b5c4-9b021c0627f7.png)
  
    
    

  
    
    

|||
|:-----|:-----|
|**1** <br/> | Using the **Include** option, you have two options: <br/> **All Online users** Using this option allows all of the people in your organization to be included in directory search. All Online users with a Skype for Business Cloud PBX license with a PSTN Calling plan will be listed. <br/> **Custom** If you use this option, you can search for a distribution list or security group that has been created in your organization, and the people added to this distribution list or security group who are **Online users with a Skype for Business Cloud PBX license** will be included in the directory search. You can add multiple distribution lists and security groups. <br/> > [!CAUTION]>  On-premises users from deployments of Skype for Business 2015 or Lync Server 2013 and 2010 won't be listed when someone searches the directory using Dial by Name.          |
|**2** <br/> | Using the ** Exclude** option, you have two options: <br/> **None** Using this option will indicate that no Online users will be excluded from directory search. <br/> **Custom** If you use this option, you can search for a distribution list or security group that has been created in your organization, and all people added to this distribution list or security groups will be excluded from directory search. <br/> > [!CAUTION]>  On-premises users from deployments of Skype for Business 2015 or Lync Server 2013 and 2010 won't be listed when someone searches the directory using Dial by Name.          |
   

    
> [!NOTE]
> It might take up to 36 hours for a new user to have their name to be listed in the directory when someone uses Dial by Name with speech recognition. 
  
    
    


  
    
    
After you put in all the required fields and set up call handling menus and options, click **Save**.
  
    
    

## Editing and testing an auto attendants

After you have saved your auto attendant, it will be listed on the **Auto attendants** page. This will allow you to quickly see some of the options that you have set up, including the name, phone number, language and status.
  
    
    
If you want to make changes to an auto attendant, click to highlight the auto attendant and in the side panel, you can click **Edit**.
  
    
    
You can also quickly place a test call to your auto attendant by using **Test** button in the side panel.
  
    
    

## Want to know more?

You can also use Windows PowerShell to create and set up auto attendants.
  
    
    

### Auto attendant cmdlets

Here are the cmdlets that you need to manage an auto attendant.
  
    
    

||||
|:-----|:-----|:-----|
| [New-CsOrganizationalAutoAttendant](https://technet.microsoft.com/en-us/library/mt796493.aspx) <br/> | [Get-CsOrganizationalAutoAttendantSupportedTimeZone]( https://technet.microsoft.com/en-us/library/mt796483.aspx) <br/> | [New-CsOrganizationalAutoAttendantMenu](https://technet.microsoft.com/en-us/library/mt796488.aspx ) <br/> |
| [Set-CsOrganizationalAutoAttendant](https://technet.microsoft.com/en-us/library/mt796486.aspx) <br/> | [Get-CsOrganizationalAutoAttendantSupportedLanguage](https://technet.microsoft.com/en-us/library/mt796481.aspx) <br/> | [New-CsOrganizationalAutoAttendantCallFlow](https://technet.microsoft.com/en-us/library/mt796489.aspx) <br/> |
| [Get-CsOrganizationalAutoAttendant](https://technet.microsoft.com/en-us/library/mt796482.aspx ) <br/> | [New-CsOrganizationalAutoAttendantCallableEntity](https://technet.microsoft.com/en-us/library/mt796480.aspx) <br/> | [New-CsOnlineTimeRange](https://technet.microsoft.com/en-us/library/mt796491.aspx ) <br/> |
| [Remove-CsOrganizationalAutoAttendant](https://technet.microsoft.com/en-us/library/mt796492.aspx) <br/> | [New-CsOrganizationalAutoAttendantPrompt](https://technet.microsoft.com/en-us/library/mt796484.aspx ) <br/> | [New-CsOnlineSchedule](https://technet.microsoft.com/en-us/library/mt796490.aspx) <br/> |
| [New- CsOnlineAudioFile](https://technet.microsoft.com/en-us/library/mt796479.aspx) <br/> | [New-CsOrganizationalAutoAttendantMenuOption](https://technet.microsoft.com/en-us/library/mt796485.aspx ) <br/> | [New-CsOrganizationalAutoAttendantCallHandlingAssociation](https://technet.microsoft.com/en-us/library/mt796487.aspx ) <br/> |
   

### More about Windows PowerShell


- When it comes to Windows PowerShell is all about managing users and what users are allowed or not allowed to do. With Windows PowerShell, you can manage Office 365 and Skype for Business Online using a single point of administration that can simplify your daily work, when you have multiple tasks to do. To get started with Windows PowerShell, see these topics:
    
  -  [An introduction to Windows PowerShell and Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525039)
    
  
  -  [Six Reasons Why You Might Want to Use Windows PowerShell to Manage Office 365 ](https://go.microsoft.com/fwlink/?LinkId=525041)
    
  
- Windows PowerShell has many advantages in speed, simplicity, and productivity over only using the Office 365 admin center such as when you are making setting changes for many users at one time. Learn about these advantages in the following topics:
    
  -  [Best ways to manage Office 365 with Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=525142)
    
  
  -  [Using Windows PowerShell to manage Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525453)
    
  
  -  [Using Windows PowerShell to do common Skype for Business Online management tasks](https://go.microsoft.com/fwlink/?LinkId=525038)
    
  
