---
title: Patient app overview       
author: jambirk           
ms.author: jambirk        
manager: serdars                    
audience: ITPro            
ms.topic: article                   
ms.service: msteams         
search.appverid: MET150
localization_priority: Normal
ms.collection: Teams_ITAdmin_PracticalGuidance
appliesto:
- Microsoft Teams
ms.reviewer: anach
description: Microsoft Teams Patient app EHR integration 
---

# Integrating Electronic Healthcare Records into Microsoft Teams

[!INCLUDE [preview-feature](../../includes/preview-feature.md)]

This article is intended for a general healthcare IT developer interested in using FHIR APIs on top of a medical information system to connect to Microsoft Teams. This would enable care coordination scenarios that match the needs of a healthcare organization.

This article documents the FHIR interface specifications for the Microsoft Teams Patient app, and understanding that is required for setting up a FHIR server and connecting to the Patient app in your development environment\tenant. You will also need to be familiar with the documentation of the FHIR server you have chosen, which must be one of the supported options:
- Datica (through their [CMI](https://datica.com/compliant-managed-integration/) offering)
- Infor Cloverleaf (through the [Infor FHIR Bridge](https://pages.infor.com/hcl-infor-fhir-bridge-brochure.html))
- Redox (through the [R^FHIR server](https://www.redoxengine.com/fhir/))
- Dapasoft (through [Corolar on FHIR](https://www.dapasoft.com/corolar-fhir-server-for-microsoft-teams/))

> [!NOTE]
> This process does not includes steps that use the Microsoft Teams admin center or PowerShell cmdlets to enable features. The configuration is entirely done on the FHIR server/service side and in the Patient app client.

Illustrated below is the architecture of the Patient app:

![Patient app architecture](../../media/patients-app-architecture.png)

The following sections explain the requirements of the FHIR-only data access layer for the Patient app that a FHIR server (or EHR enabled FHIR APIs) must meet in order to integrate with the Patient app, including the following:

- Expectations around user authentication
- Functional and technical requirements of the integration interface
- Expectations around performance and reliability
- Expectations around FHIR resources to be supported for the Patient app
- Process for integration and the expected engagement model
- How to enroll yourself and your customer in the private preview of the Patient app
- How to get started with FHIR and some common challenges faced with the Patient app
- Future requirements for the next iteration of the Patient app

> [!NOTE]
> In the following sections, the word "partner" or "Interop partner" is used to refer to any 3rd party Organization that enables integration to EHR systems for the Patient app through FHIR and is implementing a FHIR Server to match the listed specifications.

## Functional and technical requirements  

### Authentication  

App-level authorization *with no support for user level authorization* is the more commonly supported way to perform data transformations and expose connections to EHR data through FHIR, even though the EHR system might implement user level authorization. The Interop Service (Partner) gets elevated access to the EHR data, and when they expose the same data as the appropriate FHIR resources there is no authorization context passed on to the Interop Service Consumer (the Patient app) integrating with the Interop Service or Platform. The Patient app will not be able to enforce user level authorization, but does support application to application authentication between the Patient app and the Interop partner’s service.

The Application to Application authentication model is described below:

Service to service authentication should be done through OAuth 2.0 [Client Credential flow](https://www.oauth.com/oauth2-servers/access-tokens/client-credentials/). The partner service needs to provide the following:

1. The Partner service enables the Patient app to create an account with the Partner, which  enables the Patient app to generate and own client_id and client_secret, managed via an Auth registration portal on the partner’s Authentication server.
2. The Partner service owns the Authentication/Authorization system, which   accepts and verifies (authenticates) the client credentials provided and gives back an access token with tenant hint in scope, as described below.
3. For security reasons or in a case of a secret breach, the Patient app can re-generate the secret and invalidate or delete the old secret (Example of the same is available in Azure Portal - AAD App Registration)
4. The metadata endpoint hosting the conformance statement should be un-authenticated, it should be accessible without authentication token.
5. The Partner service provides the token endpoint for the Patient app to request an access token using a client credential flow. The token url as per authorization server should be part of the FHIR conformance (capability) statement fetched from metadata on the FHIR server as in this example:

![Patient app 5](../../media/Patient-app-5.png)

A request for an access token consists of the following parameters:

    POST /token HTTP/1.1
    Host: authorization-server.com

    grant-type=client_credentials
    &client_id=xxxxxxxxxx
    &client_secret=xxxxxxxxxx

The Partner service provides the client_id and client_secret for Patient app, managed via an Auth registration portal on the partner’s side. The Partner service provides the endpoint to request access token using a client credential flow. A successful response must include the token_type, access_token and expires_in parameters.

### Routing: Mapping AAD Tenant to the Provider endpoint

The Patient app connects to a partner service through a single endpoint. The Partner service owns and maintains a mechanism to map each Microsoft customer (AAD Tenant ID) to a respective healthcare Provider (FHIR server) that the Partner service is working with.

Mapping the AAD tenant to a provider endpoint uses the AAD Tenant ID (GUID). The Patient app passes the Tenant ID in scope, while requesting an access-token for each request. The Partner service keeps the mapping of Tenant ID to Provider endpoint and redirects requests to a provider endpoint based on the Tenant ID. To do this, the partner supports the configuration on their end (manually or via a portal as part of onboarding of provider organizations to their Interop Platform).

The Authentication and Routing workflow is shown below:

![Patient app 6](../../media/Patient-app-6.png)

1. Request for app access token by sending:
 
        {   grant_type: client_credentials,
            client_id: xxxxxx, 
            client_secret: xxxxxx,
            scope: {Provider Identifier, Ex: tenant ID}
        }

2. Reply with an app token:

        {  access_token: {JWT, with scope: tenant ID},
           expires_in: 156678,
           token_type: "Bearer",
        }

3. Request protected data with Access token.
4. Authorization message: Select the appropriate FHIR server to route to from tenant ID in scope
5. Sends the app protected  data from the authorized FHIR server after authenticating with the app token.

## Interfaces

Specific calls and fields used by the Patient app are documented in the following articles. Select the interface applicable to your FHIR server/FHIR APIs.

- [DSTU2 interface specification](dstu2-interface.md)
- [STU3 interface specification](stu3-interface.md)

## Performance and Reliability

While the Patient app is in private preview, there are no guarantees on the end-to-end performance. Factors in performance include the relative latencies of all the hops involved in the workflow, starting from the EHR in the health system's environment, to the Interop partner and their infra, including the FHIR Server and across to the Office 365 ecosystem and Patient app.

![Interop Partners](../../media/FHIR.png)

## Get started with FHIR  

If you're new to FHIR and need easy access to a FHIR Server that you can expose to the Microsoft Teams EHR integration interface, Microsoft has an open-source FHIR Server available for all developers to use. Please see the [What is FHIR Server for Azure](https://docs.microsoft.com/azure/healthcare-apis/overview-open-source-server) article to learn more about the open source FHIR Server available from Microsoft and deploy it for your organizations.

You can also use the HSPC Open sandbox EHR environment to create an an EHR which also supports an open FHIR Server and use this to play around with the Patient app. We recommend that you read through the [HSPC Sandbox documentation](https://healthservices.atlassian.net/wiki/spaces/HSPC/pages/64585866/HSPC+Sandbox). Not only does the sandbox provide an easy, UI oriented, and user friendly way of creating, adding and editing Patients, it also gives you several samples to get started.  

## Enroll in the private preview

Once you've created the open source FHIR Server, it's really easy to connect to the Patient app inside of your tenant by following the steps mentioned below:

1. [Contact us](mailto:Teamsforhealthcare@service.microsoft.com?subject=Microsoft%20Teams%20Patients%20App%20private%20preview) with the following initial details:  
    - Your Name, 
    - Your Position, 
    - The company or organization you represent
    - why you are interested in the Patient app for EHR integration. 

    We will get back to you as soon as possible with more questions and guide you through a process to get setup for the private preview.

2. Ensure that sideloading of custom apps is enabled in the tenant where you are going to try out the Patient app. Please refer to [App permission policies](../../admin-settings.md) to learn how to turn this on from the Teams Admin center for your or your customer's tenant.

3. Sideload the Patient app manifest that you will get from Microsoft (after we process your email to us) into a team in the tenant that is going to be used for care-coordination and patient rounding scenarios. Detailed instructions around how to side-load an app are in [Upload an app package to Microsoft Teams](/microsoftteams/platform/concepts/apps/apps-upload)

4. Navigate to the general channel as the Team owner and then click on the Patients tab. You should see a first run experience that will present two options i.e. EHR Mode and Manual Mode. Please select the **EHR mode** and copy the FHIR Server endpoint (that you've just setup earlier with all the required data and resources per the specifications above) into the Link field and give the connection a name that well represents the FHIR Server. Click on Connect, and everything should be ready to go.

    ![Patient app server settings](../../media/patients-server.png)

5. Start using the app to search for Patients from the FHIR Server/EHR and add them to a list and please [give us feedback](mailto:Teamsforhealthcare@service.microsoft.com?subject=Microsoft%20Teams%20Patients%20App%20feedback) if something doesn't work. Also, to establish a fully authenticated version of the Patient app -> FHIR Server flow, please engage in offline dialogue with Microsoft Teams for healthcare product engineering, through the email request mentioned earlier to clarify requirements and we will help enable this for you per the Authentication requirements described above in the FHIR Interface document.  


