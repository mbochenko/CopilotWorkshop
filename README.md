# GitHub Copilot Workshop 🚀

Welcome to the **GitHub Copilot Self-Paced Learning Workshop**! This comprehensive workshop will teach you how to maximize your productivity with GitHub Copilot through hands-on labs and real-world scenarios.

## 🎯 Workshop Overview

This workshop is designed as a **2-3 hour self-paced learning experience** where you'll build a complete application using GitHub Copilot's advanced features including:

- ✅ Custom Copilot Instructions
- ✅ Custom Chat Modes (TDD Mode)
- ✅ MCP (Model Context Protocol) Server Integration
- ✅ Test-Driven Development with Copilot
- ✅ Documentation Automation

**Time Required:** 2-3 hours  
**Format:** Self-paced, hands-on labs  
**Prerequisites:** Basic programming knowledge (JavaScript, Python, or .NET)

---

## 📋 Workshop Agenda

For a detailed workshop agenda with schedules and learning objectives, see:

👉 **[WORKSHOP_AGENDA.md](./WORKSHOP_AGENDA.md)**

---

## 🎓 Workshop Labs

Complete the labs in order for the best learning experience:

### Core Labs (Required)

| Lab | Title | Duration | Description |
|-----|-------|----------|-------------|
| **[Lab 00](./docs/00-setup.md)** | Setup & Configuration | 15 min | Install Copilot, configure MCP servers, choose your scenario |
| **[Lab 01](./docs/01-copilot-instructions.md)** | Copilot Instructions | 20 min | Create custom `.github/copilot-instructions.md` for your project |
| **[Lab 02](./docs/02-custom-chat-modes.md)** | Custom Chat Modes | 25 min | Build a TDD chat mode for enforcing test-first development |
| **[Lab 03](./docs/03-playwright-mcp.md)** | Playwright MCP Server | 25 min | Integrate Playwright MCP for automated E2E test generation |
| **[Lab 05](./docs/05-tdd-with-copilot.md)** | Test-Driven Development | 30 min | Apply TDD workflow using your custom chat mode |
| **[Lab 06](./docs/06-documentation.md)** | Documentation Automation | 25 min | Auto-generate README, CHANGELOG, and API docs |

### Bonus Lab (Optional)

| Lab | Title | Duration | Description |
|-----|-------|----------|-------------|
| **[Lab 04](./docs/04-dotnet.md)** | .NET Migration Example | 30 min | Migrate a .NET Framework app to .NET 8 (advanced) |

**Total Time:**
- **Express (2 hours):** Labs 00, 01, 02, 05, 06
- **Comprehensive (3 hours):** Labs 00, 01, 02, 03, 05, 06
- **Advanced (3 hours):** All labs including Lab 04

---

## 🏗️ Project Scenarios

Choose ONE scenario to implement throughout the workshop. Each has different complexity and learning focus:

| Scenario | Complexity | Time | Focus Area |
|----------|------------|------|------------|
| **[Expense Tracker](./challenges/expensetracker/README.md)** | ⭐⭐ | 45-60 min | CRUD operations, basic validation |
| **[Weather App](./challenges/weatherapp/README.md)** | ⭐⭐ | 45-60 min | API integration, caching, error handling |
| **[KYC Portal](./challenges/kycportal/README.md)** | ⭐⭐⭐⭐ | 90-120 min | File uploads, security, multi-step workflows |
| **[360° Customer View](./challenges/360customer/README.md)** | ⭐⭐⭐⭐⭐ | 90-120 min | Data aggregation, real-time updates, compliance |

### Scenario Selection Guide

**Beginners (2-hour workshop):** Choose **Expense Tracker** or **Weather App**  
**Intermediate (3-hour workshop):** Choose **KYC Portal**  
**Advanced (3-hour workshop):** Choose **360° Customer View**

---

## 🚀 Quick Start

### Step 1: Environment Setup

**Option A: GitHub Codespaces (Recommended)**

1. Click **Code** → **Create codespace on main**
2. Wait for environment to load (~2-3 minutes)
3. Extensions will install automatically

**Option B: Local Development**

1. Clone this repository:
   ```bash
   git clone https://github.com/yourusername/CopilotWorkshop.git
   cd CopilotWorkshop
   ```

2. Install prerequisites:
   - [Visual Studio Code](https://code.visualstudio.com/)
   - [Node.js 18+](https://nodejs.org/) OR [Python 3.9+](https://www.python.org/) OR [.NET 8+](https://dotnet.microsoft.com/)
   - [GitHub Copilot](https://marketplace.visualstudio.com/items?itemName=GitHub.copilot) extension
   - [GitHub Copilot Chat](https://marketplace.visualstudio.com/items?itemName=GitHub.copilot-chat) extension

### Step 2: Choose Your Scenario

Browse the [Project Scenarios](#-project-scenarios) and select one that matches your:
- Available time (2-3 hours)
- Skill level (beginner to advanced)
- Technology preference (JavaScript, Python, or .NET)

### Step 3: Start Lab 00

Begin with **[Lab 00: Setup & Configuration](./docs/00-setup.md)** to:
- Verify Copilot installation
- Configure MCP servers
- Set up your project workspace
- Create initial project structure

### Step 4: Follow the Labs

Complete labs 01-06 in order, applying the techniques to your chosen scenario.

---

## 📚 Additional Resources

### Reference Guides

- **[Copilot Best Practices](./COPILOT_BEST_PRACTICES.md)** - Tips and best practices
- **[Demo Plan](./COPILOT_DEMO_PLAN.md)** - Instructor demonstration guide
- **[Training Exercises](./COPILOT_TRAINING_EXERCISES.md)** - Additional practice exercises
- **[GitHub Issues Demo](./DEMO_GITHUB_ISSUES.md)** - GitHub Issues integration examples
- **[Quick Reference](./DEMO_QUICK_REFERENCE.md)** - Keyboard shortcuts and commands

### Custom Instructions Examples

Explore pre-built Copilot instructions for different tech stacks:

- **[JavaScript/Node.js](./docs/custom-instructions/javascript/copilot-instructions.md)**
- **[Python](./docs/custom-instructions/python/copilot-instructions.md)**
- **[.NET/C#](./docs/custom-instructions/dotnet/copilot-instructions.md)**
- **[Next.js](./docs/custom-instructions/nextjs/copilot-instructions.md)**

---

## 🎯 Learning Objectives

By completing this workshop, you will:

1. **Master Copilot Configuration**
   - Create project-specific Copilot instructions
   - Configure custom chat modes for specialized workflows
   - Integrate MCP servers to extend Copilot capabilities

2. **Build with Test-Driven Development**
   - Write tests before implementation
   - Use Copilot to generate test cases
   - Refactor with confidence using comprehensive test coverage

3. **Automate E2E Testing**
   - Set up Playwright for end-to-end testing
   - Generate E2E tests using Playwright MCP server
   - Implement Page Object Model patterns

4. **Streamline Documentation**
   - Auto-generate comprehensive README files
   - Create and maintain CHANGELOG files
   - Document APIs and add inline comments

5. **Apply Best Practices**
   - Code organization and structure
   - Security and validation
   - Error handling and logging
   - Performance optimization

---

## 🛠️ Technology Stack Options

Choose the stack you're most comfortable with:

### JavaScript/Node.js
- **Runtime:** Node.js 18+
- **Backend:** Express.js
- **Frontend:** React + Vite
- **Testing:** Jest, Playwright

### Python
- **Runtime:** Python 3.9+
- **Backend:** Flask or FastAPI
- **Frontend:** React + Vite
- **Testing:** Pytest, Playwright

### .NET
- **Runtime:** .NET 8+
- **Backend:** ASP.NET Core Web API
- **Frontend:** Blazor or React
- **Testing:** xUnit, Playwright

---

## 📖 Workshop Schedule Recommendations

### 2-Hour Express Workshop

**Focus:** Core Copilot features for everyday development

```
00:00-00:15  Lab 00: Setup & Configuration
00:15-00:35  Lab 01: Copilot Instructions
00:35-01:00  Lab 02: Custom Chat Modes
01:00-01:30  Lab 05: Test-Driven Development
01:30-02:00  Lab 06: Documentation Automation
```

**Skip:** Lab 03 (Playwright MCP), Lab 04 (.NET Migration)

### 3-Hour Comprehensive Workshop

**Focus:** All essential Copilot features including MCP integration

```
00:00-00:15  Lab 00: Setup & Configuration
00:15-00:35  Lab 01: Copilot Instructions
00:35-01:00  Lab 02: Custom Chat Modes
01:00-01:25  Lab 03: Playwright MCP Server
01:25-01:55  Lab 05: Test-Driven Development
01:55-02:20  Lab 06: Documentation Automation
02:20-03:00  Project completion and polish
```

**Skip:** Lab 04 (.NET Migration)

### 3-Hour Advanced Workshop

**Focus:** Complex scenarios and advanced techniques

```
00:00-00:15  Lab 00: Setup & Configuration
00:15-00:35  Lab 01: Copilot Instructions
00:35-01:00  Lab 02: Custom Chat Modes
01:00-01:30  Lab 04: .NET Migration (or other advanced topic)
01:30-02:00  Lab 05: Test-Driven Development
02:00-02:25  Lab 06: Documentation Automation
02:25-03:00  Project completion and polish
```

---

## 🤝 Contributing

Found an issue or have a suggestion? Contributions are welcome!

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

---

## 📄 License

This workshop is licensed under the MIT License - see [LICENSE](LICENSE) file for details.

---

## 🙋 Support

- **Issues:** Open a GitHub issue
- **Discussions:** Use GitHub Discussions
- **Documentation:** See the [docs](./docs) folder

---

## 🎉 Ready to Start?

Begin your journey with **[Lab 00: Setup & Configuration](./docs/00-setup.md)**

**Happy Coding with Copilot! 🚀**