---
title: Configure site settings for MCP server in Power Pages
description: Learn how to configure site settings in Power Pages to enable MCP Server functionality, including bearer authentication, protocols, and client ID setup.
#customer intent: As a Power Pages admin, I want to configure site settings to enable MCP server functionality so that I can integrate AI clients with my site.
author: shwetamurkute
ms.author: vipingulati
ms.reviewer: smurkute
ms.date: 12/08/2025
ms.topic: how-to
---

# Configure site settings for MCP server

This article shows you how to configure the required site settings in Power Pages to enable MCP server functionality. These settings control bearer authentication, specify the OpenID Connect protocol, and connect your MCP client application.

## Prerequisites

Before you begin, ensure you have:

- Completed the [Create and configure third party app registration](mcp-configure-third-party-app.md) setup
- The client ID from your third-party app registration
- The full MCP scope URI from your Microsoft Entra External ID app
- Access to Power Pages Management in the Power Pages maker portal

## Access site settings

Navigate to the site settings configuration area in Portal Management.

1. Sign in to [Power Pages studio](https://make.powerpages.microsoft.com/) and locate your site where you want to access the settings.
1. Select **Power Pages Management** from the navigation menu.
1. Select **Site Settings** from the Portal Management menu.

## Create site settings

Create six site settings to enable and configure MCP server functionality. For each setting, select **New** to create a new site setting record.

The following table lists all the site settings required to enable MCP server:

| Site setting |  Name | Value |
|-------|------------------|-------|
| Enable bearer authentication | `Authentication/BearerAuthentication/Enabled` | `True` |
| Set authentication protocol | `Authentication/BearerAuthentication/Protocol` | `OpenIdConnect` |
| Configure authentication provider | `Authentication/BearerAuthentication/Provider` | `OPENID_1` <br><br>**Note**: The provider name `OPENID_1` is used as a configuration identifier. The subsequent settings use this same identifier to group related authentication settings. |
| Set MCP client ID | `Authentication/OpenIdConnect/OPENID_1/MCPClientId` | Your third-party app client ID <br><br>**Note**: You can find the client ID in the Microsoft Entra admin center under your third-party app registration's Overview page. It's labeled as "Application (client) ID". |
| Configure MCP scope | `Authentication/OpenIdConnect/OPENID_1/MCPScope` | [Your MCP scope URI] openid profile. The value should contain three space-separated scopes, your full MCP scope URI (for example, `api://00000000-0000-0000-0000-000000000000/mcp`), `openid` and `profile` <br><br>**Note**: Ensure all three scopes are included and separated by single spaces. The MCP scope URI must match exactly the scope you created in your Microsoft Entra External ID app registration. |
| Enable MCP server | `MCP/Enabled` | `true` |


## Verify configuration

After creating all six site settings, verify that they're correctly configured:

1. Review each site setting to ensure the names match exactly (including case sensitivity).
1. Confirm that the client ID matches your third-party app registration.
1. Verify that the MCP scope includes all three required scopes.
1. Ensure all boolean values (`True`, `true`) are spelled correctly.

> [!IMPORTANT]
> Incorrect site setting names or values will prevent the MCP server from functioning properly. Double-check all entries before proceeding.

## Next steps

Now that you've configured site settings, you need to set up redirect URIs to enable AI clients to authenticate with your MCP server.

> [!div class="nextstepaction"]
> [Configure redirect URIs for MCP clients](mcp-redirect-uri.md)
