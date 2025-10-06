# 05: Documentation Automation with GitHub Copilot

## Scenario

You've built a complete application with features and tests, but documentation can quickly become outdated. In this lab, you'll use GitHub Copilot to automate documentation generation and maintenance.

You'll create:
- Comprehensive README.md
- CHANGELOG.md with versioning
- API documentation
- Code comments and docstrings
- User guides

Good documentation is crucial for maintainability, onboarding, and user adoption. Copilot can accelerate documentation creation while maintaining quality and consistency.

## Prerequisites

- Completed [Lab 00: Setup & Configuration](./00-setup.md)
- Completed [Lab 01: Copilot Instructions](./01-copilot-instructions.md)
- Have a working project with implemented features
- GitHub Copilot is active in Agent Mode

## Getting Started

- [Check GitHub Copilot Agent Mode](#check-github-copilot-agent-mode)
- [Generate Project README.md](#generate-project-readmemd)
- [Create CHANGELOG.md](#create-changelogmd)
- [Generate API Documentation](#generate-api-documentation)
- [Create Mermaid Diagrams](#create-mermaid-diagrams)
- [Add Code Comments and Docstrings](#add-code-comments-and-docstrings)
- [Create User Guide](#create-user-guide)
- [Keep Documentation Updated](#keep-documentation-updated)

---

## Check GitHub Copilot Agent Mode

1. Click the GitHub Copilot icon on the top of GitHub Codespace or VS Code and open GitHub Copilot window.

   ![Open GitHub Copilot Chat](./images/setup-02.png)

1. Make sure you're using **GitHub Copilot Agent Mode**.

   ![GitHub Copilot Agent Mode](./images/setup-03.png)

1. Select model to either `GPT-4.1` or `Claude Sonnet 4`.

1. Make sure that the `context7` MCP server is up and running (if configured).

---

## Generate Project README.md

### Step 1: Analyze Your Project

1. Use this prompt to have Copilot analyze your project:

   ```text
   Analyze my project structure and codebase. Provide a comprehensive summary including:
   
   - Project name and purpose
   - Main features implemented
   - Tech stack (languages, frameworks, libraries, versions)
   - Project structure (directories and their purposes)
   - Key dependencies
   - Entry points (main files)
   - Configuration files
   - Testing setup
   
   Be thorough and specific to my actual project.
   ```

1. Review Copilot's analysis to ensure accuracy.

### Step 2: Generate Complete README.md

1. Use this prompt to generate a comprehensive README:

   ```text
   Generate a professional README.md file for my project. Follow the instructions below.
   
   Include these sections in order:
   
   1. **Project Title and Description**
      - Clear project name
      - One-sentence description
      - Brief overview (2-3 sentences)
   
   2. **Features**
      - List all implemented features
      - Use emoji bullets (✅)
      - Be specific and user-focused
   
   3. **Tech Stack**
      - Separate Backend and Frontend
      - List technologies with versions
      - Include testing frameworks
   
   4. **Prerequisites**
      - List all required software
      - Include version requirements
      - Provide download links
   
   5. **Installation**
      - Step-by-step installation instructions
      - Separate backend and frontend steps
      - Include all commands
   
   6. **Configuration**
      - Environment variables needed
      - Configuration file examples
      - Default values
   
   7. **Running the Application**
      - How to start backend
      - How to start frontend
      - Access URLs
   
   8. **API Endpoints** (if applicable)
      - List all endpoints
      - HTTP methods
      - Brief description
   
   9. **Testing**
      - How to run unit tests
      - How to run E2E tests
      - How to check coverage
   
   10. **Project Structure**
       - Directory tree
       - Explanation of each directory
   
   11. **Contributing**
       - How to contribute
       - Code standards
       - PR process
   
   12. **License**
       - License type
   
   13. **Contact/Support**
       - How to get help
   
   Make it professional, clear, and beginner-friendly.
   Create the file and show me the content.
   ```

1. Review the generated README.md.

1. Click the ![keep button](https://img.shields.io/badge/keep-blue) button to save.

### Step 3: Add Badges and Screenshots

1. Enhance the README with badges:

   ```text
   Add status badges to the README.md at the top, right after the title:
   
   - Build status badge (GitHub Actions)
   - Test coverage badge
   - License badge
   - Version badge
   - Language/Framework badge
   
   Use shields.io format.
   Also add a placeholder for a screenshot with instructions on where to add it.
   ```

1. Click the ![keep button](https://img.shields.io/badge/keep-blue) button.

---

## Create CHANGELOG.md

### Step 4: Generate Initial CHANGELOG

1. Use this prompt to create a CHANGELOG:

   ```text
   Create a CHANGELOG.md file following the "Keep a Changelog" format (https://keepachangelog.com/).
   
   Requirements:
   - Follow semantic versioning (MAJOR.MINOR.PATCH)
   - Include these sections: Unreleased, and version releases
   - Categorize changes as:
     * Added (new features)
     * Changed (changes in existing functionality)
     * Deprecated (soon-to-be removed features)
     * Removed (removed features)
     * Fixed (bug fixes)
     * Security (security improvements)
   
   For version 1.0.0 (initial release), list all the features I've implemented based on my project.
   Use today's date for the release.
   
   Create the file and show me the content.
   ```

1. Review the CHANGELOG.

1. Click the ![keep button](https://img.shields.io/badge/keep-blue) button.

### Step 5: Create CHANGELOG Update Template

1. Create a template for future updates:

   ```text
   Create a CHANGELOG_TEMPLATE.md file with instructions for updating the CHANGELOG.
   
   Include:
   - How to add entries to Unreleased section
   - How to create a new release
   - Examples for each change category
   - Semantic versioning guidelines
   - When to bump MAJOR, MINOR, or PATCH version
   
   Make it easy for team members to use.
   ```

1. Click the ![keep button](https://img.shields.io/badge/keep-blue) button.

---

## Generate API Documentation

### Step 6: Create API Documentation

1. Use this prompt to generate API documentation:

   ```text
   Create comprehensive API documentation in API.md. Follow the instructions below.
   
   For each API endpoint I've implemented:
   
   1. **Endpoint Details**
      - URL pattern
      - HTTP method
      - Description (what it does)
   
   2. **Request**
      - Query parameters (if any)
      - Request body schema
      - Required vs. optional fields
      - Validation rules
   
   3. **Response**
      - Success response (200, 201, etc.)
      - Response body schema
      - Example response
   
   4. **Error Responses**
      - Error status codes (400, 404, 500, etc.)
      - Error response format
      - Example error responses
   
   5. **Examples**
      - cURL command example
      - JavaScript fetch example
      - Python requests example
   
   Include a table of contents at the top.
   Add base URL configuration section.
   Include authentication details if applicable.
   
   Analyze my codebase and create complete API documentation.
   ```

1. Review the API documentation.

1. Click the ![keep button](https://img.shields.io/badge/keep-blue) button.

### Step 7: Generate OpenAPI/Swagger Spec

1. Create an OpenAPI specification:

   ```text
   Generate an OpenAPI 3.0 specification (swagger.yaml) for my API.
   
   Include:
   - openapi version: 3.0.0
   - info section (title, version, description, contact)
   - servers section (development, production URLs)
   - paths section (all endpoints with full details)
   - components/schemas section (all data models)
   - Security schemes (if applicable)
   
   For each endpoint include:
   - Summary and description
   - Parameters (path, query, header)
   - Request body (with schema reference)
   - Responses (all status codes)
   - Examples
   
   Create swagger.yaml file.
   Make it valid OpenAPI 3.0 spec.
   ```

1. Click the ![keep button](https://img.shields.io/badge/keep-blue) button.

---

## Create Mermaid Diagrams

### Step 7A: Set Up Mermaid MCP Server

1. First, activate the Mermaid diagram tools:

   ```text
   I need to create technical diagrams for my documentation. Help me activate the Mermaid diagram tools to create flowcharts, sequence diagrams, and architecture diagrams.
   ```

### Step 7B: Create Architecture Diagram

1. Use this prompt to create a system architecture diagram:

   ```text
   Create a Mermaid architecture diagram for my project. Follow the instructions below.
   
   [Choose based on your scenario:]
   
   **For Expense Tracker:**
   ```
   Create a Mermaid diagram showing the architecture of my Expense Tracker application.
   
   Include:
   - Frontend (React/Vue/Blazor)
   - Backend API (Node.js/Python/ASP.NET)
   - Database (if used)
   - External services (if any)
   - User interactions and data flow
   
   Use either a flowchart or C4 architecture diagram format.
   Show the main components and how they interact.
   ```
   
   **For Weather App:**
   ```
   Create a Mermaid diagram showing the architecture of my Weather App.
   
   Include:
   - Frontend application
   - Backend API
   - Weather API integration (OpenWeatherMap/WeatherAPI)
   - Caching layer
   - User location services
   - Data flow from API to user
   
   Use a flowchart format showing the complete data flow.
   Include caching and error handling paths.
   ```
   
   **For KYC Portal:**
   ```
   Create a Mermaid diagram showing the KYC verification workflow.
   
   Include:
   - User document upload
   - Document validation steps
   - Manual review process
   - Approval/rejection flow
   - Audit trail creation
   - Different user roles (User, Reviewer, Admin)
   
   Use a flowchart showing the complete verification process.
   Include decision points and different paths.
   ```
   
   **For 360° Customer View:**
   ```
   Create a Mermaid diagram showing the customer data aggregation system.
   
   Include:
   - Multiple data sources (Profile, Transactions, Support, Compliance)
   - Data aggregation service
   - Real-time update mechanisms (WebSocket/SSE)
   - Frontend dashboard
   - RG (Responsible Gaming) monitoring
   
   Use a system architecture diagram format.
   Show data sources, processing, and presentation layers.
   ```
   
   Save the diagram as ARCHITECTURE.md and validate it's proper Mermaid syntax.
   ```

1. Review the generated architecture diagram.

1. Click the ![keep button](https://img.shields.io/badge/keep-blue) button.

### Step 7C: Create API Flow Diagram

1. Create a sequence diagram for API interactions:

   ```text
   Create a Mermaid sequence diagram showing a typical API interaction flow in my application.
   
   [Choose a key user flow based on your scenario:]
   
   **For Expense Tracker:** "Add New Expense" flow
   **For Weather App:** "Search Weather for City" flow  
   **For KYC Portal:** "Document Upload and Verification" flow
   **For 360° Customer:** "Load Customer Profile" flow
   
   Include:
   - User actions
   - Frontend requests
   - Backend processing
   - Database operations
   - External API calls (if any)
   - Response flow back to user
   - Error handling scenarios
   
   Use Mermaid sequence diagram format.
   Show the complete interaction from user action to response.
   Include timing and async operations.
   
   Save as API_FLOW.md
   ```

1. Review the sequence diagram.

1. Click the ![keep button](https://img.shields.io/badge/keep-blue) button.

### Step 7D: Create Database Schema Diagram

1. If your project uses a database, create a schema diagram:

   ```text
   Create a Mermaid entity relationship diagram (ERD) for my database schema.
   
   Include:
   - All database tables/collections
   - Primary keys
   - Foreign key relationships
   - Important fields for each table
   - Relationships between entities (one-to-one, one-to-many, many-to-many)
   
   Use Mermaid ERD format.
   Make it clear and easy to understand.
   
   If I don't use a database, create a data flow diagram instead showing how data moves through my application.
   
   Save as DATABASE_SCHEMA.md
   ```

1. Review the database schema diagram.

1. Click the ![keep button](https://img.shields.io/badge/keep-blue) button.

### Step 7E: Add Diagrams to README

1. Integrate the diagrams into your main documentation:

   ```text
   Update README.md to include the Mermaid diagrams I just created.
   
   Add a new "Architecture" section after the "Features" section with:
   
   1. System Architecture diagram (from ARCHITECTURE.md)
   2. Brief explanation of the architecture
   3. Link to detailed architecture documentation
   
   Add a new "API Flow" section in the API documentation with:
   1. Key API interaction sequence diagram (from API_FLOW.md)
   2. Brief explanation of the flow
   
   If database schema exists, add to "Database" section:
   1. Database schema diagram (from DATABASE_SCHEMA.md)
   2. Brief explanation of the data model
   
   Make sure the Mermaid diagrams render properly in GitHub.
   Use proper Mermaid code blocks with ```mermaid syntax.
   ```

1. Click the ![keep button](https://img.shields.io/badge/keep-blue) button.

---

## Add Code Comments and Docstrings

### Step 8: Add Function Documentation

1. Select a function/class in your code, then use:

   **For JavaScript/TypeScript:**
   ```text
   Add comprehensive JSDoc comments to the selected function/class.
   
   Include:
   - Description (what it does, why it exists)
   - @param for each parameter (type, description)
   - @returns (type, description)
   - @throws (exceptions it might throw)
   - @example (usage example)
   
   Make comments clear and helpful.
   Follow JSDoc standards.
   ```

   **For Python:**
   ```text
   Add comprehensive docstring to the selected function/class.
   
   Use Google-style docstrings including:
   - Brief description
   - Args section (each parameter with type and description)
   - Returns section (type and description)
   - Raises section (exceptions)
   - Example section (usage example)
   
   Make docstrings clear and helpful.
   Follow PEP 257 conventions.
   ```

   **For .NET/C#:**
   ```text
   Add comprehensive XML documentation comments to the selected method/class.
   
   Include:
   - <summary> (what it does)
   - <param> for each parameter (description)
   - <returns> (description)
   - <exception> (exceptions it might throw)
   - <example> (usage example with code)
   
   Make comments clear and helpful.
   Follow XML documentation standards.
   ```

1. Review the generated documentation.

1. Click the ![keep button](https://img.shields.io/badge/keep-blue) button.

### Step 9: Document All Public Functions

1. Use this prompt to document all public functions:

   ```text
   Add documentation comments to ALL public functions/methods in my project.
   
   For each function:
   - Add appropriate doc comments (JSDoc, docstrings, or XML comments)
   - Include description, parameters, return value, exceptions
   - Add usage examples for complex functions
   - Document edge cases and gotchas
   
   Skip private/internal functions.
   Focus on public API that users/developers will use.
   
   Show me files that need documentation and add comments systematically.
   ```

1. Click the ![keep button](https://img.shields.io/badge/keep-blue) button after reviewing each file.

---

## Create User Guide

### Step 10: Generate User Guide

Choose the appropriate prompt based on your scenario:

**For Expense Tracker:**
```text
Create a USER_GUIDE.md for end users (non-technical) of my Expense Tracker.

Include:

1. **Getting Started**
   - How to access the app
   - Creating your first expense
   - Overview of the interface

2. **Adding Expenses**
   - Step-by-step guide with screenshots placeholders
   - Filling in amount, category, description, date
   - Tips for categorization

3. **Viewing Expenses**
   - How to see your expense list
   - Understanding the display
   - Sorting and filtering

4. **Filtering Expenses**
   - Filter by category
   - Filter by date range
   - Filter by amount

5. **Monthly Summary**
   - Viewing monthly totals
   - Understanding category breakdown
   - Using the visualization

6. **Best Practices**
   - Tips for effective expense tracking
   - How to categorize expenses consistently
   - Reviewing expenses regularly

7. **FAQ**
   - Common questions
   - Troubleshooting

Use simple, non-technical language.
Add [Screenshot] placeholders where visuals would help.
```

**For Weather App:**
```text
Create a USER_GUIDE.md for end users (non-technical) of my Weather App.

Include:

1. **Getting Started**
   - How to access the app
   - Searching for your first city
   - Understanding the interface

2. **Searching for Weather**
   - How to search by city name
   - How to use current location (if applicable)
   - Supported locations

3. **Understanding Weather Information**
   - Temperature and "feels like"
   - Weather conditions explained
   - Humidity and what it means
   - Wind speed information

4. **5-Day Forecast**
   - Viewing extended forecast
   - Understanding forecast accuracy
   - Planning based on forecast

5. **Tips and Best Practices**
   - When weather data is updated
   - Understanding weather caching
   - Most accurate times for forecasts

6. **FAQ**
   - Why is weather data cached?
   - What if my city isn't found?
   - How accurate is the forecast?

Use simple, non-technical language.
Add [Screenshot] placeholders.
```

**For KYC Portal / 360° Customer (Administrator Guide):**
```text
Create an ADMIN_GUIDE.md for administrators and staff using my [KYC Portal / 360° Customer View].

Include:

1. **Getting Started**
   - Logging in
   - Understanding your role (Admin vs. Reviewer vs. User)
   - Dashboard overview

2. **[For KYC: Document Verification Workflow] OR [For 360°: Customer Management]**
   - Step-by-step process
   - Best practices
   - Common scenarios

3. **Security and Compliance**
   - Data privacy requirements
   - Audit trail usage
   - Compliance checks

4. **Reports and Analytics**
   - Available reports
   - How to generate reports
   - Understanding metrics

5. **Troubleshooting**
   - Common issues
   - How to escalate
   - Support contact

6. **FAQ**
   - Role-specific questions
   - Process questions
   - Technical questions

Use professional but clear language.
Add [Screenshot] placeholders.
Include compliance reminders.
```

1. Review the user guide.

1. Click the ![keep button](https://img.shields.io/badge/keep-blue) button.

---

## Keep Documentation Updated

### Step 11: Create Documentation Update Checklist

1. Create a checklist for keeping docs updated:

   ```text
   Create DOCUMENTATION_CHECKLIST.md with a checklist for updating documentation.
   
   Include checklists for:
   
   1. **When Adding a New Feature**
      - [ ] Update README Features section
      - [ ] Add to CHANGELOG (Unreleased > Added)
      - [ ] Update API.md if API changed
      - [ ] Update architecture diagrams if structure changed
      - [ ] Add code comments/docstrings
      - [ ] Update User Guide
      - [ ] Add examples if complex
   
   2. **When Fixing a Bug**
      - [ ] Add to CHANGELOG (Unreleased > Fixed)
      - [ ] Update affected documentation
      - [ ] Add note in code comments
   
   3. **When Changing API**
      - [ ] Update API.md
      - [ ] Update swagger.yaml
      - [ ] Update API flow diagrams if needed
      - [ ] Add to CHANGELOG (Changed or Removed)
      - [ ] Update code examples
      - [ ] Update README if breaking change
   
   4. **When Releasing New Version**
      - [ ] Move Unreleased items to new version in CHANGELOG
      - [ ] Update version in package.json/setup.py/etc
      - [ ] Update README badges
      - [ ] Tag release in git
      - [ ] Generate release notes
   
   5. **Monthly Maintenance**
      - [ ] Review and update README
      - [ ] Check for outdated screenshots
      - [ ] Verify all links work
      - [ ] Update dependency versions
      - [ ] Review and update diagrams for accuracy
      - [ ] Review and update examples
   
   Make it a practical checklist teams can use.
   ```

1. Click the ![keep button](https://img.shields.io/badge/keep-blue) button.

### Step 12: Create Documentation Update Prompts

1. Create reusable prompts for common documentation tasks:

   ```text
   Create DOCUMENTATION_PROMPTS.md with ready-to-use prompts for updating documentation.
   
   Include prompts for:
   
   **Update README for New Feature:**
   ```
   I added a new feature: [FEATURE_NAME]
   
   Description: [BRIEF_DESCRIPTION]
   
   Update README.md:
   1. Add to Features list
   2. Update relevant sections
   3. Add usage example if needed
   ```
   
   **Update CHANGELOG:**
   ```
   Update CHANGELOG.md for version [X.Y.Z] released today.
   
   Added:
   - [List new features]
   
   Changed:
   - [List changes]
   
   Fixed:
   - [List bug fixes]
   
   Security:
   - [List security improvements]
   
   Follow Keep a Changelog format.
   ```
   
   **Add API Endpoint Documentation:**
   ```
   I created a new API endpoint:
   
   Method: [GET/POST/PUT/DELETE]
   Path: [/api/...]
   Purpose: [What it does]
   
   Update API.md and swagger.yaml with complete documentation.
   Include request/response examples.
   ```
   
   **Generate Release Notes:**
   ```
   Generate release notes for version [X.Y.Z] based on CHANGELOG.md.
   
   Format for GitHub Release:
   - Highlight major features
   - List improvements
   - Note breaking changes
   - Thank contributors
   - Provide upgrade instructions if needed
   ```
   
   **Update Architecture Diagram:**
   ```
   I made changes to the system architecture:
   
   Changes: [Describe what changed]
   New components: [List any new services/modules]
   Removed components: [List any removed parts]
   
   Update the Mermaid architecture diagram in README.md to reflect these changes.
   Ensure the diagram accurately shows:
   - Component relationships
   - Data flow
   - External dependencies
   ```
   
   Make prompts copy-paste ready.
   ```

1. Click the ![keep button](https://img.shields.io/badge/keep-blue) button.

---

## Verify Documentation Quality

### Step 13: Documentation Quality Check

1. Use this prompt to verify documentation quality:

   ```text
   Review all documentation files I've created and check for:
   
   **Completeness:**
   - [ ] README.md covers all essential sections
   - [ ] CHANGELOG.md follows proper format
   - [ ] API.md documents all endpoints
   - [ ] User Guide is comprehensive
   - [ ] Code has appropriate comments
   
   **Accuracy:**
   - [ ] Information matches actual code
   - [ ] Examples work correctly
   - [ ] API specs match implementation
   - [ ] Version numbers are correct
   
   **Clarity:**
   - [ ] Language is clear and concise
   - [ ] Examples are easy to understand
   - [ ] Technical terms are explained
   - [ ] Structure is logical
   
   **Consistency:**
   - [ ] Formatting is consistent
   - [ ] Terminology is consistent
   - [ ] Code style in examples is consistent
   
   Provide a report with any issues found and suggestions for improvement.
   ```

1. Review the documentation quality report.

### Step 14: Apply Documentation Improvements

1. Fix any issues identified:

   ```text
   Apply the documentation improvements suggested in the quality review.
   
   - Fix accuracy issues
   - Improve clarity
   - Ensure consistency
   - Add missing information
   - Update examples
   
   Show me the changes made to each file.
   ```

1. Click the ![keep button](https://img.shields.io/badge/keep-blue) button.

---

## Best Practices for Documentation

### Documentation Best Practices

✅ **Do's:**

1. **Keep It Current**: Update docs with every code change
2. **Be Clear**: Use simple language, avoid unnecessary jargon
3. **Include Examples**: Real code examples are invaluable
4. **Add Visuals**: Screenshots and diagrams improve understanding
5. **Version Documentation**: Match docs to code versions
6. **Write for Audience**: User docs vs. developer docs
7. **Test Instructions**: Ensure setup/usage instructions actually work
8. **Link Between Docs**: Cross-reference related documentation

❌ **Don'ts:**

1. **Don't Duplicate Code**: Documentation can become outdated
2. **Don't Over-Document**: Focus on what's not obvious from code
3. **Don't Assume Knowledge**: Explain prerequisites and context
4. **Don't Ignore Errors**: Document common issues and solutions
5. **Don't Set and Forget**: Schedule regular documentation reviews
6. **Don't Use Only Text**: Visual aids significantly help
7. **Don't Hide Important Info**: Put critical information prominently

---

## Troubleshooting

### Issue: Documentation Becomes Outdated

**Solution:**

1. Add documentation updates to PR checklist
2. Use automation (generate API docs from code)
3. Schedule quarterly documentation reviews
4. Assign documentation ownership

Quick fix prompt:
```text
Review all documentation and identify sections that may be outdated based on recent code changes.

- Compare docs to current codebase
- List discrepancies
- Suggest updates
- Prioritize by importance
```

### Issue: Documentation Too Technical

**Solution:**

```text
My documentation is too technical for end users. Help me simplify it.

- Rewrite USER_GUIDE.md for non-technical audience
- Replace jargon with simple terms
- Add more examples and screenshots
- Include a glossary for necessary technical terms
- Use analogies where helpful

Show me the simplified version.
```

### Issue: Missing Documentation

**Solution:**

```text
Identify gaps in my documentation:

- What's undocumented?
- What's poorly documented?
- What needs more examples?
- What needs better explanation?

Provide a prioritized list of documentation tasks.
```

---

## Next Steps

✅ **Lab 05 Complete!** You've automated documentation for your entire project.

**What's Next:**

Proceed to [Lab 06: Advanced Techniques](./07-advanced-techniques.md) to master advanced GitHub Copilot techniques for expert developers.

**What You've Accomplished:**

1. ✅ Configured Copilot with custom instructions
2. ✅ Created specialized chat modes (TDD Mode)
3. ✅ Integrated MCP servers (Context7, Playwright)
4. ✅ Built features using Test-Driven Development
5. ✅ Automated comprehensive documentation

**What's Next:**

1. **Deploy Your Application**
   - Deploy to cloud platform (Azure, AWS, Vercel)
   - Set up CI/CD pipeline
   - Configure production environment

2. **Maintain and Improve**
   - Keep documentation updated
   - Add more features using TDD
   - Improve test coverage
   - Refactor for better performance

3. **Share Your Work**
   - Publish repository to GitHub
   - Share with team or community
   - Get feedback and iterate

4. **Continue Learning**
   - Explore more Copilot features
   - Try other MCP servers
   - Create additional custom chat modes
   - Experiment with advanced workflows

---

## Resources

- [Keep a Changelog](https://keepachangelog.com/)
- [Semantic Versioning](https://semver.org/)
- [JSDoc Documentation](https://jsdoc.app/)
- [Python Docstring Conventions](https://peps.python.org/pep-0257/)
- [OpenAPI Specification](https://swagger.io/specification/)
- [README Best Practices](https://github.com/matiassingers/awesome-readme)
- [Documentation Guide](https://www.writethedocs.org/guide/)

---

OK. You've completed Lab 05. Let's move onto [Lab 06: Advanced Techniques](./06-advanced-techniques.md).
