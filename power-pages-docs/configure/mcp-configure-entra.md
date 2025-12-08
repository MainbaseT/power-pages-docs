---
title: Create and configure Microsoft Entra External ID in Power Pages
description: Learn how to configure Microsoft Entra External ID for your Power Pages site. Follow step-by-step instructions to set up identity providers and API scopes.
#customer intent: As a Power Pages admin, I want to configure Microsoft Entra External ID as an identity provider so that users can securely authenticate on my site.
author: shwetamurkute
ms.author: smurkute
ms.reviewer: smurkute
ms.date: 12/08/2025
ms.topic: how-to
ms.collection: bap-ai-copilot
---


# Create and configure Microsoft Entra External ID

This article shows you how to set up Microsoft Entra External ID as an identity provider for your Power Pages site and configure it to expose the MCP scope. This is the first step for implementing MCP server in Power Pages. Microsoft Entra External ID serves as the primary authentication provider that handles user authentication and exposes the necessary API scopes for MCP server access.

## Prerequisites

Before you begin, ensure you have:

- A functional Power Pages site.
- Maker or admin access to the Power Pages environment.
- Access to an MCP protocol-compatible client (VS Code, Microsoft Copilot Studio).
- Access to the Microsoft Entra admin center with permissions to create app registrations.


## Configure Microsoft Entra External ID

Follow these steps to set up Microsoft Entra External ID in Power Pages and configure it to expose the MCP scope:

1. [Add Microsoft Entra External ID as an identity provider.](../security/authentication/entra-external-id#step-1-add-microsoft-entra-external-id-as-an-identity-provider)
1. [Set up Microsoft Entra External ID in the admin center.](../security/authentication/entra-external-id#step-2-set-up-microsoft-entra-external-id-in-the-admin-center)
1. In the [Microsoft Entra admin center](https://entra.microsoft.com/#home), select **App registrations** from the navigation pane.
1. Select required application, select **Expose an API**, and then select **Add a scope**.
   :::image type="content" source="media/mcp-overview/entra-admin-expose-api.png" alt-text="Screenshot showing the Expose an API section with Add a scope button.":::
1. Append `/mcp` in the field **Scope name** and enter the following information for the rest of the fields:
   - **Who can consent**: Select **Admins and users**.
   - **Admin consent display name**: Enter `MCP`
   - **Admin consent description**: Enter `MCP`
   - Select **Add scope** to complete.

   :::image type="content" source="media/mcp-overview/entra-admin-add-scope.png" alt-text="Screenshot of the scope configuration showing the MCP scope details with consent settings.":::

## Next steps

Now that you've created and configured Microasoft Entra External ID, configure third party app registration.

> [!div class="nextstepaction"]
> [Create and configure third party app registration](mcp-configure-third-party-app.md)
