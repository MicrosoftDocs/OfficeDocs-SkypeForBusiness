---   
                             
# For details about MAX content metadata requirements, see https://review.docs.microsoft.com/en-us/office-authoring-guide/metadata-for-max-content-on-dmc?branch=master

# REQUIRED METADATA

title: Article title goes here       # Very important for SEO. See https://aka.ms/seo-for-writers-cheat-sheet
author: YourGitHubUserName           # This is your GitHub alias, not your Microsoft alias
ms.author: YourMicrosoftAlias        # Your Microsoft alias without @microsoft.com
ms.date: mm/dd/yyyy                  # Use the format mm/dd/yyyy. IMPORTANT: Update manually when you modify a topic.
manager: pamgreen                    # Delete for Skype/Exchange
manager: serdars                     # Delete for SharePoint
audience: ITPro                      # One of: Admin, ITPro, Developer
ms.topic: article                    # See metadata requirements link above for additional allowed values.
localization_priority: Normal        # See metadata requirements link above for allowed values.
ms.collection: some-scs-name         # Delete if this topic isn't in a SCS, or enter the tag for SCS. 
# Choose ONLY ONE of the following values for ms.prod. Delete the ones you don't use.
ms.prod: sharepoint-server-itpro     # See metadata requirements link above for allowed values.
ms.prod: exchange-server-itpro     # See metadata requirements link above for allowed values.
ms.prod: skypeforbusiness-server-itpro     # See metadata requirements link above for allowed values.

# OPTIONAL METADATA

description:                         # Treat this like a summary tag in DxStudio. It helps with SEO.
ms.custom:                           # Similar to Set Free Tag. Use sparingly, limited character space.
ms.reviewer: MsAlias1, MsAlias2, etc # List contributors' Microsoft aliases, separated with commas.
robots:                              # Omit this field to make content searchable. Include it to hide from search.

---


# Feature name



## FeatureName overview

Short overview of what the new feature is. 

- What is the new or updated experience?

- Does this feature replace an existing feature/experience? If yes, what is the transition plan?

- Does this feature has dependency on other features? If yes, list/explain the dependencies.
    
- List the key deployment scenarios - why would people use this feature? 
     
## [OPTIONAL] Planning for feature

Some features would require careful pre-planning before deployment can begin. For those features, cover what planning tasks customers should complete.
  
## Configure feature

How do you configure this feature? Cover these points: 

- Are there any prerequisites?

- Is this feature per org or per user? 
    
- Use PowerShell or UI?
    
- Short instructions on how to turn on the feature for the organization or for individual users. 
   
## Manage feature
 
- Add subsections with basic management tasks that would be required or that we expect customer to perform. 

### Management task 1

### Management task 2
    

## Security & Compliance

List any security or compliance impact of this feature here. Cover the following:

- Where is the data associated with this feature stored?

- Include any other data implications such as GDPR compliance.

