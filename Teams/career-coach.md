---
title: Purchase, configure, and enable Career Coach for Microsoft Teams
author: cichur
ms.author: v-cichur
ms.reviewer: alaina.creager
manager: serdars
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: MET150
description: Learn how to purchase, configure, and enable Career Coach for Microsoft Teams.
localization_priority: Normal
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

# Purchase, configure, and enable Career Coach for Microsoft Teams

Career Coach is a Microsoft Teams for Education app powered by LinkedIn that provides personalized guidance for higher education students to navigate their career journey. Career Coach offers educational institutions a unified career solution for students to discover their career path, grow real-world skills, and build their network all in one place.

## Supported languages
Career Coach is localized in the following languages:

  - Chinese (Simplified, Mainland China)
  - Chinese (Traditional, Taiwan)
  - English (US)
  - English (UK)
  - French (Canada)
  - French (France)
  - German (Deutschland)
  - Japanese (Japan)
  - Portuguese (Brazil)
  - Spanish (Spain)
  - Spanish (Mexico)

Learn more about [Career Coach](https://aka.ms/career-coach).

> [!NOTE]
> Use the best practices and helpful tips in this guide to enable the capabilities of Career Coach for students, faculty, and staff. See the [Quick planning guide](https://support.microsoft.com/office/c5d0b934-bfcf-4fe7-8a85-ba7bbb1b6ad4) article.

## Review the requirements

To enable Career Coach for your educational institution, review what you need to get the app up and running.

**Technical requirements**

  - Office 365 tenant with Azure Active Directory

  - Microsoft Teams

  - LinkedIn account connections in Azure Active Directory

**Licenses**

  - Faculty 

  - Students

> [!NOTE]
> A Career Coach Faculty license must be assigned to the IT admin completing the configuration.

**Data and files from your educational institution**

  - Course catalog data

  - Fields of study offered

  - Educational institution’s LinkedIn page

  - LinkedIn Learning campus subscription (preferred)

## Purchase the Career Coach licenses

Career Coach is available worldwide (except China and Russia) for qualified higher education institutions through Enrollment for Education Solutions (EES), Cloud Service Providers (CSP), and Microsoft 365 admin center (web direct). As a Microsoft Teams app, customers must have Microsoft 365 A3/A5 or Office 365 A1/A3/A5.

### Assign app licenses to users

For step-by-step instructions, see [Assign licenses to users](/microsoft-365/admin/manage/assign-licenses-to-users).

### Turn on LinkedIn account connections

Career Coach **requires** your educational institution’s users to have the ability to connect their Microsoft 365 account to their LinkedIn account that is facilitated within Career Coach

1. Sign in to the [Azure AD admin center](https://aad.portal.azure.com/) with an account that's a global admin for the Azure AD organization.

2. Select **Users**.

3. On the **Users** page, select **User settings**.

4. Under **LinkedIn account connections**, allow users to connect their accounts to access their LinkedIn connections within some Microsoft apps. No data is shared until users consent to connect their accounts.

   - Select **Yes** to enable the service for all users in your educational institution

   - Select **Selected group** to enable the service for only a group of selected users in your educational institution

   - Select **No** to withdraw consent from all users in your educational institution

Learn how to [Integrate LinkedIn account connections in Azure Active Directory](/azure/active-directory/enterprise-users/linkedin-integration)

## Configure Career Coach in the Teams admin center

Using the admin settings in the Microsoft Teams admin center, you can configure Career Coach for your educational institution and enable it for users.

**Things to consider**

- The following sections are required to be complete before Career Coach can be used - Brand and Preferences, LinkedIn 
- CSVs for course catalog and field of study have required formats and a maximum size of 18 MB

- If you're seeing "Career Coach is currently being set up for you to use soon" in the Career Coach app the required sections have not been completed.

- On settings pages with required fields, if the fields are not completed the page will not submit
  - Users will not see a warning message, the page will simply not submit

## Access the Career Coach app settings

Use the [Manage apps page](/microsoftteams/manage-apps) to view the Teams apps in your educational institution’s app catalog.

1. Sign in to the **Teams admin center**.

2. In the left navigation, select **Teams apps** > **Manage apps**.  

    > [!NOTE]
    > You must be a global admin or Teams service admin to access the page.

3. Search or browse for **Career Coach**.  

4. Select **Career Coach**, and then select **Settings.**  

    ![shows the Career Coach app selected with the Settings option showing](media/career-coach-app.png)

### Configure the Career Coach app settings

Career Coach has five configuration categories:

- [Brand and preferences](#brand-and-preferences)

- [LinkedIn configuration](#linkedin-configuration)

- [Course catalog](#course-catalog)

- [Fields of study](#fields-of-study)

- [Customization](#customization)

> [!NOTE]
> Brand and preferences, LinkedIn configuration, Course catalog, and Fields of study are **required** to effectively enable the app for students, faculty, and staff.

#### Brand and preferences

Set your educational institution’s name, logo, and default language on the brand and preferences settings page.

> [!NOTE]
> This is a required section - Career Coach can't be enabled without the Brand and preferences submitted.

![the Career Coach branding section of the admin center](media/career-coach-brand.png)

##### Educational institution icon

The educational institution icon is used throughout Career Coach to identify content unique to your educational institution, course catalog resources throughout the app, and on the real-world experiences section of the dashboard. The icon is best formatted as:

 - A transparent PNG
 - Aspect ratio of 1:1
 - Maximum size of 64 px x 64 px.

##### Educational institution thumbnail

The educational institution icon will be used for course catalog resources throughout the app when a specific image isn't available for a course. The icon is best formatted as:

- A PNG
- Aspect ratio of 16:9
- Maximum size of 360 px x 200 px.

#### LinkedIn connection

The LinkedIn configuration connects Career Coach with public alumni data from LinkedIn.

> [!NOTE]
> This is a required section - Career Coach can't be enabled without the LinkedIn page connection verified.

##### Add and confirm the LinkedIn page

Determine the educational institution's LinkedIn page. Find the LinkedIn page by searching on LinkedIn or connecting with a career services staff member to determine the correct page to use.  
  
1. Sign in to the **Teams admin center**.

1. Select **Teams apps** > **Manage apps** > **Career Coach** > **LinkedIn connection**.

2. Add the LinkedIn school page URL. The URL must be a school page and not a company page and are typically formatted as `https://www.linkedin.com/school/devtest-school/`. [How to identify LinkedIn pages](https://www.linkedin.com/help/linkedin/answer/40133/differences-between-a-linkedin-page-for-a-school-and-company?lang=en).

3. Select **Apply**.

   ![linkedin connections for the career coach app](media/career-coach-linked-in.png)  

4. Copy the verification URL and share it with your educational institution’s LinkedIn page admin [LinkedIn page admin documentation](https://www.linkedin.com/help/linkedin/answer/102672). The verification link expires after 30 days.  

   ![linkedin page verification in the linkedin developer portal](http://placehold.it/650x650?text=Placeholder%20for%20Linked.com%20vertification%20page)


#### Course catalog

The course catalog represents the courses and classes offered to students by your educational institution. 

> [!NOTE]
> This is a required section - Career Coach can't be enabled without a course catalog.

These courses are used within the app in two areas:

- Courses are returned as part of learning resources.  

- Courses and course meta data, like descriptions, are used to help students identify their skills when they upload a transcript.  

To create the course catalog, put together a list of all courses taught at your educational institution and upload it as a CSV file. The app draws from the course catalog to identify a student’s skills from their transcript and to suggest courses to take. 

##### Course catalog documents formatting and schema

The document needs to be in CSV format with a maximum size of 18 MB. The document must contain the required fields **course title**, **course ID**, and **course URL**. Including the recommended fields improves the experience for students by returning better search results and skill identification.

> [!NOTE]
> Start with the [sample course catalog]( https://aka.ms/career-coach/docs/it-admins/sample-catalog) document to get started.

The following table shows the items to include in the course catalog:


| Name             | Status      | Type   | Description                                                                    |
|------------------|-------------|--------|--------------------------------------------------------------------------------|
| courseId         | Required    | string | Usually the course id (Typically maps to what is generated in the transcript). |
| title            | Required    | string | Usually the course title.                                                      |
| sourceLink       | Required    | URL    | Website link to the course page.                                               |
| description      | Recommended | string | Introduction text for the course.                                              |
| language         | Recommended | string | Language of the course. Use standard language codes.                           |
| format           | Recommended | string | Mode of teaching, e.g., online, video, in-person.                              |
| thumbnailLink    | Recommended | URL    | Thumbnail link to the course image.                                            |
| thumbnailAltText | Recommended | string | Accessibility alt text for the image                                           |
| educationLevel   | Recommended | string | Study level, ex. Undergraduate/Graduate.                                       |
| topics           | Recommended | string | Topics or tags that are associated with the skills the courses teach.          |

##### Add the course catalog

1. Sign in to the **Teams admin center**.

1. Select **Teams apps** &gt; **Manage apps** &gt; **Career Coach** &gt; **Settings** &gt;  **Course catalog**.

2. Upload courses in CSV format with the required columns: courseId, title, sourceLink. Each row must be include data for each of the required columns.

Including the recommended fields improves the experience for students by returning better search results and skill identification.

4. Select **Apply**.

   ![the course catalog section of the career coach app](media/course-catalog.png)

#### Fields of study

The fields of study are synonymous with major areas of interest, academic major, and degree. These titles are referenced by students when they start using the app and begin setting up their personalized profile.

> [!NOTE]
> This is a required section - Career Coach can't be enabled without a list of fields of study.

Add all fields of study available to students such as Engineering, English, Business, and so on. The list of fields lets students discover fields of study that may interest them and add their area of focus to their profile.

> [!NOTE]
> Start with the [sample field of study](https://aka.ms/career-coach/docs/it-admins/sample-fieldsofstudy) document.

The following table shows the items to include in the fields of study:


| Name          | Status   | Type   | Description                    |
|---------------|----------|--------|--------------------------------|
| fieldsOfStudy | Required | string | The name of the field of study |

##### Add the fields of study

1. Sign in to the **Teams admin center**.
1. Select **Teams apps** &gt; **Manage apps** &gt; **Career Coach** &gt; **Settings** &gt;  **Fields of study**.

2. Upload field of study in CSV format.

3. Select **Apply**.

#### Customization

Career Coach can be customized to be unique to your educational institution. The customization supports adding experiences to the dashboard. It's recommended to add links to job boards, events, career services office, career-related events, student clubs, and any other resources that help students gain real-world experience.

##### Add customized experiences

1. Sign in to the **Teams admin center**.

1. Select **Teams apps** &gt; **Manage apps** &gt; **Career Coach** > **Settings** &gt; **Customization**.

2. Add each URL, a title, and short description.  
  
3. Select **Apply**.

## Making Career Coach available to your organization

Now that Career Coach has been configured for your organization. Follow these steps to ensure that Career Coach is available to organization in Microsoft Teams.

### Enable the app

After you complete the configuration, enable the app for students and licensed users so they'll have access to Career Coach.  
  
> [!NOTE]
> You must have Global or Teams admin role permissions.

1. Sign in to the **Teams admin center**.

1. Select **Teams apps** &gt; **Manage apps** &gt; **Career Coach**.

2. Move the Status toggle to **Allowed**.  

  > [!NOTE]
  > Allowed means that the app is available for users in your educational institution. Blocked means that the app isn't available to students.

### Add Career Coach as an installed app

> [!NOTE]
> This step ensures 1) that Career Coach is properly configured for your organization 2) that students find Career Coach.

1. Sign in to the **Teams admin center**.

2. Select **Teams apps** &gt;**Setup policies** &gt; *Your policy*. 

3. Under Installed apps, select Add apps.

4. In the Add installed apps pane, search for the apps you want to automatically install for users when they start Teams. You can also filter apps by app permission policy. When you've chosen your list of apps, select Add.

### Pin the app

Pinning Career Coach will make the app more accessible and visible for students.

1. Sign in to the **Teams admin center**.

2. Select **Teams apps** &gt;**Setup policies** &gt; *Your policy*. 

3. Under **Pinned apps**, choose **Add apps**.

4. Search for **Career Coach**, and then select **Add**.

5. Choose the order for the app to appear and select **Save**.

> [!NOTE]
> Students will be notified in Microsoft Teams that Career Coach has been pinned.

Reference [Manage app setup policies in Microsoft](/microsoftteams/teams-app-setup-policies) for additional details.

## Resources

The following resources will help you plan your Career Coach app.

- [Welcome to Microsoft Teams](Teams-overview.md)

- [How to roll out Teams](get-started-with-teams-resources-for-org-wide-rollout.md?tabs=SmallBusiness)

- [Overview of teams and channels in Microsoft Teams](teams-channels-overview.md)

- [Managing apps in Microsoft Teams Admin Center](manage-apps.md)

- [Online Virtual Orientation Kit](https://www.microsoft.com/education/remote-learning/virtual-orientation) 

- [Limits and specification of Teams channels](limits-specifications-teams.md)

- [Getting started with admin training for Microsoft Teams](ITAdmin-readiness.md)

- [Teams troubleshooting](/microsoftteams/troubleshoot/teams-welcome)

- [Manage app permission policies in Microsoft Teams](teams-app-permission-policies.md)
