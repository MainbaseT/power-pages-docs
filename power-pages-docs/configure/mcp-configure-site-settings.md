---
title: Configure site settings for MCP server in Power Pages
description: Learn how to configure site settings in Power Pages to enable MCP Server functionality, including bearer authentication, protocols, and client ID setup.
#customer intent: As a Power Pages admin, I want to configure site settings to enable MCP server functionality so that I can integrate AI clients with my site.
author: shwetamurkute
ms.author: vipingulati
ms.reviewer: smurkute
ms.date: 01/28/2026
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

Create the required site settings to enable and configure MCP server functionality. For each setting, select **New** to create a new site setting record.

The following sections provide the site settings required based on your identity provider:

# [Microsoft Entra ID](#tab/entra-id)

The following table lists all the site settings required to enable MCP server with Microsoft Entra ID:

| Site setting | Name | Value | Description |
|-------|------------------|-------|----------|
| Enable bearer authentication | `Authentication/BearerAuthentication/Enabled` | `True` | Enables bearer token authentication, which lets Power Pages securely pass the authenticated user's token (such as an ID token) to external APIs for API-level authorization. |
| Set authentication protocol | `Authentication/BearerAuthentication/Protocol` | `OpenIdConnect` | This setting specifies the protocol type—most commonly OpenIdConnect—used by the backend to validate tokens passed in the `Authorization: Bearer <token>` HTTP header. |
| Configure authentication provider | `Authentication/BearerAuthentication/Provider` | `AzureAD` | This setting lets administrators define which specific authentication provider (for example, Azure AD B2C or another OpenID Connect compatible service) the Power Pages site uses to validate bearer tokens presented during requests to the site. |
| Use Microsoft Entra V2 Issuer | `Authentication/BearerAuthentication/UseEntraV2Issuer` | `True` <br><br>**Note**: Keep the source as **Table**|This site setting configures how bearer tokens are validated, specifically directing the system to use the Microsoft Entra V2.0 endpoint (v2.0 authority) for authentication token issuance and validation. |
| Set valid issuers | `Authentication/BearerAuthentication/ValidIssuers` | Your issuer URI <br><br>**Note**: To find your issuer URI: <br>1. Go to your app registration **Overview** page in the Microsoft Entra admin center. <br>2. Select **Endpoints**. <br>3. Copy the value under **OpenID Connect metadata document**. <br>4. Open the URL in a browser and locate the **issuer** field. <br>5. Copy the issuer value. | This site setting validates the issuer claim (iss) of incoming JSON Web Tokens (JWT). It ensures that a trusted identity provider issued the bearer token. |
| Set MCP client ID | `Authentication/OpenIdConnect/AzureAD/MCPClientId` | Your third-party app client ID <br><br>**Note**: You can find the client ID in the Microsoft Entra admin center under your third-party app registration's **Overview** page. It's labeled as "Application (client) ID". | This site setting identifies the third-party app registered to enable MCP server. |
| Configure MCP scope | `Authentication/OpenIdConnect/AzureAD/MCPScope` | [Your MCP scope URI] openid profile. The value should contain three space-separated scopes: your full MCP scope URI (for example, `api://00000000-0000-0000-0000-000000000000/mcp`), `openid`, and `profile` <br><br>**Note**: Ensure all three scopes are included and separated by single spaces. The MCP scope URI must match exactly the scope you created in your Microsoft Entra ID app registration. | This site setting defines the OAuth 2.0 scopes that the Power Pages runtime requests when authenticating an MCP client. |
| Enable MCP server | `MCP/Enabled` | `true` | This site setting enables or disables MCP server for the site. |

# [Microsoft Entra External ID](#tab/entra-external-id)

The following table lists all the site settings required to enable MCP server with Microsoft Entra External ID:

| Site setting |  Name | Value | Description |
|-------|------------------|-------|----------|
| Enable bearer authentication | `Authentication/BearerAuthentication/Enabled` | `True` | Enables bearer token authentication, which lets Power Pages securely pass the authenticated user's token (such as an ID token) to external APIs for API-level authorization. |
| Set authentication protocol | `Authentication/BearerAuthentication/Protocol` | `OpenIdConnect` | This setting specifies the protocol type—most commonly OpenIdConnect—used by the backend to validate tokens passed in the `Authorization: Bearer <token>` HTTP header. |
| Configure authentication provider | `Authentication/BearerAuthentication/Provider` | `AzureAD` | This setting lets administrators define which specific authentication provider (for example, Azure AD B2C or another OpenID Connect compatible service) the Power Pages site uses to validate bearer tokens presented during requests to the site. |
| Set MCP client ID | `Authentication/OpenIdConnect/{Provider}/MCPClientId` | Your third-party app client ID <br><br>**Note**: You can find the client ID in the Microsoft Entra admin center under your third-party app registration's Overview page. It's labeled as "Application (client) ID". | This site setting identifies the third-party app registered to enable MCP server.|
| Configure MCP scope | `Authentication/OpenIdConnect/{Provider}/MCPScope` | [Your MCP scope URI] openid profile. The value should contain three space-separated scopes, your full MCP scope URI (for example, `api://00000000-0000-0000-0000-000000000000/mcp`), `openid`, and `profile` <br><br>**Note**: Ensure all three scopes are included and separated by single spaces. The MCP scope URI must match exactly the scope you created in your Microsoft Entra External ID app registration. | This site setting defines the OAuth 2.0 scopes that the Power Pages runtime requests when authenticating an MCP client. |
| Enable MCP server | `MCP/Enabled` | `true` | This site setting enables or disables MCP server for the site. |

---


## Verify configuration

After creating all the site settings, verify that they're correctly configured:

1. Review each site setting to ensure the names match exactly (including case sensitivity).
1. Confirm that the client ID matches your third-party app registration.
1. Verify that the MCP scope includes all three required scopes.
1. Ensure all boolean values (`True`, `true`) are spelled correctly.

> [!IMPORTANT]
> Incorrect site setting names or values prevent the MCP server from functioning properly. Double-check all entries before proceeding.

## Next steps

Now that you've configured site settings, you need to set up redirect URIs to enable AI clients to authenticate with your MCP server.

> [!div class="nextstepaction"]
> [Configure redirect URIs for MCP clients](mcp-redirect-uri.md)
