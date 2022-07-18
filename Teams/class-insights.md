---
title: IT Admin Guide to Education Insights in Microsoft Teams
author: DaniEASmith
ms.author: danismith
manager: serdars
ms.topic: reference
ms.service: msteams
audience: admin
ms.reviewer: karsmith
description: An IT Admin guide to Insights in Microsoft Teams for Education.
ms.localizationpriority: high
search.appverid: MET150
f1.keywords:
- NOCSH
ms.collection:
  - M365-collaboration
  - m365initiative-edu
appliesto:
  - Microsoft Teams
---

# IT Admin Guide to Education Insights in Microsoft Teams

This document provides the steps required to get Education Insights in Microsoft Teams up and running and help educators and education leaders adopt the platform and successfully use the app.

## Overview

**Each student has unique experiences, skills, and voice.**<br/>
**Insights helps you understand your students and respond to their needs.**

Insights provides real-time analytics of student progress and activity within their classes. With easily digestible visualizations, school communities can proactively and easily track student experiences. Educators and education leaders are presented with meaningful, reliable data to make informed decisions regarding their class teams. Guided by this data, educators have the information they need to ensure that their students' emotional, social, and academic needs are being met.

School communities can channel their efforts and achieve a more significant impact when educators know which strategies work for their students. With the timely data provided by Insights, educators and education leaders focus time and energy on taking actions that improve the learning environment, drive student success, and help learners thrive.

## Who uses Insights?

### Educators

An educator is anyone who owns a class team. Educators may include teachers, lecturers, and professors.

Educators access Insights at the class level. They see the activity of students assigned to their classes but can't access data from other classes. Insights helps educators understand and support their students.

There are no prerequisites to using Insights, and educators just need to add the Insights to the left app bar or as a tab to each of their classes in Teams.

Educators are identified by faculty licenses. Educators must have a faculty license and be a class team owner to see the data in Insights.

### Education leaders

Education leaders are all those roles in the institution that need an organizational view to understand their student engagement, progress, well-being, etc. Educators can also be education leaders when they own a class team and need more than their classes view, such as the head of a subject department.

Education leaders may include chief academic officers, heads of department, district leaders, school principals, head teachers, counselors, heads of a subject, program directors, social workers, and psychologists.

Education leaders get an organizational view that depends on the permissions assigned by the IT Admin. For example, school district administrators can see all the schools they access. In contrast, a school principal or a school supervisor only sees that school's grade levels and classes.

Assuming a supervisor also teaches, they're considered both an educator and an education leader and can access both views of Insights (for educators and education leaders). Here, Insights helps education leaders support educators and students.
At the organizational level, the IT admin needs to connect the student information system and assign permissions to each role to access the schools or departments relevant to them.

Education leaders are identified by faculty licenses, and they also need *explicit permissions* from the IT global admin to view their organization's Insights reports.

> [!NOTE]
> **Regarding students:**
>
> Insights collects data about student activity in Teams.
>
> Students are members of a class team within Teams. They are identified by their license and **do not have access** to the Insights app or tab (even if they are the team owner).
>
> Guests *cannot* be considered students.

## Where do users find Insights?

Educators and education leaders have different ways to access Insights.

### Educators

Educators can use these two methods:

- [Personal app](https://support.microsoft.com/office/747fd8d9-00b0-43e6-bacc-a1bf030b1867) - an overview of all their active classes is available from Teams left app bar, with the ability to drill down to class data.
- [Tabs](https://support.microsoft.com/office/1386d1b4-3641-4a23-9b9c-0c6c774c2b6c) - Insights for specific classes they own are available in a tab from a class team's top navigation menu. This tab enables the educator to directly access the relevant data when they are in that class in Teams to see the data in the class context.

Insights surfaces activity data from all channels within a class team but can only be added as a tab to public channels. The tab reflects activity from everyone in the class team who isn't an owner (including educators who aren't owners of the class team).

In both views, an educator can access class data. Using the personal app, the educator needs to drill down to the class level, whereas the tab provides direct access to class data.

At the class level, if an educator owns a class Team, Insights is available without any other action on the part of the IT Admin.

### Education leaders

Education leaders can use Insights as a [personal app](https://support.microsoft.com/office/8738d1b1-4e1c-49bd-9e8d-b5292474c347) available from Teams left app bar.

At the organizational level, the IT admin needs to connect the student information system and assign permissions to each role to access the schools or departments relevant to them.

For example, a principal sees only the classes in their school, or the head of a department sees only the department's classes.
The student data is aggregated at the class, department, school, and district level, and we provide insights at each level (based on the permission of each user)
Both educators and education leaders can zoom in and see the data for individual students.

**To add the Insights app in Teams:**

- Select "**...**" on the app bar.
- Search for **Insights** and select it.
- A description screen will open. Select **Add**.

  :::image type="content" source="media/insights-add-personal-app.png" alt-text="Add Insights to Teams.":::

- Right select on the Insights icon and select **Pin**.

  :::image type="content" source="media/insights-pin-app.png" alt-text="Pin the Insights app.":::

> [!TIP]
> You can also locate the Insights app through this link: [https://aka.ms/addInsights](https://aka.ms/addInsights)

## When is Insights used?

Insights supports learning communities throughout **the learning cycle**. With real-time metrics across multiple dimensions, Insights supports a continuous cycle of identification, reflection, discussion, and taking action amongst members of the school community.

- **Identify** how and when students engage with educators, course materials, and their peers, and how they perform on assignments.
- **Reflect** on how the inputs support the students to succeed, determine areas for growth, and where assistance is required.
- **Discuss** findings with students and the school community to strengthen relationships, goal setting, self-review, spark collaboration, and improve outcomes.
- **Take Action** to develop interventions, provide feedback on growth areas, modify teaching strategies, and identify extra support required.

:::image type="content" source="media/insights-learning-cycle.png" alt-text="Insights supports learning communities throughout the learning cycle.":::

## How Insights works?

Insights produces powerful analytics to help educators deliver better learning outcomes. It does this by analyzing student activity within Teams and optionally using the Student Information System (SIS) data that you provide to help contextualize and group that activity.

Before you start to deploy Insights for your institution, take a quick look at how Insights works, our commitment to data ethics, and the required licensing.

### Data collection

Data is collected for Insights from student and educator activity in Teams. Guest data isn't collected.

Insights *doesn't* display data about educators. Analysis of the data provides actionable insights to aid in teaching and learning.

Currently, data is collected from the following areas in class teams:

|Teams component|Data collected|
|---|---|
|**Assignments**|Opening, turning in, and grade on assignments.|
|**Channel engagement**|Visiting a channel, creating a post, replying to and liking a post (not including chat content).|
|**Files**|Uploading, downloading, accessing, modifying, commenting on, and sharing a file (not including file content).|
|**OneNote Class Notebook**|Editing a page or section in a notebook (not including page content).|
|**Meetings**|Attendance (not including meeting content).|
|**[Reading Progress](https://support.microsoft.com/topic/e71705a2-a79a-4d7e-bcef-a1e0aa336017)**|Accuracy rate, most challenging words, and words per minute.|
|**[Reflect](reflect.md)**|Check-ins (including values).|
|**Career Coach**|Student provided major (field of study) and year of school, student activity in career coach app including: skills, skills interest, career interests, learnings interests and career related activities.|

> [!NOTE]
> Most of the collected data shows up in Insights within a few minutes. Attendance in class meetings (meetings associated with one of the class channels) appears a few hours after the end of the meeting, usually up to 24 hours later.

> [!NOTE]
> Data collected in Education Insights is kept until either the IT Admin turns off the [Education Analytics toggle](#turn-sds-for-insights-on-or-off) or the Office subscription for the tenant ends. Turning off specific features in Teams does not delete historic data.

### Privacy and security

Education Insights, as part of Microsoft 365, meets national, regional, and industry-specific regulations for data collection and use, including [GDPR](/compliance/regulatory/gdpr) and the [Family Educational Rights and Privacy Act (FERPA)](/compliance/regulatory/offering-ferpa) that protects the privacy of students' education records.

The data belongs to the institution, and Microsoft only collects the data and stores it. Microsoft personnel can't access the data or see it, except as allowed by compliance in an audited way to maintain the service, such as data recovery.

> [!TIP]
>
> - Visit the [Microsoft Trust Center](https://www.microsoft.com/trust-center) to learn more about how Microsoft protects your data.
> - Visit [Microsoft compliance offerings](/compliance/regulatory/offering-home) to learn how Microsoft 365 helps your institution meet regulatory compliance standards.

### Performance and reliability

Insights is designed to handle a high volume of data collected from Teams with optimal performance and reliability. We can't guarantee 100% availability, but we endeavor to be available as close as possible to that target.

The data collection process takes place on separate servers to the installation of the Insights tab in Teams. The Insights tab or personal app doesn't affect application performance or network bandwidth for educators and students using the rest of the Teams functionality.

> [!TIP]
> For more details, read [Help for low-bandwidth situations for Teams for EDU](edu-remote-low-bandwidth.md).

### Data storage

Insights is currently deployed in Europe and the United States. Data for European-based users is stored on servers in Europe. Data for Australian-based and US-based users is stored on servers in the United States. Data for users outside of Europe, Australia, or the United States, will be stored in one of our geographic regions.

### Using data ethically

We're committed to using data responsibly and ethically. Insights follows our Microsoft principles for Responsible data and AI. This means that we're transparent about how the data is used, and we put the interests of educators and students first.  We use the highest security and privacy standards, monitor for continuous reliability and accuracy, and ensure ongoing compliance for your institution.

Microsoft has built Insights from the ground up to ensure data protection. We're aware of the potential sensitivity of how this data can be used, and we care for your data and the privacy of individuals.

#### Data to support learning

Insights shines a spotlight on student learning and digital engagement. The data supports learning and shows the level of student engagement on the digital learning platform. While you can drill down to the individual level for class activities, Microsoft **does not assign any positive or negative value** assigned to these actions. The purpose of the data it collects is to support students and educators to achieve their best.

Educators know and understand their students best. The information presented in Insights is there to aid them in **providing support to students** in a digital learning scenario. It replicates the insights available in an in-person experience. For example, suppose a student hasn't been active during a specific period or didn't complete all their assignments last week on-time. The data is surfaced to the educator to provide the right nudges or to check in on the student. It remains the educator's responsibility to interact with the student, or that student's family or guardians, to determine the underlying reason for any activity or inactivity detected.

Insights has been designed to support both students and educators in the digital learning environment framework. Insights **does not directly capture data about educators**. In addition to individual student data, it provides aggregations of student activity and outcomes for a specific educator to enable education leaders to support students and educators.

### Licensing

To access Insights, users must have an A1, A3, or A5 faculty license for Microsoft 365.

*Education Insights Premium* is a paid upgrade that provides education leaders an organizational level view of Education Insights data and expanded access to historical data views for educators. Eligible educational institutions can purchase an *Education Insights Premium* add-on license through Enrollment for Education Solutions (EES), Cloud Service Providers (CSP), and Microsoft 365 admin center (web direct).

The Education Insights Premium add-on will be available for organizations based on purchasing licenses for all digitally active students in the tenant.

## Student Information System (SIS) integration

The more data is fed into Insights, the better educators can support their students, and education leaders can support the educators.

To provide organization-level Insights, we must use [School Data Sync (SDS)](/SchoolDataSync) to connect to the Student Information System (SIS) so that Insights has the hierarchical structure of the educational system mapped correctly.

Viewing class-level Insights as the class educator *doesn't* require this because we use Teams' class structure and permissions.

To learn more, read [**Sync Student Information System (SIS) data with Education Insights**](education-insights-sis-data-sync.md).

## Manage permissions

As an IT admin you can provide permissions for education leaders, district leaders, school principals, head teachers, counselors, heads of learning areas, program directors, social workers, and psychologists. Educators are *automatically* given permission when they own a class team.

To learn more, read [**Manage user access to Education Insights**](education-insights-manage-access.md).

## Manage the setup policy

As an IT Admin, you can use the app setup policy to install Insights by default for your educators and leaders when they start Teams. With the setup policy, you can customize Teams to highlight Insights and pin it on the apps bar.

If educators want direct access to each class, they can manually install the Insights tab on the top navigation menu. This tab enables the educator to directly access the relevant data when they are in that class in Teams to see the data in the class context.

In both views, an educator can access class data. Using the personal app, the educator needs to drill down to the class level, whereas the tab provides direct access to class data.

> [!TIP]
> For more details, read [Teams Policies and Policy Packages for Education](./policy-packages-edu.md).

## Encourage the adoption of Insights

Get your educational institution excited about using Insights.

Feel free to distribute the following material to your **educators**:

- Check the [Insights support page](https://support.microsoft.com/office/27b56255-90c0-47aa-bac3-1c9f50157181) for more help.
- Get up and running quickly – [get the Insights one-pager PDF](https://aka.ms/insights/start).
- Read the [complete guide PDF](https://aka.ms/insights/guide).
- Watch [step-by-step tutorials](https://aka.ms/insights/resources) on how to use Insights.
- Train yourself with the [free Insights course](https://aka.ms/insights/course) at the Microsoft Educator Center
- And lastly, check out [this blog](https://techcommunity.microsoft.com/t5/education-blog/6-ways-to-be-insight-ful-and-support-student-engagement/ba-p/1903091) dedicated to Insights.

Material for **education leaders**:

- [Insights for education organizations support page](https://support.microsoft.com/office/8738d1b1-4e1c-49bd-9e8d-b5292474c347).

### Turn on and off Insights

By default, Insights is turned on, which allows analytics of students' activities within Teams to be used in Insights. You may opt out of Insights, in which case we *delete all the data collected* for Insights and stop collecting any future data. If you turn Insights back on, we start collecting data from the time it's re-enabled.

There are two places where you can control *Education Insights*. Both options have the same result. For customers that have transitioned from *SDS (Classic)* to *SDS for provisioning*, only the Teams client option is available.

#### Turn on and off Insights from the SDS admin center

1. Open the [SDS Admin Center](https://sds.microsoft.com/).
1. Go to **Settings** > **Manage Education Insights**.
1. Adjust the **Collect activity data for Insights** toggle to on or off.

![Screenshot of the SDS admin center toggles to turn Insights off and on](media/manage-insight-toggle.png)

#### Turn on and off Insights from the Teams client

1. If you don’t have the *Education Insights* personal app pinned, follow [these instructions](class-insights.md#education-leaders) to add it.
1. With a Microsoft 365 administrator account, open the **Admin settings** page using the ellipsis icon located in the top right corner of *Education Insights*.
1. Adjust the **Collect activity data for Insights** toggle to on or off.

> [!NOTE]
> If you've turned Insights off, the data that's been collected is deleted. The deleted data on opt-out cannot be restored at a later time, even if Insights is re-enabled.

### Turn on and off Advanced inferences in Insights

When the **Allow advanced inferences** toggle for Education Insights is turned on, Education Insights may present students, educators, and education leaders with advanced inferences about learning (such as engagement warnings). These inferences allow educators to provide more tailored support to students. The toggle also controls using tenant data for modeling.

Turning on this toggle won't collect any extra data other than the data already collected by Education Insights.

There are two places where you can control *Advanced inferences*. Both options have the same result. For customers that have transitioned from *SDS (Classic)* to *SDS for provisioning*, only the Teams client option is available.  

#### Turn on and off Advanced inferences from the SDS admin center

1. Open the [SDS admin center](https://sds.microsoft.com/).
1. Go to **Settings** > **Manage Education Insights**.
1. Adjust the **Allow advanced inferences** toggle to on or off.

#### Turn on and off Advanced inferences from the Teams client

1. If you don’t have the *Education Insights* personal app pinned, follow [these instructions](class-insights.md#education-leaders) to add it.
1. With a Microsoft 365 administrator account, open the **Admin settings** page using the ellipsis icon located in the top right corner of *Education Insights*.
1. Adjust the **Allow advanced inferences** toggle to on or off.

> [!NOTE]
> This toggle depends on the **Collect activity data for Insights** toggle. Turning off **Collect activity data for Insights** will also turn off the **Allow advanced inferences** toggle.

### Turn SDS for Insights on or off

School Data Sync (SDS) helps automate the import and synchronization of the Student Information System (SIS) data with Teams.

The use of Insights *doesn't* require the use of SDS. However, you may choose to opt out from Insights at any time.

- To turn off Insights use of School Data Sync, follow the instruction in [Disabling SDS for Insights](/schooldatasync/how-to-deploy-sds-for-insights#disabling-sds-for-insights).

- To turn it back on, follow the instructions in [How to deploy SDS for Insights](/schooldatasync/how-to-deploy-sds-for-insights).

### How to delete user data from Education insights

Insights stores student and educator activities performed in Microsoft Teams for Education.

There are two types of data collected by insights:

- **Comingled data** – data that is generated as part of the class learning activities.
- **Non-comingled (private) data** – data that is collected by the students activity in Teams for education that isn't part of the class learning activity.

The full data collected by insights is listed [here](class-insights.md#data-collection).

In order to provide completeness and integrity of the data for past time frames to educator and education leaders, by default Insights doesn't automatically delete data from the service when a student or educator user accounts are closed. The IT Admin of the organization can request manual delete of a user (educator or student) data, by taking the following steps:

- Open a [support ticket](https://aka.ms/edusupport). The support ticket must state clearly the request for a GDPR Delete DSR operation and contain the user object ID to be deleted.
There's no ability to limit the data set or time window of the deletion.
- In the request the IT Admin should clearly state the type of data that needs to be deleted for that user, out of the following options:
  - All data (comingled and private)
  - All private data
  - Career coach data only
- Once filed, the support ticket waits in the queue for one week to meet compliance's minimal retention policy. You have the opportunity to cancel the operation during this time.
- After one week, the Education Insights team ensures all data related to the user ID of the specific type as described above is deleted from the service. Microsoft support monitors the ticket and will notify you once the deletion process is complete, in no more than 28 days

## Troubleshooting

### Why doesn't my institution see any data in Insights?

If it's a *new* tenant and you've *never* seen data in Insights, check that your tenant is **verified as an education tenant** to access Insights. Contact your Microsoft account manager and ask them to check that the tenant is configured correctly.

If you don't have an account manager, open a ticket. Go to the [Microsoft 365 admin center](https://admin.microsoft.com/AdminPortal/) > **Support** > **New Service Request**.  In the title of the ticket, write: "Need assistance with education verification".

Also, verify that data collection for Insights is enabled. While it's on by default, IT Admin may have turned it off and therefore deleted all the data held by Insights.

To verify this, open the [SDS Admin Center](https://sds.microsoft.com) and go to **Settings** > **Manage Education Insights**. Check the status of 'Collect activity data for Insights'.

If it's turned off, turn it back on.  Insights starts to collect data, but it may take up to 24 hours to see it in the reports.

### Why do I see data for some students or classes, not all?

We only collect data for *licensed* students, so the most probable reason is that you have guest students attending classes, and their data isn't collected. You might see their name but without any data.

Check the status of your students to ensure they all have student licenses.

### Why don't educators see meeting data?

It takes up to 24 hours to see meeting data in Insights reports. So, check that enough time has passed.

Also, check that students didn't* [join the class meeting without a Teams account](https://support.microsoft.com/office/c6efc38f-4e03-4e79-b28f-e65a4c039508). In such a scenario, the student activity isn't collected.

> [!TIP]
> For those educators who want to track student attendance, you can recommend sending a message during the meeting asking students to reply. This registers their attendance within a few minutes.

> [!NOTE]
> If your question is still unanswered, please [open a support ticket](https://aka.ms/edusupport). Include the relevant screenshots representing the problem and the date the problem occurred. Add any additional data you think might help us to resolve the issue.

### What licenses do I need to activate Education Insights Premium?

In order for Education Insights Premium to be enabled for your organization, the tenant must purchase licenses based on the number of the digitally active students in the organization's tenant. That is, for all students who use a Teams class as part of their school work for activities such as meetings, communication, chat, assignments, editing files, Class Notebook or Reflect.
