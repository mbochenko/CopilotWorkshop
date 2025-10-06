# 00: Setup & Configuration

## Scenario

Welcome to the GitHub Copilot Self-Paced Learning Workshop! In this workshop, you'll learn how to leverage GitHub Copilot's powerful AI capabilities to accelerate your software development workflow. You'll build a complete application using one of four exciting project scenarios while mastering Copilot's features.

This setup lab will ensure you have all the necessary tools and configurations in place before diving into hands-on development.

## Prerequisites

Before starting this workshop, ensure you have:

### Required Software
- ✅ **Visual Studio Code** (latest version)
- ✅ **Git** (2.30 or later)
- ✅ **GitHub Account** with **GitHub Copilot license** (active subscription)
- ✅ **Node.js 18+** OR **Python 3.9+** OR **.NET 8+** (depending on your preferred tech stack)

### Required VS Code Extensions
- ✅ **GitHub Copilot** (`GitHub.copilot`)
- ✅ **GitHub Copilot Chat** (`GitHub.copilot-chat`)
- ✅ Language-specific extensions based on your choice:
  - JavaScript/TypeScript: ESLint, Prettier
  - Python: Python extension, Pylance
  - .NET: C# Dev Kit, C#

## Getting Started

- [Set Up Your Development Environment](#set-up-your-development-environment)
- [Set Up MCP Servers](#set-up-mcp-servers)
- [Choose Your Project Scenario](#choose-your-project-scenario)
- [Verify Your Setup](#verify-your-setup)

---

## Set Up Your Development Environment

1. **Clone the repository:**

   ```powershell
   # PowerShell
   git clone https://github.com/mbochenko/CopilotWorkshop.git
   cd CopilotWorkshop
   ```

   ```bash
   # Bash/Zsh
   git clone https://github.com/mbochenko/CopilotWorkshop.git
   cd CopilotWorkshop
   ```

2. **Open in VS Code:**

   ```powershell
   code .
   ```

3. **Verify GitHub Copilot Extensions are installed and active:**

   - Open VS Code Extensions panel (`Ctrl+Shift+X` / `Cmd+Shift+X`)
   - Verify **GitHub Copilot** and **GitHub Copilot Chat** are installed and enabled
   - If not installed, install them now and restart VS Code

4. **Sign in to GitHub:**

   - Click the **Accounts** icon in the bottom-left corner of VS Code
   - Select **Sign in with GitHub** if not already signed in
   - Authorize VS Code in your browser

---

## Set Up MCP Servers

**MCP (Model Context Protocol)** allows GitHub Copilot to interact with external tools and services for enhanced capabilities.

### What are MCP Servers?

MCP servers extend GitHub Copilot's capabilities by providing access to:
- Up-to-date library documentation (Context7)
- Browser automation and testing (Playwright)
- And many other integrations

### Installing MCP Servers for VS Code

Follow the official MCP installation guide from Anthropic:

1. **Visit the MCP GitHub Repository:**
   - Go to [https://github.com/anthropics/anthropic-quickstarts](https://github.com/anthropics/anthropic-quickstarts)
   - Navigate to the **MCP Quickstart Guide** section

2. **Install MCP Servers for VS Code:**
   - Follow the instructions for installing MCP servers in Visual Studio Code
   - The guide provides detailed steps for setting up various MCP servers
   - Common servers include:
     - **Context7**: For accessing library documentation
     - **Playwright**: For browser automation (covered in Lab 03)
     - **GitHub**: For repository interactions

3. **Configure VS Code Settings:**
   - After installation, MCP servers need to be configured in VS Code settings
   - The quickstart guide provides the necessary configuration JSON
   - Restart VS Code after configuration

### Verify MCP Server Installation

1. Open GitHub Copilot Chat in VS Code
2. Look for MCP server indicators in the chat interface
3. You should see available MCP servers listed when relevant

**Note:** Specific MCP servers like Playwright will be configured in detail in subsequent labs (see [Lab 03: Playwright MCP](./03-playwright-mcp.md)).

---

## Choose Your Project Scenario

You'll work on **ONE** project throughout this workshop. Choose based on your interest and available time:

### 💰 Expense Tracker (Recommended for Beginners)
- **Complexity**: ⭐⭐☆☆☆
- **Time**: 45-60 minutes
- **Best For**: Learning CRUD, data visualization, basic business logic
- [View Details](../challenges/expensetracker/README.md)

### 🌤️ Weather App
- **Complexity**: ⭐⭐☆☆☆
- **Time**: 45-60 minutes
- **Best For**: API integration, async operations, caching
- [View Details](../challenges/weatherapp/README.md)

### 🔐 KYC/Document Verification Portal
- **Complexity**: ⭐⭐⭐⭐☆
- **Time**: 90-120 minutes
- **Best For**: Security, file handling, compliance workflows
- [View Details](../challenges/kycportal/README.md)

### 👥 360° Customer View Portal
- **Complexity**: ⭐⭐⭐⭐⭐
- **Time**: 90-120 minutes
- **Best For**: Data aggregation, real-time features, complex dashboards
- [View Details](../challenges/360customer/README.md)

### Decision Made?

Once you've chosen, navigate to your project folder:

```powershell
# PowerShell - Example for Expense Tracker
cd challenges/expensetracker
```

---

## Verify Your Setup

Let's make sure MCP servers are working before proceeding to the labs.

### Verify MCP Server Configuration

1. Open GitHub Copilot Chat in VS Code (`Ctrl+Shift+I` / `Cmd+Shift+I`)

2. Check if MCP servers are available:
   - Look for MCP server indicators in the chat interface
   - MCP servers should be listed when they're relevant to your query

3. **Expected Result**: MCP servers are configured and accessible

**Note:** If MCP servers are not showing up, revisit the [MCP installation guide](https://github.com/anthropics/anthropic-quickstarts) and ensure configuration is correct in VS Code settings.

---

## Next Steps

✅ **Setup Complete!** You're now ready to start the workshop labs.

**Continue to the next lab:**

➡️ [Lab 01: Copilot Instructions](./01-copilot-instructions.md)

---

## Resources

- [GitHub Copilot Documentation](https://docs.github.com/en/copilot)
- [MCP Quickstart Guide](https://github.com/anthropics/anthropic-quickstarts)
- [Copilot Best Practices](../COPILOT_BEST_PRACTICES.md)

---

**Ready to supercharge your development with GitHub Copilot? Let's go! 🚀**
