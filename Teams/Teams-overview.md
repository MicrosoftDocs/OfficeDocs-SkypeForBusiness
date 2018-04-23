---
title: Overview of Microsoft Teams
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 09/25/2017
ms.topic: article
ms.service: msteams
ms.reviewer: ninadara
description: Learn about Microsoft Teams, its infrastructure, and using Teams with Office 365.
ms.custom:
- NewAdminCenter_Update
MS.collection: Strat_MT_TeamsAdmin
appliesto: 
- Microsoft Teams
---

Overview of Microsoft Teams
===========================

> [!VIDEO https://videoplayercdn.osi.office.net/hub/?csid=ux-cms-en-us-msoffice&uuid=ccf507a4-4ec4-4d61-9fb0-c86b5f1fc2a6&AutoPlayVideo=false] 


Microsoft Teams는 팀워크를 위한 채팅 기반 허브를 제공하고 고객에게 개방적이고 유동적이며 디지털 환경을 조성 할 수 있는 기회를 제공하기 위한 솔루션 입니다.Microsoft Teams는 기존 Office 365 그룹에 Microsoft 기술을 기반으로 합니다.

Microsoft Teams는 Azure AD (Azure Active Directory)에 저장된 ID를 활용하고 Office 365 내의 다른 서비스와 통합하여 만든 각 팀의 SharePoint 온라인 사이트 및 Exchange Online 그룹 사서함을 만듭니다.

Outlook, Gmail 또는 기타 업체와 같은 비즈니스 또는 소비자 이메일 계정을 가진 사람은 누구든지 Microsoft Teams 게스트로 참여할 수 있습니다. 
Microsoft Teams의 모든 게스트는 나머지 Office 365와 동일한 준수 및 감사 보호를 받으며 Azure AD에서 안전하게 게스트 계정을 관리 할 수 있습니다. 
관리자는 게스트가 Office 365 환경에 참여하는 방식을 중앙에서 관리하고 게스트가 호스트 테넌트에 액세스하는 것을 쉽게보고, 추가하거나 취소 할 수 있습니다.

Microsoft Teams는 지속적인 채팅 기능, 전화 및 회의 기능, Office 365의 다른 구성 요소에 쉽게 액세스 할 수 있을 뿐 아니라 강력한 확장성을 제공합니다. 
이는 엔터프라이즈 기업, 소규모 조직 및 그 사이에 있는 모든 사람들에게 적합한 팀웍의 허브를 제공합니다.  

팀 기능을 확장하려면 [Apps] (https://go.microsoft.com/fwlink/?linkid=854629)로 제공되는 커넥터, 탭 및 봇을 사용하여 외부 정보, 콘텐츠 및 지능형 봇 상호 작용을 팀에 제공하십시오.  

Microsoft Teams의 인프라
------------------------------

Microsoft Teams는 Office 365 그룹에 의해 함께 연동되는 기존 Microsoft 기술을 기반으로 합니다. 
Microsoft 클라우드를 기반으로 하는 조직은 팀을 협업 스토리의 일부로 활용할 때 뛰어난 성능과 안정성을 기대할 수 있습니다.

Microsoft Teams에서 만든 팀은 Microsoft Teams에서 만든 Office 365 그룹, SharePoint 온라인 사이트 (문서 라이브러리가 포함 된) 및 모임에서 초대장과 같은 정보를 저장하는 데 Microsoft Teams에서 사용하는 Exchange Online 그룹 사서함을 만듭니다. 
기존 Office 365 그룹을 사용하여 Microsoft Teams를 만들 수 있으므로 기존 그룹 구성원 및 SharePoint Online 및 Exchange Online에 저장된 콘텐츠를 Microsoft Teams에 포팅 할 수 있습니다.

비공식적 인 실시간 대화가 이루어지는 지속적인 채팅 보드로서 Microsoft Teams 기능을 보완하기 위해 Microsoft Teams는 Skype 및 Skype for Business에서도 사용되는 차세대 클라우드 기반 인프라를 기반으로 회의 경험을 제공합니다. 
이러한 기술 투자에는 미디어 프로세싱 및 시그널링, H.264 비디오 코덱, SILK 및 Opus 오디오 코덱, 네트워크 탄력성, 원격 측정 및 품질 진단을위한 Azure 기반 클라우드 서비스가 포함됩니다.

Office 365 그룹은 Azure AD (Azure Active Directory)에 저장된 ID를 활용하므로 다중 인증 (MFA) 지원과 같은 Azure AD의 모든 인증 및 권한 부여 기능을 Microsoft Teams에서 즉시 사용할 수 있습니다.

또한 Microsoft Teams는 Skype 및 Skype for Business에서도 사용되는 차세대 클라우드 기반 인프라를 기반으로하는 전화 및 회의 환경을 제공합니다. 
이러한 기술 투자에는 미디어 프로세싱 및 시그널링, H.264 비디오 코덱, SILK 및 Opus 오디오 코덱, 네트워크 탄력성, 원격 측정 및 품질 진단을 위한 Azure 기반 클라우드 서비스가 포함됩니다.

> [!NOTE]
>고객 피드백을 기반으로 Microsoft Teams에서 팀을 만든 결과 생성되는 새로운 Office 365 그룹은 기본적으로 Outlook에 더 이상 표시되지 않습니다. 
Outlook에서 이러한 그룹을 표시하는 기존 동작을 계속 수행하려는 고객을 위해 Exchange Online PowerShell cmdlet이 제공되어 그룹에서 Outlook 환경을 사용할 수 있습니다. 
Outlook을 통해 만든 다음 나중에 Microsoft Teams용으로 사용할 수 있는 그룹은 Outlook과 Microsoft Teams 모두에서 계속해서 표시됩니다. 
이 업데이트는 앞으로 몇 개월 내에 Outlook 및 Microsoft Teams에서 점차적으로 출시 될 예정입니다.


Microsoft Teams and Office 365
------------------------------

서로 다른 그룹에는 기능적 역할과 작업 스타일에 따라 다양한 요구가 있습니다. 
Office 365는 모든 그룹의 독특한 작업 스타일을 위해 설계되었으며 다음과 같은 용도로 통합 된 응용 프로그램을 포함합니다.

-   Outlook 기능인 이메일, 그룹

-   Sharepoint 기능인 사이트 및 포털, 지능형 컨텐츠 서비스, 비즈니스 프로세스 자동화 및 엔터프라이즈 검색

-   Yammer 기능인 회사 전체 연결

-   Skye for Business 기능인 엔터프라이즈 음성 및 비디오

-   이제 Office 365의 새로운 채팅 기반 작업 영역 인 Microsoft Teams

다음은 Office 365의 각 응용 프로그램에 대한 일반적인 사용 사례입니다. 자세한 사용 지침은 [FastTrack Productivity Library] (https://go.microsoft.com/fwlink/?linkid=854630)를 참조하십시오.

![Microsoft Teams icon.](media/Overview_of_Microsoft_Teams_image1.png)

-   동일한 사용자 그룹과 실시간으로 공동 작업을 하려는 사용자 및 팀이 활용합니다.

-   팀이 프로젝트를 신속하게 반복하면서 파일을 공유하고 공유 된 결과물을 공동 작업하려는 팀을 지원합니다.

-   사용자가 다양한 도구를 작업 공간 (예 : Planner, Power BI, GitHub 등)에 연결할 수 있습니다.

![Microsoft Outlook icon.](media/Overview_of_Microsoft_Teams_image2.png)

-   친숙한 이메일 환경 및 / 또는보다 공식적이고 구조화 된 방식으로 공동 작업하는 것을 선호하는 사용자가 활용할 수 있습니다.

-   회사 내부 및 외부에서 문서 및 정보를 전송하기 위해 전자 메일 사용이 필요한 특정 비즈니스 프로세스를 제공합니다.

-   조직 외부에있는 사용자와 통신하고 연결합니다.

![Yammer icon.](media/Overview_of_Microsoft_Teams_image3.png)

-   조직 전체 사용자를 연결하여 실습 커뮤니티를 구성하고 모범 사례를 공유 할 수 있습니다.

-   개방적이고 투명한 피드 기반 플랫폼을 통해 여러 기능 워크 플로우를 개선합니다.

-   리더십과 더 넓은 직원 기반 간의 양방향 대화를 통해 임원 - 직원 참여를 촉진합니다.

-   지식과 전문 지식을 공유하고 전달하기 위한 협업 공간 입니다.

![Skype for Business icon.](media/Overview_of_Microsoft_Teams_image4.png)

-   고객 / 파트너와 내부 및 외부에서 실시간 커뮤니케이션 및 협업을 위해 활용됩니다.

-   소규모 팀 또는 대규모 팀 (10,000 명 규모의 타운 홀 포함)과 함께 오디오, 비디오 및 컨텐츠로 회의를 제공합니다.

-   엔터프라이즈 통화 기능을 제공합니다.


![Microsoft SharePoint icon.](media/Overview_of_Microsoft_Teams_image5.png)

-   사이트 및 포털 (예 : 회사 뉴스 및 공지 사항, 검색 및 문서 공동 작업)에 활용됩니다.

-   Microsoft Flow 및 PowerApp를 통합하여 문서 라이브러리 및 정보 목록에 대한 비즈니스 프로세스 자동화를 구현합니다.

-   전체 기능의 SharePoint 팀 사이트는 파일 저장소, 팀 뉴스, 페이지, 목록 등을 위해 모든 Microsoft 팀에 자동으로 제공됩니다.

-   See [How SharePoint Online and OneDrive for Business interact with Teams](SharePoint-OneDrive-interact.md)

## [Teams known issues](Known-issues.md)

## [Teams client release notes](https://support.office.com/article/Release-notes-for-Microsoft-Teams-d7092a6d-c896-424c-b362-a472d5f105de)

## What happened to the Teams admin FAQ?

While the Teams Admin FAQ was handy when we first released Teams, it quickly became a "junk drawer" that made it hard to find anything specific. So we busted apart the FAQ and incorporated its valuable information into the Teams documentation that you're looking at right now. You'll find all the information that was in the FAQ in this documentation, in context.

If you're looking for something that you can't find here, please tell us about it in the **Feedback** section below. We try to respond to your feedback within 24 hours.

By the way, we **do** still have an FAQ for the [Journey from Skype for Business to Microsoft Teams](FAQ-journey.md). 
