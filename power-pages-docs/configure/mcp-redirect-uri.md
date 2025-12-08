---
title: Configure Redirect URI for MCP Server Access
description: Learn how to configure redirect URIs for connecting to the MCP server across web, single-page, mobile, and desktop applications in Microsoft Entra.
#customer intent: As a developer, I want to configure a redirect URI for a web application so that I can enable secure authentication with the MCP server.
author: shwetamurkute
ms.author: smurkute
ms.reviewer: smurkute
ms.date: 12/04/2025
ms.topic: how-to
---

# Configure redirect URIs for MCP clients

This article shows you how to configure redirect URIs in your third-party app registration to enable different types of AI clients to connect to your MCP Server. Redirect URIs specify where the Microsoft identity platform sends security tokens after authentication.

After you complete these steps, your chosen AI clients can authenticate and connect to your Power Pages MCP Server.

## Prerequisites

Before you begin, make sure you have:

- Completed the [Enable MCP Server in Power Pages](mcp-configure-entra.md) configuration.
- A third-party app registration created in Microsoft Entra admin center.
- Access to the Microsoft Entra admin center with permissions to modify app registrations.
- Knowledge of which client types you need to support (web, single-page application, or mobile/desktop).

## Add platform configuration

Configure the authentication platform for your third-party app registration to specify redirect URIs for your client types.

1. Go to the [Microsoft Entra admin center](https://entra.microsoft.com/#view/Microsoft_AAD_IAM/EntraLanding.ReactView).

1. Select **App registrations**, locate the third-party app you created, select **Authentication**, and then select **Add a platform**.

      :::image type="content" source="media/mcp-redirect-url/image1.png" alt-text="Screenshot that shows the Authentication page with the Add a platform button highlighted.":::

   :::image type="content" source="media/mcp-redirect-url/image2.png" alt-text="Screenshot that shows the Configure platforms dialog with platform options including Web, Single-page application, and Mobile and desktop applications.":::

## Configure redirect URI for web applications

Use this configuration to enable AI clients that run in web browsers, such as Claude or ChatGPT.

1. Select **Web** from the platform options.

2. Enter the redirect URL for your AI client application. For example, for Claude, use: `https://claude.ai/api/mcp/auth_callback`

3. Select **Configure**.

   :::image type="content" source="media/mcp-redirect-url/image3.png" alt-text="Screenshot of the Configure Web platform dialog with redirect URI field showing Claude's callback URL.":::

> [!TIP]
> Each AI client application has its own specific callback URL. Check the documentation for your chosen AI client to find the correct redirect URI.

## Configure redirect URI for single-page applications

Use this configuration to test MCP Server connections from localhost during development.

1. Select **Single-page application** from the platform options.

2. Enter the localhost URL: `http://localhost:33418`

3. Select **Configure**.

   :::image type="content" source="media/mcp-redirect-url/image4.png" alt-text="Screenshot of the Configure Single-page application dialog with localhost redirect URI.":::

> [!NOTE]
> This configuration is primarily for testing and development purposes. For production scenarios, use web or mobile/desktop platform configurations.

## Configure redirect URI for mobile and desktop applications

Use this configuration to enable desktop AI clients, such as VS Code extensions or other native applications.

1. Select **Mobile and desktop applications** from the platform options.

2. Enter the local loopback address: `http://127.0.0.1:33418`

3. Select **Configure**.

   :::image type="content" source="media/mcp-redirect-url/image5.png" alt-text="Screenshot of the Configure Mobile and desktop applications dialog with loopback address redirect URI.":::

> [!IMPORTANT]
> The loopback address `127.0.0.1` is used instead of `localhost` for desktop applications to ensure compatibility across different operating systems and network configurations.

## Verify configuration

After adding your platform configurations, verify that the redirect URIs appear in the Authentication settings of your app registration. You can add multiple platform configurations to support different client types simultaneously.

## Next steps

Now that you've configured redirect URIs, you can connect AI clients to your MCP Server.

> [!div class="nextstepaction"]
> [Connect to MCP Server via Microsoft Copilot Studio](mcp-connect-clients.md)

## Related content

- [Enable MCP Server in Power Pages](mcp-configure-entra.md)
- [Model Context Protocol (MCP) Server for Power Pages overview](mcp-overview.md)
- [Redirect URI (reply URL) restrictions and limitations](/entra/identity-platform/reply-url)
