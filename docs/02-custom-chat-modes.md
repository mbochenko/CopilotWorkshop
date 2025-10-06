# 02: Create Custom Chat Modes (TDD Mode)

## Scenario

You want to enforce Test-Driven Development (TDD) practices across your team, but it's easy to forget to write tests first. By creating a custom chat mode for GitHub Copilot, you can create a specialized "TDD Mode" that enforces the Red-Green-Refactor cycle and ensures tests are always written before implementation.

Custom chat modes allow you to:
- Create specialized workflows (TDD, Security Review, API Design, etc.)
- Enforce best practices through guided interactions
- Provide context-specific assistance
- Maintain consistency across team members

In this lab, you'll create a TDD chat mode that strictly enforces writing tests before implementation code.

## Prerequisites

- Completed [Lab 00: Setup & Configuration](./00-setup.md)
- Completed [Lab 01: Copilot Instructions](./01-copilot-instructions.md)
- GitHub Copilot is active in Agent Mode
- VS Code or GitHub Codespaces open

## Getting Started

- [Check GitHub Copilot Agent Mode](#check-github-copilot-agent-mode)
- [Understand Custom Chat Modes](#understand-custom-chat-modes)
- [Create TDD Chat Mode Instructions](#create-tdd-chat-mode-instructions)
- [Test Your TDD Chat Mode](#test-your-tdd-chat-mode)
- [Use TDD Mode for Your Project](#use-tdd-mode-for-your-project)
- [Create Additional Custom Modes (Optional)](#create-additional-custom-modes-optional)

---

## Check GitHub Copilot Agent Mode

1. Click the GitHub Copilot icon on the top of GitHub Codespace or VS Code and open GitHub Copilot window.

   ![Open GitHub Copilot Chat](./images/setup-02.png)

1. Make sure you're using **GitHub Copilot Agent Mode**.

   ![GitHub Copilot Agent Mode](./images/setup-03.png)

1. Select model to either `GPT-4.1` or `Claude Sonnet 4`.

---

## Understand Custom Chat Modes

### What Are Custom Chat Modes?

Custom chat modes are specialized instruction sets that you can activate in Copilot Chat to enforce specific workflows or behaviors. Think of them as "personalities" or "roles" for Copilot.

### Examples of Custom Chat Modes

- **TDD Mode**: Enforces test-first development
- **Security Auditor**: Reviews code for security vulnerabilities
- **API Designer**: Helps design RESTful APIs
- **Performance Optimizer**: Focuses on performance improvements
- **Documentation Writer**: Generates comprehensive documentation

### How They Work

Custom modes are defined in `.github/copilot-instructions.md` using special markdown sections. When activated, Copilot follows the mode's specific rules and workflow.

---

## Create TDD Chat Mode Instructions

### Step 1: Create TDD Mode Definition

1. Make sure you're using GitHub Copilot Agent Mode with the model of `Claude Sonnet 4` or `GPT-4.1`.

1. Use the prompt below to add a TDD mode to your Copilot instructions:

   ```text
   Update .github/chatmodes/TDD.md to add a custom TDD (Test-Driven Development) chat mode. Follow the instructions below.
   
   You are an expert AI pair programmer following strict Test-Driven Development (TDD) principles.
   
   **TDD Mode Requirements:**
   1. Mode name: "TDD Mode" or activated with "I want to use TDD"
   2. Strict Red-Green-Refactor enforcement:
      - RED: Always write failing tests FIRST
      - GREEN: Write minimal code to make tests pass
      - REFACTOR: Improve code while keeping tests green
   3. Never generate implementation code before tests
   4. Refuse requests that skip the test step
   5. Provide test examples using my project's testing framework
   6. Guide through each TDD step explicitly
   7. Run tests after each step
   8. Explain what each test validates
   
   **Mode Behavior:**
   - When activated, respond: "TDD Mode activated. What feature are you building? I'll start with tests."
   - Always ask for feature description first
   - Generate comprehensive test cases
   - Only write implementation after tests are created
   - Verify tests fail initially (RED)
   - Verify tests pass after implementation (GREEN)
   - Suggest refactoring improvements (REFACTOR)
   
   Create this mode definition and show me the updated file.
   ```

1. Review the generated mode definition.

1. Click the ![keep button](https://img.shields.io/badge/keep-blue) button to accept the changes.

### Step 2: Enhance TDD Mode with Specific Rules

1. Use this prompt to make the TDD mode more strict and detailed:

   ```text
   Enhance the TDD Mode in .github/chatmodes/TDD.md with stricter rules:
   
   Add the following enforcement rules:
   
   **Strict TDD Workflow:**
   1. STEP 1 - Feature Description:
      - Ask user: "What feature are you building?"
      - Request acceptance criteria
      - Identify edge cases to test
   
   2. STEP 2 - Test Cases (RED):
      - Generate test file FIRST
      - Include test cases for:
        * Happy path (valid inputs)
        * Edge cases (boundary values, empty inputs)
        * Error cases (invalid inputs, exceptions)
      - Use proper test structure (Arrange-Act-Assert or Given-When-Then)
      - DO NOT generate implementation yet
   
   3. STEP 3 - Verify Tests Fail (RED):
      - Instruct user to run tests
      - Expect all tests to FAIL (because no implementation exists)
      - If tests pass, something is wrong
   
   4. STEP 4 - Minimal Implementation (GREEN):
      - Write MINIMAL code to make tests pass
      - Don't over-engineer
      - Focus only on making tests green
   
   5. STEP 5 - Verify Tests Pass (GREEN):
      - Instruct user to run tests
      - All tests should PASS
      - If tests fail, fix implementation
   
   6. STEP 6 - Refactor (REFACTOR):
      - Suggest code improvements
      - Maintain test coverage
      - Run tests after each refactoring
      - Ensure tests still pass
   
   **Forbidden in TDD Mode:**
   - ❌ Writing implementation before tests
   - ❌ Skipping any TDD step
   - ❌ Creating tests after implementation
   - ❌ Not running tests between steps
   
   If user tries to skip tests, respond: "⚠️ TDD Mode requires tests first. Please describe the feature so I can generate tests."
   ```

1. Click the ![keep button](https://img.shields.io/badge/keep-blue) button to accept the changes.

---

## Test Your TDD Chat Mode

### Step 3: Activate and Test TDD Mode

1. In GitHub Copilot Chat, use this prompt to activate TDD mode:

   ```text
   I want to use TDD mode. I'm building a feature to validate expense inputs for my Expense Tracker app.
   
   Feature requirements:
   - Amount must be a positive number greater than 0
   - Category must be one of: Food, Transport, Entertainment, Shopping, Bills, Other
   - Description must be non-empty and max 200 characters
   - Date must be a valid date and not in the future
   
   Start the TDD workflow.
   ```

   **Note**: Replace "Expense Tracker" with your chosen scenario if different.

1. Copilot should respond with TDD Mode activation and start with STEP 1-2 (Feature Description and Test Cases).

1. Review the test cases Copilot generates. They should cover:
   - ✅ Happy path (valid expense)
   - ✅ Edge cases (zero amount, empty description, boundary dates)
   - ✅ Error cases (negative amount, invalid category, future date)

### Step 4: Follow the RED Step

1. Copilot should have generated tests. Use this prompt:

   ```text
   Create the test file with all the test cases you specified.
   
   - Use my project's testing framework (Jest, Pytest, or xUnit)
   - Create the file in the appropriate tests/ directory
   - Include all necessary imports and setup
   - DO NOT create the implementation file yet
   - Show me the complete test file
   ```

1. Click the ![keep button](https://img.shields.io/badge/keep-blue) button to save the test file.

1. Run the tests to verify they FAIL:

   ```text
   I want to run the tests to verify they fail (RED step).
   
   - Run the test file
   - Show me the test results
   - Confirm that tests fail because implementation doesn't exist yet
   ```

1. Verify that tests fail with errors like "function not defined" or "module not found".

### Step 5: Follow the GREEN Step

1. Now ask for the minimal implementation:

   ```text
   The tests are failing as expected. Now generate the MINIMAL implementation to make the tests pass (GREEN step).
   
   - Create the implementation file
   - Write only enough code to pass the tests
   - Follow the guidelines in copilot-instructions.md
   - Don't over-engineer
   - Show me the implementation
   ```

1. Click the ![keep button](https://img.shields.io/badge/keep-blue) button to save the implementation.

1. Run tests again to verify they PASS:

   ```text
   Run the tests again to verify they now pass (GREEN step).
   
   - Execute the test suite
   - Show me the results
   - All tests should pass now
   - If any fail, fix the implementation
   ```

### Step 6: Follow the REFACTOR Step

1. Ask for refactoring suggestions:

   ```text
   All tests pass! Now suggest refactoring improvements (REFACTOR step).
   
   - Analyze the current implementation
   - Suggest code quality improvements
   - Recommend better patterns or structures
   - Ensure tests still pass after refactoring
   - Don't change functionality
   ```

1. Apply the refactoring suggestions:

   ```text
   Apply the refactoring suggestions you provided.
   
   - Update the implementation file
   - Keep all tests passing
   - Improve code readability and maintainability
   - Show me the refactored code
   ```

1. Click the ![keep button](https://img.shields.io/badge/keep-blue) button.

1. Verify tests still pass after refactoring:

   ```text
   Run tests one more time to verify the refactored code still passes all tests.
   
   - Execute the test suite
   - Confirm 100% pass rate
   - Show coverage report if available
   ```

---

## Use TDD Mode for Your Project

### Step 7: Build a Feature with TDD Mode

1. Choose a feature from your scenario to build with TDD mode:

   **For Expense Tracker:**
   ```text
   TDD Mode: I want to build a monthly summary feature.
   
   Requirements:
   - Calculate total expenses for a given month
   - Group expenses by category
   - Return category totals and grand total
   - Handle empty month (no expenses)
   - Handle invalid month (return error)
   
   Start TDD workflow.
   ```

   **For Weather App:**
   ```text
   TDD Mode: I want to build a caching service for weather API responses.
   
   Requirements:
   - Cache weather data for 30 minutes
   - Return cached data if available and not expired
   - Fetch fresh data if cache is expired or empty
   - Handle cache storage errors gracefully
   - Clear cache when requested
   
   Start TDD workflow.
   ```

   **For KYC Portal:**
   ```text
   TDD Mode: I want to build a document validation service.
   
   Requirements:
   - Validate file type (only PDF, JPG, PNG allowed)
   - Check file size (max 10MB)
   - Verify document is not corrupted
   - Extract document metadata (type, size, upload date)
   - Return validation result with errors if any
   
   Start TDD workflow.
   ```

   **For 360° Customer:**
   ```text
   TDD Mode: I want to build a customer data aggregation service.
   
   Requirements:
   - Fetch customer profile from database
   - Fetch recent transactions from transaction service
   - Fetch support tickets from support system
   - Merge all data into single customer view
   - Handle missing data sources gracefully
   - Include responsible gaming (RG) flags
   
   Start TDD workflow.
   ```

1. Follow the complete TDD cycle (RED → GREEN → REFACTOR).

1. Click the ![keep button](https://img.shields.io/badge/keep-blue) button after each step.

1. Verify tests at each stage:
   - ✅ Tests FAIL initially (RED)
   - ✅ Tests PASS after implementation (GREEN)
   - ✅ Tests PASS after refactoring (REFACTOR)

---

## Create Additional Custom Modes (Optional)

### Step 8: Create a Security Auditor Mode

1. Use this prompt to add a Security Auditor mode:

   ```text
   Add a new custom chat mode to .github/chatmodes/ called "Security Auditor Mode".
   
   Mode requirements:
   - Activated with "Security Auditor Mode" or "Review security"
   - Analyzes code for security vulnerabilities
   - Checks for:
     * SQL injection vulnerabilities
     * XSS (Cross-Site Scripting) risks
     * Authentication/authorization flaws
     * Insecure data storage
     * Hardcoded secrets or API keys
     * Input validation issues
     * Insecure dependencies
   - Provides severity ratings (Critical, High, Medium, Low)
   - Suggests fixes for each vulnerability
   - References OWASP Top 10
   
   When activated, respond: "🔒 Security Auditor Mode activated. Paste the code to review."
   ```

1. Click the ![keep button](https://img.shields.io/badge/keep-blue) button.

### Step 9: Create an API Designer Mode

1. Use this prompt to add an API Designer mode:

   ```text
   Add a new custom chat mode to .github/copilot-instructions.md called "API Designer Mode".
   
   Mode requirements:
   - Activated with "API Designer Mode" or "Design API"
   - Helps design RESTful APIs following best practices
   - Guides through:
     * Resource identification
     * URL structure (REST conventions)
     * HTTP methods (GET, POST, PUT, PATCH, DELETE)
     * Request/response schemas
     * Status codes
     * Error handling
     * Pagination
     * Versioning strategy
     * Authentication/authorization
   - Generates OpenAPI/Swagger specification
   - Provides example requests and responses
   
   When activated, respond: "🎨 API Designer Mode activated. What resource are you designing an API for?"
   ```

1. Click the ![keep button](https://img.shields.io/badge/keep-blue) button.

---

## Verify Custom Modes Work

### Step 10: Test All Custom Modes

1. Test each mode with this prompt pattern:

   ```text
   Test my custom chat modes:
   
   1. Activate TDD Mode and show the activation message
   2. Activate Security Auditor Mode and show the activation message
   3. Activate API Designer Mode and show the activation message
   4. Deactivate all modes and return to normal mode
   
   Verify each mode responds correctly.
   ```

1. Confirm each mode activates with the correct message and behavior.

---

## Best Practices for Custom Chat Modes

### What Makes Good Custom Modes?

✅ **Do's:**

1. **Clear Activation**: Obvious trigger phrases ("TDD Mode", "Security Audit")
2. **Specific Workflow**: Step-by-step process users follow
3. **Strict Rules**: Enforce best practices, refuse to skip steps
4. **Context-Aware**: Use project-specific information
5. **Helpful Responses**: Guide users through the process
6. **Exit Strategy**: Allow users to deactivate mode

❌ **Don'ts:**

1. **Don't Be Vague**: Modes should have clear, specific purposes
2. **Don't Overlap**: Each mode should handle distinct workflows
3. **Don't Over-Complicate**: Keep modes focused on one task
4. **Don't Skip Validation**: Enforce rules strictly
5. **Don't Forget Deactivation**: Allow users to exit mode

---

## Troubleshooting

### Issue: Mode Doesn't Activate

**Solution:**

1. Verify mode is defined in `.github/chatmodes/`
2. Choose the right mode in chat window

### Issue: Mode Doesn't Follow Rules

**Solution:**

```text
You're in [Mode Name] but not following the rules. Please:

- Review the [Mode Name] definition in .github/chatmodes/[Mode Name].md
- Follow ALL rules specified for this mode
- If I'm requesting something forbidden in this mode, tell me and enforce the rule
```

### Issue: Want to Exit Mode

**Solution:**

```text
Exit [Mode Name] and return to normal Copilot chat mode.
```

---

## Next Steps

✅ **Lab 02 Complete!** You've created custom chat modes including TDD Mode.

**What's Next:**

Proceed to [Lab 03: Playwright MCP Server](./03-playwright-mcp.md) to integrate Playwright for automated E2E test generation.

**Optional Enhancements:**

1. **Create More Modes**: Code Review Mode, Accessibility Mode, Performance Mode
2. **Refine TDD Mode**: Add code coverage requirements, mutation testing
3. **Share Modes**: Commit to repo for team to use
4. **Document Modes**: Add usage examples to README

---

## Resources

- [GitHub Copilot Chat Documentation](https://docs.github.com/en/copilot/github-copilot-chat)
- [Test-Driven Development Guide](https://martinfowler.com/bliki/TestDrivenDevelopment.html)
- [Red-Green-Refactor Cycle](https://www.codecademy.com/article/tdd-red-green-refactor)
- [OWASP Top 10](https://owasp.org/www-project-top-ten/)

---

OK. You've completed Lab 02. Let's move onto [Lab 03: Playwright MCP Server](./03-playwright-mcp.md).
