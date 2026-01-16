---
title: Power Pages Server Logic Debugging Guide
description: Learn how to debug Power Pages server logic locally in Visual Studio Code. Discover supported features, limitations, and how to customize mock runtime values.
author: shwetamurkute
ms.author: nabha
ms.reviewer: smurkute
ms.date: 01/15/2026
ms.topic: how-to
---

# Debug server logic

To help validate and troubleshoot server logic during development, Power Pages provides a lightweight, local debugging experience in Visual Studio Code desktop. This debugging capability allows you to set breakpoints, step through code, and inspect variables without deploying to your live site.

While the runtime environment is partially mocked, it enables faster development iteration and early validation of server logic before deployment. This article explains how to debug server logic, what functionality is supported during debugging, and important limitations to understand.

## Prerequisites

Before you begin debugging server logic, ensure that you have:

- A Power Pages site with server logic configured
- Visual Studio Code desktop installed on your machine
- The Power Pages Visual Studio Code extension installed
- Server logic source code opened in Visual Studio Code desktop

## Start debugging session

Power Pages server logic debugging is enabled through a debug helper method that is automatically provided by the Power Pages Visual Studio Code extension.

1. Open your server logic JavaScript file in Visual Studio Code Desktop.

1. Paste the method name that you want to start debugging at the end of the server logic file.

   Example: `get();`

   Once the method is added, Visual Studio Code recognizes the file as debuggable server logic.

1. Select the **Debug** or **Run** button that appears at the beginning of the file.

1. Set breakpoints at the required lines in your server logic code.

The debugging session starts, and execution pauses at your breakpoints, allowing you to inspect variables and step through the code.

## Understand the debugging model

Server logic debugging in Power Pages uses a mock runtime environment. This means the local debugging experience does not fully replicate the live Power Pages runtime. Understanding what is supported and what is mocked helps you interpret debugging results accurately.

### Supported during debugging

The following functionality supports actual execution during local debugging:

- **[HttpClient](server-objects.md#httpclient)**: This is the only object that supports actual execution. HTTP calls made using this client behave similar to runtime execution and connect to external endpoints.

### Mocked during debugging

All other server logic objects are mocked and return predefined values without connecting to live services. Mocked objects include (but are not limited to):

- Website
- SiteSetting
- User
- Dataverse
- Logger
- Context

These mocked objects allow you to test code structure and logic flow without requiring live connections or affecting production data.

## Customize mock runtime values

To simulate real-world scenarios more accurately during debugging, you can modify the predefined mock values used by the local runtime. This allows you to test different logic paths and edge cases without deploying the server logic to a live site.

1. In your project, open the following file:

   `.vscode/server-logic-debug-runtime.js`

1. Update the predefined values for mocked objects as needed to match your testing scenarios.

1. Save the file.

1. Restart the debugging session to apply the updated mock values.

The new mock values are used in subsequent debugging sessions, allowing you to validate different code paths and conditions.

## Limitations and considerations

When debugging server logic locally, keep the following limitations in mind:

- The debugging experience does not attach to or interact with the live Power Pages runtime environment.
- Debugging is available only in Visual Studio Code Desktop, not in browser-based versions of Visual Studio Code.
- Most server objects are mocked and return static values rather than connecting to live services.
- Results observed during local debugging may differ from production behavior due to the mocked runtime environment.
- Use local debugging primarily for validating code structure, logic flow, and HTTP client operations. Always test deployed server logic in a development or test environment before moving to production.

## Next steps

After debugging your server logic locally, deploy and test your code in a non-production Power Pages environment to validate behavior in the actual runtime environment.
