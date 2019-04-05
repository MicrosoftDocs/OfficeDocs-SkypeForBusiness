---
title: "Install Moodle integration with Microsoft Teams"
author: MicrosoftHeidi
ms.author: heidip
manager: serdars
ms.date: 01/30/2019
ms.topic: article
ms.service: msteams
ms.reviewer: 
search.appverid: MET150
description: "Learn how to install and configure the Moodle integration app for Microsoft Teams."
keywords: Teams Moodle app integration plugin
localization_priority: Normal
MS.collection: Teams_ITAdmin_Help
appliesto: Microsoft Teams
---


# Install Moodle integration with Microsoft Teams

> [!VIDEO https://www.youtube.com/embed/OHlPt22nKoE]

[Moodle](https://moodle.org/), the most popular and open source Learning Management System (LMS) in the world, is now integrated with Microsoft Teams! This integration helps educators and teachers collaborate around Moodle courses, ask questions about their grades and assignments, and stay updated with notifications -- right within Teams!

To help IT admins easily set up this integration, we have updated our open source Office 365 Moodle Plugin with the following capabilities:

- Auto-registration of your Moodle server with Azure AD.
- One-click deployment of your Moodle Assistant bot to Azure.
- Auto-provisioning of teams and auto-synchronization of team enrollments for all or select Moodle courses.
- Auto-installation of the Moodle tab and the Moodle Assistant bot into each synchronized team. (Coming soon)
- One-click publishing of the Moodle app into your private Teams App Store. (Coming soon)

## Prerequisites

To install and configure this application you'll need:

- Moodle administrator credentials
- Azure AD administrator credentials
- An Azure subscription that you can create new resources in

## Step 1: Install the Office 365 Moodle Plugin

> [!VIDEO https://www.youtube.com/embed/SETEC5nzMgk]

The Moodle integration in Microsoft Teams is powered by the open source [Office 365 Moodle plugin](https://github.com/Microsoft/o365-moodle). To install the plugin on your Moodle server:

1. Download the [Office 365 plugin set](https://moodle.org/plugins/pluginversions.php?plugin=local_o365) and save it on your local computer. You'll need to use version 3.5 or newer.
2. Log on to your Moodle server as an administrator, and select **Site administration** from the left navigation pane.
3. Select the **Plugins** tab, and then click **Install plugins**.
4. Under the **Install plugin from ZIP file** section click the **Choose a file** button.
5. Select the **Upload a file** options from the left navigation pane, browse for the file you downloaded above, and click **Upload this file**.
6. Select the **Site administration** option from the left navigation pane again to return to your admin dashboard. Scroll down to the **Local plugins** and click the **Microsoft Office 365 Integration** link. Keep this configuration page open in a separate browser tab: you'll be using it throughout the rest of this process.

You can find more information on how to install Moodle plugins in the [Moodle documentation](https://docs.moodle.org/34/en/Installing_plugins).

> [!IMPORTANT]
> Keep your Office 365 Moodle plugin configuration page open in a separate browser tab: you'll be returning to this set of pages throughout this process.

*Don't have a Moodle site already?* You might want to check out our Moodle on Azure [repo](https://github.com/azure/moodle) where you can quickly deploy a Moodle instance on Azure and customize it to your needs.

## Step 2: Configure the connection between the Office 365 plugin and Azure Active Directory

> [!VIDEO https://www.youtube.com/embed/FpGEezaJ3SA]

Next you'll need to register Moodle as an application in your Azure Active Directory (Azure AD). We've provided a PowerShell script to help you complete this process. The PowerShell Script provisions a new Azure AD application for your Office 365 tenant, which will be used by the Office 365 Moodle plugin. The script will provision the app for your O365 tenant, set up all the required Reply URLs and permissions for the provisioned app, and return the AppID and Key. You can use the generated AppID and Key in your O365 Moodle plugin setup Page to configure your Moodle server with Azure AD. If you want to see the detailed manual steps that the PowerShell script is automating, you can find them in the full [documentation for the plugin](https://docs.moodle.org/34/en/Office365#Register_your_Moodle_instance_as_an_Application).

1. On the Microsoft Office 365 Integration plugin page, select the **Setup** tab.
2. Click the **Download PowerShell Script** button, and save the script on your local computer.
3. You'll need to prepare the PowerShell script from the ZIP file. To do this:
    1. Download and extract the Moodle-AzureAD-Powershell.zip file.
    2. Open the extracted folder.
    3. Right-click the Moodle-AzureAD-Script.ps1 file, and select **Properties**.
    4. On the **General** tab of the Properties window, check the **Unblock** box next to the **Security** attribute at the bottom.
    5. Click **OK**.
    6. Copy the directory path of the extracted folder.
4. Next you'll run PowerShell as an administrator:
    1. Click Start.
    2. Type **PowerShell**.
    3. Right-click **Windows PowerShell**.
    4. Click **Run as Administrator**.
5. Navigate to the unzipped directory by typing `cd ...\...\Moodle-AzureAD-Powershell` where `...\...` is the path to the directory.
6. Execute the PowerShell script:
    1. Enter `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser`.
    2. Enter `.\Moodle-AzureAD-Script.ps1`.
    3. Sign in to your O365 Adminstrator account in the pop-up window.
    4. Enter the name of the Azure AD application (for example, **Moodle/Moodle plugin**).
    5. Enter the URL of your Moodle server.
    6. Copy the **Application ID** and **Application Key** generated by the script, and save them.
7. Next you'll need to add the ID and key to the Office 365 Moodle plugin. Return to the plugin administration page (**Site administration** > **Plugins** > **Microsoft Office 365 Integration**).
8. On the **Setup** tab add the **Application ID** and **Application Key** you copied previously, and then click **Save changes**.
9. Once the page refreshes you should see a new section called **Choose connection method**. Click the check box labeled **Default**, and then click **Save changes**.
10. When the page refreshes you'll see a new section called **Admin consent & additional information**.
    1. Click the **Provide Admin Consent** link, enter your Office3 365 Global Administrator credentials, and then click **Accept** to grant the permissions.
    2. Next to the **Azure AD Tenant** field, click the **Detect** button.
    3. Next to **OneDrive for Business URL**, click the **Detect** button.
    4. Once the fields populate, click the **Save changes** button.
11. Click the **Update** button to verify the installation, and then click **Save changes**.
12. Next you'll need to synchronize users between your Moodle server and Azure AD. Depending on your environment, you may select different options during this stage. Note that the configuration you set here will run with each Moodle cron run (typically once a day) to keep everything in sync. To get started:
    1. Switch to the **Sync Settings tab**
    2. In the **Sync users with Azure AD** section, select the checkboxes that apply to your environment. Typically you would select at least:
        - **Create accounts in Moodle for users in Azure AD**
        - **Update all accounts in Moodle for users in Azure AD**
    3. In the **User Creation Restriction** section you can set up a filter to limit the Azure AD users that will be synced to Moodle.
    4. The **User Field Mapping** section will allow you to customize the Azure AD to Moodle User Profile field mapping.
    5. In the **Teams Sync** section you can choose to automatically create groups (that is, teams) for some or all of your existing Moodle courses.
13. To validate the cron jobs (and run them manually if you wish to for the first run), click the **Scheduled tasks management page** link in the **Sync users with Azure AD** section. This will take you to the **Scheduled Tasks** page.
    1. Scroll down and find the job **Sync users with Azure AD** job and click **Run now**.
    2. If you chose to create groups based on existing courses, you can also run the **Create user groups in Office 365** job.
14. Return to the plugin administration page (**Site administration** > **Plugins** > **Microsoft Office 365 Integration**) and select the **Teams Settings** page. You'll need to configure some security settings to enable the Teams app integration.
    1. To enable OpenID Connect, click the **Manage Authentication** link, and click the eye icon on the **OpenId Connect** line if it is dimmed.
    2. To enable frame embedding, click the **HTTP Security** link, and then select the check box next to **Allow frame embedding**.
    3. Enable web services (which will enable the Moodle API features). Click the **Advanced Features** link, and then make sure the check box next to **Enable web services** is selected.
    4. Enable the external services for Office 365. Click the **External services** link, and then:
        1. Click **Edit** on the **Moodle Office 365 Webservices** row.
        2. Select the check box next to **Enabled**, and then click **Save Changes**
    5. Finally, you need to edit your authenticated user permissions to allow users to create web service tokens. Click the **Editing role Authenticated user** link. Scroll down and find the **Create a web service token** capability, and select the **Allow** check box.

## Step 3: Deploy the Moodle Assistant Bot to Azure

> [!VIDEO https://www.youtube.com/embed/gbkJxf8FlfY]

The Moodle Assistant Bot for Microsoft Teams helps teachers and students answer questions about their courses, assignments, grades, and other information in Moodle. The bot also sends Moodle notifications to students and teachers right within Teams. This bot is an open source project maintained by Microsoft and is [available on GitHub](https://github.com/microsoft/Moodle-Teams-Bot).

First, you'll need to register your bot on the [Microsoft Identity Platform](https://identity.microsoft.com/Landing). This will allow your bot to authenticate with your Microsoft endpoints. To register your bot:

1. Return to the plugin administration page (**Site administration** > **Plugins** > **Microsoft Office 365 Integration**) and select the **Teams Settings** tab.
2. Click the **Microsoft Application Registration Portal** link and login with your Microsoft ID.
3. Enter a name for you app (for example, MoodleBot) and click the **Create** button.
4. Copy the **Application ID** and paste it into the **Bot Application ID** field on the **Team Settings** page.
5. Click the **Generate New Password** button. Copy the generated password and and paste it into the **Bot Application Password** field on the **Team Settings** page.
6. Scroll to the bottom of the form and click **Save Changes**.

Now that you've generated your application ID and password, it's time to deploy your bot to Azure. Click the **Deploy to Azure** button and complete the form with the necessary information (the bot ID and password are on the **Team Settings** page, and the Azure information is on the **Setup** page). Once you've got the form filled out, click the check box to agree to the terms and conditions, and then click the **Purchase** button.

After the resources are finished deploying to Azure, you'll need to configure the Office 365 Moodle plugin with its messaging endpoint. First, you'll need to get the endpoint from your bot in Azure. To do this:

1. If you aren't signed in already, sign in to the [Azure portal](https://portal.azure.com).
2. In the left pane, select **Resource groups**.
3. From the list, select the resource group you just used (or created) while deploying your bot.
4. Select the **WebApp Bot** resource from the list of resources in the group.
5. Copy the **Messaging Endpoint** from the **Overview** section.
6. In Moodle, open the **Team Settings** page of your Office 365 Moodle plugin.
7. In the **Bot Endpoint** field, paste the URL you just copied, and change the word *messages* to *webhook*. The URL should now look like **https://botname.azurewebsites.net/api/webhook**.
8.** Click **Save Changes**.
9. Once your changes are saved, go back to the **Team Settings** tab, click the **Download manifest file** button, and save the manifest package to your computer (you'll use it in the next step).

## Step 4: Deploy your Microsoft Teams app

> [!VIDEO https://www.youtube.com/embed/2rMb7gtM_ZM]

Now that you have your bot deployed in Azure and configured it to talk to your Moodle server, it's time to deploy your Microsoft Teams app. To do this you'll load the manifest file you downloaded from the Office 365 Moodle Plugin **Team Settings** page in the previous step.

Before you can install the app you'll need to make sure that external apps and sideloading of apps is enabled. To do this, follow [these steps](https://docs.microsoft.com/en-us/MicrosoftTeams/admin-settings). Once you've ensured that external apps are enabled, follow the steps below to deploy your app.

1. Open Microsoft Teams.
2. Click the **Store** icon on the lower-left of the navigation bar.
3. Click the **Upload a custom app** link from the list of options. 
   > [!NOTE]
   > If you're signed in as a global administer you'll have the option of uploading the app to your organization's app store; otherwise you'll only be able to load the app for the teams you're a part of ("sideloading").
4. Select the manifest.zip package you downloaded previously, and click **Save**.

Now that you have the app installed, you can add the tab to any channel that you have access to. To do this, navigate to the channel, click the **+** symbol, and select your app from the list. Follow the prompts to finish adding your Moodle course tab to a channel.

That's it! You and your team, can now start working with your Moodle courses directly from Microsoft Teams.