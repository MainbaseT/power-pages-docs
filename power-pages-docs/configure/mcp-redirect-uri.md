---
title: Configure redirect URI for MCP server access
description: Learn how to configure redirect URIs for connecting to the MCP server across web, single-page, mobile, and desktop applications in Microsoft Entra.
#customer intent: As a developer, I want to configure a redirect URI for a web application so that I can enable secure authentication with the MCP server.
author: shwetamurkute
ms.author: vipingulati
ms.reviewer: smurkute
ms.date: 01/28/2026
ms.topic: how-to
---

# Configure redirect URIs for MCP clients

This article shows you how to configure redirect URIs in your third-party app registration to enable different types of AI clients to connect to your MCP Server. Redirect URIs specify where the Microsoft identity platform sends security tokens after authentication. Configure redirect URIs in platform configurations in the Microsoft Entra admin center. For web and single-page applications, specify a redirect URI manually. For mobile and desktop platforms, select from generated redirect URIs. For more information, see [Add a redirect URI to your application](/entra/identity-platform/how-to-add-redirect-uri).

After you complete the following steps, your chosen AI clients can authenticate and connect to your Power Pages MCP server.

## Prerequisites

Before you begin, make sure you have:

- Completed the [identity provider setup](mcp-configure-entra.md) and [configured site settings for MCP](mcp-configure-site-settings.md)
- Access to the Microsoft Entra admin center with permissions to modify app registrations
- Knowledge of which client types you need to support (web, single-page application, or mobile/desktop)

## Add platform configuration

Configure the authentication platform for your third-party app registration to specify redirect URIs for your client types.

1. Go to the [Microsoft Entra admin center](https://entra.microsoft.com/#home).
1. Select **App registrations** and then locate the third-party app you created.
1. Select **Authentication**, and then select **Add Redirect URI**.

## Configure redirect URI for web applications

Use this configuration to access MCP server via apps such as Microsoft 365.

1. Select **Web** from the platform options.
1. Enter the redirect URL for your AI client application.
1. Select **Configure**.

## Configure redirect URI for single-page applications

Use this configuration to test MCP Server connections from localhost.

1. Select **Single-page application** from the platform options.
1. Enter the URL of the single-page application (for example, `www.example.com/callback`).
1. Select **Configure**.

> [!NOTE]
> Use this configuration primarily for testing and development purposes. For production scenarios, use web, mobile, or desktop platform configurations.

## Configure redirect URI for mobile and desktop applications

Use this configuration to enable desktop AI clients, such as VS Code extensions or other native applications.

1. Select **Mobile and desktop applications** from the platform options.
1. Enter the local loopback address. For example, for VSCode - `http://127.0.0.1:33418`. 
1. Select **Configure**.

> [!IMPORTANT]
> Use the loopback address `127.0.0.1` instead of `localhost` for desktop applications to ensure compatibility across different operating systems and network configurations.

## Verify configuration

After adding your platform configurations, verify that the redirect URIs appear in the Authentication settings of your app registration. You can add multiple platform configurations to support different client types simultaneously.

## Next steps

After configuring redirect URIs, you can connect AI clients to your MCP Server.

> [!div class="nextstepaction"]
> [Connect to MCP Server via Microsoft 365 Copilot](mcp-connect-clients.md)
