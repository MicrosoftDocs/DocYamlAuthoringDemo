---
title: Microsoft Learn support - Troubleshooting known issues
description: Troubleshooting resources for Microsoft Learn.
author: Sadadow
ms.author: Saadad
ms.date: 04/04/2019
ms.topic: article
ms.prod: learning
featureFlags: 
- show_feedback_report
# layout: ContentPage
---
# Troubleshooting known issues

We’re continually improving Microsoft Learn. But if you have a issue, one of these troubleshooting steps might help.

| Common issue or error message        | Recommended quick fix  |
| :-------------------------------------- |:-----------------------|
| MSA account requires additional verification steps|The account that you use to sign into docs may need verification if you haven’t used that account for a while, like email or phone verification or more complicated steps. There is no resolution for this issue at this time. If this happens, you will have to follow additional verification process to be able to sing into your docs account.|
| You get an error when you're activating the sandbox, such as “An unexpected error occurred” or “Hmm, something went wrong.”       |     Continue to select the **Retry activating sandbox** button. Waiting and coming back to the page at a later time will often fix the issue.  |
| Invitation redemption failed.   |   In your browser, go back to the unit page and accept the invitation again.  |
|Cloud Shell is blank after Sandbox is activated | For Cloud Shell to work on Microsoft Learn, you need to have third-party cookies enabled in your browser. Use the following steps for your browser to enable them. <br><br>**Internet Explorer** - go to Internet Options > Privacy > Advanced > Accept Third-party Cookies <br>**Firefox** - go to Tools > Options > Privacy > Accept Third-party Cookies <br>**Chrome** - go to Settings > Privacy and security > Content Setting > Cookies, and turn off "Block third-party cookies."|
|You're signed into the cloud shell with an account that's different from your docs account. |Click the "Sign out"button below the error message. If that still doesn't fix the issue, we recommend clearing your browser’s cache/cookies and login with an incognito window again.|
| You get an “AuthorizationFailed” or “does not have authorization to perform action” or “resource group not found” error. | Try the steps again by signing in through a new, private browser window. If that fixes the issue, we recommend clearing your browser’s cache/cookies before you try again in your normal browser window.|
| Storage creation failed. |   Try the steps again by signing in through a new, private browser window. If that fixes the issue, we recommend clearing your browser’s cache/cookies before you try again in your normal browser window.   |
| You're unable to provision Azure resources. | We currently block users with the onmicrosoft.com domain for security and fraud prevention. We're looking for ways to remove this restriction going forward. For now, we recommend that you use the Azure Sandbox with a personal Microsoft account. |
| Azure Cloud Shell opens without bringing up the prompt. |   This is a known issue in Edge and Safari. For now, use Chrome for the best user experience.  |
| The resource group is in a deprovisioning state and can't perform this operation, or the resource group is deleted. |   There's a one-hour time limit for the VM-related sandbox, and a four-hour time limit for other sandboxes. The whole module must be finished before it times out. If it times out, you won't be able to use the expired sandbox. Activate a new sandbox and start from the first unit again. |
| Progress isn't saving. | Progress can take a few seconds to register in our system, so it might look like it isn't registered right away. Try refreshing the page after a few seconds. If the issue persists, please reach out to our team. |
| Completing a module or learning path doesn't grant you a badge/trophy. | This issue primarily occurs when using Internet Explorer to view profiles. Try again with Edge, Chrome, or Firefox. |
| Deployment failed or you get a "The template deployment failed because of policy violation" error. |   Please let us know by sending a message to our team. Include any relevant reproduction steps, error messages, and/or screenshots.|
| You get a "No such file or directory" error. |   Please check you are using the right commands. |
| The sandbox for this module is temporarily disabled for maintenance. |  We're working on improvements to the module. Please check back again later. |
