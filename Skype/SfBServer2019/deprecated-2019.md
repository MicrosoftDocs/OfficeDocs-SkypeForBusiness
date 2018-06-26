---
title: "Skype for Business Server 2019 deprecations"
ms.author: jambirk
author: jambirk
manager: serdars
ms.date: 6/31/2018
ms.audience: ITPro
ms.topic: overview
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
description: "Summary: These features have been removed from Skype for Business Server 2019."
---

# Skype for Business Server 2019 deprecations

For new features in 2019, we are writing new topics. For features 2015 and 2019 have in common, we will make many topics release agnostic and they will be visible in the TOC for both products. For features being removed, we will in some cases deliberately not surface some topics in the 2019 TOC, and these 2015 articles will remain release specific with notes explaining the differences between releases.

 Persitent Chat, SQL Mirroring, and XMPP Gateway functionalities are no longer available as Skype for Business Server 2019 features. Persistent Chat functionality is available in Teams and we recommend adopting Teams for situations requiring that functionality. SQL Mirroring can be replaced with other methods that are still supported. XMPP Gateway services can be maintained using a coexistence environment, if they were previously deployed. If you want to continue using these features, then plan a coexistence environment where some users remain in legacy pools.
<!--  above paragraph elaborates on [Migrating multiple sites and pools](migration/migrating-multiple-sites-and-pools.md) -->




<!--Heidi, feel free to add whatever you wanted to add in place of this comment.  -->




<!-- In addition to deprecations, this document reflects notes on what topic areas can and can't be evergreened to generically apply to 2019 and 2015 alike. It's not a doc plan in that it provides no schedule, but it is a general plan of attack to deal with legacy topics requiring minimal investment for 2019's release. -->

[!INCLUDE [disclaimer](disclaimer.md)]

The following features are found in Skype for Business Server 2015 but are no longer present in Skype for Business Server 2019. They are discussed in the topics linked, which will need to have appropriate notices added, and the references to server versions will be left specific to 2015 

<!-- (136 topics impacted with mention, 21 topics in plan/deploy/manage leave unevergreened deliberately? create new stub topic in 2019 toc explaining deprecation?)-->
- Persistent chat 
    - [Plan for Persistent Chat Server in Skype for Business Server 2015](../SfbServer/plan-your-deployment/persistent-chat-server/persistent-chat-server.md) --5 subtopics
    - [Deploy Persistent Chat Server in Skype for Business Server 2015](../SfbServer/deploy/deploy-persistent-chat-server/deploy-persistent-chat-server.md) -- 6 subtopics
    - [Manage Persistent Chat Server in Skype for Business Server 2015](../SfbServer/manage/persistent-chat/persistent-chat.md) -- 7 subtopics
    - and about 100 more topics where it's mentioned

Those 21 specific Persistent chat topics could be dropped entirely from the 2019 TOC. Suggest adding this note: 

> [!NOTE]
> Persistent chat is available in Skype for Business Server 2015 but is no longer supported in Skype for Business Server 2019. Teams offers similar functionality, refer to INSERT LINK HERE.

<!-- There is no migration topic for Pchat, but there is one for XMPP. Reconcile w/ Ken. -->  
<!-- (most HADR topics impacted, 15 topics mention, but the 5 below topics highest Pri for getting a note) -->
- SQL Mirroring 
     - [Back End Server high availability in Skype for Business Server](../SfbServer/plan-your-deployment/high-availability-and-disaster-recovery/back-end-server.md)
     - [Deploy high availability and disaster recovery](../SfbServer/deploy/deploy-high-availability-and-disaster-recovery/deploy-high-availability-and-disaster-recovery.md)
     - [Deploy SQL mirroring for Back End Server high availability in Skype for Business Server](../SfbServer/deploy/deploy-high-availability-and-disaster-recovery/sql-mirroring-for-high-availability.md)
     - [Create and publish new topology in Skype for Business Server](../SfbServer/deploy/install/create-and-publish-new-topology.md)
     - [Server requirements for Skype for Business Server 2019](plan/server-requirements.md)


SQL Mirroring is one of several methods for back end server HADR, so we suggest using the other methods. Topics surface in both TOCs. Suggest adding this note: 

> [!NOTE]
> SQL Mirroring is available in Skype for Business Server 2015 but is no longer supported in Skype for Business Server 2019. The  AlwaysOn Availability Groups, AlwaysOn Failover Cluster Instances (FCI), and SQL failover clustering methods are preferred with Skype for Business Server 2019.
<!-- so we offer the other methods instead -->

<!-- (7 Edge topics impacted, so collaborate w/Heidi, parallell topics in migration) -->
- XMPP Gateway    
    - Migration [Configure XMPP gateway access policies and certificates](migration/configure-xmpp-gateway-access-policies-and-certificates.md)  <!--    (what happened? check w/ Ken) -->
    - [Configure XMPP gateway access policies and certificates](migration/configure-xmpp-gateway-access-policies-and-certificates.md)
    - [Feature Overview (Planning Tool)](../SfbServer/management-tools/planning-tool/feature-overview.md)
    - [Configure watcher node test users and settings](../SfbServer/management-tools/use-scom-management-pack/test-users-and-settings.md)
    - [Edge Server environmental requirements in Skype for Business Server 2015](../SfbServer/plan-your-deployment/edge-server-deployments/edge-environmental-requirements.md)
    - [Edge Server system requirements in Skype for Business Server 2015](../SfbServer/plan-your-deployment/edge-server-deployments/system-requirements.md)
    - [Topology Basics for Skype for Business Server 2015](../SfbServer/plan-your-deployment/topology-basics/topology-basics.md)
    - [Migrating XMPP federation](migration/migrating-xmpp-federation.md)
    -  [Phase 3: Deploy Skype for Business Server 2019 pilot pool](migration/phase-3-deploy-pilot-pool.md)
    - [Verify the legacy environment](migration/verify-environment.md)

Migration topics describe how to set up coexistence for XMPP, but the 2015 topics should get a pointer inside a note. We could drop the 2015 topics from the 2019 TOC and add some notes to the topics. Suggested note:

> [!NOTE]
> XMPP Gateways are available in Skype for Business Server 2015 but are no longer supported in Skype for Business Server 2019. See [Migrating XMPP federation](migration/migrating-xmpp-federation.md) for more information.

<!-- 5 files impacted in the 2015 plan/deploy nodes, plus "what's new" -->
- In-place upgrade
    - [Install Skype for Business Server on servers in the topology](../SfbServer/deploy/install/install-skype-for-business-server.md)
    - [Upgrade to Skype for Business Server 2015](../SfbServer/deploy/upgrade-to-skype-for-business-server.md)
    - [Server requirements for Skype for Business Server 2015](../SfbServer/plan-your-deployment/requirements-for-your-environment/server-requirements.md)
    - [Plan to upgrade to Skype for Business Server 2015](../SfbServer/plan-your-deployment/upgrade.md)
    - [What's new in Skype for Business Server 2015](../SfbServer/what-s-new-in-skype-for-business-server.md)


> [!NOTE]
>  In-place upgrades were available in Skype for Business Server 2015 but are no longer supported in Skype for Business Server 2019. See [Migration to Skype for Business Server 2019](migration/migration-to-skype-for-business-server-2019.md) for more information.

<!-- 12 files impacted, many in monitoring which may require undoing some evergreening  -->
- MCX (preceded UCWA and used by old mobile clients like 2010)
    - [Deploy and Configure Mobility for Skype for Business Server 2015](../SfbServer/deploy/deploy-and-configure-mobility.md)
    - [Manage conferencing in Skype for Business Server 2015](../SfbServer/manage/conferencing/conferencing.md)
    - [Configure Mobility Service for high performance in Skype for Business Server](../SfbServer/manage/health-and-monitoring/configure-service.md)
    - [Monitoring IIS request tracing log files in Skype for Business Server](../SfbServer/manage/health-and-monitoring/iis-request-tracing-log-files.md)
    - [Monitor mobility for performance in Skype for Business Server](../SfbServer/manage/health-and-monitoring/monitor-mobility-performance.md)
    - [Mobility performance counters in Skype for Business Server](../SfbServer/manage/health-and-monitoring/performance-counters.md)
    - [Monitor for server memory capacity limits in Skype for Business Server](../SfbServer/manage/health-and-monitoring/server-memory-capacity-limits.md)
    - [Monitor Mobility Service and UCWA usage in Skype for Business Server](../SfbServer/manage/health-and-monitoring/service-and-ucwa-usage.md)
    - [Configure watcher node test users and settings](../SfbServer/management-tools/use-scom-management-pack/test-users-and-settings.md)
    - [Manage Skype for Business Server 2015 using SCOM Management pack](../SfbServer/management-tools/use-scom-management-pack/use-scom-management-pack.md)
    - [Install and configure watcher nodes](../SfbServer/management-tools/use-scom-management-pack/watcher-nodes.md)
    - [Plan for Mobility for Skype for Business Server 2015](../SfbServer/plan-your-deployment/mobility.md)

> [!NOTE]
> MCX support for legacy mobile clients is no longer available in Skype for Business Server 2019. Your users will need to upgrade to a current client.

<!-- The file counts reflect file hits in searches, and in some cases refer to un-migrated 2013 topics we can link to once they are migrated. 

The following deprecation notes may be necessary. Or not. If 2019 has a seperate toc but single sources files from 2015 folders we can simply omit entire files and nodes from the 2019 toc and reffrain from evergreening them, so they self-identify as 2015 topics.

> [!NOTE]
> Persistent chat is available in Skype for Business Server 2015 but is no longer supported in Skype for Business Server 2019.

> [!NOTE]
> XMPP Gateways are available in Skype for Business Server 2015 but are no longer supported in Skype for Business Server 2019.

> [!NOTE]
> SQL Mirroring is available in Skype for Business Server 2015 but is no longer supported in Skype for Business Server 2019. The Clustering and AlwaysOn methods are preferred with Skype for Business Server 2019.

> [!NOTE]
>  In-place upgrades were available in Skype for Business Server 2015 but are no longer supported in Skype for Business Server 2019. See [Migration to Skype for Business Server 2019](migration/migration-to-skype-for-business-server-2019.md) for more information.

> [!NOTE]
> MCX support for legacy mobile clients is no longer available in Skype for Business Server 2019. Your users will need to upgrade to a current client.


Add following to encryption.md:  -- done!
> [!SECURITY NOTE]
> To ensure the strongest cryptographic protocol is used, Skype for Business Server 2019 will offer TLS encryption protocols in the following order to clients: **TLS 2.0, TLS 1.2**. TLS is a critical aspect of Skype for Business Server 2019 and thus it is required in order to maintain a supported environment. 
-->




## Evergreen

Where a link exists, it should be ok to evergreen the topic linked to.

Documentation for the following features (including all relevant plan/deploy/manage nodes) applies equally to Skype for Business Server 2015 and 2019:
- Monitoring (plan, deploy, manage)  &#x2714; (need to reassess for MCX)
- Archiving (plan, deploy, manage)  &#x2714;
- Authentication (Manage) &#x2714;
    - Please check "How to use Modern Authentication (ADAL) with Skype for Business" for applicability to 2019 (as well as Office 2013 references).
- Modern Authentication (Plan) &#x2714;
- Capacity planning &#x2714;
    - [Capacity planning for Skype for Business Server 2015](../SfbServer/plan-your-deployment/capacity/capacity.md)
    - [Estimating voice usage and traffic for Skype for Business Server 2015](../SfbServer/plan-your-deployment/capacity/estimating-voice-traffic.md)
    - [Deployment guidelines for Mediation Server in Skype for Business Server 2015](../SfbServer/plan-your-deployment/capacity/mediation-server-deployment-guidelines.md)
    - [Capacity planning user model usage for Skype for Business Server 2015](../SfbServer/plan-your-deployment/capacity/user-model.md)
    - [User models in Skype for Business Server 2015](../SfbServer/plan-your-deployment/capacity/user-models.md)
- Clients (plan, deploy, manage)  **(Not done yet)*** - may need some clarification 
- Conferencing (plan, deploy, manage)
    - [Plan your conferencing topology for Skype for Business Server 2015](../SfbServer/plan-your-deployment/conferencing/conferencing-topology.md) 
        - Contains links to 2015 non-evergreened topics: "Topology Basics for Skype for Business Server 2015," "Reference topologies for Skype for Business Server 2015," "Create a file share in Skype for Business Server 2015"
    - [Plan for conferencing in Skype for Business Server 2015](../SfbServer/plan-your-deployment/conferencing/conferencing.md) 
        - Contains link to 2015 non-evergreened topic: "Configure your on-premises deployment for Skype Meeting Broadcast"
    - [Plan for dial-in conferencing in Skype for Business Server 2015](../SfbServer/plan-your-deployment/conferencing/dial-in-conferencing.md) &#x2714;
    - [Hardware and software requirements for conferencing in Skype for Business Server 2015](../SfbServer/plan-your-deployment/conferencing/hardware-and-software-requirements.md) 
        - Contains links to 2015-only topics: "Server requirements for Skype for Business Server 2015," "Environmental requirements for Skype for Business Server 2015"
    - [Plan for large meetings in Skype for Business Server 2015](../SfbServer/plan-your-deployment/conferencing/large-meetings.md) 
        - Contains link to 2015 non-evergreened topic: "Configure your on-premises deployment for Skype Meeting Broadcast"
    - [Deploy conferencing in Skype for Business Server 2015](../SfbServer/deploy/deploy-conferencing/deploy-conferencing.md)
        - Contains links to 2015-only topics: "Server requirements for Skype for Business Server 2015," "Environmental requirements for Skype for Business Server 2015," "Plan for Edge Server deployments in Skype for Business Server 2015," "Deploy Edge Server in Skype for Business Server 2015"
    - [Configure dial-in conferencing in Skype for Business Server 2015](../SfbServer/deploy/deploy-conferencing/dial-in-conferencing.md)
        - Contains "Skype for Business 2015" in UI steps x 2.
    - [Configure integration with Office Web Apps Server in Skype for Business Server 2015](../SfbServer/deploy/deploy-conferencing/office-web-app-server.md) &#x2714;
    - [Deploy SRS v1 Administrative Web Portal in Skype for Business Server 2015](../SfbServer/deploy/deploy-conferencing/room-system-v1-administrative-web-portal.md) 
        - Contains external links to "Microsoft Skype Room Systems v1 Administrative Web Portal for Skype for Business Server 2015," "Updates for Skype for Business Server 2015." Step 3 of installation includes "%Program Files%\Skype for Business Server 2015" file location. Also, link to "Required DNS Records for Automatic Client Sign-In" has note that the content is no longer being updated. Are screen shots OK as is?
    - [Manage dial-in conferencing access numbers in Skype for Business Server 2015](../SfbServer/manage/conferencing/access-numbers.md) &#x2714;
    - [Assign conferencing policies in Skype for Business Server 2015](../SfbServer/manage/conferencing/assign-policies.md) &#x2714;
    - [Manage conferencing policies in Skype for Business Server 2015](../SfbServer/manage/conferencing/conferencing-policies.md) &#x2714;
    - [Manage conferencing server configuration settings in Skype for Business Server 2015](../SfbServer/manage/conferencing/conferencing-server-configuration-settings.md) &#x2714;
    - [Manage conferencing in Skype for Business Server 2015](../SfbServer/manage/conferencing/conferencing.md) &#x2714;
    - [Create conferencing policies in Skype for Business Server 2015](../SfbServer/manage/conferencing/create-policies.md) &#x2714;
    - [Create meeting configuration settings in Skype for Business Server 2015](../SfbServer/manage/conferencing/create-settings.md) &#x2714;
    - [Delete conferencing policies in Skype for Business Server 2015](../SfbServer/manage/conferencing/delete-policies.md) &#x2714;
    - [Delete meeting configuration settings in Skype for Business Server 2015](../SfbServer/manage/conferencing/delete-settings.md) &#x2714;
    - [Manage dial-in conferencing in Skype for Business Server 2015](../SfbServer/manage/conferencing/dial-in-conferencing.md) &#x2714;
    - [Create conference directories in Skype for Business Server 2015](../SfbServer/manage/conferencing/directories.md) &#x2714;
    - [Enable or disable dial-in conferencing in Skype for Business Server 2015](../SfbServer/manage/conferencing/enable-or-disable.md) &#x2714;
    - [Manage conference join and leave announcements in Skype for Business Server 2015](../SfbServer/manage/conferencing/join-and-leave-announcements.md) 
        - Contains UI step that references "Skype for Business 2015."
    - [Manage key mapping for DTMF commands in Skype for Business Server 2015](../SfbServer/manage/conferencing/key-mapping-for-dtmf-commands.md) 
        - Contains UI step that references "Skype for Business 2015."
    - [Manage meeting configuration settings in Skype for Business Server 2015](../SfbServer/manage/conferencing/meeting-configuration-settings.md) &#x2714;
    - [Configure the meeting join page in Skype for Business Server 2015](../SfbServer/manage/conferencing/meeting-join-page.md) 
        - Specifically mentions "the 2015 version of Skype for Business client."
    - [Modify conferencing policies in Skype for Business Server 2015](../SfbServer/manage/conferencing/modify-policies.md) &#x2714;
    - [Modify meeting configuration settings in Skype for Business Server 2015](../SfbServer/manage/conferencing/modify-settings.md) &#x2714;
    - [Configure PIN-less meeting join in Skype for Business Server](../SfbServer/manage/conferencing/pin-less-meeting-join.md) &#x2714;
    - [Manage PIN policies for dial-in conferencing in Skype for Business Server 2015](../SfbServer/manage/conferencing/pin-policies.md) &#x2714;
    - [Test dial-in conferencing in Skype for Business Server 2015](../SfbServer/manage/conferencing/tests.md) 
        - Contains 3 procedures with UI steps that reference "Skype for Business 2015."
    - [View meeting configuration settings in Skype for Business Server 2015](../SfbServer/manage/conferencing/view-settings.md) &#x2714;
    - [View conferencing policies in Skype for Business Server 2015](../SfbServer/manage/conferencing/view.md) &#x2714;
    - [Send welcome email to dial-in users in Skype for Business Server 2015](../SfbServer/manage/conferencing/welcome-emails.md) 
        - Contains UI step that references "Skype for Business 2015."
- Edge (unclear, verify w/ Heidi  XMPP Gateway related topics in Edge)
- Enterprise Voice (plan, deploy, manage)
- Exchange integration (plan, deploy, manage)
- HADR (except for adding SQL Mirroring deprecation notes)
- Modern Auth
- Security (plan, deploy, manage) encryption.md now has 2 security notes RE: TLS, still need to add links to converted blog topics on TLS 1.0 and 1.1
- IM and Presence (plan, deploy)
    - [Plan for instant messaging and presence in Skype for Business Server 2015](../SfbServer/plan-your-deployment/instant-messaging-and-presence.md)
    - [Enable or Disable Offline Instant Messaging (IM) in Skype for Business Server 2015](../SfbServer/deploy/im-and-presence/enable-or-disable-offline-im.md)
    - [Deploy instant messaging and presence in Skype for Business Server 2015](../SfbServer/deploy/im-and-presence/im-and-presence.md) 
- Mobility (plan, deploy, manage)
- SRS v1 and v2 (plan,deploy,manage)
- VIS role (plan, deploy)
    - [Plan for Video Interop Server in Skype for Business Server 2015](../SfbServer/plan-your-deployment/video-interop-server.md) &#x2714;
    - [Configure a VTC for Interoperation with Skype for Business Server 2015](../SfbServer/deploy/deploy-video-interop-server/configure-a-vtc-for-interoperation.md) &#x2714;
    - [Configure CUCM for Interoperation with Skype for Business Server 2015](../SfbServer/deploy/deploy-video-interop-server/configure-cucm-for-interoperation.md) &#x2714;
    - [Configure the Video Interop Server in Skype for Business Server 2015](../SfbServer/deploy/deploy-video-interop-server/configure-the-vis.md) &#x2714;
    - [Create a VIS pool in Skype for Business Server 2015](../SfbServer/deploy/deploy-video-interop-server/create-a-vis-pool.md) 
        - Contains non-evergreened link to "Create and publish new topology in Skype for Business Server 2015" x2
    - [Deploy the VIS server role in Skype for Business Server 2015](../SfbServer/deploy/deploy-video-interop-server/deploy-the-vis-server-role.md) &#x2714;
    - [Deploy Video Interop Server in Skype for Business Server 2015](../SfbServer/deploy/deploy-video-interop-server/deploy-video-interop-server.md) &#x2714;
- Topology management
- User account management
    - [Manage user accounts for Skype for Business Server 2015](../SfbServer/manage/user-accounts/user-accounts.md)
    - [Customize user account properties for Skype for Business Server 2015](../SfbServer/manage/user-accounts/customize-properties.md)
- [Technical diagrams for Skype for Business Server 2015](../SfbServer/technical-diagrams.md)

As these topics are evergreened, they get added into the TOC for 2019, they are already in the SFBServer TOC.


## New items
New items we may need by RTM include: 
- What's new in 2019
- Deprecated (this document)
