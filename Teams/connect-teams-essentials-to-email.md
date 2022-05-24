---
title: Connect Microsoft Teams Essentials (AAD Identity) to an existing email system with calendar
author: adjoseph
ms.author: adjoseph
ms.reviewer: jimmyw
manager: serdars
ms.topic: article
audience: admin
ms.service: msteams
searchScope:
  - Microsoft Teams
search.appverid: MET150
description: Learn how to connect Microsoft Teams Essentials (AAD Identity) to an existing email system with calendar like Google Workspace
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.collection:
  - M365-collaboration
appliesto:
  - Microsoft Teams
---

# Connect Microsoft Teams Essentials (AAD Identity) to an existing email system with calendar

This guide provides configuration steps for connecting Microsoft Teams Essentials (AAD Identity) to an existing email system with calendar.

Microsoft Teams Essentials (AAD Identity) brings together the best of Teams with meetings, chat, calling, and collaboration. Teams Essentials (AAD Identity) can connect to your existing email system to provide an integrated experience like having all Teams notifications in an existing email inbox, all calendar events in Teams, and the ability to sign into Teams with your existing email address.

Once connected, you can see responses to scheduled meetings and invitations to collaborate in your mailbox and Microsoft Teams. You can also view and interact with incoming meetings from your calendar using Teams and third-party meeting software like Google Workspace.

## Prerequisites

The configuration steps in this article involve the process of automatically forwarding items from Exchange Online. By default, automatic forwarding is disabled by the anti-spam outbound policy. This policy must be enabled to connect Teams Essentials to an existing mailbox and calendar system.

To enable automatic forwarding:

1. Go to the Microsoft 365 Defender portal at <https://security.microsoft.com/>
2. Under the left navigation menu, go to **Email & collaboration** > **Policies & rules** > **Threat policies** > **Anti-spam** in the Policies section
3. On the **Anti-spam policies** page, select **Anti-spam outbound policy (Default)** from the list
4. In the policy details flyout that appears, select **Edit protection settings** to modify the autoforwarding rule.
5. Under **Forwarding rules**, change the automatic forwarding condition to **On – forwarding is enabled** and save your changes.

:::image type="content" source="media/essentials-antispam.png" alt-text="Image showing the Microsoft Defender Portal anti-spam outbound policy flyout with On, forwarding is enabled condition under Forwarding rules." :::

To learn more about configuring outbound spam policies, visit [Configure outbound spam filtering - Office 365 | Microsoft Docs](/microsoft-365/security/office-365-security/configure-the-outbound-spam-policy?view=o365-worldwide&preserve-view=true).

## Connect Teams Essentials to Exchange Online with Exchange on-premises

You can enjoy all that Teams Essentials (AAD) has to offer by using a hybrid approach to configure the connection between Microsoft Teams and Exchange Online with Exchange on-premises.

To make calendar access work for your on-prem mailboxes, follow the guidance provided at[Configuring Teams calendar access for Exchange on-premises mailboxes - Microsoft Tech Community](https://techcommunity.microsoft.com/t5/exchange-team-blog/configuring-teams-calendar-access-for-exchange-on-premises/ba-p/1484009)

To deploy Microsoft Teams Rooms in a hybrid environment with Exchange on premises, visit [Deploy Microsoft Teams Rooms with Exchange on-premises - Microsoft Teams | Microsoft Docs](rooms/with-exchange-on-premises.md)

## Connect Teams Essentials to third-party email systems with calendar

If you don't plan to switch your organization's mailbox to Microsoft 365, you can connect Teams Essentials to an existing third-party email and calendar system. This connection allows you to receive Teams notifications in your existing email system while viewing existing meeting invites and calendar events in Microsoft Teams.

### Connect Teams Essentials to third-party email using vanity domain (Google Workspace example)

The following section shows you how to connect Microsoft Teams to an existing email system with calendar, like Google Workspace. You will accomplish this connection by leaving the current email system intact, forwarding all email to Exchange Online, filtering everything except emails of the calendaring type. In doing so, calendaring emails automatically appear in the Teams calendar accepted as tentative and non-calendaring type emails are deleted.

All email generated in Microsoft 365 is forwarded to Google Workspace so that users get Teams reminders and notifications. User identities, like the user's primary email, can be duplicated. Single sign-on is also possible, but not required. Users should be able to join Teams meetings from either the third-party calendar or Teams calendar. Another Teams features will work as expected.

:::image type="content" source="media/essentials-googleworkspace.png" alt-text="Image depicting a diagram of the mail flow between EXO and Gmail":::

These examples rely on the [Connect-ExchangeOnline](/powershell/module/exchange/connect-exchangeonline?view=exchange-ps&preserve-view=true) PowerShell commandlet that is part of the [Exchange Online PowerShell V2 module](/powershell/exchange/exchange-online-powershell-v2&preserve-view=true). If you get an error when running Connect-ExchangeOnline, ensure that you've followed the recommended instructions for installing the module using [Install the EXO V2 module](/powershell/exchange/exchange-online-powershell-v2?view=exchange-ps&preserve-view=true). When Connect-ExchangeOnline prompts for credentials, be sure to use a tenant administrator account.

#### Step One: Set up a new Microsoft 365 tenant domain

1. Go to the admin center at <https://admin.microsoft.com>.

2. Go to **Set Up** > **Domains**  and select **Add domain** to add your existing domain. If you don't add a domain, people in your organization will use the onmicrosoft.com domain for their email addresses until you do. Be sure to add your domain before adding users, so you don't have to set them up twice.

3. Verify the domain with a TXT record by following the steps at [Verify with a TXT Record](/microsoft-365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider?view=o365-worldwide&preserve-view=true).

4. When prompted, select **Do not allow Microsoft 365 to configure DNS**.

5. When prompted, leave the existing MX records in place without altering them.

6. Update the existing SPF TXT record to include Microsoft 365.

7. Configure DomainKeys Identified Mail (DKIM) for Microsoft 365 by following these steps to manually [set up DKIM](/microsoft-365/security/office-365-security/use-dkim-to-validate-outbound-email?view=o365-worldwide&preserve-view=true).

8. Sign back into the Microsoft 365 admin center at <https://admin.microsoft.com/AdminPortal/> to enable DKIM

9. In the navigation panel on the left, select **Setup** > **Domains**

10. Using the checkbox, select your existing non-Microsoft domain (ex: TomislavK@thephone-company.com) from the current lists of domains.

11. Select the button with **three vertical dots** to open a menu.

12. From the menu, select **Set as default**

13. **Confirm set as default** in the window that appears to set your existing domain as default.
    :::image type="content" source="media/essentials-internalrelay2.png" alt-text="Image of the confirmation dialog for setting domain as default":::

    For more guidance on adding a domain to Microsoft 365, follow the steps described in [Add a domain to Microsoft 365](https://support.office.com/article/add-a-domain-to-office-365-6383f56d-3d09-4dcb-9b41-b5f5a5efd611?ui=en-US&rs=en-US&ad=US).

#### Step Two: Add users and assign Teams Essentials licenses

1. Go to the admin center at <https://admin.microsoft.com> to add an individual user

2. Go to **Users** > **Active users**, and select **Add a user**

3. In the **Set up the basics** pane, fill in the basic user information, then select **Next**.
    - **Name:** Fill in the first and last name, display name, and username.
    - **Domain:** Choose the domain for the user's account. For example, if the user's username is Jakob, and the domain is contoso.com, they'll sign in by using jakob@contoso.com.
    - **Password settings:** Choose to use the autogenerated password or to create your own strong password for the user.  Determine whether you want to send the password in an email when the user is added.

4. In the **Assign product licenses** pane, select the location and the appropriate license for the user. If you don't have any licenses available, you can still add a user and buy more licenses. Select Next.

5. In the **Optional settings** pane, expand **Roles** if you would like to make this user an admin. Expand **Profile info** to add additional information about the user.

6. Select **Next**, review your new user's settings, make any other changes if necessary, then select **Finish adding**, then close.

To add multiple users at the same time, follow the recommend steps at [Add users and assign licenses - Microsoft 365 admin | Microsoft Docs](/microsoft-365/admin/add-users/add-users?view=o365-worldwide&preserve-view=true)

#### Step Three: Configure Google Workspace

***Configure email dual delivery to Microsoft 365 and strip attachments:***

1. Follow Google's steps for setting up dual delivery: <https://support.google.com/a/answer/9228551?hl=en>

2. Add route for Office 365

    - Go the Google Admin console at <https://admin.google.com>)
    - Go to Apps > Google Workspace > Gmail > Hosts.
    - Enter a route name. (For example, Microsoft 365)
    - Choose ‘Single host' and enter the MX record specified for domain in Microsoft 365 (For example:  ContosoLandscaping2-m365master-com.mail.protection.outlook.com)

    **Smart host method to resolve ATTR35 response code when mail is sent to Exchange on premises/Exchange Online :**
    - Choose ‘Single host' and enter the MX record for the initial domain of the tenant as the smart host. The initial domain is in the format GUID.onmicrosoft.com. A GUID is a unique value that's provided to every organization as part of their enrollment in the service. A GUID is a 128-bit integer (16 bytes) that can be used across all computers and networks wherever a unique identifier is required.
    - You can use command line: nslookup -type MX  GUID.onmicrosoft.com to resolve the MX record (For example:  contosolandscaping2.mail.protection.outlook.com)
    - Choose **Port:25**
    - Proceed with recommended options

3. Configure route to Office 365

    - Open the **Google Admin console** at <https://admin.google.com>

    - Go to **Apps** > **Google Workspace** > **Gmail** > **Routing**

    - On the **Routing** tab, select **Configure**

    - Enter **Name** for rule. (For example, Gmail to Office 365)

    - For **email messages to affect**, select both **Inbound** and  **Internal receiving**

    - Under **For the above types of messages**, select **Modify message**

    - Under **Also deliver to**, select **Add more recipients** then select **Add to add the secondary mail route.**

    - Under **Recipients**, select the down arrow "" and select **Advanced.**

    - Select **Change route.**

    - From the list, select the secondary mail route you created earlier

    - Under **Attachments**, select **Remove attachments from message**

    - Scroll down and select **Save**.

***Add your subdomain in Google workspace to receive email from Microsoft 365.***

  Next, you'll create forwarding rules on Microsoft 365 mailboxes to your subdomain. Choose a subdomain to use in Google Workspace to receive email from Microsoft 365 (For example, g.contosolandscaping2.m365master.com)

1. Start at **Google Admin console** (at admin.google.com)

2. Go to **Account** > **Domains** > **Manage Domains**

3. Select **Add a domain**

4. Enter the domain name you selected

5. Select **user alias domain**

6. Select **Add domain & start verification**

7. Wait for verification to complete and refresh the page

8. Select **Activate Gmail**

9. Choose **Skip MX record setup** and then select **NEXT**

10. On the **Route mail to another server** dialog, take note of the server to route mail to (For example, aspmx.l.google.com) and select **I use another mail server**

***Allow email from Microsoft 365 to bypass SPAM filter***

1. Find an appropriate header from the Microsoft 365 tenant by sending an email to a user on Google workspace.

2. Open the message and select **Show Original**

3. Choose an email header that uniquely identifies mail coming from your Microsoft 365 tenant. (For example, X-MS-Exchange-CrossTenant-id: 92f60fc7-eab3-403b-9d7d-9d683bf0a4b5)

4. Go to **Google Admin console** at <https://admin.google.com>

5. Go to **Apps** > **Google Workspace** > **Gmail** > **Compliance**

6. Navigate to **Content Compliance** and select **Configure**

7. Give the setting a name. For example, Allowlist Microsoft 365 email.

8. Under **email messages to affect** check Inbound

9. Under **Add expressions that describe the content you want to search for in each message** select **if ANY of the following match the message**

10. Under **Expressions**, select **Add**
xi. Under **Add setting**, choose **Advanced content match**

11. Under **Location** choose **Full Headers**

12. Under **Match Type** choose **Full Text**

13. Under content, enter the  email header that uniquely identifies email coming from your Microsoft 365 tenant (For example, X-MS-Exchange-CrossTenant-id: 92f60fc7-eab3-403b-9d7d-9d683bf0a4b5)

14. Select **Save**

15. In the **If the above expressions match, do the following** field > **Modify Message** and  check **Bypass spam filter for this message** under **Spam**.

16. Select **Save**

#### Step Four: Configure Microsoft 365 settings for the integration

*Configure connector to route mail from Microsoft 365 to Gmail:*

1. Go to the **Microsoft Admin Center** at <https://admin.microsoft.com/AdminPortal>

2. Select **Show all** in the left-hand navigation menu.

3. Under **Admin centers**, select **Exchange** to open the Exchange admin center in a new tab

4. In the **Exchange admin center**'s left-hand navigation menu, select **Mail flow** > **Connectors**, open the overflow menu (...) and select Add a connector

5. Under **Connection from** in the new connector window, select **Office 365**

6. Under **Connection to** select your organization's email server then select **Next**

7. Enter a **Name** for the new connector (Ex: To Gmail) and continue **Next**

8. In the **Use of Connector** section, select **Only when I have a transport rule set up that redirects messages to this connector** and select **Next**.

9. In the Routing section, enter the appropriate smart mail host (For example, aspmx.l.google.com), select **+**, and then continue **Next**.

10. In the **Security restrictions** section, accept the default settings by selecting **Next**

11. In the **Validation email section**, enter a valid email address for the Gmail system (For example, johannal@g.contosolandscaping2.m365master.com), select the **plus sign (+)**, and then select **Validate**

12. Wait for validation to complete and if successful press Next

13. Under **Review connector**, verify configuration is correct and press Create Connector

14. When you see the Connector created notification, press **Done**

*Forward mail from Microsoft 365 mailboxes to Gmail:*

1. Use the **Microsoft 365 Admin Center** to update each mailbox or you can use a **PowerShell** script, such as the following:

    ```powershell
    $forwardingDomain = "g.contosolandscaping2.m365master.com"
    Connect-ExchangeOnline
    $Mailboxes = Get-Mailbox -ResultSize Unlimited -Filter {RecipientTypeDetails -eq "UserMailbox"}
    Foreach ($mbx in $mailboxes) {

    Set-Mailbox $mbx.Identity -DeliverToMailboxAndForward $true -ForwardingSMTPAddress $($mbx.Alias,$forwardingDomain -join "@")
    }
    ```

    **Troubleshooting Connect-ExchangeOnline:**

    Are you experiencing an error when running Connect-ExchangeOnline? This could be the result of your organization's automatic email forwarding rule. By default, automatic forwarding is disabled. In order to connect Teams Essentials to Google Workspace, the rule must be enabled.

    Enter the following script:

   ```powershell
    Set-ExecutionPolicy Unrestricted
     ```

    Afterwards, run the following commands:

    ```powershell
    Enable-OrganizationCustomization
    Get-HostOutboundSpamFilterPolicy | set-HostedOutboundSpamFilterPolicy -AutoForwardingMode On
    ```

*Configure Exchange Online direct to calendar transport rule:*

1. Configuring this setting will automatically accept calendar invites so that they show up in Teams calendar without requiring users to interact with the invite in Outlook Web App.

2. The following script can be used to create the transport rules:

    ```powershell
    Connect-ExchangeOnline
    New-TransportRule -Name "Direct to Calendar" -MessageTypeMatches Calendaring -SetHeaderName "X-MS-Exchange-Organization-CalendarBooking-Response" -SetHeaderValue Tentative
    New-TransportRule -Name "Direct to Calendar triage action" -MessageTypeMatches Calendaring -SetHeaderName "X-MS-Exchange-Organization-CalendarBooking-TriageAction" -SetHeaderValue MoveToDeletedItems

    ```

*Disable Outlook on the web for mailboxes:*

1. Follow the instructions at [Enable or disable Outlook on the web for a mailbox in Exchange Online](/exchange/recipients-in-exchange-online/manage-user-mailboxes/enable-or-disable-outlook-web-app) to disable Outlook on the web for mailboxes.

2. You can disable Outlook on the web using the **Exchange Admin Center** or **PowerShell**. You may use the following PowerShell example to disable Outlook on the web for all mailboxes:

    ```powershell
    Connect-ExchangeOnline
    $Mailboxes = Get-Mailbox -ResultSize Unlimited -Filter {RecipientTypeDetails -eq "UserMailbox"}
    Foreach ($mbx in $mailboxes) {
    Set-CASMailbox $mbx.Identity -OWAEnabled $false
    }
    ```

#### Step Five: Configure Exchange Online domain for internal relay

This step ensures that email is sent to third-party system for final resolution.

1. Go to the **Microsoft Admin Center** at <https://admin.microsoft.com/AdminPortal>

2. In left-hand navigation, select **Show all**

3. Under **Admin Centers**, select **Exchange** to open Exchange admin center in a new tab

4. In **Exchange admin center**, select **Mail flow** from the left-hand navigation menu, then select **Accepted domains**

5. Tap on the domain name configured in the third-party system (For example, contosoLandscaping2.m365master.com)

    :::image type="content" source="media/essentials-internalrelay1.png" alt-text="Image showing the Exchange admin center settings for Mail flow. ":::

6. Select **Internal Relay**, then click **Save**

    :::image type="content" source="media/essentials-internalrelay2.png" alt-text="Image showing the act of saving internal relay setting.":::

#### Step Six: Create a rule to delete all inbound mail to Exchange Online except for Calendaring

1. You can configure this rule in the **Exchange Admin Center** or **PowerShell**. You may use the following **PowerShell** example to create the rule:

    ```powershell
    Connect-ExchangeOnline
    New-TransportRule -Name "Delete all except Calendaring" -ExceptIfMessageTypeMatches Calendaring -FromScope NotInOrganization -DeleteMessage:$true
    ```

### Connect Teams Essentials to third-party email not using vanity domain (Gmail example)

You can schedule and join a Teams meeting directly from Google Workspace by connecting a consumer Gmail account to Teams Essentials with primary reliance on the [Teams G Suite Add On](https://support.microsoft.com/office/install-the-teams-meeting-add-on-for-google-workspace-bba2dfbe-0b2b-4ee7-be10-261ad80ddb60). This gives you the opportunity to schedule video and audio conferencing with screen sharing, meeting chat, digital whiteboards, and more.

You will configure Gmail to pull email from Exchange Online to ensure mail generated in Microsoft 365 and Teams arrive successfully in Gmail. Security defaults may need to be disabled to accomplish this connection, which makes using a strong unique password essential. A custom domain isn't required for this scenario, but it can be configured in Microsoft 365 for use in Gmail if you'd like to use one.

:::image type="content" source="media/essentials-gmail.png" alt-text="Image depiciting the mail flow between Teams Essentials and Gmail":::

#### 1. Ensure that you have a Gmail account set up

If you already have an existing account, you can proceed to the next step. If not, visit [Create new Google account](https://accounts.google.com/SignUp?hl=en) to set up a new Gmail account.

#### 2. Set up your Microsoft 365 tenant

*Configure Teams AAD users:*

1. Follow the guidance at[Add users and assign licenses](/microsoft-365/admin/add-users/add-users?view=o365-worldwide&preserve-view=true) to add multiple users

*Configure identity protection:*

1. Disable Security defaults if active.

2. Configure multifactor authentication for users

3. If using conditional access, be sure to make exception for POP access to mailbox

*Add domain to Microsoft 365 Admin Center (optional):*

1. Under navigation, select Settings > Domain, then select Add domain

2. Enter your domain name in the appropriate field

3. Follow the instructions on screen to verify your domain with TXT record

4. When prompted, allow Microsoft to configure DNS

5. Complete the instructions to verify MX record route to Microsoft 365

6. Configure SPF TXT record to include Microsoft 365

7. Complete the instructions for configuring DKIM TXT records for Microsoft 365

8. Verify DKIM is enabled by logging out and signing back into the Admin center

#### 3. Configure Gmail

1. Configure Gmail to pull Exchange Online mail into its system

2. Configure the Teams Calendar add-in

3. Enable Gmail to use business domain (optional)
