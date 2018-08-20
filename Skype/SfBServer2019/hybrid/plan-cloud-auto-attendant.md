---
title: "Plan Cloud Auto Attendant"
ms.author: jambirk
author: jambirk
manager: serdars
ms.date: 7/31/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
description: "Overview of using a Cloud Auto Attendant with Skype for Business Server 2019."
---

# Plan cloud auto attendant

[!INCLUDE [disclaimer](../disclaimer.md)]

## Feature Overview 

The Auto Attendant used with Exchange Unified Messaging  (with Exchange Server 2013 or Exchange Server 2016) is no longer available in Exchange Server 2019 or Exchange Online. If your implementation integrates with either of these Exchange versions, you'll need to use the online Cloud Voice features. 

If you have already implemented [Cloud Voicemail](plan-cloud-voicemail.md), your next step is to implement a new Cloud Auto Attendant Service with Skype for Business Server 2019. Further Skype for Business Server 2019 configuration is not necessary. 

With Cloud Auto Attendant you will be able to: 

* Create a new Cloud Auto Attendant.
* Define routing of inbound PSTN calls that arrive on a local (on-prem) trunk, gateway/SBC and Mediation Server and must be routed to an instance of the Auto Attendant service in the cloud. 
* Export an existing Exchange UM Auto Attendant configuration to design a new Cloud PBX Auto Attendant. 
* Access reporting and other service information. 

See: 

+ [What are Phone System auto attendants?](../../SfbOnline/what-is-phone-system-in-office-365/what-are-phone-system-auto-attendants.md)
+ [Set up a Phone System auto attendant](../../SfbOnline/what-is-phone-system-in-office-365/set-up-a-phone-system-auto-attendant.md)
+ [Automatically answer and route incoming calls](https://docs.microsoft.com/en-us/exchange/voice-mail-unified-messaging/automatically-answer-and-route-calls/automatically-answer-and-route-calls) 


## Do's and Don'ts for Auto Attendant scripts

Your auto-attendant script can make or break the impression left on your customers or callers. Think it through carefully, write it out, and consider having it professionally recorded. 

Consider some of these guidelines when planning a brand new auto attendant system:

**Do:**
1. Greet and thank the caller for contacting you. Keep this short, no more than three sentences and under 30 seconds. If your web site offers self-service options, mention it but otherwise present choices and options as soon as possible without being abrupt.  It's a good idea to have alternate initial greetings for calls taken outside business hours, or on holidays or weekends. 
2. Put your most frequently used options as early as possible in the first set of menu options. If possible, reserve zero in the first menu for a transfer to a live operator, but mention it last. 
3. Have the menu repeat once if nothing is selected, and if there still isn't a selection, transfer the call to a live operator rather than having the call disconnect.
4. Use multilingual prompts, but put the secondary language or languages at the end of the first set of options.
5. Present the option, then the number to press ("For Sales, press 3"). When the caller hears the option they want, their attention immediately focuses, so that's the time to tell them what will get them there.
6. Choose the person reading your script carefully, make sure their voice leaves the impression you want and their voice is clearly understandable when recorded. If the reader mumbles, sounds condescending, or sounds like they might be a machine, you can probably find a better choice.
7. Mention significant changes to your option strucuture when that happens, but don't leave that part of the greeting active for more than a month. If you have frequent updates and expect that to be the case most of the time, just omit it from the script. 

And finally, take a few extra minutes to flow chart the options you want to create, and make sure you aren't creating opportunities for users to go around in circles in the option menus. It should ideally be possible to get connected to a person or their voicemail in three menus or less.


**Don't:**
1. Clutter the initial greeting with hours of operation or your business address. Make those available as a choice in the first menu if it's frequently requested information, but keep the initial greeting short and sweet.
2. Create menus with more than 5 choices. If you do, you'll likely confuse your callers and force them to repeat the menu.
3. Say please or use other pleasantries over and over. Just get the callers to the option or person they need as efficiently as possible.
4. Include "http://<span></span>www." when mentioning a web address. It's just a poor use of script time.
5. Use abbreviations like St for street or CA for California. Spell them out in the script and say the whole word in the recording. 
6. Use reserved menu option numbers or keys. If all extensions in your office start with 6, then don't use that number.  The * and # characters frequently have reserved meanings too, so review which DTMF keys are reserved
7. Include sales information in the scripts, you'll annoy your callers. Let your sales force take care of that sort of thing.

And finally, if your company has a slogan, think twice about including it in the script at all. Chances are your callers have heard it before if they're calling you. If you do include it, put it somewhere it brings the Auto Attendant experience to a close, like when transferring to an individual's desk line or voicemail. Never make up a slogan just to include it in a voicemail script.

With all that in mind, proceed to [Configure Cloud Auto Attendant](configure-cloud-auto-attendant.md)

## See Also

[Enable custom prompt recording using the telephone user interface](https://docs.microsoft.com/en-us/exchange/voice-mail-unified-messaging/greetings-announcements-menus-and-prompts/enable-custom-prompt-recording)

[Plan Cloud Voicemail service](plan-cloud-voicemail.md)

[Configure Cloud Voicemail service](configure-cloud-voicemail.md)

[What are Phone System auto attendants?](../../SfbOnline/what-is-phone-system-in-office-365/what-are-phone-system-auto-attendants.md)

[Set up a Phone System auto attendant](../../SfbOnline/what-is-phone-system-in-office-365/set-up-a-phone-system-auto-attendant.md)

[Automatically answer and route incoming calls](https://docs.microsoft.com/en-us/exchange/voice-mail-unified-messaging/automatically-answer-and-route-calls/automatically-answer-and-route-calls) 
