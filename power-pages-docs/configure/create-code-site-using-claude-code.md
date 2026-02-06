---
title: Tutorial on how to create and configure single-page application using agentic AI coding tool
description: This page provides a walk-through on how to create, customize, and deploy single-page applications for Microsoft Power Pages using using agentic AI coding tool.
author: neerajnandwana-msft
ms.topic: tutorial
ms.date: 02/06/2026
ms.author: nenandw
ms.reviewer: smurkute
contributors:
- neerajnandwana-msft
- shwetamurkute
---

# Get started with Power Pages plugin for Claude Code

The Power Pages plugin for Claude Code enables AI-assisted development of Power Pages sites using modern single-page application (SPA) frameworks. With this plugin, you can create, configure, and deploy Power Pages sites through a conversational interface.

This article guides you through:

- Installing required software and the plugin
- Creating your first Power Pages SPA site
- Configuring Dataverse tables and Web API access
- Configuring Web roles, table permissions and site settings
- Connecting your frontend to backend data

## Prerequisites

Before you begin, verify that you have the required software and permissions.

### Software requirements

| Component | Minimum version | More information |
|-----------|-----------------|------------------|
| Node.js | 18.0 or later | [Download Node.js](https://nodejs.org/) |
| Visual Studio Code | Latest | [Download VS Code](https://code.visualstudio.com/) |
| Power Platform Tools extension | Latest | [Install Power Platform Tools](/power-platform/developer/tools/devtools-install) |
| Power Platform CLI (PAC CLI) | Latest | [Install PAC CLI](/power-platform/developer/cli/introduction) |
| Azure CLI | Latest | [Install Azure CLI](/cli/azure/install-azure-cli) |

### Permission requirements

You need **System Administrator** or **System Customizer** role for Power Pages and Dataverse.

### Verify your environment

Run the following commands to verify your environment is configured correctly.

**Verify software installations:**

```powershell
node --version          # Should return v18.x or later
code --version          # Should return version number
pac help                # Should display PAC CLI help
az --version            # Should display Azure CLI version
```

**Verify authentication:**

```powershell
pac auth list           # Should show authenticated profile
```

If you're not authenticated, run these commands:

```powershell
pac auth create --url <Instance url>        # Authenticate to Power Platform
```

> [!TIP]
> To get the instance URL, go to Power Pages home, select the **Settings** icon in the upper-right corner, and then select **Session details**.

**Verify Power Platform Tools extension:**

1. Open Visual Studio Code.
1. Select **View** > **Extensions** or press **Ctrl+Shift+X**.
1. Search for **Power Platform Tools**.
1. Verify the extension is installed and enabled.

## Install the plugin

You can install the Power Pages plugin from the Claude Code marketplace or from a local GitHub repository.

### Option 1: Install from marketplace (recommended)

1. Open Claude Code in your terminal.

1. Add the Microsoft marketplace:

   ```bash
   /plugin marketplace add microsoft/power-platform-claude-plugins
   ```

1. Install the Power Pages plugin:

   ```bash
   /plugin install power-pages@power-platform-claude-plugins
   ```

### Option 2: Install from GitHub

1. Clone the repository:

   ```bash
   git clone https://github.com/microsoft/power-platform-claude-plugins.git
   ```

1. Launch Claude Code with the plugin directory:

   ```bash
   claude --plugin-dir /path/to/power-platform-claude-plugins/plugins/power-pages
   ```

## Build your first site

This section guides you through creating a complete Power Pages SPA site with Dataverse tables, Web API configuration, and authentication.

### What you build

By the end of this quickstart, you have a modern single-page application (SPA) deployed to Power Pages with:

- A responsive frontend using React, Angular, Vue, or Astro
- Dataverse tables for data storage
- Web API for frontend-backend communication
- Authentication with role-based access control

### Step 1: Create your site

1. Run the create site skill:

   ```bash
   /create-site
   ```

1. Answer the prompts when Claude asks:

   | Prompt | Description |
   |--------|-------------|
   | Site purpose | Describe what your site does |
   | Framework | Choose React (recommended), Angular, Vue, or Astro |
   | Features | Select landing page, forms, authentication, and other features |
   | Design | Describe your preferred style and colors |

The skill creates a complete SPA project, configures it for Power Pages, builds and previews locally, and uploads and activates on Power Pages.

> [!NOTE]
> Only client side JavaScript frameworks are supported. Server-side rendering frameworks like Next.js, Nuxt.js, Remix, and SvelteKit aren't supported.

### Step 2: Add Dataverse tables

1. Run the setup Dataverse skill:

   ```bash
   /setup-dataverse
   ```

The skill analyzes your site for data patterns, designs an optimal schema, and creates tables with relationships.

### Step 3: Configure Web API access

1. Run the setup Web API skill:

   ```bash
   /setup-webapi
   ```

The skill creates site settings to enable API endpoints, configures web roles (Anonymous, Authenticated), sets up table permissions, and uploads configuration changes.

### Step 4: Connect frontend to API

1. Run the integrate Web API skill:

   ```bash
   /integrate-webapi
   ```

The skill creates a Web API service layer, generates TypeScript interfaces, replaces mock data with API calls, and uploads the updated frontend.

### Step 5: Add authentication (optional)

1. Run the setup auth skill:

   ```bash
   /setup-auth
   ```

The skill adds login/logout functionality, creates role-based UI components, implements protected routes, and uploads the updated frontend.

### Verify your site

After you complete the skills, verify your Power Pages site works correctly.

1. Go to [Power Pages](https://make.powerpages.microsoft.com/).

1. Locate your site in the **Active sites** list.

1. Preview your site on desktop with the **Preview** option.

1. Test the functionality.

## Example: Complete workflow

The following example shows a typical session that creates a product catalog site.

```text
User: /create-site

Claude: What kind of site would you like to create?

User: A product catalog with categories, search, and a contact form

Claude: [Creates React site with products, categories, contact form]
        [Uploads to Power Pages]
        Site created! URL: https://my-site.powerappsportals.com

User: /setup-dataverse

Claude: [Analyzes site, detects products, categories, contact submissions]
        [Creates tables with relationships]
        Tables created: cr_product, cr_category, cr_contactsubmission

User: /setup-webapi

Claude: [Creates site settings, web roles, table permissions]
        [Uploads configuration]
        Web API configured for all tables

User: /integrate-webapi

Claude: [Creates API services, replaces mock data]
        [Uploads updated frontend]
        Frontend now connected to Dataverse!

User: /add-sample-data

Claude: [Inserts 4 categories, 10 products, 3 sample submissions]
        Sample data inserted successfully
```

## Skills reference

The plugin provides eight skills organized into core workflows and optional enhancements.

### Core skills

| Skill | Command | Description |
|-------|---------|-------------|
| Create site | `/create-site` | Create Power Pages SPA sites using React, Angular, Vue, or Astro |
| Setup Dataverse | `/setup-dataverse` | Create Dataverse tables, columns, and relationships |
| Setup Web API | `/setup-webapi` | Configure table permissions, web roles, and site settings |
| Integrate Web API | `/integrate-webapi` | Connect frontend code to Power Pages Web API |
| Setup auth | `/setup-auth` | Implement sign-in/sign-out and role-based access control |

### Enhancement skills

| Skill | Command | Description |
|-------|---------|-------------|
| Add SEO | `/add-seo` | Add SEO assets (meta tags, robots.txt, sitemap.xml, favicon) |
| Add tests | `/add-tests` | Add unit tests (Vitest) and E2E tests (Playwright) |
| Add sample data | `/add-sample-data` | Insert sample data with proper foreign key relationships |

### Recommended workflow

For a complete Power Pages SPA site implementation, run the skills in the following order.

:::image type="content" source="media/workflow-diagram.png" alt-text="Diagram showing the recommended workflow: create-site, setup-dataverse, setup-webapi, integrate-webapi, setup-auth.":::

1. `/create-site` - Create SPA with your chosen framework
1. `/setup-dataverse` - Design and create Dataverse tables
1. `/setup-webapi` - Configure Web API permissions
1. `/integrate-webapi` - Connect frontend to Web API
1. `/setup-auth` - Add authentication (optional)

After each core skill, you can optionally run enhancement skills:

- After `/create-site`: Run `/add-seo` and `/add-tests`
- After `/setup-dataverse`: Run `/add-sample-data`

### Related content

- [Create and deploy a single-page application in Power Pages](https://learn.microsoft.com/en-us/power-pages/configure/create-code-sites)
- [Power Pages Web API reference](https://learn.microsoft.com/en-us/power-pages/configure/web-api-overview)
- [PAC CLI pages command reference](https://learn.microsoft.com/en-us/power-pages/configure/power-platform-cli)

