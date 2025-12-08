---
title: Configure third party app registration in Microsoft Entra
description: Learn how to create and configure third party app registrations in Microsoft Entra. Follow step-by-step instructions to set up user flows and API permissions.
#customer intent: As an IT admin, I want to register a third-party app in Microsoft Entra so that I can enable secure authentication for external users.
author: shwetamurkute
ms.author: smurkute
ms.reviewer: smurkute
ms.date: 12/08/2025
ms.topic: how-to
---

# Create and configure third party app registration

This article shows you how to create a third-party app registration that AI clients will use to authenticate with your MCP server. The third-party app acts as a client application that requests delegated permissions to access the MCP scope exposed by your Microsoft Entra External ID application.

## Prerequisites

Before you begin, ensure you have:

- Completed the [Create and configure Microsoft Entra External ID](mcp-configure-entra.md) setup.
- The name or application ID of the Microsoft Entra External ID app you created.
- Permissions to grant admin consent for API permissions in your tenant.

## Configure the third-party app

1. Sign in to [Microsoft Entra admin center](https://entra.microsoft.com/#home).
1. Select **App registrations**, and then select **New registration**.
1. Enter a name for your application and then select **Register**.
1. Complete the user flow creation by following the steps in [Create a user flow.](../security/authentication/entra-external-id.md#create-a-user-flow).
1. Add your application to the user flow by following the steps in [Add your application to the user flow](../security/authentication/entra-external-id.md#add-your-application-to-the-user-flow).
1. In the [Microsoft Entra admin center](https://entra.microsoft.com/#home), go to **App registrations**, select **All applications**, and locate the application you created.
1. Select **API permissions**, and then select **Add a permission**.
1. On the **Request API permissions** tab, select **APIs my organization uses**, search for the Microsoft Entra External ID app you created earlier, and select it.
   :::image type="content" source="media/enable-mcp-server/image12.png" alt-text="Screenshot of the API selection showing the search results for the organization's APIs.":::
1. Select the checkbox next to **MCP** and select **Add permissions**.
1. Select **API permissions** again, then select **Add a permission**. This time, select **Microsoft APIs** and then select **Microsoft Graph**.
   :::image type="content" source="media/enable-mcp-server/image14.png" alt-text="Screenshot of Request API permissions panel showing Microsoft APIs tab with Microsoft Graph option.":::
1. Select **Delegated permissions**, select the checkboxes next to **openid** and **profile**, and then select **Add permissions**.
   :::image type="content" source="media/enable-mcp-server/image15.png" alt-text="Screenshot showing delegated permissions selection with openid and profile permissions selected.":::
1. Select **Grant admin consent for [your tenant]**, and then select **Yes** to finish the permissions setup.

## Next steps

Now that you've created and configured third party app registration, configure the site settings for MCP server. 

> [!div class="nextstepaction"]
> [Configure site settings for MCP server](mcp-configure-site-settings.md)