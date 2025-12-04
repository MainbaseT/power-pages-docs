---
title: Secure AI Integration with MCP Server on Power Pages
description: Enable secure AI interactions with your Power Pages data using the Model Context Protocol (MCP) Server. Learn how to expose APIs, manage permissions, and more.
#customer intent: As a Power Pages maker, I want to enable the MCP Server so that AI agents can securely interact with my portal data and APIs
author: shwetamurkute
ms.author: smurkute
ms.reviewer: smurkute
ms.date: 12/04/2025
ms.topic: concept-article
ms.collection: bap-ai-copilot
---

# Model Context Protocol (MCP) Server for Power Pages overview

The **Model Context Protocol (MCP) Server for Power Pages** lets AI agents and copilots securely interact with Power Pages data through a standardized interface. This capability lets organizations extend their Power Pages sites into AI-native experiences while maintaining full control over security and permissions.

## What is MCP Server for Power Pages?

**MCP Server for Power Pages** is a feature that exposes Power Pages data, APIs, and business logic through an MCP-compliant interface. It lets Large Language Models (LLMs) like ChatGPT, Claude, or Microsoft Copilot Studio perform secure CRUD (Create, Read, Update, Delete) operations on Dataverse data while respecting web roles, table permissions, and authentication boundaries.

As organizations increasingly use AI agents to interact with business data, the need for secure, standardized interfaces between AI systems and enterprise applications grows. The Model Context Protocol provides this standardization, letting AI assistants query and manipulate Power Pages data conversationally through any MCP-compatible AI client.

## Key capabilities

With MCP Server for Power Pages, makers can:

- **Expose Power Pages resources**: Makes data, APIs, and business logic available through an MCP-compliant interface
- **Enable secure CRUD operations**: Allows AI agents to create, read, update, and delete Dataverse records
- **Maintain security controls**: Keeps full control through web roles, table permissions, and authentication boundaries
- **Extend to AI experiences**: Enables Power Pages sites to be consumed from Microsoft Teams, ChatGPT, Claude, or any MCP-aware client
- **Support internal workflows**: Empowers internal teams to perform portal operations without navigating the portal UI

## Prerequisites

Before you implement MCP Server for Power Pages:

- A Power Pages site connected to a Dataverse environment.
- Maker or admin access to the environment.
- Access to an MCP protocol-compatible client (VS Code, Microsoft Copilot Studio).
- The MCP Server for Power Pages feature flag enabled (Preview).


## Next steps

- [Configure MCP Server for Power Pages](mcp-configure.md)
- [Connect AI clients to MCP Server](mcp-connect-clients.md)
- [Set up Microsoft Entra External ID](../security/authentication/entra-external-id.md)




















