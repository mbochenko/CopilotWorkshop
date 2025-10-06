# GitHub Copilot Self-Paced Learning Workshop
## 2-3 Hour Hands-On Development Workshop

---

## 📋 Workshop Overview

**Duration:** 2-3 hours (self-paced)  
**Format:** Hands-on, scenario-based learning  
**Skill Level:** Beginner to Intermediate developers  
**Prerequisites:** Basic programming knowledge in at least one language (JavaScript, Python, or .NET)

---

## 🎯 Learning Objectives

By the end of this workshop, you will be able to:

1. ✅ Set up and configure GitHub Copilot for maximum productivity
2. ✅ Create and use custom Copilot instructions for project-specific guidance
3. ✅ Build custom chat modes for specialized workflows (e.g., TDD mode)
4. ✅ Leverage MCP (Model Context Protocol) servers for enhanced functionality
5. ✅ Use Copilot to scaffold, develop, and test complete applications
6. ✅ Maintain up-to-date documentation automatically with Copilot
7. ✅ Apply Test-Driven Development (TDD) practices with Copilot assistance

---

## 📚 Workshop Structure

### Self-Paced Learning Path

| Step | Topic | Link | Duration | Type |
|------|-------|------|----------|------|
| 00 | **Setup & Configuration** | [00-setup.md](./docs/00-setup.md) | 15-20 min | Setup |
| 01 | **Copilot Instructions** | [01-copilot-instructions.md](./docs/01-copilot-instructions.md) | 20-25 min | Lab |
| 02 | **Custom Chat Modes (TDD)** | [02-custom-chat-modes.md](./docs/02-custom-chat-modes.md) | 25-30 min | Lab |
| 03 | **MCP Server Integration** | [03-playwright-mcp.md](./docs/03-playwright-mcp.md) | 20-25 min | Lab |
| 04 | **Full-Stack Development** | [04-dotnet.md](./docs/04-dotnet.md) | 45-60 min | Lab |
| 05 | **Test-Driven Development** | [05-tdd-with-copilot.md](./docs/05-tdd-with-copilot.md) | 30-40 min | Lab |
| 06 | **Documentation Automation** | [06-documentation.md](./docs/06-documentation.md) | 20-25 min | Lab |

**Total Time:** 2h 55min - 3h 45min (flexible based on your pace)

---

## 🎭 Project Scenarios

Choose **ONE** scenario to work through during the workshop. All labs can be applied to any scenario:

### 1. 💰 Expense Tracker (Recommended for Beginners)
**Complexity:** ⭐⭐☆☆☆  
**Description:** Build a microservice to log daily expenses and visualize spending patterns  
**Tech Stack:** Frontend + Backend API + Data Visualization  
**Time:** 45-60 minutes  
**Best For:** Learning CRUD operations, data visualization, and basic business logic

[👉 Start with Expense Tracker](./challenges/expensetracker/README.md)

---

### 2. 🌤️ Weather App
**Complexity:** ⭐⭐☆☆☆  
**Description:** Create a weather dashboard that fetches real-time weather data and displays forecasts  
**Tech Stack:** Frontend + External API Integration + Data Caching  
**Time:** 45-60 minutes  
**Best For:** Learning API integration, async operations, and responsive UI design

[👉 Start with Weather App](./challenges/weatherapp/README.md)

---

### 3. 🔐 KYC/Document Verification Portal
**Complexity:** ⭐⭐⭐⭐☆  
**Description:** Build a secure portal for Know Your Customer (KYC) document verification and compliance  
**Tech Stack:** Frontend + Backend + File Upload + Document Processing + Security  
**Time:** 90-120 minutes  
**Best For:** Learning security patterns, file handling, workflow management, and compliance

[👉 Start with KYC Portal](./challenges/kycportal/README.md)

---

### 4. 👥 360° Customer View Portal (Gaming Company)
**Complexity:** ⭐⭐⭐⭐⭐  
**Description:** Create a comprehensive dashboard showing complete customer data for gambling company operations  
**Tech Stack:** Frontend + Backend + Data Aggregation + Real-time Updates + Analytics  
**Time:** 90-120 minutes  
**Best For:** Learning data aggregation, complex UI, real-time features, and business intelligence

[👉 Start with 360 Customer Portal](./challenges/360customer/README.md)

---

## 🗓️ Recommended Schedules

### ⏱️ Option 1: 2-Hour Express Workshop

**Focus:** Core Copilot features + Quick project build

| Time | Activity | Duration |
|------|----------|----------|
| 0:00-0:15 | Setup & Configuration (Lab 00) | 15 min |
| 0:15-0:35 | Copilot Instructions (Lab 01) | 20 min |
| 0:35-0:55 | Custom Chat Modes (Lab 02) | 20 min |
| 0:55-1:50 | Build Your Project (Lab 04 - Choose Scenario) | 55 min |
| 1:50-2:00 | Documentation (Lab 06) | 10 min |

**Recommended Scenarios:** Expense Tracker or Weather App

---

### ⏱️ Option 2: 3-Hour Comprehensive Workshop

**Focus:** All features + Complete project with TDD

| Time | Activity | Duration |
|------|----------|----------|
| 0:00-0:20 | Setup & Configuration (Lab 00) | 20 min |
| 0:20-0:45 | Copilot Instructions (Lab 01) | 25 min |
| 0:45-1:15 | Custom Chat Modes (Lab 02) | 30 min |
| 1:15-1:35 | Playwright MCP Server (Lab 03) | 20 min |
| 1:35-2:35 | Build Your Project with TDD (Labs 04 & 05) | 60 min |
| 2:35-3:00 | Documentation & Best Practices (Lab 06) | 25 min |

**Recommended Scenarios:** Any scenario (choose based on interest)

---

### ⏱️ Option 3: 3-Hour Advanced Workshop

**Focus:** Complex scenario + Advanced features

| Time | Activity | Duration |
|------|----------|----------|
| 0:00-0:15 | Setup & Configuration (Lab 00) | 15 min |
| 0:15-0:35 | Copilot Instructions (Lab 01) | 20 min |
| 0:35-1:00 | Custom Chat Modes (Lab 02) | 25 min |
| 1:00-1:20 | Playwright MCP Server (Lab 03) | 20 min |
| 1:20-2:40 | Build Complex Project (KYC or 360 Portal) | 80 min |
| 2:40-3:00 | Documentation (Lab 06) | 20 min |

**Recommended Scenarios:** KYC Portal or 360 Customer Portal

---

## 🎓 Workshop Pedagogy

### Learning Approach

This workshop follows a **Learn-by-Doing** methodology:

1. **📖 Understand:** Each lab starts with clear objectives and context
2. **🔧 Configure:** Set up tools and environments step-by-step
3. **💻 Practice:** Hands-on exercises with guided prompts
4. **✅ Verify:** Validation steps to confirm success
5. **🚀 Extend:** Bonus challenges for deeper learning

### Copilot-First Development

Throughout the workshop, you'll practice:
- **Prompt Engineering:** Crafting effective prompts for Copilot
- **Context Management:** Providing the right context for better results
- **Iterative Development:** Refining code through conversation
- **Best Practices:** Learning when and how to use Copilot effectively

---

## 📦 What You'll Build

Depending on your chosen scenario, you'll create:

- ✅ **Full-Stack Application** with frontend and backend
- ✅ **RESTful API** with CRUD operations
- ✅ **Data Visualization** or dashboards
- ✅ **Unit Tests** following TDD principles
- ✅ **End-to-End Tests** using Playwright
- ✅ **Complete Documentation** (README, CHANGELOG, API docs)
- ✅ **Custom Copilot Configuration** for your project

---

## 🛠️ Technical Requirements

### Required Software
- Visual Studio Code or GitHub Codespaces
- GitHub Copilot subscription (or trial)
- Git
- Node.js 18+ OR Python 3.9+ OR .NET 8+

### Recommended VS Code Extensions
- GitHub Copilot
- GitHub Copilot Chat
- Language-specific extensions (ESLint, Python, C# Dev Kit, etc.)

### Optional Tools
- Docker (for containerization labs)
- Postman or REST Client (for API testing)

---

## 📝 Assessment & Success Criteria

### You'll Know You've Succeeded When:

✅ **Setup Complete:**
- GitHub Copilot is active and responding
- Custom instructions are configured
- MCP servers are connected

✅ **Application Functional:**
- All core features are working
- Tests are passing
- Application runs without errors

✅ **Documentation Complete:**
- README.md is comprehensive
- CHANGELOG.md tracks changes
- Code includes helpful comments

✅ **Best Practices Applied:**
- Code follows TDD principles
- Security considerations are addressed
- Error handling is implemented

---

## 🎁 Bonus Challenges

After completing the core workshop, try these:

1. **🔄 Add CI/CD Pipeline:** Set up GitHub Actions with Copilot
2. **🐳 Containerize:** Create Docker containers for your app
3. **☁️ Deploy:** Deploy to Azure, AWS, or Vercel
4. **🔒 Add Authentication:** Implement user login and authorization
5. **📊 Advanced Analytics:** Add complex data analysis features
6. **🌐 Internationalization:** Support multiple languages
7. **♿ Accessibility:** Ensure WCAG compliance

---

## 📚 Additional Resources

- [GitHub Copilot Documentation](https://docs.github.com/en/copilot)
- [Copilot Best Practices](./COPILOT_BEST_PRACTICES.md)
- [Training Exercises](./COPILOT_TRAINING_EXERCISES.md)
- [Demo Quick Reference](./DEMO_QUICK_REFERENCE.md)

---

## 🤝 Support & Feedback

- **Questions?** Use GitHub Discussions
- **Issues?** Submit to GitHub Issues
- **Feedback?** We'd love to hear how this workshop went!

---

## 🚀 Ready to Start?

Choose your path:

1. **🏃 Quick Start (2 hours):** [Go to Lab 00: Setup](./docs/00-setup.md)
2. **📖 Learn More:** [Read Copilot Best Practices](./COPILOT_BEST_PRACTICES.md)
3. **🎯 Choose Scenario:** [Browse Project Scenarios](#-project-scenarios)

**Happy Coding with GitHub Copilot! 🎉**
