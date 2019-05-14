---
title: 'Lync Server 2013: Design interactive voice response call flows'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Design interactive voice response call flows
ms:assetid: f3477f0a-3ad5-4b13-a73c-046aa451db19
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg413020(v=OCS.15)
ms:contentKeyID: 48185826
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Design interactive voice response call flows in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-25_

You can use interactive voice response (IVR) to obtain information from callers and direct the call to the appropriate queue. Question-and-answer pairs determine which queue to use. Depending on the caller’s response, the caller either hears a follow-up question, or is routed to the appropriate queue. The IVR questions and the caller’s responses are provided to the responding agent who accepts the call, providing valuable information to the agent.

<div>

## Overview of IVR Features

The Response Group application offers speech recognition and text-to-speech capabilities in 26 languages. You can enter IVR questions using text-to-speech or a wave (.wav) or Windows Media audio (.wma) file. Callers can respond by using voice or dual-tone multifrequency (DTMF) responses.

Interactive workflows support up to two levels of questions, with each question having up to four possible answers. The IVR asks the caller a question, and depending on the caller’s response, routes the caller to a queue or asks a second question. The second question can also have four possible answers. Depending on the answer to the second-level question, the caller is routed to the appropriate queue.

<div>


> [!NOTE]  
> When you design call flows by using Lync Server Management Shell, you can define any number levels of IVR questions and any number of answers. However, for caller usability, we recommend that you not use more than three levels of questions, with not more than five answers each. In addition, if you design a call flow that has more than two levels of questions with more than four answers each, you cannot edit the call flow by using Lync Server 2013 Control Panel.



</div>

The IVR questions and the caller’s responses are provided to the responding agent who accepts the call.

</div>

<div>

## Working with Speech Technologies

Speech technologies, such as speech recognition and text-to-speech, can enhance customer experience and let people access information more naturally and effectively. However, there can be cases where the specified text or the user voice response is not recognized correctly by the speech engine. For example, the "\#" symbol is translated by the text-to-speech engine as the word "number." This issue can be mitigated by the following:

  - The speech engine gives the caller five attempts to answer the question. If the caller answers the question incorrectly (that is, the answer is not one of the specified responses) or does not provide an answer at all, the caller gets another chance to answer the question. The caller has five attempts to answer the question before being disconnected. You can configure the IVR to play a customized message after each caller error. The question is repeated each time.

  - To minimize the potential for ambient noise to be interpreted by the speech engine as a response, use longer responses. For example, responses should have more than one syllable and should sound significantly different from each other.

  - If your questions have both speech and DTMF responses, configure the speech responses with words that represent the concept rather than the DTMF response. For example, instead of using "Press or say one" use "Press 1 or say billing."

  - After you design your IVR, call the workflow, listen to the prompts, respond to each of the prompts using voice, and verify that the IVR sounds and behaves as expected. You can then modify the IVR to fix any interpretation issues. Following the previous example, if you need to refer to the \# key, you can rewrite your IVR prompt to use the key name, rather than the \# symbol. For example, "To talk to sales, press the pound key."

</div>

<div>

## IVR Design Examples

The following sections contain examples of different IVR scenarios and question-and-answer pairs.

<div>

## IVR with One Level of Questions

The following example shows an IVR that uses one level of questions. It uses speech recognition to detect the caller’s response.

**Question:** "Thank you for calling Human Resources. If you would like to speak to payroll, say payroll. Otherwise, say HR."

  - **Option 1 is selected:** The caller is routed to the payroll team.

  - **Option 2 is selected:** The caller is routed to the human resources team.

The following figure shows the call flow.

**One-level interactive call flow**

![Design Call Flows by Using Interactive Voice Respo](images/Gg413020.4820a9f7-b5b0-4831-b972-baae0c015ec1(OCS.15).jpg "Design Call Flows by Using Interactive Voice Respo")

</div>

<div>

## IVR with Two Levels of Questions

The following example shows an IVR that uses two levels of questions. It allows callers to respond using either speech or DTMF keypad input.

**Question:** "Thank you for calling the IT Help Desk. If you have a network access problem, press 1 or say network. If you have a software problem, press 2 or say software. If you have a hardware problem, press 3 or say hardware."

  - **Option 1 is selected:** The caller is routed to the network support team.

  - **Option 2 is selected:** The caller is asked a follow-up question:
    
    **Question:** "If this is an operating system problem, press 1 or say operating system. If this is a problem with an internal application, press 2 or say internal application. Otherwise, press 3 or say other."
    
      - **Option 1 is selected:** The caller is routed to the operating systems support team.
    
      - **Option 2 is selected:** The caller is routed to the internal applications support team.
    
      - **Option 3 is selected:** The caller is routed to the software support team.

  - **Option 3 is selected:** The caller is asked a follow-up question:
    
    **Question:** "If this is a printer problem press 1. Otherwise, press 2."
    
      - **Option 1 is selected:** The caller is routed to the printer support team.
    
      - **Option 2 is selected:** The caller is routed to the hardware support team.

The following figure shows the call flow.

**Two-level interactive call flow**

![Design Call Flows by Using Interactive Voice Respo](images/Gg413020.a5b62083-312d-4419-898b-d1a225a5379f(OCS.15).jpg "Design Call Flows by Using Interactive Voice Respo")

</div>

</div>

<div>

## Best Practices

The following list describes some best practices for designing your IVR:

  - Let the caller get to the task quickly. Avoid providing too much information or lengthy marketing messages in your IVR.

  - If you want to include a lengthy message, consider appending it to the first question instead of to the welcome message. Callers can bypass the message if it is part of the first question by answering the question, but they cannot bypass the welcome message.

  - Speak in the caller’s language. Avoid stilted language. Speak naturally.

  - Write efficient and effective prompts. Remove any unnecessary options. Structure the information so that the caller’s expected response is at the end of the sentence. For example, “To speak to the sales team, press 1."

  - Make voice responses user friendly. For example, if you specify both DTMF and voice responses, use something like: "To speak to the sales team, press 1 or say sales."

  - Test the IVR on a group of users before you deploy it across your organization.

</div>

</div>

<span> </span>

</div>

</div>

</div>

