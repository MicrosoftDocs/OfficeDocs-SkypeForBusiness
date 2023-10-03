---
title: Understand Insights for Reading Progress recommendations
author: DaniEASmith
ms.author: danismith
manager: serdars
ms.topic: reference
ms.service: msteams
audience: admin
ms.reviewer: 
ms.date: 07/26/2022
description: Learn how Insights data is used in Reading Progress to help improve students' reading proficiency.
search.appverid: MET150
ms.collection: 
  - M365-collaboration
  - m365initiative-edu
  - tier2
appliesto: 
  - Microsoft Teams
---

# Understand Insights for Reading Progress recommendations

This article is for education IT admins who want to understand how Insights data is used for Reading Progress recommendations.

Insights allows educators to track their students' reading fluency using Reading Progress, a tool that records students reading out loud and automatically detects errors.

Reading Progress provides the following types of reading challenge assignments:

- **Contextual words**: practice words recommended based on the words students mispronounced in past Reading Progress assignments.
- **Correlated words**: practice words recommended based on mistakes common to students with the same type of reading challenges.

For educator guidance on using Insights for Reading Progress, see [Create Reading Progress challenge assignments with Insights](https://support.microsoft.com/topic/c2f8f4c0-69d5-4302-b3a5-ee4dfb7a8ffe).

## How does Microsoft recommend correlated words?

Correlated words are personalized, recommended words that Insights for Education identified as challenging for other students who share similar reading patterns.

Correlated words are based on a machine learning technique called **Collaborative filtering**.

- Insights analyzes students’ reading data across classes that share your geographical area and language to identify clusters of words that are challenging to students.

- Given a set of challenging words, Insights also identifies similar clusters and uses those to recommend other words to students for targeted practice.

## Does Microsoft keep students' data private and secure?

Microsoft is committed to using data responsibly and ethically.

Here are some of the measures taken to build this feature:

- Student data analyses are built in an eyes-off manner, meaning Microsoft doesn't have access to students’ reading data, only to the analysis results.

- Tenant admins can opt out from the data analysis process by turning off the [Advanced inferences toggle](class-insights.md#turn-on-and-off-advanced-inferences-in-insights).

- Inappropriate words are filtered out from the **Correlated words** recommendation lists. This is done through a combination of data science techniques and blocking of known problematic words. However, this process isn't error proof. Educators should review the recommendations.

## What are the limitations of Insights' word recommendations?

- Word recommendations for Reading Progress are currently supported in [these languages](https://support.microsoft.com/topic/getting-started-with-reading-progress-in-teams-7617c11c-d685-4cb7-8b75-3917b297c407#ID0EDD=Supported_Languages).

- Correlated words are only presented in classes with at least five students who have submitted Reading Progress assignments.

- Insights may not recommend new words in cases where there are no students with similar, but not identical, mistake patterns.
