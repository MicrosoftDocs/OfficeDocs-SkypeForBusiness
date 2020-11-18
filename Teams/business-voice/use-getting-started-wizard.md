---
title: Use the Getting Started wizard to set up Business Voice
author: dstrome 
ms.author: dstrome
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
f1.keywords:
- NOCSH
localization_priority: Priority
MS.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
- Teams_Business_Voice
- m365initiative-voice
search.appverid: MET150
description: 
appliesto: 
- Microsoft Teams
---

# Use the Getting Started wizard to set up Business Voice

> [!IMPORTANT]
> The information in this article is applicable to Business Voice **with** Calling Plan only. Business Voice with Calling Plan is available only in select countries and regions. Before reading this article, check [Country and region availability for Business Voice](country-region-availability.md) to see whether your country or region supports Business Voice with Calling Plan.
>
> If your tenant is located in a country or region that doesn't support Business Voice with Calling Plan, check out [Get help from a Microsoft reseller or partner](reseller-partner-support.md).

The Getting Started wizard for Microsoft 365 Business Voice gets you set up quickly to make and receive phone calls in Microsoft Teams. If you're a small business just starting out, the wizard can get you up and running in a few minutes with phone numbers, call menus, greetings, and more. If you're a larger business with an established telephony solution, the wizard can help you set up a pilot so a few users can try Business Voice before you roll it out for everyone. Either way, you can start using Business Voice as soon as the wizard is finished!

It's a good idea to read this article before you start the wizard. When you're ready to run the wizard, select **Get started** on the [Get started with Microsoft 365 Business Voice](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/featureexplorer/apps/SmbVoice) page. Sign in by using the account you used to create your subscription or another account that's a Global Administrator.

> [!IMPORTANT]
> Microsoft Teams and Business Voice only work when your users' mailboxes are located in Microsoft 365.  They don't support mailboxes on on-premises Exchange Server.
>
> The Getting Started Wizard doesn't support Skype for Business hybrid deployments. If you have a Skype for Business hybrid deployment and want to set up Business Voice, check out [Set up Phone System in your organization](../setting-up-your-phone-system.md).

<!-- After you've finished the wizard, you may want to check out the following articles:

* [Things to try with Business Voice](things-to-try.md)
* [Business Voice design customization](customize-business-voice.md)-->

If you don't want to customize anything immediately, you're done! You can start using Business Voice right away.

## Emergency services location

<table>
    <tr>
        <td>If you want to change the emergency address, click <b>Edit</b>, and then enter a new address. The address that you provide is validated to make sure that it's legitimate and correctly formatted for emergency response services. This address is then assigned to all users that you assign a number to in the next step. If you have employees in more than one location, see <a href="./customize-business-voice.md">Business Voice design customization</a> to add and assign more emergency addresses after you prepare the Getting Started wizard.</td>
        <td><img src="https://docs.microsoft.com/MicrosoftTeams/media/voice-wizard-choose-number.png" width="400"></td></tr>
</table>

For more information, see [What are emergency locations, addresses, and call routing](../what-are-emergency-locations-addresses-and-call-routing.md)?

## Company phone number

<table>
    <tr>
        <td>In addition to a new local phone number, you can purchase a toll-free number or port an existing number to Microsoft 365. To set up a toll-free number, you need to purchase Communications Credits. To port one or more numbers to Microsoft 365, go to the <a href="https://admin.teams.microsoft.com">Teams admin center</a> after the wizard finishes.
        </td>
        <td><img src="https://docs.microsoft.com/MicrosoftTeams/media/voice-wizard-choose-number.png" width="400">
        </td>
    </tr>
</table>

> [!IMPORTANT]
> If you port an existing phone number to Microsoft 365, you'll still see a temporary phone number in the wizard. This is expected. After you complete the wizard and the porting process, the temporary phone number will be replaced by the pre-existing number.

## User licenses

<table>
    <tr>
        <td>To assign user licenses, select the people in your organization who need to make or receive phone calls outside of Teams (such as calling a supplier). You can only assign as many Business Voices licenses as you have available. If you need more, you can buy additional licenses after the wizard is finished.
        </td>
        <td><img src="https://docs.microsoft.com/MicrosoftTeams/media/voice-wizard-get-numbers.png" width="400">
        </td>
    </tr>
</table>

> [!IMPORTANT]
> You can port existing phone numbers to Microsoft 365 after the wizard is finished. After you complete the porting process, the ported phone numbers will replace the temporary phone numbers that the wizard provided.

## Incoming-call greeting

<table>
    <tr>
        <td>You can upload a sound file (MP3 or WAV) of up to 5 Megabytes (MB) to use as a call greeting, or you can type your greeting, and Microsoft 365 will use text-to-speech to read it to the caller. The greeting will be the first thing callers hear when they call your company phone number. For text-to-speech, you might need to use phonetic spellings to get the pronunciations correct.
        </td>
        <td><img src="https://docs.microsoft.com/MicrosoftTeams/media/voice-wizard-greeting.png" width="400">
        </td>
    </tr>
</table>

## Call menu and forwarding

<table>
    <tr>
        <td>You can forward all calls to a specific user, or you can set up a menu that the caller can choose options from. If you create a call menu, you specify options that the caller can select by voice or by pressing a number on a phone's keypad. Each menu option can forward calls to a specific user.<br><br>
        You can upload a sound file (MP3 or WAV) of up to 5 MB that gives instructions to the caller, or you can type the instructions. Microsoft 365 will use text-to-speech to read them to the caller. You might need to spell words phonetically to get the pronunciations right.
        </td>
        <td><img src="https://docs.microsoft.com/MicrosoftTeams/media/voice-wizard-call-forwarding-rules.png" width="400">
        </td>
    </tr>
</table>

> [!IMPORTANT]
> The Getting Started wizard helps you set up a simple call menu to get you up and running quickly. If you have multiple phone numbers that you want to set up call menus for or you want to set up more complex call menus (also called auto attendants), see [Set up a Cloud auto attendant](set-up-auto-attendants.md) after you finish the wizard.

<table>
    <tr>
        <td> <p>The Getting Started wizard takes the information that you enter and sets up Business Voice. On the <b>Overview</b> page, you can see what phone numbers are assigned to your users, look at your call menu, listen to your greeting, and more.</p>
             <p>Setup takes several minutes. If you select <b>Done</b>, we'll continue to set up Business Voice in the background. Or just wait until setup is finished. After it's finished, go to <b>Voice</b> in the <a href="https://admin.teams.microsoft.com" target="_blank">Teams admin center</a> to set up more Business Voice features.</p>
        </td>
        <td><img src="https://docs.microsoft.com/MicrosoftTeams/media/voice-wizard-finish-page.png" width="400">
        </td>
    </tr>
</table>
