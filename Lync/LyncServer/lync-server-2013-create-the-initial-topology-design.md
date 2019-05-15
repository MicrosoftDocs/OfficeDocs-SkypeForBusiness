---
title: 'Lync Server 2013: Create the initial topology design'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Create the initial design
ms:assetid: f3131153-de14-41be-b1e6-7d4bb0191af1
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg615047(v=OCS.15)
ms:contentKeyID: 51541530
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Create the initial topology design for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

After you have finished installing the Lync Server 2013, Planning Tool, you are ready to start the Planning Tool and begin designing the proposed Lync Server 2013 infrastructure.

<div>


> [!NOTE]  
> The Planning Tool is a wizard-driven tool with detailed guides to inform your decision-making process in designing your sites and topology. This topic is intended not as an exhaustive guide, but simply to help get you started using the Planning Tool in your design sessions.



</div>

<div>

## To get started using the Planning Tool and create the initial design

1.  Start the Lync Server 2013, Planning Tool: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Planning Tool**.

2.  After the Planning Tool has started, the **Welcome to the Planning Tool for Microsoft Lync Server 2013** page appears. Choose one of the following options to begin your design:
    
      - **Option 1: Get Started**   Clicking **Get Started** provides a specific series of interview questions with relevant selections to define the criteria. After you have finished the initial **Get Started** interview section, you proceed into **Design Sites** to define your site architecture. To complete this option, proceed to step 3.
    
      - **Option 2: Design Sites**   Clicking **Design Sites** at the Welcome page bypasses the interview questions presented in the **Get Started** section. The information that would have been gathered by responding to the interview questions in **Get Started** section is set to default values with this option. By clicking **Design Sites**, the experienced designer can bypass the initial interview and change the default values, as needed, on the **Central Sites** start page. To complete this option, skip over steps 3-5 and start at step 6.
    
      - **Option 3: Display Your Saved Topology**   If you have already completed and saved a topology through previous use of the Planning Tool, you can skip over most of these steps and start by opening and displaying the topology. You can also make changes and updates to the topology, resave it, and then export it to Microsoft Excel or Microsoft Visio. To complete this option, skip over steps 3-12 and start at step 13.

3.  Click **Get Started** to begin designing your Lync Server 2013 topology.

4.  Answer each section by selecting the appropriate criteria for your design, and then click **Next** to proceed to the next Wizard page. Click **Back** to make changes on previous pages.
    
    <div>
    

    > [!TIP]  
    > Each page has a description of the selection criteria, and recommendations based on preferred practices and capacity planning. If you require additional details, click <STRONG>Learn more</STRONG> to read detailed information from the Lync Server 2013 Planning documentation on the Microsoft TechNet website. You must have Internet connectivity to access the Microsoft TechNet website.

    
    </div>

5.  Select the appropriate options for your design. After the initial criteria are defined, a page will confirm that your Features Overview is complete.

6.  Click **Design Sites** to define your central site.
    
    <div>
    

    > [!NOTE]  
    > Each Lync Server 2013 topology will have at least one central site. Your design may have a single central site, a central site with a number of branch sites, a number of central sites, or a number of central sites with branch sites associated with each central site.

    
    </div>

7.  In **Site Name**, type the name that will identify this central site.

8.  In **Site Homed Users**, type the expected number of on-premises concurrent users who will be homed in this central site.

9.  In **Cloud Homed Users**, type the expected number of online concurrent users who will be homed in this central site.

10. Modify the selections for Online Collaboration, Users, Voice, Additional Deployment Options, or Server Applications, as needed.
    
    <div>
    

    > [!IMPORTANT]  
    > At this point in the design, you can only select or clear options for your deployment. However, you can configure more options in a later phase of the Planning Tool. There are also options that are unavailable and cannot be cleared. In addition, you may have to clear one option in order to clear another. For example, if you clear the <STRONG>Enterprise Voice</STRONG> option under Voice, then the <STRONG>Response Group</STRONG>, <STRONG>Announcement</STRONG>, and <STRONG>Call Park</STRONG> options under Server Applications (all of which are features of Enterprise Voice) are also cleared.

    
    </div>

11. After defining a site name and number of users, click **Next**.

12. The following pages ask for information about SIP domains, conference settings, voice settings and infrastructure, Exchange UM, external user access, Persistent Chat settings, client settings, collocation options, and branch sites. Answer these questions as appropriate.

13. The final question asks if you want to create another central site. If you select **Yes**, then the Planning Tool returns to the Central Sites page. If you select **No**, click **Next**, and then click **Draw** to display the high-level Global Topology view.

14. To view an existing topology, click **Display**.

15. Click the .xml file that represents the previously saved topology, and then click **Open**.

16. The Planning Tool displays the Global Topology page. You can now begin editing, updating, or changing the topology by using the tools available in the Planning Tool.

</div>

<div>

## See Also


[Editing the design in Lync Server 2013](lync-server-2013-editing-the-design.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

