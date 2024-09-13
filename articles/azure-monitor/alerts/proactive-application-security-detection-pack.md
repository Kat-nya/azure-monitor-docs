---
title: Security detection Pack with Azure Application Insights
description: Monitor application with Azure Application Insights and smart detection for potential security issues.
ms.author: abbyweisberg
ms.topic: conceptual
ms.date: 04/01/2024
ms.reviewer: yagil
---

# Application security detection pack (preview)

Smart detection automatically analyzes the telemetry generated by your application, and detects potential security issues. It enables you to identify potential security problems. You can mitigate these problems by fixing the application, or by taking the necessary security measures.

This feature requires no special setup, other than [configuring your app to send telemetry](../app/usage.md).

## When would I get this type of smart detection notification?
There are three types of security issues that are detected:
1. Insecure URL access: a URL in the application is accessible via both HTTP and HTTPS. Typically, a URL that accepts HTTPS requests shouldn't accept HTTP requests. This detection may indicate a bug or security issue in your application.
2. Insecure form: a form (or other "POST" request) in the application uses HTTP instead of HTTPS. Using HTTP can compromise the user data that is sent by the form.
3. Suspicious user activity: the same user accesses the application from multiple countries or regions, around the same time. For example, the same user accessed the application from Spain and the United States within the same hour. This detection indicates a potentially malicious access attempt to your application.

## Does my app definitely have a security issue?
A notification doesn't mean that your app definitely has a security issue. A detection of any of the scenarios above can, in many cases, indicate a security issue. In other cases, the detection may have a natural business justification, and can be ignored.

## How do I fix the "Insecure URL access" detection?
1. **Triage.** The notification provides the number of users who accessed insecure URLs, and the URL that was most affected by insecure access. This information can help you assign a priority to the problem.
3. **Scope.** What percentage of the users accessed insecure URLs? How many URLs were affected? This information can be obtained from the notification.
4. **Diagnose.** The detection provides the list of insecure requests, and the lists of URLs and users that were affected, to help you further diagnose the issue.

## How do I fix the "Insecure form" detection?
1. **Triage.** The notification provides the number of insecure forms, and number of users whose data was potentially compromised. This information can help you assign a priority to the problem.
2. **Scope.** Which form was involved in the largest number of insecure transmissions, and what is the distribution of insecure transmissions over time? This information can be obtained from the notification.
3. **Diagnose.** The detection provides the list of insecure forms, and a breakdown of insecure transmissions for each form, to help you further diagnose the issue.

## How do I fix the "Suspicious user activity" detection?
1. **Triage.** The notification provides the number of different users that presented the suspicious behavior. This information can help you assign a priority to the problem.
2. **Scope.** From which countries or regions did the suspicious requests originate? Which user was the most suspicious? This information can be obtained from the notification.
3. **Diagnose.** The detection provides the list of suspicious users and the list of countries or regions for each user, to help you further diagnose the issue.