# GitHub Copilot in VS Code Demo Plan

## Overview

This demo plan showcases GitHub Copilot's advanced capabilities in Visual Studio Code using a .NET 9 Blazor WeatherApp with .NET Aspire. The scenarios progress from basic features to advanced AI-powered development workflows.

## Demo Flow (45-60 minutes)

### 1. Copilot Instructions File (5-7 minutes)

**Scenario**: Set up project-specific AI behavior and coding standards

#### What to Show:

- Create `.copilot-instructions.md` file in the workspace root
- Configure project-specific coding guidelines for the WeatherApp
- Demonstrate how Copilot follows these instructions consistently

#### Demo Steps:

1. Create `.copilot-instructions.md` with WeatherApp-specific rules
2. Show Copilot suggesting code that follows the defined patterns
3. Compare code generation before/after instructions

#### Key Points:

- Customizes Copilot behavior per project
- Enforces team coding standards
- Works across all Copilot features (chat, inline, etc.)

---

### 2. Mermaid Diagrams for Architecture Visualization (7-10 minutes)

**Scenario**: Document and visualize the WeatherApp architecture

#### What to Show:

- Generate Mermaid diagrams for system architecture
- Create flow diagrams for data flow
- Visualize component relationships in Blazor app

#### Demo Steps:

1. Ask Copilot to analyze the WeatherApp structure
2. Generate Mermaid diagrams for:
   - Overall system architecture (.NET Aspire)
   - Component hierarchy (Blazor components)
   - Data flow for weather forecast retrieval
3. Show live preview of diagrams in VS Code

#### Key Points:

- AI-powered architecture documentation
- Visual understanding of complex systems
- Automatic diagram generation from code analysis

---

### 3. Weather API Integration with Emojis and Testing (12-15 minutes)

**Scenario**: Enhance the weather app with real API integration, emoji visualization, and comprehensive testing

#### What to Show:

- Replace mock data with real weather API (OpenWeatherMap)
- Add weather condition emojis
- Generate unit and integration tests
- Implement error handling and resilience patterns

#### Demo Steps:

1. **API Integration**:

   - Add weather service with HTTP client
   - Configure API key management
   - Replace mock data in Weather.razor

2. **Emoji Enhancement**:

   - Create weather condition to emoji mapping
   - Add visual weather indicators

3. **Testing Suite**:
   - Generate unit tests for weather service
   - Create integration tests for weather component
   - Add test data and mocking strategies

#### Key Points:

- Real-world API integration patterns
- User experience enhancements
- Test-driven development with AI assistance
- Production-ready error handling

---

### 4. Azure Application Insights + Bug Fixing with Telemetry (10-12 minutes)

**Scenario**: Add observability and use telemetry data to identify and fix issues

#### What to Show:

- Integrate Azure Application Insights
- Generate telemetry and logging
- Use GitHub MCP server to create issues from telemetry
- AI-powered bug diagnosis and fixes

#### Demo Steps:

1. **Add Application Insights**:

   - Configure Application Insights in the app
   - Add custom telemetry and logging
   - Deploy to Azure (or simulate locally)

2. **Simulate and Detect Issues**:

   - Introduce a performance issue or bug
   - Show telemetry data collection
   - Use Copilot to analyze telemetry patterns

3. **GitHub Integration**:
   - Use GitHub MCP server to create issues from telemetry
   - Generate bug reports with context
   - AI-assisted debugging and resolution

#### Key Points:

- Production monitoring and observability
- Data-driven development decisions
- Automated issue creation and tracking
- AI-powered root cause analysis

---

### 5. Documentation Generation (5-7 minutes)

**Scenario**: Generate comprehensive project documentation

#### What to Show:

- API documentation generation
- README.md creation and updates
- Code comments and XML documentation
- Architecture decision records (ADRs)

#### Demo Steps:

1. Generate API documentation for weather services
2. Create/update comprehensive README.md
3. Add XML documentation comments to key methods
4. Generate architecture decision records

#### Key Points:

- Automated documentation maintenance
- Consistent documentation standards
- Living documentation that stays current

---

### 6. GitHub Issues to Implementation Workflow (8-10 minutes)

**Scenario**: Complete development workflow from issue creation to implementation

#### What to Show:

- Create GitHub issues using MCP server
- AI-powered feature implementation
- Code review and pull request generation
- Issue tracking and closure

#### Demo Steps:

1. **Issue Creation**:

   - Use GitHub MCP server to create feature requests
   - Generate user stories with acceptance criteria
   - Prioritize and label issues

2. **Implementation**:

   - Select an issue to implement
   - Use Copilot to generate feature code
   - Follow best practices and coding standards

3. **Code Review Flow**:
   - Generate pull request descriptions
   - AI-assisted code review comments
   - Automated testing and validation

#### Key Points:

- End-to-end development workflow
- AI-powered project management
- Seamless integration between planning and coding
- Quality assurance through AI assistance

---

## Demo Environment Setup

### Prerequisites:

- VS Code with GitHub Copilot extension
- .NET 9 SDK
- Azure subscription (for Application Insights demo)
- GitHub repository access
- OpenWeatherMap API key

### Preparation Checklist:

- [ ] Verify WeatherApp builds and runs
- [ ] Set up Azure Application Insights resource
- [ ] Obtain OpenWeatherMap API key
- [ ] Configure GitHub MCP server
- [ ] Prepare sample issues and scenarios
- [ ] Test all demo scenarios in advance

---

## Key Talking Points

### For Technical Audience:

- Productivity gains in real development scenarios
- Code quality improvements through AI assistance
- Integration with existing development workflows
- Scalability of AI-powered development practices

### For Business Audience:

- Faster time-to-market for features
- Reduced development costs
- Improved code quality and maintainability
- Enhanced developer experience and satisfaction

---

## Backup Scenarios

If any primary demo fails, these alternatives showcase similar capabilities:

1. **Simple Refactoring**: Show Copilot refactoring the existing weather component
2. **Code Explanation**: Have Copilot explain complex parts of the .NET Aspire setup
3. **Performance Optimization**: Ask Copilot to optimize the weather data loading
4. **Security Review**: Use Copilot to review code for security best practices

---

## Success Metrics

- Demonstrate measurable productivity improvements
- Show code quality enhancements
- Highlight seamless workflow integration
- Prove practical applicability to real projects

---

## Next Steps for Attendees

- Install GitHub Copilot in their environment
- Set up .copilot-instructions.md in their projects
- Explore GitHub MCP server integration
- Implement observability in their applications
- Adopt AI-powered documentation practices
