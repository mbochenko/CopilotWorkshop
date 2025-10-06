# 00: Setup & Configuration

## Scenario

Welcome to the GitHub Copilot Self-Paced Learning Workshop! In this workshop, you'll learn how to leverage GitHub Copilot's powerful AI capabilities to accelerate your software development workflow. You'll build a complete application using one of four exciting project scenarios while mastering Copilot's features.

This setup lab will ensure you have all the necessary tools and configurations in place before diving into hands-on development.

## Prerequisites

Before starting this workshop, ensure you have:

### Required Software
- ✅ **Visual Studio Code** (latest version) OR **GitHub Codespaces**
- ✅ **Git** (2.30 or later)
- ✅ **GitHub Account** with Copilot access (or start a free trial)
- ✅ **Node.js 18+** OR **Python 3.9+** OR **.NET 8+** (depending on your preferred tech stack)

### Recommended VS Code Extensions
- ✅ **GitHub Copilot** (`GitHub.copilot`)
- ✅ **GitHub Copilot Chat** (`GitHub.copilot-chat`)
- ✅ Language-specific extensions based on your choice:
  - JavaScript/TypeScript: ESLint, Prettier
  - Python: Python extension, Pylance
  - .NET: C# Dev Kit, C#

### Hardware Requirements
- 8GB RAM minimum (16GB recommended)
- 2GB free disk space
- Stable internet connection

## Getting Started

- [Verify GitHub Copilot Access](#verify-github-copilot-access)
- [Set Up Your Development Environment](#set-up-your-development-environment)
- [Install Required Extensions](#install-required-extensions)
- [Configure GitHub Copilot](#configure-github-copilot)
- [Set Up MCP Servers](#set-up-mcp-servers)
- [Choose Your Project Scenario](#choose-your-project-scenario)
- [Verify Your Setup](#verify-your-setup)

---

## Verify GitHub Copilot Access

### Step 1: Check Copilot Subscription

1. Navigate to [https://github.com/settings/copilot](https://github.com/settings/copilot)
2. Verify that you have an active Copilot subscription
3. If not, start a **free 30-day trial** or subscribe

   ![GitHub Copilot Subscription](./images/setup-copilot-subscription.png)

### Step 2: Confirm Copilot Settings

1. In the Copilot settings page, ensure:
   - ✅ **Public code suggestions**: Allowed (or match your organization's policy)
   - ✅ **GitHub Copilot in the CLI**: Enabled (optional)
   - ✅ **GitHub Copilot Chat**: Enabled

---

## Set Up Your Development Environment

### Option 1: Use GitHub Codespaces (Recommended)

GitHub Codespaces provides a cloud-based development environment with everything pre-installed.

1. Fork this repository to your GitHub account
2. Click the **Code** button and select **Codespaces**
3. Click **Create codespace on main** (or dev branch)
4. Wait for the environment to initialize (~2-3 minutes)
5. Skip to [Install Required Extensions](#install-required-extensions)

### Option 2: Use Local VS Code

1. **Clone the repository:**

   ```powershell
   # PowerShell
   git clone https://github.com/YOUR-USERNAME/CopilotWorkshop.git
   cd CopilotWorkshop
   ```

   ```bash
   # Bash/Zsh
   git clone https://github.com/YOUR-USERNAME/CopilotWorkshop.git
   cd CopilotWorkshop
   ```

2. **Open in VS Code:**

   ```powershell
   code .
   ```

3. **Set environment variable for repository root:**

   ```powershell
   # PowerShell
   $REPOSITORY_ROOT = git rev-parse --show-toplevel
   ```

   ```bash
   # Bash/Zsh
   export REPOSITORY_ROOT=$(git rev-parse --show-toplevel)
   ```

---

## Install Required Extensions

### Step 1: Install GitHub Copilot Extensions

1. Open VS Code
2. Click the Extensions icon in the sidebar (or press `Ctrl+Shift+X` / `Cmd+Shift+X`)
3. Search for and install:
   - **GitHub Copilot** (`GitHub.copilot`)
   - **GitHub Copilot Chat** (`GitHub.copilot-chat`)

   ![Install Copilot Extensions](./images/setup-extensions.png)

4. Restart VS Code if prompted

### Step 2: Sign In to GitHub

1. Click the **Accounts** icon in the bottom-left corner of VS Code
2. Select **Sign in with GitHub**
3. Authorize VS Code in your browser
4. Return to VS Code

### Step 3: Verify Copilot is Active

1. Open any code file (create a new `.js`, `.py`, or `.cs` file)
2. Type a comment like: `// Function to calculate the sum of two numbers`
3. Press `Enter` and wait for Copilot to suggest code
4. If you see a suggestion, Copilot is working! ✅

   ![Copilot Suggestion](./images/setup-copilot-working.png)

---

## Configure GitHub Copilot

### Step 1: Check Copilot Agent Mode

1. Click the **GitHub Copilot icon** in the Activity Bar (left sidebar)
2. This opens the Copilot Chat panel
3. Verify you're using **Agent Mode** (look for agent selector at the top)

   ![GitHub Copilot Agent Mode](./images/setup-agent-mode.png)

4. Select your preferred AI model:
   - **GPT-4o** (faster, good for most tasks)
   - **Claude Sonnet 4** (better for complex reasoning)

### Step 2: Configure Copilot Settings

1. Open VS Code Settings (`Ctrl+,` / `Cmd+,`)
2. Search for "Copilot"
3. Recommended settings:
   - ✅ **Enable Auto-Completions**: On
   - ✅ **Enable Copilot Chat**: On
   - ✅ **Inline Suggest**: Enabled
   - ✅ **Trigger Automatically**: On (or set to manual if you prefer)

   ![Copilot Settings](./images/setup-copilot-settings.png)

---

## Set Up MCP Servers

**MCP (Model Context Protocol)** allows Copilot to interact with external tools and services for enhanced capabilities.

### Step 1: Install Context7 MCP Server

The Context7 MCP server provides up-to-date documentation for libraries and frameworks.

1. Open the Copilot Chat panel
2. Type the following command:

   ```text
   @terminal install context7 mcp server
   ```

3. Alternatively, install manually:

   **For Node.js projects:**
   ```powershell
   npx @context7/mcp-server
   ```

   **For Python projects:**
   ```powershell
   pip install context7-mcp
   ```

### Step 2: Install Playwright MCP Server (Optional)

This will be covered in detail in [Lab 03](./03-playwright-mcp.md), but you can install it now:

```powershell
# PowerShell
npm install -g @playwright/mcp-server
```

```bash
# Bash
npm install -g @playwright/mcp-server
```

### Step 3: Verify MCP Servers

1. In Copilot Chat, type:

   ```text
   List available MCP servers
   ```

2. You should see `context7` in the list
3. If not, restart VS Code and check again

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

Let's make sure everything is working before proceeding to the labs.

### Test 1: Copilot Code Suggestions

1. Create a new file: `test-copilot.js` (or `.py` or `.cs`)
2. Type the following comment:

   ```javascript
   // Function to reverse a string
   ```

3. Press `Enter` and wait for Copilot to suggest code
4. Accept the suggestion with `Tab`
5. **Expected Result**: Copilot should suggest a complete function

### Test 2: Copilot Chat

1. Open Copilot Chat (`Ctrl+Shift+I` / `Cmd+Shift+I`)
2. Type the following prompt:

   ```text
   Explain how async/await works in JavaScript
   ```

3. **Expected Result**: Copilot should provide a detailed explanation

### Test 3: Agent Mode

1. In Copilot Chat, ensure Agent Mode is enabled
2. Type the following prompt:

   ```text
   Create a simple Express server with one GET endpoint at /hello that returns "Hello World"
   ```

3. **Expected Result**: Copilot should generate code and ask if you want to apply it

### Test 4: Context7 MCP

1. In Copilot Chat, type:

   ```text
   Use context7 to explain how to use React hooks
   ```

2. **Expected Result**: Copilot should fetch React documentation and provide an answer

---

## Troubleshooting

### Issue: Copilot Not Showing Suggestions

**Solutions:**
- Verify your GitHub account is signed in (bottom-left corner)
- Check that Copilot extension is enabled (Extensions panel)
- Restart VS Code
- Check Copilot status icon in the status bar (should not show errors)

### Issue: MCP Server Not Found

**Solutions:**
- Restart VS Code after installing MCP servers
- Verify installation with `npm list -g` (for Node.js) or `pip list` (for Python)
- Check VS Code Output panel for MCP errors

### Issue: Agent Mode Not Available

**Solutions:**
- Update GitHub Copilot extensions to the latest version
- Ensure you have GitHub Copilot Chat installed
- Restart VS Code

### Issue: Copilot Subscription Error

**Solutions:**
- Go to [GitHub Copilot Settings](https://github.com/settings/copilot)
- Verify your subscription is active
- Sign out and sign back in to VS Code

---

## Next Steps

✅ **Setup Complete!** You're now ready to start the workshop labs.

**Recommended Learning Path:**

1. **For 2-hour workshop**: Go to [Lab 01: Copilot Instructions](./01-copilot-instructions.md)
2. **For 3-hour workshop**: Go to [Lab 01: Copilot Instructions](./01-copilot-instructions.md)

**Alternative Paths:**

- If you want to jump straight into coding: [Lab 04: Full-Stack Development](./04-dotnet.md)
- If you're interested in TDD: [Lab 05: Test-Driven Development](./05-tdd-with-copilot.md)

---

## Resources

- [GitHub Copilot Documentation](https://docs.github.com/en/copilot)
- [Copilot Best Practices](../COPILOT_BEST_PRACTICES.md)
- [Workshop Quick Reference](../DEMO_QUICK_REFERENCE.md)

---

**Ready to supercharge your development with GitHub Copilot? Let's go! 🚀**

---

Let's move on to [Lab 01: Copilot Instructions](./01-copilot-instructions.md).
