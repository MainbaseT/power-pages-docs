---
title: Setup and connect MCP Server through AI chat clients
description: Learn how to connect AI chat clients to your MCP Server for seamless Power Pages data interaction. Follow step-by-step instructions for setup and integration.
#customer intent: As a developer, I want to set up and publish an agent in Microsoft Copilot Studio so that it can be accessed via Microsoft 365 Copilot and Teams.
author: shwetamurkute
ms.author: smurkute
ms.reviewer: smurkute
ms.date: 12/04/2025
ms.topic: how-to
---

# Connect to MCP Server via Microsoft Copilot Studio

This article shows you how to create and configure an agent in Microsoft Copilot Studio that connects to your Power Pages MCP Server. You also learn how to publish the agent to Microsoft 365 Copilot and Teams, and how end users can interact with your Power Pages data through conversational AI.

After completing these steps, users in your organization can perform CRUD operations on Power Pages data through natural language conversations in Microsoft 365 Copilot or Teams.

## Prerequisites

Before you begin, ensure you have:

- Completed the [Enable MCP Server in Power Pages](enable-mcp-server.md) configuration.
- Completed the [Configure redirect URIs for MCP clients](mcp-redirect-uri.md) setup.
- Access to [Microsoft Copilot Studio](https://copilotstudio.microsoft.com/).
- Permissions to create and publish agents in Microsoft Copilot Studio.
- The third-party app registration details (Client ID, Client Secret, Authorization URL, Token URL, and Scopes).
- Microsoft 365 Copilot license for end users who use the agent.

## Create agent in Microsoft Copilot Studio

Create a new agent in Microsoft Copilot Studio that will serve as the interface. Sign in to [Microsoft Copilot Studio](https://copilotstudio.microsoft.com/).

   :::image type="content" source="media/mcp-connect-clients/image1.png" alt-text="Screenshot of the Microsoft Copilot Studio home page.":::

1. In the left navigation pane, select **Create**, and then select **New agent**, and then select **New agent**.

   :::image type="content" source="media/mcp-connect-clients/image2.png" alt-text="Screenshot of the Create menu with New agent option highlighted.":::

   :::image type="content" source="media/mcp-connect-clients/image3.png" alt-text="Screenshot of the new agent creation interface.":::

## Add MCP tool to agent

Configure the Model Context Protocol tool to connect your agent to the Power Pages MCP Server.

1. In the agent configuration, select **Tools**, and then select **Add a tool**.

   :::image type="content" source="media/mcp-connect-clients/image4.png" alt-text="Screenshot of the agent configuration showing the Tools section with Add a tool button.":::

2. In the search bar, enter `Model Context Protocol`, select **Model Context Protocol** from the results, and then select **New tool**.

   :::image type="content" source="media/mcp-connect-clients/image5.png" alt-text="Screenshot of the tool selection dialog with Model Context Protocol in the search results.":::

3. Select **Model Context Protocol** again and enter the MCP server details:
   - **Server Name**: Enter a descriptive name for your server
   - **Server Description**: Enter a description of what the server provides
   - **Server URL**: Enter your Power Pages MCP Server endpoint URL

   :::image type="content" source="media/mcp-connect-clients/image6.png" alt-text="Screenshot showing the Model Context Protocol tool selection.":::

   :::image type="content" source="media/mcp-connect-clients/image7.png" alt-text="Screenshot of the MCP server configuration form with server details fields.":::

## Configure OAuth authentication

Set up OAuth 2.0 authentication to enable secure connections between the agent and your MCP Server.

1. Under **Authentication**, select **OAuth 2.0**, and then select **Manual** as the type.

2. Enter the OAuth configuration details from your third-party app registration:
   - **Client ID**: Enter the application (client) ID
   - **Client Secret**: Enter the client secret value
   - **Authorization URL**: Enter the authorization endpoint
   - **Token URL Template**: Enter the token endpoint
   - **Scopes**: Enter the required scopes (MCP scope, openid, profile)

3. In the **Refresh URL** field, enter a period (`.`).

4. Select **Create**.

   :::image type="content" source="media/mcp-connect-clients/image8.png" alt-text="Screenshot of the OAuth 2.0 configuration form showing authentication settings.":::

   :::image type="content" source="media/mcp-connect-clients/image9.png" alt-text="Screenshot showing the OAuth configuration fields with client ID, secret, and URLs.":::

## Add redirect URI to app registration

Copy the redirect URL from Copilot Studio and add it to your third-party app registration.

1. After the tool is created, copy the **Redirect URL** shown in the success message, and then select **Next**.

   :::image type="content" source="media/mcp-connect-clients/image10.png" alt-text="Screenshot showing the successful tool creation with redirect URL to copy.":::

2. Navigate to the [Microsoft Entra admin center](https://entra.microsoft.com/), select **App registrations**, and locate your third-party app.

3. Select **Authentication**, select **Add URI**, paste the redirect URL, and then select **Save**.

   :::image type="content" source="media/mcp-connect-clients/image11.png" alt-text="Screenshot of the app registration Authentication page with the redirect URI being added.":::

## Create connection for agent

Establish a connection that allows the agent to authenticate with your MCP Server.

1. Return to Microsoft Copilot Studio and select **Next**.

   :::image type="content" source="media/mcp-connect-clients/image12.png" alt-text="Screenshot of the tool configuration wizard showing the Next button.":::

2. Select the **Connection** dropdown and select **Create new connection**.

   :::image type="content" source="media/mcp-connect-clients/image13.png" alt-text="Screenshot showing the Connection dropdown with Create new connection option.":::

3. Select **Create**. A sign-in window appears.

4. Enter your credentials and select **Sign in**.

   :::image type="content" source="media/mcp-connect-clients/image14.png" alt-text="Screenshot of the created connection dialog.":::

   :::image type="content" source="media/mcp-connect-clients/image15.png" alt-text="Screenshot of the authentication flow.":::

   :::image type="content" source="media/mcp-connect-clients/image16.png" alt-text="Screenshot of the sign-in dialog prompting for credentials.":::

5. After signing in, select **Add and configure**.

   :::image type="content" source="media/mcp-connect-clients/image17.png" alt-text="Screenshot showing the Add and configure button after successful authentication.":::

## Publish agent

Make the agent available to users by publishing it and configuring channels.

1. On the agent configuration screen, select **Publish**.

   :::image type="content" source="media/mcp-connect-clients/image18.png" alt-text="Screenshot of the agent configuration screen with Publish button highlighted.":::

2. Select the menu button (three dots) at the top right of the page, and then select **Share**.

   :::image type="content" source="media/mcp-connect-clients/image19.png" alt-text="Screenshot showing the menu button and Share option.":::

3. Select the users or groups that should have access to this agent, assign the **Viewer** role so they can chat with the agent, and then select **Update**.

   :::image type="content" source="media/mcp-connect-clients/image20.png" alt-text="Screenshot of the Share dialog showing user and group access configuration.":::

> [!TIP]
> Before making an agent available to users, provide a clear description and appropriate branding to help users understand the agent's purpose.

## Add channels

Configure the agent to be available in Microsoft Teams and Microsoft 365 Copilot.

1. Select **Channels** and select **Teams and Microsoft 365 Copilot**.

2. In the pane that appears, select **Add channel**.

   :::image type="content" source="media/mcp-connect-clients/image21.png" alt-text="Screenshot of the Channels page showing available channel options.":::

   :::image type="content" source="media/mcp-connect-clients/image22.png" alt-text="Screenshot of the Teams and Microsoft 365 Copilot channel configuration pane.":::

   :::image type="content" source="media/mcp-connect-clients/image23.png" alt-text="Screenshot showing the Add channel button for Teams and Microsoft 365 Copilot.":::

3. After the channel is added, you'll see links to access the agent in Teams and Microsoft 365 Copilot.

   :::image type="content" source="media/mcp-connect-clients/image24.png" alt-text="Screenshot showing the successful channel addition with access links.":::

> [!NOTE]
> For detailed guidance on creating channels and configuring permissions, see [Add an agent to Microsoft Teams](/microsoft-copilot-studio/publication-add-bot-to-microsoft-teams).

## Connect as end user

After the agent is published, end users can add it to Microsoft 365 Copilot and interact with Power Pages data through natural language.

### Prerequisites for end users

- Membership in the organization or group that has access to the agent
- A valid Microsoft 365 Copilot license

### Add agent in Microsoft 365 Copilot

1. Sign in to [Microsoft 365 Copilot](https://copilot.cloud.microsoft/) with your credentials.

2. Add the agent from the left pane. The agent appears in the left pane and the chat interface will open on the right.

   :::image type="content" source="media/mcp-connect-clients/image25.png" alt-text="Screenshot of Microsoft 365 Copilot interface showing the agent added in the left pane.":::

### Perform operations through chat

1. Enter a query related to your Power Pages data. For example: "Find me the account details".

   :::image type="content" source="media/mcp-connect-clients/image26.png" alt-text="Screenshot showing a query being entered in the chat interface.":::

> [!NOTE]
> The current release supports CRUD (Create, Read, Update, Delete) operations through the MCP interface.

### Establish connection (first-time users)

First-time users need to establish a connection through the Connection Manager.

1. When prompted, select the **Open Connection Manager** link.

   :::image type="content" source="media/mcp-connect-clients/image27.png" alt-text="Screenshot showing the prompt to open Connection Manager.":::

2. In the Connection Manager window, select **Connect**.

   :::image type="content" source="media/mcp-connect-clients/image28.png" alt-text="Screenshot of the Connection Manager interface with Connect button.":::

3. Select the menu button (three dots) and select **Add new connection**.

   :::image type="content" source="media/mcp-connect-clients/image29.png" alt-text="Screenshot showing the options menu with Add new connection option.":::

4. Enter your credentials and select **Sign in**. After signing in, select **Submit**.

   :::image type="content" source="media/mcp-connect-clients/image30.png" alt-text="Screenshot of the authentication dialog for creating a new connection.":::

5. After the connection is established, a confirmation message appears.

   :::image type="content" source="media/mcp-connect-clients/image31.png" alt-text="Screenshot showing the successful connection confirmation.":::

6. Return to the chat window and select **Retry** to resubmit your query.

   :::image type="content" source="media/mcp-connect-clients/image32.png" alt-text="Screenshot of the chat window with Retry button after establishing connection.":::

7. After a few moments, the agent returns the response to your query.

   :::image type="content" source="media/mcp-connect-clients/image33.png" alt-text="Screenshot showing the agent's response with requested data in the chat interface.":::

## Next steps

Now that you've connected AI clients to your MCP Server, explore other scenarios and use cases.

> [!div class="nextstepaction"]
> [MCP Server functional scenarios](mcp-overview.md)

## Related content

- [Model Context Protocol (MCP) Server for Power Pages overview](mcp-overview.md)
- [Enable MCP Server in Power Pages](enable-mcp-server.md)
- [Install an agent in Teams and Microsoft 365 Copilot](/microsoft-copilot-studio/publication-add-bot-to-microsoft-teams#install-an-agent-in-teams-and-microsoft-365-copilot)
