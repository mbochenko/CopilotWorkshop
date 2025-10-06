# 07: Advanced Copilot Techniques

## Scenario

You've mastered the fundamentals of GitHub Copilot and built complete features using TDD. Now it's time to explore advanced techniques that will make you a Copilot power user.

In this lab, you'll learn:
- Advanced prompting strategies for complex scenarios
- Performance optimization with AI assistance
- Architecture design and refactoring
- AI-powered code review and security analysis
- Integration testing patterns
- Real-world problem-solving techniques

This lab focuses on advanced, production-ready scenarios that experienced developers encounter daily. You'll push Copilot to its limits and learn techniques that can transform your development workflow.

## Prerequisites

- Completed [Lab 00: Setup & Configuration](./00-setup.md)
- Completed [Lab 01: Copilot Instructions](./01-copilot-instructions.md)
- Completed [Lab 05: TDD with Copilot](./05-tdd-with-copilot.md)
- Have a working project with implemented features
- GitHub Copilot is active in Agent Mode
- Comfortable with advanced programming concepts

## Getting Started

- [Check GitHub Copilot Agent Mode](#check-github-copilot-agent-mode)
- [Advanced API Integration](#advanced-api-integration)
- [Performance Optimization](#performance-optimization)
- [Architecture Design](#architecture-design)
- [AI-Powered Code Review](#ai-powered-code-review)
- [Integration Testing](#integration-testing)
- [Refactoring Complex Code](#refactoring-complex-code)

---

## Check GitHub Copilot Agent Mode

1. Click the GitHub Copilot icon on the top of GitHub Codespace or VS Code and open GitHub Copilot window.

   ![Open GitHub Copilot Chat](./images/setup-02.png)

1. Make sure you're using **GitHub Copilot Agent Mode**.

   ![GitHub Copilot Agent Mode](./images/setup-03.png)

1. Select model to either `GPT-4.1` or `Claude Sonnet 4`.

1. Make sure that the `context7` MCP server is up and running (if configured).

---

## Advanced API Integration

### Step 1: Implement Resilient API Client

1. Use this prompt to create a production-ready API client:

   **For Expense Tracker (External Receipt OCR API):**
   ```text
   Create a resilient HTTP client for a receipt OCR API integration. Follow the instructions below.
   
   Requirements:
   - Use IHttpClientFactory for proper HttpClient lifecycle management
   - Implement Polly retry policy for transient failures (3 retries with exponential backoff)
   - Handle rate limiting (HTTP 429) with retry-after header support
   - Add circuit breaker pattern (open after 5 failures, half-open after 30 seconds)
   - Implement timeout policy (30 seconds per request, 90 seconds total)
   - Add structured logging with correlation IDs
   - Deserialize JSON to ReceiptData strongly-typed model
   - Include custom telemetry for success/failure tracking
   - Support cancellation tokens throughout
   - Add request/response logging for debugging
   
   Tech stack:
   - Microsoft.Extensions.Http.Polly for resilience
   - System.Text.Json for deserialization
   - ILogger for structured logging
   
   List all steps first, then implement the complete solution.
   Create Services/ReceiptOcrClient.cs and configure in Program.cs/Startup.cs.
   ```

   **For Weather App (OpenWeatherMap API):**
   ```text
   Create a resilient HTTP client for OpenWeatherMap API integration. Follow the instructions below.
   
   Requirements:
   - Use IHttpClientFactory for proper HttpClient lifecycle management
   - Implement Polly retry policy for transient failures (3 retries with exponential backoff)
   - Handle rate limiting (HTTP 429) with retry-after header support
   - Add circuit breaker pattern (open after 5 failures, half-open after 30 seconds)
   - Implement timeout policy (30 seconds per request, 90 seconds total)
   - Add structured logging with correlation IDs
   - Deserialize JSON to WeatherData strongly-typed model
   - Include custom telemetry for API call success/failure
   - Support cancellation tokens throughout
   - Add request/response logging for debugging
   - Handle API key authentication
   
   Tech stack:
   - Microsoft.Extensions.Http.Polly for resilience
   - System.Text.Json for deserialization
   - ILogger for structured logging
   
   List all steps first, then implement the complete solution.
   Create Services/WeatherApiClient.cs and configure in Program.cs/Startup.cs.
   ```

   **For KYC Portal (External ID Verification API):**
   ```text
   Create a resilient HTTP client for ID verification API integration. Follow the instructions below.
   
   Requirements:
   - Use IHttpClientFactory for proper HttpClient lifecycle management
   - Implement Polly retry policy for transient failures (3 retries with exponential backoff)
   - Handle rate limiting (HTTP 429) with retry-after header support
   - Add circuit breaker pattern (open after 5 failures, half-open after 30 seconds)
   - Implement timeout policy (30 seconds per request, 90 seconds total)
   - Add structured logging with correlation IDs (redact sensitive data)
   - Deserialize JSON to VerificationResult strongly-typed model
   - Include custom telemetry for verification success/failure
   - Support cancellation tokens throughout
   - Add request/response logging (sanitize PII)
   - Handle authentication with bearer tokens
   
   Tech stack:
   - Microsoft.Extensions.Http.Polly for resilience
   - System.Text.Json for deserialization
   - ILogger for structured logging
   
   List all steps first, then implement the complete solution.
   Create Services/IdVerificationClient.cs and configure in Program.cs/Startup.cs.
   ```

   **For 360° Customer (CRM Data Aggregation API):**
   ```text
   Create a resilient HTTP client for CRM data aggregation API. Follow the instructions below.
   
   Requirements:
   - Use IHttpClientFactory for proper HttpClient lifecycle management
   - Implement Polly retry policy for transient failures (3 retries with exponential backoff)
   - Handle rate limiting (HTTP 429) with retry-after header support
   - Add circuit breaker pattern (open after 5 failures, half-open after 30 seconds)
   - Implement timeout policy (30 seconds per request, 90 seconds total)
   - Add structured logging with correlation IDs
   - Deserialize JSON to CustomerData strongly-typed model
   - Include custom telemetry for aggregation operations
   - Support cancellation tokens throughout
   - Add request/response logging for debugging
   - Handle OAuth 2.0 authentication
   
   Tech stack:
   - Microsoft.Extensions.Http.Polly for resilience
   - System.Text.Json for deserialization
   - ILogger for structured logging
   
   List all steps first, then implement the complete solution.
   Create Services/CrmAggregationClient.cs and configure in Program.cs/Startup.cs.
   ```

1. Review the generated code and implementation plan.

1. Click the ![keep button](https://img.shields.io/badge/keep-blue) button.

### Step 2: Add Comprehensive Unit Tests

1. Generate tests for the resilient client:

   ```text
   Generate comprehensive unit tests for the API client created in the previous step.
   
   Test scenarios to cover:
   
   **Happy Path:**
   - Successful API call returns expected data
   - Deserialization works correctly
   - Correlation IDs are logged
   
   **Retry Logic:**
   - Transient failures trigger retry (3 attempts)
   - Exponential backoff delays are correct
   - Eventually succeeds after retries
   - Fails after max retries exceeded
   
   **Rate Limiting:**
   - HTTP 429 triggers retry-after delay
   - Retry-after header is respected
   - Rate limit recovery works correctly
   
   **Circuit Breaker:**
   - Opens after 5 consecutive failures
   - Rejects requests when open
   - Transitions to half-open after timeout
   - Closes after successful request in half-open state
   
   **Timeout Handling:**
   - Request timeout after 30 seconds
   - Total timeout after 90 seconds
   - Cancellation token propagation
   
   **Error Handling:**
   - Network failures handled gracefully
   - Invalid JSON responses handled
   - HTTP error codes (400, 404, 500, 503) handled
   - Null/empty responses handled
   
   **Logging:**
   - Success logged with correlation ID
   - Failures logged with details
   - Retry attempts logged
   - Circuit breaker state changes logged
   
   Use:
   - xUnit or NUnit for test framework
   - Moq for mocking HttpMessageHandler
   - FluentAssertions for assertions
   - Bogus for test data generation
   
   Create comprehensive test file in Tests/Services/[ClientName]Tests.cs.
   Include setup, teardown, and helper methods.
   ```

1. Click the ![keep button](https://img.shields.io/badge/keep-blue) button.

---

## Performance Optimization

### Step 3: Implement Intelligent Caching

1. Use this prompt to add production-ready caching:

   ```text
   Implement an intelligent caching service for the application. Follow the instructions below.
   
   Requirements:
   
   **Cache Strategy:**
   - Support both in-memory (IMemoryCache) and distributed (Redis) caching
   - Use cache-aside pattern (lazy loading)
   - Implement cache key generation with consistent hashing
   - Support multiple cache regions/namespaces
   
   **Cache Configuration:**
   - Configurable TTL (Time To Live) per cache region
   - Sliding expiration support
   - Absolute expiration support
   - Size limits and eviction policies
   
   **Cache Operations:**
   - GetOrCreateAsync with factory pattern
   - Invalidate by key
   - Invalidate by pattern (wildcard support)
   - Bulk invalidation
   - Cache warming on startup
   
   **Observability:**
   - Cache hit/miss metrics
   - Cache size metrics
   - Eviction rate metrics
   - Performance metrics (get/set duration)
   - Structured logging for cache operations
   
   **Advanced Features:**
   - Prevent cache stampede (single flight)
   - Support for cache dependencies
   - Compression for large values
   - Serialization optimization
   
   Implementation:
   - Create ICacheService interface
   - Implement InMemoryCacheService
   - Implement RedisCacheService
   - Add CacheConfiguration settings
   - Register services in DI container
   - Add cache metrics collection
   
   List all steps first, then implement the complete solution.
   Create Services/Caching/ directory with all necessary files.
   ```

1. Click the ![keep button](https://img.shields.io/badge/keep-blue) button.

### Step 4: Add Performance Monitoring

1. Implement comprehensive performance tracking:

   ```text
   Add performance monitoring and metrics collection to the application.
   
   Requirements:
   
   **Metrics to Track:**
   - API response times (p50, p95, p99)
   - Database query duration
   - Cache hit/miss rates
   - External API call duration
   - Memory usage and GC metrics
   - Request throughput (requests per second)
   - Error rates by type
   
   **Implementation:**
   - Use System.Diagnostics.Metrics for .NET metrics
   - Create custom meters and instruments
   - Add middleware for automatic HTTP metrics
   - Add decorators for database metrics
   - Add interceptors for cache metrics
   
   **Instrumentation:**
   - Add metrics to all service methods
   - Track custom business metrics
   - Add distributed tracing correlation
   - Include custom dimensions/tags
   
   **Visualization:**
   - Configure Prometheus exporters
   - Add Grafana dashboard JSON
   - Create alerting rules
   - Document metrics and their meaning
   
   **Best Practices:**
   - Use semantic naming conventions
   - Add units to metric names
   - Include helpful descriptions
   - Minimize performance overhead
   - Use sampling for high-frequency operations
   
   List all steps first, then implement the complete solution.
   Create Services/Metrics/ directory with implementation.
   Add Grafana dashboard to /monitoring/dashboards/.
   ```

1. Click the ![keep button](https://img.shields.io/badge/keep-blue) button.

---

## Architecture Design

### Step 5: Design Event-Driven Architecture

1. Use this prompt to design an event-driven system:

   **For Expense Tracker:**
   ```text
   Design and implement an event-driven notification system for expense alerts. Follow the instructions below.
   
   Architecture:
   - Domain events for expense-related actions (ExpenseCreated, ExpenseApproved, BudgetExceeded)
   - Event publisher using MediatR or custom implementation
   - Event handlers for notifications (Email, SMS, Push)
   - Event store for audit trail
   - Retry and dead-letter queue handling
   
   Components:
   
   **Domain Events:**
   - ExpenseCreatedEvent
   - ExpenseUpdatedEvent
   - ExpenseDeletedEvent
   - MonthlyBudgetExceededEvent
   - CategoryBudgetWarningEvent
   
   **Event Handlers:**
   - EmailNotificationHandler
   - SmsNotificationHandler
   - PushNotificationHandler
   - AuditLogHandler
   - AnalyticsHandler
   
   **Infrastructure:**
   - IEventPublisher interface
   - InMemoryEventBus for development
   - Support for Azure Service Bus / RabbitMQ for production
   - Event serialization and deserialization
   - Idempotency handling
   
   **Patterns:**
   - CQRS for separating reads and writes
   - Saga pattern for multi-step workflows
   - Outbox pattern for reliable publishing
   - Circuit breaker for external notifications
   
   List all architecture components first.
   Then implement domain events, publishers, and handlers.
   Create Events/, EventHandlers/, and Infrastructure/Messaging/ directories.
   ```

   **For Weather App:**
   ```text
   Design and implement an event-driven weather alert system. Follow the instructions below.
   
   Architecture:
   - Domain events for weather-related alerts (SevereWeatherAlert, TemperatureThresholdExceeded)
   - Event publisher using MediatR or custom implementation
   - Event handlers for notifications (Email, SMS, Push)
   - Event store for alert history
   - Retry and dead-letter queue handling
   
   Components:
   
   **Domain Events:**
   - WeatherDataUpdatedEvent
   - SevereWeatherAlertEvent
   - TemperatureThresholdCrossedEvent
   - WeatherForecastChangedEvent
   - UserLocationUpdatedEvent
   
   **Event Handlers:**
   - EmailAlertHandler
   - SmsAlertHandler
   - PushNotificationHandler
   - WeatherHistoryHandler
   - TrendAnalysisHandler
   
   **Infrastructure:**
   - IEventPublisher interface
   - InMemoryEventBus for development
   - Support for Azure Service Bus / RabbitMQ for production
   - Event serialization and deserialization
   - Idempotency handling
   
   **Patterns:**
   - CQRS for separating reads and writes
   - Saga pattern for multi-step alert workflows
   - Outbox pattern for reliable publishing
   - Circuit breaker for external notifications
   
   List all architecture components first.
   Then implement domain events, publishers, and handlers.
   Create Events/, EventHandlers/, and Infrastructure/Messaging/ directories.
   ```

   **For KYC Portal / 360° Customer:**
   ```text
   Design and implement an event-driven workflow system for [KYC verification / customer data updates]. Follow the instructions below.
   
   Architecture:
   - Domain events for workflow state changes
   - Event publisher using MediatR or custom implementation
   - Event handlers for workflow steps
   - Event store for compliance audit trail
   - Retry and dead-letter queue handling
   
   Components:
   
   **Domain Events:**
   - [DocumentSubmittedEvent / CustomerDataUpdatedEvent]
   - [VerificationCompletedEvent / AggregationCompletedEvent]
   - [DocumentRejectedEvent / DataConflictDetectedEvent]
   - [ApprovalRequiredEvent / ManualReviewRequiredEvent]
   - [WorkflowCompletedEvent / SyncCompletedEvent]
   
   **Event Handlers:**
   - NotificationHandler (email, SMS)
   - AuditLogHandler (compliance trail)
   - WorkflowOrchestrationHandler
   - ReportGenerationHandler
   - IntegrationSyncHandler
   
   **Infrastructure:**
   - IEventPublisher interface
   - InMemoryEventBus for development
   - Support for Azure Service Bus / RabbitMQ for production
   - Event serialization and deserialization
   - Idempotency handling (critical for compliance)
   
   **Patterns:**
   - CQRS for separating reads and writes
   - Saga pattern for multi-step verification workflows
   - Outbox pattern for reliable publishing
   - Circuit breaker for external integrations
   
   List all architecture components first.
   Then implement domain events, publishers, and handlers.
   Create Events/, EventHandlers/, and Infrastructure/Messaging/ directories.
   Include compliance considerations in event design.
   ```

1. Review the architecture design.

1. Click the ![keep button](https://img.shields.io/badge/keep-blue) button.

### Step 6: Create Architecture Documentation

1. Generate architecture diagrams and documentation:

   ```text
   Create comprehensive architecture documentation for the event-driven system.
   
   Generate:
   
   **1. Architecture Decision Record (ADR):**
   - Decision: Implement event-driven architecture
   - Context: Why we need events
   - Consequences: Benefits and trade-offs
   - Alternatives considered
   - Implementation approach
   
   Save as docs/architecture/ADR-001-event-driven-architecture.md
   
   **2. Mermaid Architecture Diagram:**
   - Component diagram showing all services
   - Event flow diagram
   - Deployment diagram
   - Sequence diagram for key scenarios
   
   Save as docs/architecture/event-architecture.mermaid
   
   **3. Event Catalog:**
   - List all domain events
   - Event schema for each
   - Publishers and subscribers
   - SLA and retry policies
   
   Save as docs/architecture/event-catalog.md
   
   **4. Runbook:**
   - How to monitor event processing
   - How to handle failures
   - How to replay events
   - Troubleshooting guide
   
   Save as docs/operations/event-system-runbook.md
   
   Create all documentation files with professional quality.
   Use clear diagrams and practical examples.
   ```

1. Click the ![keep button](https://img.shields.io/badge/keep-blue) button.

---

## AI-Powered Code Review

### Step 7: Security Analysis

1. Use Copilot to perform security review:

   ```text
   Perform a comprehensive security analysis of the codebase. Follow the instructions below.
   
   Review for:
   
   **1. Authentication & Authorization:**
   - [ ] Missing authentication checks
   - [ ] Weak password policies
   - [ ] Insecure token storage
   - [ ] Missing authorization on endpoints
   - [ ] Privilege escalation vulnerabilities
   
   **2. Input Validation:**
   - [ ] SQL injection vulnerabilities
   - [ ] XSS (Cross-Site Scripting) vulnerabilities
   - [ ] Command injection risks
   - [ ] Path traversal vulnerabilities
   - [ ] Insufficient input sanitization
   
   **3. Data Protection:**
   - [ ] Sensitive data in logs
   - [ ] Unencrypted sensitive data
   - [ ] Weak encryption algorithms
   - [ ] Missing data masking
   - [ ] Insecure data transmission
   
   **4. API Security:**
   - [ ] Missing rate limiting
   - [ ] CORS misconfiguration
   - [ ] API key exposure
   - [ ] Insecure deserialization
   - [ ] Missing HTTPS enforcement
   
   **5. Dependency Security:**
   - [ ] Vulnerable NuGet packages
   - [ ] Outdated dependencies
   - [ ] Known CVEs in dependencies
   
   **6. Error Handling:**
   - [ ] Information disclosure in error messages
   - [ ] Stack traces exposed to users
   - [ ] Unhandled exceptions
   
   For each issue found:
   - Severity level (Critical/High/Medium/Low)
   - Location in code
   - Detailed explanation
   - Recommended fix with code example
   - OWASP reference (if applicable)
   
   Generate a comprehensive security report in docs/security/security-audit.md.
   Prioritize issues by severity.
   Include remediation roadmap.
   ```

1. Review the security report.

### Step 8: Apply Security Fixes

1. Fix identified security issues:

   ```text
   Apply the security fixes recommended in the security audit report.
   
   Prioritize in this order:
   1. Critical severity issues first
   2. High severity issues
   3. Medium severity issues
   4. Low severity issues
   
   For each fix:
   - Implement the recommended solution
   - Add security-focused unit tests
   - Verify no regression in existing functionality
   - Document the security improvement
   
   Show me each fix one at a time with:
   - Issue description
   - Code changes
   - Test coverage
   - Verification steps
   
   Start with critical severity issues.
   ```

1. Review and apply each fix.

1. Click the ![keep button](https://img.shields.io/badge/keep-blue) button after each fix.

---

## Integration Testing

### Step 9: Create Integration Test Suite

1. Generate comprehensive integration tests:

   ```text
   Create a complete integration test suite for the application. Follow the instructions below.
   
   Test Infrastructure:
   
   **Test Containers:**
   - Use Testcontainers for .NET
   - Spin up real database (SQL Server/PostgreSQL)
   - Spin up Redis for caching tests
   - Spin up message broker (RabbitMQ/Azure Service Bus emulator)
   
   **WebApplicationFactory:**
   - Configure test host with realistic settings
   - Replace external dependencies with test versions
   - Configure logging for test output
   - Set up test data seeding
   
   Test Scenarios:
   
   **1. API Integration Tests:**
   - Full request/response cycle
   - Authentication and authorization
   - Data persistence verification
   - Cache behavior verification
   - Error handling scenarios
   
   **2. Database Integration Tests:**
   - CRUD operations
   - Transaction handling
   - Concurrency and locking
   - Migration verification
   - Query performance
   
   **3. External Service Integration:**
   - API client behavior
   - Retry and circuit breaker
   - Timeout handling
   - Error scenarios
   
   **4. Event-Driven Integration:**
   - Event publishing and handling
   - Saga workflow completion
   - Dead-letter queue handling
   - Idempotency verification
   
   **5. End-to-End Scenarios:**
   - Complete user workflows
   - Multi-service interactions
   - Data consistency verification
   
   **Best Practices:**
   - Use builder pattern for test data
   - Implement test fixtures for common setups
   - Clean up resources after tests
   - Use meaningful test names
   - Add integration test markers/categories
   
   Create Tests/Integration/ directory structure.
   Implement base test classes and helpers.
   Generate comprehensive test coverage.
   ```

1. Click the ![keep button](https://img.shields.io/badge/keep-blue) button.

### Step 10: Add Performance Benchmarks

1. Create performance benchmark tests:

   ```text
   Create performance benchmark tests using BenchmarkDotNet.
   
   Benchmarks to create:
   
   **1. API Performance:**
   - Baseline request/response time
   - Throughput (requests per second)
   - Concurrent request handling
   - Different payload sizes
   
   **2. Database Performance:**
   - Query execution time
   - Bulk insert performance
   - Complex query optimization
   - Connection pooling efficiency
   
   **3. Cache Performance:**
   - Cache get/set operations
   - Cache hit rate under load
   - Memory usage patterns
   - Serialization overhead
   
   **4. Serialization:**
   - JSON serialization/deserialization
   - Different payload sizes
   - System.Text.Json vs Newtonsoft.Json
   
   **5. Algorithm Performance:**
   - Core business logic methods
   - Data transformation pipelines
   - Filtering and sorting operations
   
   **Configuration:**
   - Multiple iterations for statistical significance
   - Memory diagnostics enabled
   - Export results to markdown/HTML
   - Set baseline for comparisons
   
   **Analysis:**
   - Identify performance bottlenecks
   - Memory allocation hotspots
   - GC pressure points
   - Optimization opportunities
   
   Create Benchmarks/ directory with all benchmark classes.
   Include README with instructions for running benchmarks.
   Add baseline results for comparison.
   ```

1. Click the ![keep button](https://img.shields.io/badge/keep-blue) button.

---

## Refactoring Complex Code

### Step 11: Analyze Code Quality

1. Use Copilot to analyze code quality:

   ```text
   Perform comprehensive code quality analysis of the entire codebase.
   
   Analyze for:
   
   **1. Code Smells:**
   - Long methods (>30 lines)
   - Large classes (>300 lines)
   - Duplicate code
   - Complex conditional logic
   - God objects / God classes
   - Feature envy
   - Inappropriate intimacy
   
   **2. SOLID Violations:**
   - Single Responsibility violations
   - Open/Closed violations
   - Liskov Substitution violations
   - Interface Segregation violations
   - Dependency Inversion violations
   
   **3. Design Issues:**
   - Tight coupling
   - Missing abstractions
   - Circular dependencies
   - Leaky abstractions
   - Premature optimization
   
   **4. Maintainability:**
   - Cyclomatic complexity (>10)
   - Cognitive complexity
   - Lack of unit tests
   - Missing documentation
   - Inconsistent naming
   
   **5. Performance Issues:**
   - N+1 query problems
   - Missing async/await
   - Inefficient LINQ queries
   - Memory leaks potential
   - Unnecessary allocations
   
   For each issue:
   - Severity (High/Medium/Low)
   - File and line number
   - Explanation of the problem
   - Refactoring recommendation
   - Estimated effort
   
   Generate report in docs/quality/code-quality-analysis.md.
   Create prioritized refactoring backlog.
   ```

1. Review the code quality report.

### Step 12: Refactor Critical Issues

1. Refactor the most critical code quality issues:

   ```text
   Refactor the top 5 critical code quality issues identified in the analysis.
   
   For each refactoring:
   
   **Before Refactoring:**
   - Ensure comprehensive test coverage exists
   - Document current behavior
   - Create baseline performance metrics if applicable
   
   **Refactoring Steps:**
   - Extract method/class where appropriate
   - Introduce abstractions and interfaces
   - Apply design patterns (Strategy, Factory, etc.)
   - Simplify complex conditionals
   - Remove duplication
   
   **After Refactoring:**
   - Verify all tests still pass
   - Add new tests if coverage decreased
   - Compare performance metrics
   - Update documentation
   - Code review checklist
   
   **Documentation:**
   - Explain what was changed and why
   - Document any behavior changes
   - Update architecture diagrams if needed
   
   Show me each refactoring one at a time:
   1. Issue description
   2. Before code
   3. Refactoring plan
   4. After code
   5. Test verification
   6. Performance impact
   
   Start with the highest priority issue.
   ```

1. Review and apply each refactoring.

1. Click the ![keep button](https://img.shields.io/badge/keep-blue) button after each refactoring.

---

## Advanced Prompting Techniques

### Step 13: Multi-Step Problem Solving

1. Practice breaking down complex problems:

   ```text
   I need to add a complex feature: [Choose one based on your scenario]
   
   Expense Tracker: "Implement predictive budget analytics using historical expense data to forecast future spending and alert users about potential budget overruns"
   
   Weather App: "Create a weather-based recommendation engine that suggests activities and clothing based on current and forecasted weather conditions"
   
   KYC Portal: "Build an ML-powered risk scoring system that analyzes documents and user behavior to automatically assign risk levels"
   
   360° Customer: "Implement an intelligent customer health score that aggregates data from multiple sources and predicts churn risk"
   
   IMPORTANT: Do NOT implement anything yet.
   
   Instead, provide:
   1. Feature breakdown into components
   2. Technical architecture proposal
   3. Required third-party libraries/services
   4. Database schema changes
   5. API design (endpoints, request/response)
   6. Implementation phases (what to build first)
   7. Testing strategy
   8. Performance considerations
   9. Security considerations
   10. Rollout plan
   
   Give me a comprehensive implementation plan first.
   Wait for my approval before implementing anything.
   ```

1. Review the implementation plan.

1. Approve specific phases to implement:

   ```text
   Implement Phase 1 of the plan you created.
   
   Follow TDD approach:
   1. Write failing tests first
   2. Implement minimum code to pass tests
   3. Refactor for quality
   
   Show me:
   - Tests written (RED phase)
   - Implementation (GREEN phase)
   - Refactoring improvements (REFACTOR phase)
   
   Include:
   - Comprehensive error handling
   - Logging and telemetry
   - Performance optimization
   - Security best practices
   
   Proceed with Phase 1 implementation.
   ```

1. Click the ![keep button](https://img.shields.io/badge/keep-blue) button.

---

## Verification and Review

### Step 14: Comprehensive Testing

1. Run all tests and verify implementation:

   ```text
   Run comprehensive test suite and generate quality report.
   
   Execute:
   1. All unit tests with coverage report
   2. All integration tests
   3. Performance benchmarks
   4. Security scans
   5. Code quality analysis
   
   Generate report including:
   - Test results summary (passed/failed/skipped)
   - Code coverage percentage (target: >80%)
   - Performance benchmark results
   - Security scan findings
   - Code quality metrics
   
   Identify any:
   - Failing tests (with root cause)
   - Coverage gaps (untested code)
   - Performance regressions
   - New security vulnerabilities
   - Code quality regressions
   
   Provide actionable recommendations for improvements.
   Generate report in docs/quality/test-report.md.
   ```

1. Review the comprehensive test report.

### Step 15: Final Code Review

1. Perform final code review:

   ```text
   Perform a final comprehensive code review of all changes made in this lab.
   
   Review checklist:
   
   **Code Quality:**
   - [ ] Follows project coding standards
   - [ ] Proper naming conventions
   - [ ] Appropriate comments and documentation
   - [ ] No code smells or anti-patterns
   - [ ] SOLID principles followed
   
   **Testing:**
   - [ ] Comprehensive unit test coverage
   - [ ] Integration tests for key scenarios
   - [ ] Performance benchmarks in place
   - [ ] All tests passing
   
   **Security:**
   - [ ] No security vulnerabilities
   - [ ] Input validation present
   - [ ] Proper error handling
   - [ ] Sensitive data protected
   
   **Performance:**
   - [ ] No obvious performance issues
   - [ ] Async/await used appropriately
   - [ ] Efficient database queries
   - [ ] Caching implemented where beneficial
   
   **Architecture:**
   - [ ] Clean architecture principles
   - [ ] Proper separation of concerns
   - [ ] Dependency injection used correctly
   - [ ] Event-driven patterns implemented correctly
   
   **Documentation:**
   - [ ] README updated
   - [ ] API documentation current
   - [ ] Architecture diagrams accurate
   - [ ] ADRs documented
   
   Provide:
   - Summary of review findings
   - List of any issues found
   - Recommendations for improvements
   - Overall quality assessment
   
   Generate final review report in docs/quality/final-review.md.
   ```

1. Review the final assessment.

---

## Best Practices for Advanced Copilot Usage

### Advanced Prompting Strategies

✅ **Effective Techniques:**

1. **Iterative Refinement**: Start broad, then refine with follow-up prompts
2. **Context Loading**: Provide relevant code context before asking for changes
3. **Constraint Setting**: Explicitly state requirements, patterns, and limitations
4. **Template Usage**: Create reusable prompt templates for common tasks
5. **Multi-Phase Approach**: Break complex tasks into logical phases
6. **Verification Loops**: Always ask Copilot to verify and test its output
7. **Documentation First**: Generate architecture docs before implementation
8. **Comparative Analysis**: Ask for multiple approaches before choosing one

### When to Use vs. Not Use Copilot

✅ **Use Copilot For:**
- Boilerplate code generation
- Test case generation
- Documentation creation
- Refactoring suggestions
- Code review and analysis
- Performance optimization ideas
- Security vulnerability scanning
- API client implementation

❌ **Don't Rely on Copilot For:**
- Business logic decisions
- Architecture decisions (use as assistant, not decision maker)
- Critical security implementations (always verify)
- Complex algorithms (verify correctness)
- Production secrets or credentials
- Final deployment decisions

### Advanced Workflow Tips

1. **Version Control Integration**: Commit before major Copilot-assisted changes
2. **Review Everything**: Never blindly accept generated code
3. **Test Immediately**: Run tests after each generation
4. **Document AI Assistance**: Note when Copilot helped in commit messages
5. **Learn from Outputs**: Study generated code to improve your skills
6. **Combine with Research**: Use Copilot + documentation together
7. **Pair Programming**: Use Copilot as a pairing partner, not a replacement

---

## Troubleshooting

### Issue: Copilot Generates Incorrect Code

**Solution:**

```text
The code you generated has [specific issue]. Let's fix it.

Requirements:
- [Describe what the code should actually do]
- [List specific constraints]
- [Mention any patterns to follow]

Please:
1. Analyze why the previous implementation was wrong
2. Propose a corrected solution
3. Explain the key differences
4. Add tests to prevent this issue
5. Show me the fixed code
```

### Issue: Performance Degradation

**Solution:**

```text
Analyze the performance impact of recent changes.

Compare:
- Benchmark results before changes
- Benchmark results after changes
- Identify performance regressions
- Explain root causes
- Propose optimizations

For each regression:
- Show the problematic code
- Explain why it's slower
- Provide optimized version
- Show performance improvement
- Verify correctness maintained
```

### Issue: Test Coverage Decreased

**Solution:**

```text
Code coverage has decreased from [X]% to [Y]%. Identify gaps and add tests.

Analyze:
- Which files/methods lost coverage
- Why coverage decreased
- What scenarios are untested

Then:
- Generate comprehensive tests for uncovered code
- Ensure edge cases are covered
- Add integration tests if needed
- Verify coverage improves to at least [X]%

Show me the coverage report and new tests.
```

---

## Next Steps

✅ **Lab 07 Complete!** You've mastered advanced GitHub Copilot techniques.

**What You've Accomplished:**

1. ✅ Built production-ready resilient API clients
2. ✅ Implemented intelligent caching and performance monitoring
3. ✅ Designed event-driven architecture
4. ✅ Performed AI-powered security and code quality analysis
5. ✅ Created comprehensive integration test suites
6. ✅ Refactored complex code with Copilot assistance

**Advanced Skills Acquired:**

- Advanced prompting strategies
- Multi-phase problem decomposition
- Architecture design with AI assistance
- Security-first development
- Performance optimization techniques
- Comprehensive testing approaches

**Continue Your Journey:**

1. **Apply to Real Projects**
   - Use these techniques in your daily work
   - Build a personal reference library of prompts
   - Share learnings with your team

2. **Explore More:**
   - Try GitHub Copilot Workspace
   - Explore additional MCP servers
   - Create custom Copilot extensions
   - Experiment with other AI coding tools

3. **Share Your Knowledge**
   - Write blog posts about your experience
   - Present to your team
   - Contribute to open source with Copilot
   - Mentor others learning Copilot

4. **Stay Updated**
   - Follow GitHub Copilot blog
   - Join AI-assisted development communities
   - Attend webinars and conferences
   - Experiment with new features

---

## Resources

### Advanced Topics

- [Polly Resilience Documentation](https://github.com/App-vNext/Polly)
- [BenchmarkDotNet Guide](https://benchmarkdotnet.org/)
- [Testcontainers for .NET](https://dotnet.testcontainers.org/)
- [MediatR for CQRS](https://github.com/jbogard/MediatR)
- [OpenTelemetry .NET](https://opentelemetry.io/docs/instrumentation/net/)

### Architecture Patterns

- [Clean Architecture by Uncle Bob](https://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html)
- [Event-Driven Architecture](https://learn.microsoft.com/en-us/azure/architecture/guide/architecture-styles/event-driven)
- [CQRS Pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/cqrs)
- [Saga Pattern](https://learn.microsoft.com/en-us/azure/architecture/reference-architectures/saga/saga)

### Security Resources

- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [.NET Security Best Practices](https://learn.microsoft.com/en-us/dotnet/standard/security/)
- [Secure Coding Guidelines](https://github.com/OWASP/CheatSheetSeries)

---

**Congratulations on completing the Advanced Copilot Techniques lab! 🚀**

You're now equipped with professional-grade skills for leveraging AI in software development. Keep practicing, stay curious, and continue pushing the boundaries of what's possible with AI-assisted development!

---

**Workshop Feedback:**

Please share your experience with this advanced lab:
- Which techniques were most valuable?
- What challenges did you face?
- What would you like to learn next?

[Create a GitHub Issue](https://github.com/yourusername/CopilotWorkshop/issues) with your feedback!
