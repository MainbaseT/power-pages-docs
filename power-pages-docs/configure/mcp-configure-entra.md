---
title: Create and configure Microsoft Entra ID or Entra External ID in Power Pages
description: Learn how to configure Microsoft Entra ID or Microsoft Entra External ID for your Power Pages site. Follow step-by-step instructions to set up identity providers and API scopes.
author: shwetamurkute
ms.author: vipingulati
ms.reviewer: smurkute
ms.date: 01/19/2026
ms.topic: how-to
ms.collection: bap-ai-copilot
---


# Create and configure Microsoft Entra ID or Microsoft Entra External ID

This article shows you how to set up Microsoft Entra ID or Microsoft Entra External ID as an identity provider for your Power Pages site and configure it to expose the MCP scope. This is the first step for implementing MCP server in Power Pages.

You can choose between two options:
- **Microsoft Entra ID**: Standard identity provider with simpler configuration
- **Microsoft Entra External ID**: External customer identity and access management (CIAM) solution

## Prerequisites

Before you begin, ensure you have:

- A functional Power Pages site
- Maker or admin access to the Power Pages environment
- Access to an MCP protocol-compatible client (VS Code, Microsoft Copilot Studio)
- Access to the Microsoft Entra admin center with permissions to create app registrations


## Configure identity provider

Choose the identity provider you want to configure for your Power Pages site:

### [Microsoft Entra ID](#tab/entra-id)

Follow these steps to set up Microsoft Entra ID in Power Pages and configure it to expose the MCP scope:

1. Go to [Power Pages design studio](https://make.powerpages.microsoft.com) and create your portal or site.
1. Once you create the site, find the application ID of the portal under **Site Details** and copy it.
1. Go to the [Azure Portal](https://portal.azure.com), open **App Registrations**, find your application by using the app ID you copied in the previous step, and select it.
1. On the overview page of the application, expand **Manage**, select **Expose an API**, and then select **Add a scope**.
1. On the **Add a Scope** pane, configure the following settings:
   - **Scope name**: Enter an appropriate scope name.
   - **Who can consent**: Select **Admins and users**.
   - **Admin consent display name**: Enter an appropriate display name.
   - **Admin consent description**: Enter an appropriate description.
   - Select **Add scope** to complete.

### [Microsoft Entra External ID](#tab/entra-external-id)

Follow these steps to set up Microsoft Entra External ID in Power Pages and configure it to expose the MCP scope:

1. [Add Microsoft Entra External ID as an identity provider.](../security/authentication/entra-external-id.md#step-1-add-microsoft-entra-external-id-as-an-identity-provider)
1. [Set up Microsoft Entra External ID in the admin center.](../security/authentication/entra-external-id.md#step-2-set-up-microsoft-entra-external-id-in-the-admin-center)
1. In the [Microsoft Entra admin center](https://entra.microsoft.com/#home), select **App registrations** from the navigation pane.
1. Select the application, select **Expose an API**, and then select **Add a scope**.
   :::image type="content" source="media/mcp-overview/entra-admin-expose-api.png" alt-text="Screenshot showing the Expose an API section with Add a scope button." lightbox="media/mcp-overview/entra-admin-expose-api.png":::
1. In the **Scope name** field, enter `mcp` and configure the following settings:
   - **Who can consent**: Select **Admins and users**.
   - **Admin consent display name**: Enter an appropriate display name.
   - **Admin consent description**: Enter an appropriate description.
   - Select **Add scope** to complete.

---


## Next steps

Now that you've created and configured Microsoft Entra ID or Entra External ID, configure third party app registration.

> [!div class="nextstepaction"]
> [Create and configure third party app registration](mcp-configure-third-party-app.md)
