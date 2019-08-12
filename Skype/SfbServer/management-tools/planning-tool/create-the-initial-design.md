---
title: "Create the initial topology design for Skype for Business Server 2015"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 4/5/2016
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: f3131153-de14-41be-b1e6-7d4bb0191af1
description: "After you have finished installing the Skype for Business Server Planning Tool, you are ready to start the Planning Tool and begin designing the proposed Skype for Business Server 2015 infrastructure."
---

# Create the initial topology design for Skype for Business Server 2015

After you have finished installing the Skype for Business Server Planning Tool, you are ready to start the Planning Tool and begin designing the proposed Skype for Business Server 2015 infrastructure.

> [!NOTE]
>  The Planning Tool is a wizard-driven tool with detailed guides to inform your decision-making process in designing your sites and topology. This topic is intended not as an exhaustive guide, but simply to help get you started using the Planning Tool in your design sessions.

### To get started using the Planning Tool and create the initial design

1. Start the Skype for Business Server 2015 Planning Tool: Click **Start**, click **All Programs**, click **Skype for Business Server 2015**, and then click **Planning Tool**.

2. After the Planning Tool has started, the **Welcome to the Planning Tool for Skype for Business Server 2015** page appears. Choose one of the following options to begin your design:

   - **Option 1: Get Started** Clicking **Get Started** provides a specific series of interview questions with relevant selections to define the criteria. After you have finished the initial **Get Started** interview section, you proceed into **Design Sites** to define your site architecture. To complete this option, proceed to step 3.

   - **Option 2: Design Sites** Clicking **Design Sites** at the Welcome page bypasses the interview questions presented in the **Get Started** section. The information that would have been gathered by responding to the interview questions in **Get Started** section is set to default values with this option. By clicking **Design Sites**, the experienced designer can bypass the initial interview and change the default values, as needed, on the **Central Sites** start page. To complete this option, skip over steps 3-5 and start at step 6.

   - **Option 3: Display Your Saved Topology** If you have already completed and saved a topology through previous use of the Planning Tool, you can skip over most of these steps and start by opening and displaying the topology. You can also make changes and updates to the topology, resave it, and then export it to Microsoft Excel or Microsoft Visio. To complete this option, skip over steps 3-12 and start at step 13.

3. Click **Get Started** to begin designing your Skype for Business Server 2015 topology.

4. Answer each section by selecting the appropriate criteria for your design, and then click **Next** to proceed to the next Wizard page. Click **Back** to make changes on previous pages.

    > [!TIP]
    > Each page has a description of the selection criteria, and recommendations based on preferred practices and capacity planning. If you require additional details, click **Learn more** to read detailed information from the Skype for Business Server 2015 Planning documentation on the Microsoft  website. You must have Internet connectivity to access the Microsoft  website.

5. Select the appropriate options for your design. After the initial criteria are defined, a page will confirm that your Features Overview is complete.

6. Click **Design Sites** to define your central site.

    > [!NOTE]
    > Each Skype for Business Server 2015 topology will have at least one central site. Your design may have a single central site, a central site with a number of branch sites, a number of central sites, or a number of central sites with branch sites associated with each central site.

7. In **Site Name**, type the name that will identify this central site.

8. In **Site Homed Users**, type the expected number of on-premises concurrent users who will be homed in this central site.

9. In **Cloud Homed Users**, type the expected number of online concurrent users who will be homed in this central site.

10. Modify the selections for Online Collaboration, Users, Voice, Additional Deployment Options, or Server Applications, as needed.

    > [!IMPORTANT]
    > At this point in the design, you can only select or clear options for your deployment. However, you can configure more options in a later phase of the Planning Tool. There are also options that are unavailable and cannot be cleared. In addition, you may have to clear one option in order to clear another. For example, if you clear the **Enterprise Voice** option under Voice, then the **Response Group**, **Announcement**, and **Call Park** options under Server Applications (all of which are features of Enterprise Voice) are also cleared.

11. After defining a site name and number of users, click **Next**.

12. The following pages ask for information about SIP domains, conference settings, voice settings and infrastructure, Exchange UM, external user access, Persistent Chat settings, client settings, collocation options, and branch sites. Answer these questions as appropriate.

13. The final question asks if you want to create another central site. If you select **Yes**, then the Planning Tool returns to the Central Sites page. If you select **No**, click **Next**, and then click **Draw** to display the high-level Global Topology view.

14. To view an existing topology, click **Display**.

15. Click the .xml file that represents the previously saved topology, and then click **Open**.

16. The Planning Tool displays the Global Topology page. You can now begin editing, updating, or changing the topology by using the tools available in the Planning Tool.

## See also

[Editing the Design](https://technet.microsoft.com/library/08f639ba-0e5f-4ae7-9191-c3d96c25b169.aspx)
