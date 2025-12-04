---
title: Enable MCP Server in Power Pages for AI Integration
description: Learn how to enable the MCP Server feature in Power Pages to securely connect AI agents with your Dataverse data. Follow this step-by-step guide.
#customer intent: As a Power Pages admin, I want to enable MCP Server so that AI agents can securely interact with my site data.
author: shwetamurkute
ms.author: smurkute
ms.reviewer: smurkute
ms.date: 12/04/2025
ms.topic: how-to
ms.collection: bap-ai-copilot
---

# Enable MCP Server in Power Pages

This article shows you how to enable the Model Context Protocol (MCP) Server feature in your Power Pages site so that AI agents and copilots can securely interact with your data. When you enable MCP Server, AI agents and copilots can securely interact with your Power Pages data through a standardized interface.

After you complete these steps, your Power Pages site accepts connections from MCP-compatible AI clients, lets them perform CRUD operations on your Dataverse data, and respects your security settings.

## Configure Microsoft Entra External ID

Set up Microsoft Entra External ID as an identity provider for your Power Pages site and configure it to expose the MCP scope.

1. Open your Power Pages site in Power Pages Studio.

2. Select the **Security** tab, then select **Identity Providers**, and select **New provider**.

   :::image type="content" source="media/enable-mcp-server/image1.png" alt-text="Screenshot of Power Pages Studio showing the Security tab with Identity Providers option and New provider button highlighted.":::

3. On the provider configuration screen, select **Microsoft Entra External ID**.

   :::image type="content" source="media/enable-mcp-server/image2.png" alt-text="Screenshot showing the identity provider selection screen with Microsoft Entra External ID option.":::

4. Follow the instructions in [Set up Microsoft Entra External ID with Power Pages](../security/authentication/entra-external-id.md) to complete the setup.

   :::image type="content" source="media/enable-mcp-server/image3.png" alt-text="Screenshot of the Microsoft Entra admin center showing an app registration named MCP-DemoTesting.":::

5. In the Microsoft Entra admin center, go to your app registration, select **Expose an API**, and then select **Add a scope**.

   :::image type="content" source="media/enable-mcp-server/image4.png" alt-text="Screenshot showing the Expose an API section with Add a scope button.":::

   :::image type="content" source="media/enable-mcp-server/image5.png" alt-text="Screenshot of the Add a scope dialog box.":::

6. In the scope field, append `/mcp` to the Application ID URI, and then select **Save**. On the following screen, configure the scope:
      - **Who can consent**: Select **Admins and users**.
   - **Admin consent display name**: Enter `MCP`.
   - **Admin consent description**: Enter `MCP`.
   - Select **Add scope** to complete.

   :::image type="content" source="media/enable-mcp-server/image6.png" alt-text="Screenshot of the scope configuration showing the MCP scope details with consent settings.":::

## Create third-party app registration

Create a separate app registration that AI clients use to authenticate with the MCP server.

1. Go to the [Microsoft Entra admin center](https://entra.microsoft.com/#home), select **App registrations**, and then select **New registration**.

   :::image type="content" source="media/enable-mcp-server/image7.png" alt-text="Screenshot of Microsoft Entra admin center showing App registrations page with New registration button.":::

2. Enter a name for your application (for example, `MCP-Demo-Testing`) and select **Register**.

   :::image type="content" source="media/enable-mcp-server/image8.png" alt-text="Screenshot of the Register an application form with application name field.":::

3. Complete the user flow creation by following the steps in [Create a user flow](../security/authentication/entra-external-id.md#create-a-user-flow).

4. Add your application to the user flow by following the steps in [Add your application to the user flow](../security/authentication/entra-external-id.md#add-your-application-to-the-user-flow).

5. In the Microsoft Entra admin center, go to **App registrations**, select **All applications**, and locate the application you created.

   :::image type="content" source="media/enable-mcp-server/image9.png" alt-text="Screenshot showing the list of all applications in App registrations.":::

6. Select **API permissions**, and then select **Add a permission**.

   :::image type="content" source="media/enable-mcp-server/image10.png" alt-text="Screenshot of API permissions page with Add a permission button.":::

   :::image type="content" source="media/enable-mcp-server/image11.png" alt-text="Screenshot showing the Request API permissions panel.":::

7. On the **Request API permissions** panel, select **APIs my organization uses**, search for the Microsoft Entra External ID app you created earlier, and select it.

   :::image type="content" source="media/enable-mcp-server/image12.png" alt-text="Screenshot of the API selection showing the search results for the organization's APIs.":::

8. Select the checkbox next to **MCP** and select **Add permissions**.

   :::image type="content" source="media/enable-mcp-server/image13.png" alt-text="Screenshot showing the MCP permission selection with checkbox selected.":::

9. Select **API permissions** again, then select **Add a permission**. This time, select **Microsoft APIs** and then select **Microsoft Graph**.

   :::image type="content" source="media/enable-mcp-server/image14.png" alt-text="Screenshot of Request API permissions panel showing Microsoft APIs tab with Microsoft Graph option.":::

10. Select **Delegated permissions**, select the checkboxes next to **openid** and **profile**, and then select **Add permissions**.

    :::image type="content" source="media/enable-mcp-server/image15.png" alt-text="Screenshot showing delegated permissions selection with openid and profile permissions selected.":::

11. Select **Grant admin consent for [your tenant]**, and then select **Yes** to finish the permissions setup.

    :::image type="content" source="media/enable-mcp-server/image16.png" alt-text="Screenshot of API permissions page showing the Grant admin consent button and permission status.":::

## Configure site settings

Create the required site settings to enable MCP Server functionality in your Power Pages site.

1. Navigate to the Power Pages maker portal, open **Portal Management**, and select **Site Settings**.

   :::image type="content" source="media/enable-mcp-server/image17.png" alt-text="Screenshot of Portal Management navigation with Site Settings option.":::

   :::image type="content" source="media/enable-mcp-server/image18.png" alt-text="Screenshot of the Site Settings list view.":::

2. Create six site settings by selecting **New** for each setting. Configure each setting as described in the following steps.

   :::image type="content" source="media/enable-mcp-server/image19.png" alt-text="Screenshot showing the New button to create a new site setting.":::

### Enable bearer authentication

Create a site setting to enable bearer token authentication.

- **Name**: `Authentication/BearerAuthentication/Enabled`
- **Value**: `True`

Select **Save & Close**.

:::image type="content" source="media/enable-mcp-server/image20.png" alt-text="Screenshot of site setting configuration for bearer authentication enabled.":::

### Set authentication protocol

Create a site setting to specify the authentication protocol.

- **Name**: `Authentication/BearerAuthentication/Protocol`
- **Value**: `OpenIdConnect`

Select **Save & Close**.

:::image type="content" source="media/enable-mcp-server/image21.png" alt-text="Screenshot of site setting configuration for authentication protocol.":::

### Configure authentication provider

Create a site setting to identify the authentication provider.

- **Name**: `Authentication/BearerAuthentication/Provider`
- **Value**: `OPENID_1`

Select **Save & Close**.

:::image type="content" source="media/enable-mcp-server/image22.png" alt-text="Screenshot of site setting configuration for authentication provider.":::

### Set MCP client ID

Create a site setting with the client ID from your third-party app registration.

- **Name**: `Authentication/OpenIdConnect/OPENID_1/MCPClientId`
- **Value**: [Your third-party app client ID]

Select **Save & Close**.

:::image type="content" source="media/enable-mcp-server/image23.png" alt-text="Screenshot of site setting configuration for MCP client ID.":::

### Configure MCP scope

Create a site setting with the required OAuth scopes. The value should include your MCP scope URI followed by `openid` and `profile`, all separated by spaces.

- **Name**: `Authentication/OpenIdConnect/OPENID_1/MCPScope`
- **Value**: `[Your MCP scope URI] openid profile`

Select **Save & Close**.

:::image type="content" source="media/enable-mcp-server/image24.png" alt-text="Screenshot of site setting configuration for MCP scope with multiple scope values.":::

### Enable MCP Server

Create the final site setting to enable the MCP Server feature.

- **Name**: `MCP/Enabled`
- **Value**: `true`

Select **Save & Close**.

:::image type="content" source="media/enable-mcp-server/image25.png" alt-text="Screenshot of site setting configuration enabling MCP Server feature.":::

## Next steps

After enabling MCP Server, you need to configure redirect URIs for the AI clients that will connect to your server.

> [!div class="nextstepaction"]
> [Configure redirect URIs for MCP clients](configure-redirect-uris.md)

## Related content

- [Model Context Protocol (MCP) Server for Power Pages overview](mcp-overview.md)
- [Connect AI clients to MCP Server](connect-mcp-clients.md)
- [Set up Microsoft Entra External ID with Power Pages](../security/authentication/entra-external-id.md)
