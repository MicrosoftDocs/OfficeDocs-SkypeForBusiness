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

Career Coach is a Microsoft Teams for Education app powered by LinkedIn that provides personalized guidance for higher education students to navigate their career journey.  Career Coach offers educational institutions a unified career solution for students to discover their career path, grow real-world skills, and build their network all in one place.

Learn more about Career Coach here – aka.ms/career-coach

> [!NOTE]
> Use the best practices and helpful tips in this guide to enable the capabilities of Career Coach for students, faculty, and staff. /\*\*\*Link to marketing & edu support \*\*\*/

## Review the requirements

To enable Career Coach for your educational institution, review what you need to get the app up and running.

**Technical requirements**

  - Office 365 tenant with Azure Active Directory

  - Microsoft Teams

  - LinkedIn account connections in Azure Active Directory

**Licenses**

  - Faculty

  - Students

**Data and files from your educational institution**

  - Course catalogue data

  - Fields of study and degrees offered

  - Educational institution’s LinkedIn page

  - LinkedIn Learning campus subscription (preferred)

## Configure and enable Career Coach

Career Coach is available as an add-on SKU to Office 365 A1, A3, and A5 licenses. For an educational institution to access Career Coach, this SKU must be purchased with the appropriate number of licenses for the users who will use the app.

### Assign app licenses to users

For step-by-step instructions, see [Assign licenses to users](https://docs.microsoft.com/microsoft-365/admin/manage/assign-licenses-to-users).

### Turn on LinkedIn account connections

Career Coach **requires** your educational institution’s users to have the ability to connect their Microsoft 365 account to their LinkedIn account which is facilitated within Career Coach

#### To enable LinkedIn account connections in the Azure portal

1. Sign in to the [Azure AD admin center](https://aad.portal.azure.com/) with an account that's a global admin for the Azure AD organization.

2. Select **Users**.

3. On the **Users** page, select **User settings**.

4. Under **LinkedIn account connections**, allow users to connect their accounts to access their LinkedIn connections within some Microsoft apps. No data is shared until users consent to connect their accounts.

   - Select **Yes** to enable the service for all users in your educational institution

   - Select **Selected group** to enable the service for only a group of selected users in your educational institution

   - Select **No** to withdraw consent from all users in your educational institution

Learn how to [Integrate LinkedIn account connections in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/enterprise-users/linkedin-integration)

## Configure Career Coach in the Microsoft Teams admin center

Using the admin settings in the Microsoft Teams admin center, you can configure Career Coach for your educational institution and enable it for users. The following are settings related to Assignments:

## Access the Career Coach app settings

Use the [Manage apps page](https://docs.microsoft.com/en-us/microsoftteams/manage-apps) to view the Teams apps in your educational institution’s app catalog.

1. Visit the **Microsoft Teams admin center**.

2. In the left navigation of the Microsoft Teams admin center, go to **Teams apps** &gt; **Manage apps**.  
    *You must be a global admin or Teams service admin to access the page.*

3. Search or browse for **Career Coach**.  

4. Select Career Coach and select **Settings.**  

Learn how to [manage your apps in the Microsoft Teams admin center](https://docs.microsoft.com/en-us/microsoftteams/manage-apps)

### Configure the Career Coach app settings

Career Coach has five configuration categories:

- Brand and preferences

- LinkedIn configuration

- Course catalog

- Fields of study

- Customization

Brand and preferences, LinkedIn configuration, Course catalog, and Fields of study are **required** to effectively enable the app for students, educators, faculty, and staff.

#### Brand and preferences – Required

You can set your educational institution’s name, logo, and default language on the brand and preferences settings page.

##### Educational institution icon

The educational institution icon will be used throughout Career Coach to identify content unique to your educational institution – course catalog resources throughout the app and in the optional Real world experiences on the dashboard. **The icon is best formatted as a transparent PNG, with aspect ratio of 1:1, and maximum size of 64x64px.**

##### Educational institution thumbnail

The educational institution icon will be used for course catalog resources throughout the app when a specific image is not available for a course. **The icon is best formatted as a PNG, with aspect ratio of 16:9, and maximum size of 360x200px.**

#### LinkedIn configuration – Required

The LinkedIn configuration connects Career Coach with your educational institution’s alumni data from LinkedIn.

> [!NOTE]
> Career Coach can't be enabled without the LinkedIn page connection verified.

##### Process for adding and confirming the LinkedIn page

Determine the educational institutions LinkedIn page. This can be done by searching on LinkedIn or connecting with a career services staff member to determine the correct page to use.  
  
1. In the Microsoft Teams admin center, select **Teams apps** &gt; **Manage apps** &gt; **Career Coach** &gt;  **LinkedIn connection**.

2. Enter your educational institution's LinkedIn Page URL  

3. Select **Apply**.

4. Copy the verification URL and share it with your educational institution’s LinkedIn page admin [LinkedIn page admin documentation](#Xa39a3ee5e6b4b0d3255bfef95601890afd80709).  
    *The verification link provided in step 4 expires after 48 hours.  
    *  
    /\*\*\* Screenshot of flow and LinkedIn page+URL \*\*\*/

#### Course catalog – Required

The course catalog represents the courses offered to students by your educational institution. These courses are used within the app in two areas:

1. Courses are returned as part of learning resources.  

2. Courses and course meta data, like descriptions, are used to help students identify their skills when they upload a transcript.  

To create the course catalog, put together a list of all courses taught at your educational institution and upload it as a CSV. file. The app draws from the Course Catalog to identify a student’s skills from their transcript and to suggest courses to take.

#### Process for adding the course catalog

1. Go to the Microsoft Teams admin center. Select **Teams apps** &gt; **Manage apps** &gt; **Career Coach** &gt; **Settings** &gt;  **Course catalog**.

2. Upload courses in CSV format. 

3. Add the course title, ID, and description.

4. Select **Apply**.

#### Documents formatting:

- Formatted as a CSV with a maximum size of 18MB.

- Contain the required fields: course title, course ID.

- Including the recommended fields improve the experience for students by returning better search results and skill identification.

> [!NOTE]
> Start with the sample course catalog document to get started. Download sample course catalog

#### Course catalog schema

| Name             | Status      | Type   | Description |
|------------------|-------------|--------|-------------|
| courseId         | Required    | string |             |
| title            | Required    | string |             |
| description      | Recommended | string |             |
| language         | Recommended | string |             |
| sourceLink       | Recommended | string |             |
| thumbnailLink    | Recommended | string |             |
| thumbnailAltText | Recommended | string |             |
| format           | Recommended | string |             |

| Name              | Status      | Type           | Description                                                                    |
|-------------------|-------------|----------------|--------------------------------------------------------------------------------|
| externalId        | Required    | string         | Usually the course id (Typically maps to what is generated in the transcript). |
| title             | Required    | string         | Usually the course title.                                                      |
| sourceLink        | Required    | url            | Website link to the course page.                                               |
| shortDescription  | Required    |                | Introduction text for the course.                                              |
| longDescription   | Recommended | string         | Extended description for the course.                                           |
| format            | Recommended | string         | Mode of teaching, e.g., online, video, in-person.                              |
| topics            | Recommended | list           | Topics or tags that are associated with the skills the courses teach.          |
| sourceLastUpdated | Recommended | dateTimeOffset | Datetime when the content/metadata for the course is updated.                  |
| thumbnailLink     | Recommended | url            | Thumbnail link to tin                                                          |
| thumbnailAltText  | Recommended | string         |                                                                                |
| sourceSkills      | Recommended | string         |                                                                                |
| industries        | Recommended | string         |                                                                                |
| keyPhrases        | Recommended | list           |                                                                                |

#### Fields of study - Required

The fields of study are synonymous with major areas of interest, academic major, and degree. These titles are referenced by students when they start using the app and begin setting up their personalized profile.

Add all fields of study available to students such as Engineering, English, Business, and so on. This lets students discover fields of study that may interest them and add their area of focus to their profile.

#### Add the course catalog

1. Go to the Microsoft Teams admin center. Select **Teams apps** &gt; **Manage apps** &gt; **Career Coach** &gt; **Settings** &gt;  **Fields of study**.

2. Under Upload Field of study document, add the field of study document in CSV format.

3. Select **Apply**.

#### Documents formatting

- Formatted as a CSV with a maximum size of 18MB.

- Single column of fields of study

> [!NOTE] 
> Start with the sample fields of study document to get started. Download sample fields of study document

#### Customization

Career Coach can be customized to be unique to your educational institution. The customization supports adding experiences to the dashboard. It is recommended to add links to the educational institution’s job boards, events, career services office and career-related events, clubs, educational institutions, and experiences and any other resources that help students gain experience.

#### Add customized experiences

1. Go to the Microsoft Teams admin center. Select **Teams apps** &gt; **Manage apps** &gt; **Career Coach** &gt; **Customization**.

2. Add each URL, a title, and short description.  
  
3. Select **Apply**.

#### Enable the app


### Allow users to access Career Coach

After you complete customization, you’ll be able to enable the app for students and licensed users.  
  
> [!NOTE] 
> You must have Global or Teams admin role permissions.

1. Go to the Microsoft Teams admin center. Select **Teams apps** &gt; **Manage apps** &gt; **Career Coach**.

2. Move the Status toggle to **Allowed**.  

    > (!) Note: Allowed means that the app is available for users in your educational institution. Blocked means that the app isn't available to students.

### Pin the app

Pinning Career Coach will make the app more accessible and visible for students.
1. Go to the Microsoft Teams admin center. Select **Teams apps** &gt; **Manage apps** &gt;**Setup polices** &gt; ***Specific policy***.

2. Under **Pinned apps** choose **Add apps**. Search for **Career Coach**. Select **Add**.


1. Choose the order for the app to appear and select **Save**.

2. Student will be notified in Microsoft Teams that Career Coach has been pinned.  

## FAQs / Troubleshooting / Resources

Include Career Coach links

**Planning Guide**

-  [Welcome to Microsoft Teams](Teams-overview.md)

-   [How to roll out Teams](get-started-with-teams-resources-for-org-wide-rollout.md?tabs=SmallBusiness)

-   [Overview of teams and channels in Microsoft Teams](teams-channels-overview.md)

-   [Managing apps in Microsoft Teams Admin Center](manage-apps.md)

-   [Security, privacy, and compliance in Microsoft Teams](security-compliance-overview.md)

-   [Teams Learning Orientation Kit]() need the link

-   [Limits and specification of Teams channels](limits-specifications-teams.md)

-   [Location of data in Microsoft Teams](location-of-data-in-teams.md)

-   [Getting started with admin training for Microsoft Teams](ITAdmin-readiness.md)

-   [Teams troubleshooting](https://docs.microsoft.com/microsoftteams/troubleshoot/teams-welcome)

-   [Manage app permission policies in Microsoft Teams](teams-app-permission-policies.md)
