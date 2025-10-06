# 04: Test-Driven Development with Copilot

## Scenario

You've created a TDD chat mode in Lab 02, and now it's time to put it into practice. Test-Driven Development (TDD) is a powerful methodology that ensures code quality, reduces bugs, and provides confidence when refactoring.

In this lab, you'll build real features for your chosen scenario using the strict TDD workflow:
- **RED**: Write failing tests first
- **GREEN**: Write minimal code to pass tests
- **REFACTOR**: Improve code while keeping tests green

By the end of this lab, you'll have production-ready features with comprehensive test coverage.

## Prerequisites

- Completed [Lab 00: Setup & Configuration](./00-setup.md)
- Completed [Lab 01: Copilot Instructions](./01-copilot-instructions.md)
- Completed [Lab 02: Custom Chat Modes](./02-custom-chat-modes.md)
- TDD Mode configured in `.github/copilot-instructions.md`
- GitHub Copilot is active in Agent Mode
- Testing framework installed (Jest, Pytest, or xUnit)

## Getting Started

- [Check GitHub Copilot Agent Mode](#check-github-copilot-agent-mode)
- [Activate TDD Mode](#activate-tdd-mode)
- [Build Feature 1: Core Validation](#build-feature-1-core-validation)
- [Build Feature 2: Business Logic](#build-feature-2-business-logic)
- [Build Feature 3: API Integration](#build-feature-3-api-integration)
- [Verify Test Coverage](#verify-test-coverage)
- [Review and Refactor](#review-and-refactor)

---

## Check GitHub Copilot Agent Mode

1. Click the GitHub Copilot icon on the top of GitHub Codespace or VS Code and open GitHub Copilot window.

   ![Open GitHub Copilot Chat](./images/setup-02.png)

1. Make sure you're using **GitHub Copilot Agent Mode**.

   ![GitHub Copilot Agent Mode](./images/setup-03.png)

1. Select model to either `GPT-4.1` or `Claude Sonnet 4`.

1. Make sure that the `context7` MCP server is up and running (if configured).

---

## Activate TDD Mode

### Step 1: Activate TDD Mode

1. In GitHub Copilot Chat, use this prompt to activate TDD Mode:

   ```text
   Activate TDD Mode as defined in .github/copilot-instructions.md.
   
   I'm ready to build features using Test-Driven Development.
   Enforce the Red-Green-Refactor cycle strictly.
   ```

1. Copilot should respond with the TDD Mode activation message.

1. Verify TDD Mode is active before proceeding.

---

## Build Feature 1: Core Validation

### Step 2: Define the Feature (RED Phase - Part 1)

Choose the appropriate prompt based on your scenario:

**For Expense Tracker:**
```text
TDD Mode: I want to build expense validation logic.

Feature requirements:
- Validate amount (must be positive number > 0, max 2 decimal places)
- Validate category (must be one of: Food, Transport, Entertainment, Shopping, Bills, Other)
- Validate description (required, non-empty, max 200 characters, no special chars that could cause XSS)
- Validate date (valid ISO date, not in future, not more than 1 year in past)
- Return validation result: { valid: boolean, errors: string[] }

Edge cases to test:
- Zero amount
- Negative amount
- Amount with more than 2 decimals
- Invalid category
- Empty description
- Description with XSS attempts (<script>)
- Very long description (> 200 chars)
- Future date
- Very old date (> 1 year ago)
- Invalid date format

Start TDD workflow with STEP 1: Feature Description and STEP 2: Test Cases.
```

**For Weather App:**
```text
TDD Mode: I want to build weather API caching service.

Feature requirements:
- Cache weather data for a specific location
- Cache expires after 30 minutes
- Return cached data if available and not expired
- Fetch fresh data if cache is expired or empty
- Handle cache storage errors gracefully
- Provide cache statistics (hits, misses, size)

Edge cases to test:
- First request (cache miss)
- Subsequent request within 30 min (cache hit)
- Request after 30 min (cache expired)
- Cache storage failure
- Multiple locations cached simultaneously
- Clearing cache
- Cache size limits

Start TDD workflow with STEP 1: Feature Description and STEP 2: Test Cases.
```

**For KYC Portal:**
```text
TDD Mode: I want to build document validation service.

Feature requirements:
- Validate file type (only PDF, JPG, PNG, max file size 10MB)
- Validate file is not corrupted (can be opened)
- Extract metadata (filename, size, type, upload timestamp)
- Scan for malicious content (basic checks)
- Return validation result with detailed errors
- Log all validation attempts for audit trail

Edge cases to test:
- Valid PDF document
- Valid image (JPG, PNG)
- Invalid file type (.exe, .txt)
- File exceeds 10MB
- Corrupted file
- File with no extension
- Empty file (0 bytes)
- Malicious file name (path traversal attempts)

Start TDD workflow with STEP 1: Feature Description and STEP 2: Test Cases.
```

**For 360° Customer:**
```text
TDD Mode: I want to build customer data aggregation service.

Feature requirements:
- Fetch customer profile from database
- Fetch transaction history (last 30 days)
- Fetch support tickets (open and recent closed)
- Fetch compliance flags (RG status, limits, self-exclusion)
- Merge all data into unified customer view
- Handle missing/failed data sources gracefully
- Return comprehensive customer object
- Track data freshness (last updated timestamp for each source)

Edge cases to test:
- All data sources available
- One data source fails (profile, transactions, support, or compliance)
- Multiple data sources fail
- Empty data (new customer with no history)
- Large transaction history (pagination needed)
- Customer with self-exclusion flag
- Network timeout on data source
- Invalid customer ID

Start TDD workflow with STEP 1: Feature Description and STEP 2: Test Cases.
```

1. Review the test cases Copilot generates.

### Step 3: Create Test File (RED Phase - Part 2)

1. Use this prompt to create the test file:

   ```text
   TDD Mode STEP 2: Create the test file with all test cases.
   
   - Use my project's testing framework (Jest, Pytest, or xUnit)
   - Create test file in tests/ directory
   - Include all test cases you identified:
     * Happy path tests
     * Edge case tests
     * Error case tests
   - Use Arrange-Act-Assert pattern
   - Include descriptive test names
   - DO NOT create implementation yet
   - Show me the complete test file
   ```

1. Review the generated test file carefully.

1. Click the ![keep button](https://img.shields.io/badge/keep-blue) button to save the test file.

### Step 4: Verify Tests Fail (RED Phase - Part 3)

1. Run the tests to verify they fail:

   ```text
   TDD Mode STEP 3: Run the tests to verify they fail (RED phase).
   
   - Run the test file
   - All tests should FAIL because implementation doesn't exist
   - Show me the test results
   - Confirm we're in RED phase
   ```

1. Verify all tests fail with errors like "function not defined" or "module not found".

1. ✅ **RED Phase Complete** - You have failing tests!

### Step 5: Create Minimal Implementation (GREEN Phase)

1. Now create the implementation to make tests pass:

   ```text
   TDD Mode STEP 4: Create the MINIMAL implementation (GREEN phase).
   
   - Create the implementation file in src/ or appropriate directory
   - Write only enough code to make ALL tests pass
   - Don't over-engineer or add extra features
   - Follow guidelines in .github/copilot-instructions.md
   - Include error handling as tested
   - Show me the implementation code
   ```

1. Review the implementation.

1. Click the ![keep button](https://img.shields.io/badge/keep-blue) button to save the implementation.

### Step 6: Verify Tests Pass (GREEN Phase Validation)

1. Run tests again to verify they now pass:

   ```text
   TDD Mode STEP 5: Run tests to verify they all PASS (GREEN phase).
   
   - Run the test suite
   - All tests should now PASS
   - Show me the test results
   - If any fail, fix the implementation
   - Confirm we're in GREEN phase
   ```

1. Verify all tests pass.

1. ✅ **GREEN Phase Complete** - All tests pass!

### Step 7: Refactor (REFACTOR Phase)

1. Improve the code quality:

   ```text
   TDD Mode STEP 6: Suggest refactoring improvements (REFACTOR phase).
   
   - Analyze the current implementation
   - Suggest code quality improvements:
     * Extract reusable functions
     * Improve naming
     * Reduce duplication
     * Better error messages
     * Add type safety (if applicable)
   - Don't change functionality
   - Ensure tests still pass after refactoring
   - Show me the refactoring suggestions
   ```

1. Apply the refactoring:

   ```text
   TDD Mode: Apply the refactoring suggestions.
   
   - Update the implementation file
   - Keep all tests passing
   - Improve code readability and maintainability
   - Show me the refactored code
   ```

1. Click the ![keep button](https://img.shields.io/badge/keep-blue) button.

1. Verify tests still pass after refactoring:

   ```text
   Run tests after refactoring to ensure they all still PASS.
   
   - Execute test suite
   - Confirm 100% pass rate
   - Show results
   ```

1. ✅ **REFACTOR Phase Complete** - Clean code with passing tests!

---

## Build Feature 2: Business Logic

### Step 8: Build Complex Business Logic

Now build a more complex feature using TDD. Choose based on your scenario:

**For Expense Tracker:**
```text
TDD Mode: I want to build monthly expense summary calculator.

Feature requirements:
- Calculate total expenses for a given month/year
- Group expenses by category
- Calculate percentage of total for each category
- Find highest expense
- Find most frequent category
- Return summary object with all statistics
- Handle empty month (no expenses)
- Handle invalid month/year

Test cases should cover:
- Month with multiple expenses
- Month with no expenses
- All expenses in one category
- Expenses evenly distributed
- Invalid month (0, 13, -1)
- Invalid year (future year, too old)
- Leap year handling (February expenses)

Start full TDD cycle: RED → GREEN → REFACTOR
```

**For Weather App:**
```text
TDD Mode: I want to build weather data transformer.

Feature requirements:
- Transform raw API response to app format
- Convert temperature units (Celsius ↔ Fahrenheit)
- Format date/time for display
- Extract relevant weather conditions
- Calculate "feels like" temperature
- Determine weather icon based on conditions
- Handle missing data fields gracefully
- Validate API response structure

Test cases should cover:
- Valid API response
- Missing optional fields
- Temperature conversion (both directions)
- Different weather conditions (sunny, rainy, cloudy, stormy)
- Edge temperatures (very hot, very cold, freezing)
- Invalid API response structure
- Null/undefined values

Start full TDD cycle: RED → GREEN → REFACTOR
```

**For KYC Portal:**
```text
TDD Mode: I want to build document verification workflow manager.

Feature requirements:
- Track document through verification workflow
- States: Pending → In Review → Approved/Rejected
- Only allow valid state transitions
- Create audit log entry on each transition
- Assign reviewer to document
- Set verification deadline (3 business days)
- Send notifications on state change
- Prevent unauthorized state changes

Test cases should cover:
- Valid transitions (Pending → In Review → Approved)
- Valid transitions (Pending → In Review → Rejected)
- Invalid transitions (Pending → Approved directly)
- Expired verification deadline
- Unauthorized reviewer assignment
- Duplicate state transitions
- Concurrent state changes
- Audit trail completeness

Start full TDD cycle: RED → GREEN → REFACTOR
```

**For 360° Customer:**
```text
TDD Mode: I want to build responsible gaming (RG) alert system.

Feature requirements:
- Monitor customer betting patterns
- Detect threshold breaches (daily, weekly, monthly limits)
- Track deposit/withdrawal ratios
- Identify self-exclusion status
- Generate RG risk score (Low, Medium, High, Critical)
- Create alerts for support team
- Log all RG events for compliance
- Calculate cooling-off period end dates

Test cases should cover:
- Normal betting within limits
- Daily limit breach
- Weekly limit accumulation
- Monthly limit exceeded
- High deposit frequency (addiction indicator)
- Self-excluded customer attempting access
- Risk score calculation (various patterns)
- Multiple simultaneous limit breaches
- Historical pattern analysis

Start full TDD cycle: RED → GREEN → REFACTOR
```

1. Follow the complete TDD cycle for this feature:
   - Generate tests (RED)
   - Run and verify tests fail
   - Create implementation (GREEN)
   - Verify tests pass
   - Refactor
   - Verify tests still pass

1. Click the ![keep button](https://img.shields.io/badge/keep-blue) button after each phase.

---

## Build Feature 3: API Integration

### Step 9: Build API Integration with TDD

Build an API integration feature. Choose based on your scenario:

**For Expense Tracker:**
```text
TDD Mode: I want to build expense filtering API endpoint.

Feature requirements:
- GET /api/expenses with query parameters
- Filter by: category, month, year, minAmount, maxAmount
- Support multiple filters simultaneously
- Return filtered expenses array
- Return total count of filtered results
- Return summary statistics (total, average)
- Handle invalid filters gracefully
- Return 400 for invalid parameters

Test cases should cover:
- No filters (return all)
- Single filter (category only)
- Multiple filters (category + month)
- Amount range (minAmount, maxAmount)
- Invalid category
- Invalid date range
- No results found
- Large result set (pagination may be needed)
- Query parameter validation

Start full TDD cycle: RED → GREEN → REFACTOR
Mock external dependencies (database).
```

**For Weather App:**
```text
TDD Mode: I want to build weather API client with error handling.

Feature requirements:
- Fetch current weather by city name
- Fetch 5-day forecast by coordinates
- Handle API rate limiting (429 status)
- Handle API errors (4xx, 5xx)
- Retry logic (3 retries with exponential backoff)
- Timeout handling (5 second timeout)
- Parse and validate API responses
- Use API key from environment variable

Test cases should cover:
- Successful API call (current weather)
- Successful API call (forecast)
- API returns 404 (city not found)
- API returns 429 (rate limited)
- API returns 500 (server error)
- Network timeout
- Retry succeeds on 2nd attempt
- All retries fail
- Invalid API response format
- Missing API key

Start full TDD cycle: RED → GREEN → REFACTOR
Mock HTTP requests (use mock library).
```

**For KYC Portal:**
```text
TDD Mode: I want to build document upload API endpoint.

Feature requirements:
- POST /api/documents with multipart form data
- Accept PDF, JPG, PNG files only
- Validate file size (max 10MB)
- Scan file for malware (integrate with scanning service)
- Save file to secure storage
- Create database record
- Create audit log entry
- Return upload confirmation with document ID
- Handle concurrent uploads

Test cases should cover:
- Valid file upload (PDF)
- Valid file upload (image)
- Invalid file type
- File too large (> 10MB)
- Malware detected
- Storage service failure
- Database failure
- Concurrent uploads from same user
- Missing required fields
- Unauthorized upload attempt

Start full TDD cycle: RED → GREEN → REFACTOR
Mock file storage and virus scanning services.
```

**For 360° Customer:**
```text
TDD Mode: I want to build customer data sync service.

Feature requirements:
- Fetch data from multiple microservices
- Services: ProfileService, TransactionService, SupportService, ComplianceService
- Implement parallel fetching (Promise.all or async)
- Handle partial failures (some services down)
- Implement circuit breaker pattern
- Cache responses (5 minute TTL)
- Fallback to stale cache if all services fail
- Track service health metrics
- Timeout per service (3 seconds)

Test cases should cover:
- All services respond successfully
- Profile service fails (others succeed)
- Transaction service fails (others succeed)
- Multiple services fail
- All services fail (use stale cache)
- Service timeout
- Parallel fetching works correctly
- Circuit breaker opens after 5 failures
- Circuit breaker half-open retry
- Cache hit/miss scenarios

Start full TDD cycle: RED → GREEN → REFACTOR
Mock all external service calls.
```

1. Follow the complete TDD cycle for this API integration.

1. Click the ![keep button](https://img.shields.io/badge/keep-blue) button after each phase.

---

## Verify Test Coverage

### Step 10: Check Test Coverage

1. Run test coverage analysis:

   ```text
   Run test coverage analysis for all the code we've written.
   
   - Execute test suite with coverage reporting
   - Show coverage percentages for:
     * Overall coverage
     * Statement coverage
     * Branch coverage
     * Function coverage
   - Identify uncovered code paths
   - Show me the coverage report
   
   Target: Minimum 85% coverage
   ```

1. Review the coverage report.

### Step 11: Add Tests for Uncovered Code

1. If coverage is below 85%, add more tests:

   ```text
   Coverage is below 85%. Add tests to cover the missing code paths.
   
   - Identify uncovered lines/branches
   - Write additional test cases
   - Focus on edge cases and error paths
   - Follow TDD RED-GREEN-REFACTOR cycle
   - Show me the new tests
   
   Goal: Achieve 85%+ coverage
   ```

1. Click the ![keep button](https://img.shields.io/badge/keep-blue) button.

1. Run coverage again to verify improvement:

   ```text
   Run coverage analysis again to verify we've reached 85%+ coverage.
   
   - Show updated coverage report
   - Confirm all critical paths are tested
   ```

1. ✅ **Coverage Target Achieved!**

---

## Review and Refactor

### Step 12: Final Code Review

1. Exit TDD Mode and do a comprehensive code review:

   ```text
   Exit TDD Mode.
   
   Now review all the code we created in this lab:
   
   1. Check code quality:
      - Is code readable and maintainable?
      - Are functions small and focused?
      - Is naming clear and consistent?
      - Is error handling comprehensive?
   
   2. Check tests quality:
      - Are tests clear and descriptive?
      - Do tests test behavior, not implementation?
      - Are tests independent?
      - Can tests run in any order?
   
   3. Check architecture:
      - Is separation of concerns maintained?
      - Are dependencies properly managed?
      - Is the code following project conventions?
   
   Provide a summary report with any improvement suggestions.
   ```

1. Review Copilot's analysis.

### Step 13: Apply Final Improvements

1. Apply any recommended improvements:

   ```text
   Apply the improvement suggestions from the code review.
   
   - Refactor code as recommended
   - Keep all tests passing
   - Update tests if needed
   - Maintain 85%+ coverage
   - Show me the final version
   ```

1. Click the ![keep button](https://img.shields.io/badge/keep-blue) button.

1. Run final test suite:

   ```text
   Run the complete test suite one final time.
   
   - Execute all tests
   - Show pass/fail summary
   - Show coverage report
   - Confirm everything is green ✅
   ```

1. ✅ **All Tests Passing with High Coverage!**

---

## Best Practices Applied

### What You've Learned

Throughout this lab, you've practiced:

✅ **TDD Cycle**
- Write tests first (RED)
- Make tests pass (GREEN)
- Improve code (REFACTOR)
- Repeat for every feature

✅ **Test Quality**
- Comprehensive test coverage (happy path, edge cases, errors)
- Descriptive test names
- Arrange-Act-Assert pattern
- Independent tests

✅ **Code Quality**
- Minimal implementation
- Separation of concerns
- Error handling
- Maintainable code

✅ **Development Workflow**
- Feature-driven development
- Incremental progress
- Confidence through tests
- Safe refactoring

---

## Troubleshooting

### Issue: Tests Are Too Slow

**Solution:**

```text
My tests are running slowly. Help me optimize them.

- Identify slow tests
- Suggest optimizations:
  * Remove unnecessary setup/teardown
  * Mock expensive operations
  * Parallelize test execution
  * Use test data factories
- Show me the optimized tests
```

### Issue: Tests Are Brittle

**Solution:**

```text
My tests break whenever I change implementation details. Help me make tests more robust.

- Review test implementation
- Test behavior, not implementation details
- Use public APIs only
- Avoid testing private methods
- Refactor tests for stability
- Show me the improvements
```

### Issue: Hard to Test Code

**Solution:**

```text
I'm struggling to test this code because it has tight coupling. Help me refactor for testability.

- Identify coupling issues
- Suggest dependency injection
- Extract interfaces/abstractions
- Make code more modular
- Show me the refactored code with tests
```

---

## Next Steps

✅ **Lab 04 Complete!** You've built features using Test-Driven Development with high test coverage.

**What's Next:**

Proceed to [Lab 05: Documentation Automation](./06-documentation.md) to generate comprehensive documentation for your project.

**Optional Enhancements:**

1. **Mutation Testing**: Use mutation testing to verify test quality
2. **Property-Based Testing**: Add property-based tests for complex logic
3. **Performance Tests**: Add performance benchmarks
4. **Integration Tests**: Test components working together

---

## Resources

- [Test-Driven Development (Martin Fowler)](https://martinfowler.com/bliki/TestDrivenDevelopment.html)
- [Red-Green-Refactor Cycle](https://www.codecademy.com/article/tdd-red-green-refactor)
- [Testing Best Practices](https://testingjavascript.com/)
- [Jest Documentation](https://jestjs.io/)
- [Pytest Documentation](https://docs.pytest.org/)
- [xUnit Documentation](https://xunit.net/)

---

OK. You've completed Lab 04. Let's move onto [Lab 05: Documentation Automation](./06-documentation.md).
