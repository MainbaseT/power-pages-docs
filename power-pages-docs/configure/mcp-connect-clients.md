---
title: Setup and connect to MCP Server via Microsoft 365 Copilot
description: Learn how to connect AI chat clients to your MCP Server for seamless Power Pages data interaction. Follow step-by-step instructions for setup and integration.
#customer intent: As a developer, I want to set up and publish an agent in Microsoft 365 Copilot.
author: shwetamurkute
ms.author: smurkute
ms.reviewer: smurkute
ms.date: 12/04/2025
ms.topic: how-to
---

# Connect to MCP server via Microsoft 365 Copilot

This article shows you how to create and configure an agent in Microsoft 365 Copilot that connects to your Power Pages MCP Server, and how end users can interact with your Power Pages data through conversational AI.

After completing these steps, users in your organization can perform CRUD operations on Power Pages data through natural language conversations in Microsoft 365 Copilot.

## Prerequisites

Before you begin, ensure you have:

- Completed the [Configure redirect URIs for MCP clients](mcp-redirect-uri.md) setup
- The third-party app registration details (Client ID, Client Secret, Authorization URL, Token URL, and Scopes)
- Microsoft 365 Copilot license for end users who use the agent

## Create and configure agent in Microsoft Copilot Studio


### Create an agent

Create a new agent in Microsoft Copilot Studio that will serve as the interface.

1. Sign in to [Microsoft Copilot Studio](https://copilotstudio.microsoft.com/).
1. In the left navigation pane, select **Create**, and then select **New agent**. 

This will create a new agent that we will publish later to Microsoft 365 Copilot.  

### Add MCP tool to agent

Configure the Model Context Protocol tool to connect your agent to the Power Pages MCP Server.

1. In the agent configuration, select **Tools**, and then select **Add a tool**.
1. In the search bar, enter `Model Context Protocol`, select **Model Context Protocol** from the results, and then select **New tool**.
   :::image type="content" source="media/mcp-overview/tool-selection-search.png" alt-text="Screenshot of the tool selection dialog with Model Context Protocol in the search results.":::
1. Select **Model Context Protocol** again and enter the MCP server details:
   - **Server Name**: Enter a descriptive name for your server
   - **Server Description**: Enter a description of what the server provides
   - **Server URL**: Enter your Power Pages MCP Server endpoint URL


### Configure OAuth authentication

Set up OAuth 2.0 authentication to enable secure connections between the agent and your MCP Server.

1. Under **Authentication**, select **OAuth 2.0**, and then select **Manual** as the type.
1. Enter the OAuth configuration details from your third-party app registration:
   - **Client ID**: Enter the application (client) ID
   - **Client Secret**: Enter the client secret value
   - **Authorization URL**: Enter the authorization endpoint
   - **Token URL Template**: Enter the token endpoint
   - **Scopes**: Enter the required scopes (MCP scope, openid, profile)
1. In the **Refresh URL** field, enter a period (`.`).
1. Select **Create**.

### Add redirect URI to app registration

Copy the redirect URL from Copilot Studio and add it to your third-party app registration.

1. After the tool is created, copy the **Redirect URL** shown in the success message, and then select **Next**.
1. Navigate to the [Microsoft Entra admin center](https://entra.microsoft.com/), select **App registrations**, and locate your third-party app.
1. Select **Authentication**, select **Add URI**, paste the redirect URL, and then select **Save**.

### Create connection for agent

Establish a connection that allows the agent to authenticate with your MCP Server.

1. Return to Microsoft Copilot Studio and select **Next**.
1. Select the **Connection** dropdown and select **Create new connection**.
1. Select **Create**. A sign-in window appears.
1. Enter your credentials and select **Sign in**.
1. After signing in, select **Add and configure**.

### Publish agent

Make the agent available to users by publishing it and configuring channels.

1. On the agent configuration screen, select **Publish**.
1. Select the menu button (three dots) at the top right of the page, and then select **Share**.
1. Select the users or groups that should have access to this agent, assign the **Viewer** role so they can chat with the agent, and then select **Update**.

:::image type="content" source="media/mcp-overview/share-dialog.png" alt-text="Screenshot of the Share dialog showing user and group access configuration.":::

> [!TIP]
> Before making an agent available to users, provide a clear description and appropriate branding to help users understand the agent's purpose.

### Add channels

Configure the agent to be available in Microsoft 365 Copilot.

1. Select **Channels** and select **Teams and Microsoft 365 Copilot**.
1. In the pane that appears, select **Add channel**.
1. After the channel is added, you'll see links to access the agent in Microsoft 365 Copilot.

   :::image type="content" source="media/mcp-overview/channel-added.png" alt-text="Screenshot showing the successful channel addition with access links.":::

> [!NOTE]
> For detailed guidance on creating channels and configuring permissions, see [Connect and configure an agent for Teams and Microsoft 365](/microsoft-copilot-studio/publication-add-bot-to-microsoft-teams).

## Connect via Microsoft 365 Copilot  

After the agent is published, end users can add it to Microsoft 365 Copilot and interact with Power Pages data through natural language.

### Prerequisites

- Membership in the organization or group that has access to the agent
- A valid Microsoft 365 Copilot license

### Add agent in Microsoft 365 Copilot and perform operations

1. Sign in to [Microsoft 365 Copilot](https://copilot.cloud.microsoft/) with your credentials.
1. Add the agent from the left pane. The agent appears in the left pane and the chat interface will open on the right.
1. Enter a query related to your Power Pages data. For example: "Find me the account details".

> [!NOTE]
> The current release supports CRUD (Create, Read, Update, Delete) operations through the MCP interface.

### Establish connection (first-time users)

First-time users need to establish a connection through the Connection Manager.

1. When prompted, select the **Open Connection Manager** link.
1. In the Connection Manager window, select **Connect**.
1. Select the menu button (three dots) and select **Add new connection**.
   :::image type="content" source="media/mcp-overview/new-connection.png" alt-text="Screenshot showing the options menu with Add new connection option.":::
1. Enter your credentials and select **Sign in**. After signing in, select **Submit**.
1. After the connection is established, a confirmation message appears.
1. Return to the chat window and select **Retry** to resubmit your query.
1.  After a few moments, the agent returns the response to your query.




## Related content

- [Connect to Power Pages MCP server](mcp-overview.md)   
- [Enable Power Pages MCP server](mcp-configure-entra.md)   
- [Connect to Dataverse with Model Context Protocol](/power-apps/maker/data-platform/data-platform-mcp)  
