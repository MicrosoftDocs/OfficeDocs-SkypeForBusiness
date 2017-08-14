---
title: Rate my Call in Skype for Business Server 2015
ms.prod: SKYPEFORBUSINESS
ms.assetid: c4e0c905-33a1-49d8-9276-1b338f94d085
---


# Rate my Call in Skype for Business Server 2015
[] **Summary:** Learn about the Rate My Call feature in Skype for Business Server 2015.
Rate My Call is a new feature in Skype for Business that provides enterprises a way to get feedback from their end-users.
  
    
    

The Rate My Call window offers a "star" rating system and predefined tokens for audio and video calls. In addition, administrators can enable custom field to provide feedback.
Collected Rate My Call data is not currently included in any existing monitoring report, but it has a separate monitoring report. Data is collected in SQL tables that can be accessed by running SQL queries (work on reports in progress).
  
    
    


## Rate my Call Prerequisites

Before the users in your Skype for Business Server deployment can access Rate My Call functionality, the following set of components must be deployed and configured:
  
    
    

-  You must have Skype for Business Server installed (version 9160 or higher).
    
  
- Have your users install and update to the latest version of Skype for Business and also be ask them to use the Skype for Business UI.
    
  
- Users must be homed on the Skype for Business Server front end pool.
    
  
- You must have a Skype for Business Server monitoring database deployed and associated to your Skype for Business Server pools.
    
  
- We recommend deploying Call Quality Dashboard (CQD).
    
  

## Configure Rate my Call

The Rate My Call feature is automatically enabled in the Client policy with the following defaults:
  
    
    

- Rate My Call Display Percentage - 10%
    
  
- Rate My Call Allow Custom User Feedback - disabled
    
  
There is no action required to enable the base feature, however custom feedback will need to be enabled separately if it is desired. The following Windows PowerShell cmdlet is an example of enabling custom end user feedback and changing the interval from 10% to 80%.
  
    
    



```

Set-CSClientPolicy -Identity <PolicyIdentity> -RateMyCallDisplayPercentage 80 - RateMyCallAllowCustomUserFeedback $true

```


## Accessing Rate My Call Data

Data collected from users is collected in two tables in the Monitoring database.
  
    
    
 **[QoeMetrics].[dbo].[CallQualityFeedbackToken]** this table contains results of token polling by end users.
  
    
    
 **[QoeMetrics].[dbo].[CallQualityFeedbackTokenDef]** - this table contains token definitions.
  
    
    
Token definitions are coded as follows:
  
    
    

|||
|:-----|:-----|
|1  <br/> |DistortedSpeech  <br/> |
|2  <br/> | ElectronicFeedback <br/> |
|3  <br/> | BackgroundNoise <br/> |
|4  <br/> |MuffledSpeech  <br/> |
|5  <br/> |Echo  <br/> |
|21  <br/> | FrozenVideo <br/> |
|22  <br/> | PixelatedVideo <br/> |
|23  <br/> | BlurryImage <br/> |
|24  <br/> | PoorColor <br/> |
|25  <br/> | DarkVideo <br/> |
   
 **[QoeMetrics].[dbo].[CallQualityFeedback]** This table contains polling results from "Star" voting and customer feedback if enabled.
  
    
    
Data from tables can be called by using a **select * from [Table.Name]** query or by using Microsoft SQL Server Management Studio.
  
    
    
The following SQL queries can be used:
  
    
    
 **Audio**
  
    
    



```

SELECT
        s.ConferenceDateTime
        ,Caller.URI as Caller
        ,CallerCqf.FeedbackText 
        ,CallerCqf.Rating
        ,CallerCqfTokenDef.TokenDescription 
        ,CallerCqfToken.TokenValue
    FROM [Session] s WITH (NOLOCK)
        INNER JOIN [MediaLine] AS m WITH (NOLOCK) ON 
            m.ConferenceDateTime = s.ConferenceDateTime
            AND m.SessionSeq = s.SessionSeq                        
        INNER JOIN [AudioStream] AS a WITH (NOLOCK) ON -- only look at Audio related feedback
            a.MediaLineLabel = m.MediaLineLabel    
            and a.ConferenceDateTime = m.ConferenceDateTime 
            and a.SessionSeq = m.SessionSeq
            and a.SenderIsCallerPAI = 1                
        INNER JOIN [CallQualityFeedback] AS CallerCqf WITH (NOLOCK) ON
            CallerCqf.ConferenceDateTime  = s.ConferenceDateTime 
            and
            CallerCqf.SessionSeq = s.SessionSeq 
        INNER JOIN [CallQualityFeedbackToken] AS CallerCqfToken WITH (NOLOCK) ON
            CallerCqfToken.ConferenceDateTime  = s.ConferenceDateTime 
            and
            CallerCqfToken.SessionSeq = s.SessionSeq
            and
            CallerCqfToken.FromURI = CallerCqf.FromURI
        INNER JOIN [CallQualityFeedbackTokenDef] AS CallerCqfTokenDef WITH (NOLOCK) ON
            CallerCqfTokenDef.TokenId = CallerCqfToken.TokenId
            and
            CallerCqfToken.TokenId < 20 -- only look at Audio related feedback
        INNER JOIN [User] AS Caller WITH (NOLOCK) ON
            Caller.UserKey = CallerCqf.FromURI
 
```

 **Video**
  
    
    



```

SELECT
        s.ConferenceDateTime
        ,Caller.URI as Caller
        ,CallerCqf.FeedbackText 
        ,CallerCqf.Rating
        ,CallerCqfTokenDef.TokenDescription 
        ,CallerCqfToken.TokenValue
    FROM [Session] s WITH (NOLOCK)
        INNER JOIN [MediaLine] AS m WITH (NOLOCK) ON 
            m.ConferenceDateTime = s.ConferenceDateTime
            AND m.SessionSeq = s.SessionSeq                        
        INNER JOIN [VideoStream] AS v WITH (NOLOCK) ON -- only look at Video related feedback
            v.MediaLineLabel = m.MediaLineLabel    
            and v.ConferenceDateTime = m.ConferenceDateTime 
            and v.SessionSeq = m.SessionSeq
            and v.SenderIsCallerPAI = 1                
        INNER JOIN [CallQualityFeedback] AS CallerCqf WITH (NOLOCK) ON
            CallerCqf.ConferenceDateTime  = s.ConferenceDateTime 
            and
            CallerCqf.SessionSeq = s.SessionSeq 
        INNER JOIN [CallQualityFeedbackToken] AS CallerCqfToken WITH (NOLOCK) ON
            CallerCqfToken.ConferenceDateTime  = s.ConferenceDateTime 
            and
            CallerCqfToken.SessionSeq = s.SessionSeq
            and
            CallerCqfToken.FromURI = CallerCqf.FromURI
        INNER JOIN [CallQualityFeedbackTokenDef] AS CallerCqfTokenDef WITH (NOLOCK) ON
            CallerCqfTokenDef.TokenId = CallerCqfToken.TokenId
            and
            CallerCqfToken.TokenId > 20 -- only look at Video related feedback
        INNER JOIN [User] AS Caller WITH (NOLOCK) ON
            Caller.UserKey = CallerCqf.FromURI
```


