## Integration models for solution providers

<a name="steps"></a>

As a contact center solution provider, there are three models to choose from to integrate your connected contact center solution into Teams:

- If you want to use certified SBCs and Direct Routing to connect a contact center solution to Teams, see the [Connect model](?tabs=connect#steps).

- If you want to use Azure bots and the Microsoft Graph Communication APIs to enable solution providers to create Teams apps, see the [Extend model](?tabs=extend#steps).

- If you want to use an SDK that enables solution providers to imbed native Teams experiences in their App, see the [Power model](?tabs=power#steps). Power solutions will be possible when the SDK is available. Coming soon.

### [**The Connect model**](#tab/connect)

The Connect model uses Microsoft certified SBCs and Direct Routing to connect contact center solutions to Teams phone system infrastructure, enabling enhanced routing, configuration, and system insights.

Agents can set up automated virtual assistants and skill-based routing queues to gather information and connect customers with subject matter experts.

**Feature highlights:**

While these features aren't a comprehensive list of feature capabilities for this model of integration, the focus areas include:

- Office 365 authN for agents to connect to their Microsoft tenant from their integrated CCaaS client

- See when agents are available with Teams

- Transfers and group call support with Teams

- Teams Graph APIs and Cloud Communication APIs for integration with Teams

- Multi-tenant SIP trunking to support several customers on solution provider's SBC.

- Solution providers to use [<span class="underline">Microsoft certified session border controller (SBC)</span>](../direct-routing-border-controllers.md)

### [**The Extend model**](#tab/extend)

The Extend model integrates with the Teams client using the [Teams client platform](/microsoftteams/platform/overview), [Teams Graph APIs](/graph/api/resources/teams-api-overview) and [Cloud Communications API in Microsoft Graph](/graph/api/resources/communications-api-overview). The Extend model also uses the Teams phone system for all contact center calls and call control experiences, and the contact center solution provider acts as a telephony carrier alongside Microsoft 365.

Agents can use Teams for internal collaboration and external communication and can benefit from dynamic, contextual notes correlating data from multiple systems prior to starting an engagement and then avoid costly context switching.

Organizations can design workflows and advanced routing configurations down to the individual and measure the quality of their system and interactions.

**Feature highlights:**

While these features aren't a comprehensive list of feature capabilities for this model of integration, the focus areas include:

- Teams Graph APIs and Cloud Communication APIs for integration with Teams

- Teams-based app for agent experiences

- Teams as the primary calling endpoint for the agents

- Teams client calling for all the call controls

- Agent experience app for both Teams web and mobile client

- Analytics, workflow management, role-based experiences for agents in the CCaaS app in Teams

- Chat and collaboration experiences integrated with Teams clients

- Preserve performance and quality of Teams client experiences in all apps

### [**The Power model**](#tab/power)

The Power model enables solution providers to create native Azure-based voice applications using the Teams calling infrastructure and client platform to deliver modern, intelligent solutions for collaborative customer and agent connection. The goal of the Power model is to provide a one-app, one-screen contact center experience.


> [!NOTE]
> Coming soon.
