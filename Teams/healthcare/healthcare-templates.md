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
ms.prod: sharepoint-server-itpro           # See metadata requirements link above for allowed values.
ms.prod: exchange-server-itpro             # See metadata requirements link above for allowed values.
ms.prod: skypeforbusiness-server-itpro     # See metadata requirements link above for allowed values.

# OPTIONAL METADATA

description:                         # Treat this like a summary tag in DxStudio. It helps with SEO.
ms.custom:                           # Similar to Set Free Tag. Use sparingly, limited character space.
ms.reviewer: MsAlias1, MsAlias2, etc # List contributors' Microsoft aliases, separated with commas.
robots:                              # Omit this field to make content searchable. Include it to hide from search.

---

# Healthcare templates 

Teams templates allow you to quickly and easily create teams by providing a predefined template of settings, channels, and pre-installed apps. For healthcare organizations, templates can be especially powerful, as they provide structure for users to become oriented with how to best leverage Teams effectively. Templates also allow administrators to deploy consistent teams across their organizations. We currently offer three first party healthcare templates that you can leverage for a variety of situations.  

# First party healthcare templates 

Care coordination template:  TemplateID: healthcareCareCoordination 

The care coordination template is meant to facilitate communication within a patient care team, with some specific examples including interdisciplinary and multidisciplinary teams. Our proprietary Patients Application1 – a FHIR conformant EHR integrated app – is preloaded in this template and sits in the General channel. With the Patients Application, you can curate lists of patients and their associated values and vitals, making it useful for rounding and patient management scenarios. More information on the Patients Application can be found here: LINK.  

 1 The Patients Application is currently in private preview; access to the application is contingent upon pilot participation. 

## Ward-wide template 

TemplateID: healthcareWardWide 

The ward-wide template is meant for communication and collaboration within a ward, pod, or department. The template can be used to facilitate patient management, as well as the operational needs of a ward. For example, ward-wide announcements can be posted in the ‘Announcements’ channel and shifts can be managed in ‘Scheduling and Patient Census’. If you’re looking to streamline your ward, then this template is for you. 

Hospital-wide template 

TemplateID: healthcareHospitalWide 

The hospital-wide template is meant for communication and collaboration between multiple wards, pods, and departments within a hospital. Included in this template are several operational channels including ‘Announcements,’ ‘Custodial,’ ‘Pharmacy,’ and ‘Laboratory,’ but we also provide a script below which extends the template with a variety of additional department or specialty-centric channels that you can add to, delete from, or edit to your liking. For example, if you have an ‘Endocrinology’ department, but don’t need a channel for ‘Ophthalmology,’ then the script can be adapted to include an ‘Endocrinology’ channel and remove the ‘Ophthalmology’ channel. We recommend that these specialty or ward-modeled channels not be auto-favorited to avoid notification saturation. Users generally favorite any channels that they find relevant. 
How to use first party templates 

To use these templates, simply change the ‘template@odata.bind’ property in the request body from ‘standard’ to the TemplateIDs above.  For more information on how to deploy Teams templates, see this article: LINK 
Hospital-wide template extension script 
~~~
{  
          "template@odata.bind": "https://graph.microsoft.com/beta/teamsTemplates/healthcareHospitalWide", 
          "DisplayName": "Contoso Hospital", 
          "Description": "Team for all staff in Contoso Hospital", 
          "Channels": [ 
            { 
              "displayName": "Ambulatory", 
              "IsFavoriteByDefault": false 
            }, 
            { 
              "displayName": "Anesthesiology", 
              "IsFavoriteByDefault": false 
            }, 
            { 
              "displayName": "Cardiology", 
              "IsFavoriteByDefault": false 
            }, 
            { 
              "displayName": "CCU", 
              "IsFavoriteByDefault": false 
            }, 
            { 
              "displayName": "Ear, Nose, and Throat", 
              "IsFavoriteByDefault": false 
            }, 
            { 
              "displayName": "Emergency Care", 
              "IsFavoriteByDefault": false 
            }, 
            { 
              "displayName": "Family Medicine", 
              "IsFavoriteByDefault": false 
            }, 
            { 
              "displayName": "Gynecology", 
              "IsFavoriteByDefault": false 
            }, 
            { 
              "displayName": "ICU", 
              "IsFavoriteByDefault": false 
            }, 
            { 
              "displayName": "Mother-Baby", 
              "IsFavoriteByDefault": false 
            },  
            { 
              "displayName": "Neonatal", 
              "IsFavoriteByDefault": false 
            }, 
            { 
              "displayName": "Neurology", 
              "IsFavoriteByDefault": false 
            }, 
            { 
              "displayName": "Oncology", 
              "IsFavoriteByDefault": false 
            }, 
            { 
              "displayName": "Ophthalmology", 
              "IsFavoriteByDefault": false 
            }, 
            { 
              "displayName": "PACU", 
              "IsFavoriteByDefault": false 
            }, 
            { 
              "displayName": "Psychiatric", 
              "IsFavoriteByDefault": false 
            }, 
            { 
              "displayName": "Radiology", 
              "IsFavoriteByDefault": false 
            }, 
            { 
              "displayName": "Rehabilitation", 
              "IsFavoriteByDefault": false 
            }, 
            { 
              "displayName": "Surgical", 
              "IsFavoriteByDefault": false 
            }, 
            { 
              "displayName": "Urology", 
              "IsFavoriteByDefault": false 
            }, 
            { 
              "displayName": "Women’s Health", 
              "IsFavoriteByDefault": false 
            } 
          ], 
          "Apps": [ 
            { 
              "Id": "1542629c-01b3-4a6d-8f76-1938b779e48d" 
            } 
          ] 
          } 
~~~

## Healthcare templates breakdown 

Hospital-wide template  

- Announcements (Favorited)  
- Compliance (Favorited) 
- Custodial  
- Finance  
- Fun Stuff (Favorited) 
- Human Resources  
- Laboratory 
- Patient Safety and Quality Improvement (Favorited) 
- Pharmacy 

## Ward-wide template 

- Announcements (Favorited) 
- Call Lights  
- Fun Stuff (Favorited) 
- Huddles (Favorited) 
- Scheduling and Patient Census (Favorited) 
- Training and Certification (Favorited) 
- Rounds (Favorited) 

## Care coordination template 

- General (Favorited) (Includes the Patients Application) 
- Literature and Training (Favorited) 
- Post-Treatment Review (Favorited) 
- Scheduling (Favorited) 


