---
title: Purchase, configure, and enable Career Coach for Microsoft Teams
author: HowlinWolf-92
ms.author: v-mahoffman
ms.reviewer: alaina.creager
manager: serdars
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: MET150
description: Learn how to purchase, configure, and enable Career Coach for Microsoft Teams.
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

# Purchase, configure, and enable Career Coach for Microsoft Teams

Career Coach is a Microsoft Teams for Education app powered by LinkedIn that provides personalized guidance for higher education students to navigate their career journey. Career Coach offers educational institutions a unified career solution for students to discover their career path, grow real-world skills, and build their network all in one place.

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

> [!TIP]
> Use the best practices and helpful tips in this guide to enable the capabilities of Career Coach for students, faculty, and staff. See the [Quick planning guide](https://support.microsoft.com/office/c5d0b934-bfcf-4fe7-8a85-ba7bbb1b6ad4) article.

## Review the requirements

To enable Career Coach for your educational institution, review what you need to get the app up and running.

**Technical requirements**

- Office 365 tenant with Azure Active Directory.

- Microsoft Teams.

- LinkedIn account connections in Azure Active Directory.

**Licenses**

- Faculty

- Students

> [!IMPORTANT]
> A Career Coach Faculty license must be assigned to the IT admin completing the configuration.

**Data and files from your educational institution**

- Educational institution's logo and graphical assets in the required format.

- Course catalog data.

- List of fields of study offered.

- Educational institution’s [LinkedIn page](https://www.linkedin.com/help/linkedin/answer/40133/differences-between-a-linkedin-page-for-a-school-and-company?lang=en).

- Educational institution's privacy policy URL.

- Educational institution links to career-related resources such as career services and student job postings (optional).

- LinkedIn Learning campus subscription (preferred).

## Purchase the Career Coach licenses

Career Coach is available worldwide (except China and Russia) for qualified higher education institutions as an add-on license through Enrollment for Education Solutions (EES), Cloud Service Providers (CSP), and Microsoft 365 admin center (web direct). As a Microsoft Teams app, the tenant must have Microsoft 365 A3/A5 or Office 365 A1/A3/A5 in order to purchase the add-on Career Coach license. Separate licenses are offered for students and faculty/staff users.

A standard 90-day free trial is available for 25 student and 25 faculty/staff licenses. Trial licenses can be activated from Microsoft 365 admin center by tenants who are qualified to purchase Career Coach.

### Assign app licenses to users

For step-by-step instructions, see [Assign licenses to users](/microsoft-365/admin/manage/assign-licenses-to-users).

### Turn on LinkedIn account connections

Career Coach **requires** your educational institution’s users to have the ability to connect their Microsoft 365 account to their LinkedIn account that is facilitated within Career Coach.

1. Sign in to the [Azure AD admin center](https://aad.portal.azure.com/) with an account that's a global admin for the Azure AD organization.

2. Select **Users**.

3. On the **Users** page, select **User settings**.

4. **LinkedIn account connections** must be set to **Yes** or **Selected group** for Career Coach to be properly configured.

   ![Integrate LinkedIn account connections in the organization](/azure/active-directory/enterprise-users/media/linkedin-integration/linkedin-integration.png)

   > [!NOTE]
   > No data is shared until users consent to connect their accounts.

   - Select **Yes** to enable the service for all users in your educational institution.

   - Select **Selected group** to enable the service for only a group of selected users in your educational institution.

For more information, see [LinkedIn account connections in Azure Active Directory](/azure/active-directory/enterprise-users/linkedin-integration).

## Access the Career Coach app settings

Use Microsoft Teams admin center to configure Career Coach for your educational institution and enable it for users.

> [!IMPORTANT]
> You must be a global admin or Teams service admin to access the page.

1. Sign in to the **[Teams admin center](https://admin.teams.microsoft.com)**.

2. In the left navigation, select **Teams apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)**.  

3. Search or browse for **Career Coach**.  

4. Select **Career Coach**, and then select **Settings**.  

    ![shows the Career Coach app selected with the Settings option showing.](media/career-coach-app.png)

## Configure the Career Coach app settings

Career Coach has five configuration categories:

- [Brand and preferences](#brand-and-preferences) - required

- [LinkedIn connection](#linkedin-connection) - required

- [Course catalog](#course-catalog) - required

- [Fields of study](#fields-of-study) - required

- [Customization](#customization)

> [!IMPORTANT]
> Brand and preferences, LinkedIn configuration, Course catalog, and Fields of study are __required__ to effectively enable the app for students, faculty, and staff.

### Brand and preferences

Customize Career Coach to match your educational institution’s brand. You are responsible for respecting others' rights, including copyright and trademark rights.

> [!IMPORTANT]
> This is a required section - Career Coach can not be enabled without the Brand and preferences submitted.

![the Career Coach branding section of the admin center.](media/career-coach-brand.png)

1. Sign in to the **[Teams admin center](https://admin.teams.microsoft.com)**.

2. Select **Teams apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)** > **Career Coach** > **Brand and preferences**.

3. Upload the **educational institution icon**. The icon is used throughout Career Coach to identify content unique to your educational institution, course catalog resources throughout the app, and on the real-world experiences section of the dashboard. The icon is best formatted as:

    - A transparent PNG
    - Aspect ratio of 1:1
    - Maximum size of 64 px x 64 px

4. Upload the **educational institution thumbnail**. The thumbnail will be used for course catalog resources throughout the app when a specific image isn't available for a course. The thumbnail is best formatted as:

    - A PNG
    - Aspect ratio of 16:9
    - Maximum size of 360 px x 200 px

5. Add the **educational institution's privacy policy URL**. If added, the institution's privacy policy will be available for students to review in the Career Coach app.

6. Select **Submit**.

### LinkedIn connection

The LinkedIn configuration connects Career Coach with public alumni data from LinkedIn.

> [!IMPORTANT]
> This is a required section - Career Coach can not be enabled without the LinkedIn page connection verified.

#### Add the LinkedIn page
  
1. Sign in to the **[Teams admin center](https://admin.teams.microsoft.com)**.

2. Select **Teams apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)** > **Career Coach** > **LinkedIn connection**.

3. Find the LinkedIn page by searching on LinkedIn and selecting the **School** filter. Or connect with a career services staff member to determine the correct LinkedIn school page to use. For more information, see [How to identify LinkedIn pages](https://www.linkedin.com/help/linkedin/answer/40133/differences-between-a-linkedin-page-for-a-school-and-company?lang=en).

    ![linkedin search for school.](media/career-coach-school-search.png)

4. Add the LinkedIn school page URL. The URL must be a school page and not a company page and are typically formatted as `https://www.linkedin.com/school/willow-university/`.

   ![linkedin school page example.](media/career-coach-linkedin-page-url.png)

5. Select **Submit**.
#### Verify the LinkedIn page 

> [!IMPORTANT]
> The verification must be completed by your educational institution’s LinkedIn page super admin.

1. If successfully submitted, the page will be updated to show the **Verification link** and **Verification link expiration**. The verification link expires after 30 days.

   ![linkedin connections for the career coach app.](media/career-coach-linked-in.png)  

2. Copy the verification link and share it with your educational institution’s LinkedIn page super admin. Learn more about the LinkedIn page super admin role in the [LinkedIn page admin documentation](https://www.linkedin.com/help/linkedin/answer/102672).

3. The LinkedIn page super admin will use the unique verification link to associate Career Coach with your school's page. See [Additional documentation about LinkedIn page verification](https://www.linkedin.com/help/linkedin/answer/102672) for more information.

   ![linkedin page verification in the linkedin developer portal.](media/career-coach-linkedin-verification.png)

### Course catalog

The course catalog represents the courses and classes offered to students by your educational institution.

> [!IMPORTANT]
> This is a required section - Career Coach can not be enabled without a course catalog.

These courses are used within the app in two areas:

- Courses are returned as part of learning resources.  

- Courses and course meta data, like descriptions, are used to help students identify their skills when they upload a transcript.  

To create the course catalog, put together a list of all courses taught at your educational institution and upload it as a CSV file. The app draws from the course catalog to identify a student’s skills from their transcript and to suggest courses to take.

#### Add the course catalog

1. Sign in to the **[Teams admin center](https://admin.teams.microsoft.com)**.

1. Select **Teams apps** &gt; **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)** &gt; **Career Coach** &gt; **Settings** &gt;  **Course catalog**.

2. Upload courses in CSV format with the required columns: courseId, title, and sourceLink. Each row must include data for each of the required columns. _Including the recommended fields improves the experience for students by returning better search results and skill identification._

4. Select **Submit**.

   ![the course catalog section of the career coach app.](media/course-catalog.png)

#### Course catalog document format and schema

The document needs to be in CSV format with a maximum size of 18 MB. The document must contain the required fields **course title**, **course ID**, and **course URL**. 

> [!TIP]
> Start with the [sample course catalog]( https://aka.ms/career-coach/docs/it-admins/sample-catalog) document to ensure proper formatting. _Including the recommended fields improves the experience for students by returning better search results and skill identification._

The following table shows the items to include in the course catalog:

| Name             | Status      | Type   | Description                                                                    |
|------------------|-------------|--------|--------------------------------------------------------------------------------|
| courseId         | Required    | string | Usually the course id (Typically maps to what is generated in the transcript). |
| title            | Required    | string | Usually the course title.                                                      |
| sourceLink       | Required    | URL    | Website link to the course page.                                               |
| description      | Recommended | string | Introduction text for the course.                                              |
| language         | Recommended | string | Language of the course. Use standard language codes.                           |
| format           | Recommended | string | Mode of teaching (online, video, in person).                                   |
| thumbnailLink    | Recommended | URL    | Thumbnail link to the course image.                                            |
| thumbnailAltText | Recommended | string | Accessibility alt text for the image                                           |
| educationLevel   | Recommended | string | Study level, ex. Undergraduate/Graduate.                                       |
| topics           | Recommended | string | Topics or tags that are associated with the skills the courses teach.          |

### Fields of study

The fields of study are synonymous with major areas of interest, academic major, and degree. These titles are referenced by students when they start using the app and begin setting up their personalized profile.

> [!IMPORTANT]
> This is a required section - Career Coach can not be enabled without a list of fields of study.

#### Add the fields of study

1. Sign in to the **[Teams admin center](https://admin.teams.microsoft.com)**.
1. Select **Teams apps** &gt; **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)** &gt; **Career Coach** &gt; **Settings** &gt;  **Fields of study**.

2. Upload field of study in CSV format.

3. Select **Submit**.

#### Fields of study document format and schema

Add all fields of study available to students such as Engineering, English, Business, and so on. The list of fields lets students discover fields of study that may interest them and add their area of focus to their profile.

> [!TIP]
> Start with the [sample field of study](https://aka.ms/career-coach/docs/it-admins/sample-fieldsofstudy) document to ensure proper formatting.

The following table shows the items to include in the fields of study:

| Name          | Status   | Type   | Description                    |
|---------------|----------|--------|--------------------------------|
| fieldsOfStudy | Required | string | The name of the field of study |

### Customization

Career Coach can be customized to be unique to your educational institution. The customization supports adding experiences to the dashboard. It's recommended to add links to job boards, events, career services office, career-related events, student clubs, and any other resources that help students gain real-world experience.

#### Add customized experiences

1. Sign in to the **[Teams admin center](https://admin.teams.microsoft.com)**.

1. Select **Teams apps** &gt; **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)** &gt; **Career Coach** > **Settings** &gt; **Customization**.

2. Add each title, URL, and short description.  
  
3. Select **Submit**.

## Making Career Coach available to your organization

Now that Career Coach has been configured for your organization. Follow these steps to ensure that Career Coach is available to organization in Microsoft Teams.

### Enable the app

After you complete the configuration, enable the app for students and licensed users so they'll have access to Career Coach.  
  
> [!IMPORTANT]
> You must have Global or Teams admin role permissions.

1. Sign in to the **[Teams admin center](https://admin.teams.microsoft.com)**.

1. Select **Teams apps** &gt; **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)** &gt; **Career Coach**.

2. Move the Status toggle to **Allowed**.  

   > [!NOTE]
   > **Allowed** means that the app is available for users in your educational institution. Blocked means that the app isn't available to students.

### Add Career Coach as an installed app

> [!IMPORTANT]
> This step ensures that Career Coach is properly configured for your organization and that students find Career Coach.

1. Sign in to the **[Teams admin center](https://admin.teams.microsoft.com)**.

2. Select **Teams apps** &gt; **Setup policies** and select your preferred policy.
If you are unsure which policy to use you can refer to the [Microsoft Teams Policy management documentation](/microsoftteams/policy-packages-edu) or utilize the [Education Policy Wizard](/microsoftteams/easy-policy-setup-edu?tabs=students%2Cstudent-settings) to configure a policy for Microsoft Teams.

3. Under Installed apps, select **Add apps**.

4. In the Add installed apps pane, search for the apps you want to automatically install for users when they start Teams. You can also filter apps by app permission policy. When you've chosen your list of apps, select **Add**.

5. Select **Save**.

> [!NOTE]
> Editing or assigning a policy can take a few hours for changes to take effect. The Career Coach app will not be available in Microsoft Teams until the changes are complete.

### Pin the app

Pinning Career Coach will make the app more accessible and visible for students.

1. Sign in to the **[Teams admin center](https://admin.teams.microsoft.com)**.

2. Select **Teams apps** &gt; **Setup policies** and select your preferred policy.
If you are unsure which policy to use you can refer to the [Microsoft Teams Policy management documentation](/microsoftteams/policy-packages-edu) or utilize the [Education Policy Wizard](/microsoftteams/easy-policy-setup-edu?tabs=students%2Cstudent-settings) to configure a policy for Microsoft Teams.

3. Under **Pinned apps**, choose **Add apps**.

4. Search for **Career Coach**, and then select **Add**.

5. Choose the order for the app to appear and select **Save**.

> [!NOTE]
> Students will be notified in Microsoft Teams that Career Coach has been pinned.

Reference [Manage app setup policies in Microsoft](/microsoftteams/teams-app-setup-policies) for more details.

## Career Coach settings status

The Career Coach settings page in Teams Admin Center provides a status report of incomplete, pending, complete, and failed steps for configuring the app. These statuses can help you determine whether Career Coach is properly configured and ready to release to your tenant.

### Configuration status

The configuration status section of the app settings page will display the current status.

![the configuration status section of the career coach app.](media/career-coach-config-status.png)

| Category              | Status                    | Description                                                 |
| --------------------- | ------------------------- | ----------------------------------------------------------- |
| Service provisioning  | Pending                   | App is being added to the tenant. No further action needed. |
| Service provisioning  | Complete                  | Ready for IT admin to submit settings.                      |
| Brand and preferences | Not started               | Settings need to be submitted.                              |
| Brand and preferences | Missing _required fields_ | IT admin needs to add or upload the missing fields.         |
| Brand and preferences | Complete                  | No further action needed.                                   |
| Course catalog        | Not started               | Catalog needs to be submitted.                              |
| Course catalog        | Incomplete                | Check the ingestion status for details on how to resolve.   |
| Course catalog        | Complete                  | No further action needed.                                   |
| LinkedIn connection   | Not started               | LinkedIn school page URL needs to be submitted.             |
| LinkedIn connection   | Pending                   | Awaiting LinkedIn school page admin approval.               |
| LinkedIn connection   | Complete                  | No further action needed.                                   |
| Fields of study       | Not started               | Document needs to be submitted.                             |
| Fields of study       | Complete                  | No further action needed.                                   |

> [!NOTE]
> Once all steps are marked as complete the app can be successfully released to your tenant and assign Career Coach licenses. For step-by-step instructions, see [Assign licenses to users](/microsoft-365/admin/manage/assign-licenses-to-users?view=o365-worldwide).

### Course catalog status

The course catalog status is shown on the Course catalog settings page once a document has been uploaded, providing details of the document upload and processing.


![the course catalog upload status of the career coach app.](media/career-coach-course-catalog-status.png)

| Column           | Value     | Description                                                                                        |
| ---------------- | --------- | -------------------------------------------------------------------------------------------------- |
| Time uploaded    | Timestamp | Date and time an IT admin uploaded a document.                                                     |
| Time completed   | Timestamp | Date and time the document was processed completely.                                               |
| Courses uploaded | Integer   | Number of courses found in the document.                                                           |
| Ingestion status | Pending   | Document in queue for processing.                                                                  |
| Ingestion status | Running   | Document is currently be processed. This process can take up to 60 minutes.                        |
| Ingestion status | Success   | Ingestion process is complete and courses and will be available in app once completely configured. |
| Ingestion status | Failed    | Check the document format and reupload.                                                            |
| Duplicates       | Integer   | Number of duplicate courses found in the document.                                                 |

> [!NOTE]
> If a column is blank, the document is currently being processed and those values are not available. Once the document has been processed the values will be populated. You can refresh the page to check for updates.

## Troubleshooting

- If you see "Career Coach is currently being set up for you to use soon" in the Career Coach app, __the required sections have not been completed__. The following __sections are required__ to be complete before Career Coach can be used: [Brand and preferences](#brand-and-preferences), [LinkedIn connection](#linkedin-connection), [Course catalog](#course-catalog), and [Fields of study](#fields-of-study).

- CSVs for course catalog and field of study have required formats and a maximum size of 18 MB. Reference the Career Coach [course catalog document schema](#course-catalog-document-format-and-schema) and Career Coach [fields of study document schema](#fields-of-study-document-format-and-schema) to ensure proper configuration.

- On settings pages with required fields, if the fields are not completed, the page will not submit. You will not see a warning message; the page will simply not submit.

- When first configuring Career Coach, an error banner may appear stating "We can't update the app's settings. Try again." This is likely due to the tenant provisioning the Career Coach app, which can take up to 15 minutes. If this happens, wait 15 minutes before submitting again.

- If the Career Coach app is not showing in Microsoft Teams, the policy changes may not have taken effect. Policy changes can take a few hours to update. The Career Coach app will not be available in Microsoft Teams until the changes are complete.

## Removing your tenant data

Your tenant data includes information that's uploaded or generated as a part of application configuration. To delete all data within a Career Coach tenant, have your tenant’s global administrator [open a support ticket](https://edusupport.microsoft.com/support?product_id=career_coach) requesting that the tenant’s data be permanently deleted. Be aware that this process isn't reversible. After the data removal is complete, the Career Coach application will return to its pre-configured, non-personalized state for all users and a Teams administrator will need to set up the application again to continue using it.

The following explains the process for deletion:

- A support ticket must be filed by a tenant global admin clearly stating the request for your tenant’s data to be permanently deleted. **There's no ability to limit the data set or time window of the deletion**.

- Once filed, the support ticket will be addressed after one week to meet compliance's minimal retention policy. You can cancel the operation during this time.

- After one week, the Career Coach team ensures all data related to the tenant is deleted. Microsoft support monitors the ticket and will notify you once the deletion process is complete, **in no more than 30 days**.


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
