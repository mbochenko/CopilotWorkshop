# Sample GitHub Issues for Copilot Demo

This file contains sample GitHub issues that can be created during the demo to showcase the GitHub MCP server integration with Copilot.

## Issue 1: Weather API Integration

**Title**: Integrate real weather API to replace mock data

**Labels**: enhancement, api-integration, high-priority

**Description**:
As a user, I want to see real weather data instead of mock data so that I can get accurate weather forecasts.

**Acceptance Criteria**:

- [ ] Replace mock weather data in Weather.razor with real API calls
- [ ] Integrate with OpenWeatherMap API
- [ ] Add proper error handling for API failures
- [ ] Implement caching to reduce API calls
- [ ] Add loading states during API calls
- [ ] Support both current weather and 5-day forecast
- [ ] Include weather condition icons/emojis

**Technical Requirements**:

- Use HttpClientFactory for API calls
- Implement retry policies with Polly
- Add structured logging for API interactions
- Store API key in user secrets for development
- Add unit tests for weather service

---

## Issue 2: Add Weather Emojis and Visual Enhancements

**Title**: Enhance weather display with emojis and improved UI

**Labels**: enhancement, ui-ux, good-first-issue

**Description**:
As a user, I want to see weather conditions represented with emojis and improved visual design so that the information is more engaging and easy to understand.

**Acceptance Criteria**:

- [ ] Add weather condition emojis (☀️ ⛅ 🌧️ ❄️ ⛈️ etc.)
- [ ] Create emoji mapping for different weather conditions
- [ ] Improve the weather table design
- [ ] Add temperature color coding (cold=blue, hot=red)
- [ ] Include weather icons alongside emojis
- [ ] Make the layout mobile-responsive
- [ ] Add animation for weather data updates

**Design Requirements**:

- Use consistent emoji style
- Ensure accessibility with alt text
- Follow material design principles
- Test on different screen sizes

---

## Issue 3: Implement Application Insights Telemetry

**Title**: Add comprehensive telemetry and monitoring

**Labels**: enhancement, observability, production-ready

**Description**:
As a developer, I want comprehensive telemetry and monitoring so that I can understand application performance and quickly identify issues.

**Acceptance Criteria**:

- [ ] Integrate Azure Application Insights
- [ ] Add custom telemetry for weather API calls
- [ ] Implement performance tracking
- [ ] Add dependency tracking for external services
- [ ] Create custom dashboards for key metrics
- [ ] Set up alerting for critical issues
- [ ] Add correlation IDs for request tracing

**Telemetry Requirements**:

- Track API response times
- Monitor cache hit/miss ratios
- Log user interactions
- Track error rates and exceptions
- Monitor resource usage

---

## Issue 4: Add Comprehensive Unit Tests

**Title**: Implement comprehensive unit and integration tests

**Labels**: testing, technical-debt, high-priority

**Description**:
As a developer, I want comprehensive test coverage so that I can confidently make changes and catch regressions early.

**Acceptance Criteria**:

- [ ] Add unit tests for weather service
- [ ] Create integration tests for weather API
- [ ] Test Blazor components with bUnit
- [ ] Add tests for error scenarios
- [ ] Implement test data builders
- [ ] Achieve >80% code coverage
- [ ] Add performance tests

**Testing Strategy**:

- Use xUnit for unit tests
- Mock external dependencies
- Test happy path and edge cases
- Include parameterized tests
- Set up CI/CD test pipeline

---

## Issue 5: Performance Bug - Slow Weather Loading

**Title**: Weather data loading is too slow on initial page load

**Labels**: bug, performance, user-experience

**Description**:
Users are experiencing slow loading times when accessing the weather page for the first time. The loading spinner shows for 3-5 seconds before data appears.

**Current Behavior**:

- Weather page takes 3-5 seconds to load
- No indication of progress during loading
- Users may think the page is broken

**Expected Behavior**:

- Weather data should load within 1-2 seconds
- Show progressive loading indicators
- Display cached data immediately when available

**Investigation Steps**:

- [ ] Profile the weather service performance
- [ ] Check API response times
- [ ] Analyze caching effectiveness
- [ ] Review database query performance
- [ ] Test with Application Insights data

**Potential Solutions**:

- Implement background data refresh
- Add predictive caching
- Optimize API calls
- Use streaming rendering
- Add progressive enhancement

---

## Issue 6: Add Location-Based Weather

**Title**: Implement geolocation-based weather forecasts

**Labels**: enhancement, feature-request, geolocation

**Description**:
As a user, I want to see weather for my current location automatically so that I don't have to manually enter location information.

**Acceptance Criteria**:

- [ ] Request user's geolocation permission
- [ ] Get weather for current coordinates
- [ ] Add manual location input as fallback
- [ ] Support location search by city name
- [ ] Remember user's preferred locations
- [ ] Add multiple location support
- [ ] Show location name with weather data

**Technical Considerations**:

- Handle geolocation permission denials
- Add graceful fallbacks
- Implement location caching
- Support offline scenarios
- Add privacy considerations

---

## Issue 7: Create Weather Alerts System

**Title**: Implement weather alerts and notifications

**Labels**: enhancement, notifications, advanced-feature

**Description**:
As a user, I want to receive notifications about severe weather conditions so that I can take appropriate precautions.

**Acceptance Criteria**:

- [ ] Integrate weather alerts API
- [ ] Display active weather warnings
- [ ] Add push notification support
- [ ] Allow users to customize alert types
- [ ] Show alert history
- [ ] Add alert severity levels
- [ ] Implement alert dismissal

**Alert Types**:

- Severe weather warnings
- Temperature extremes
- Precipitation alerts
- Wind speed warnings
- Air quality notifications

---

## Usage Instructions for Demo

1. **Create Issues**: Use GitHub MCP server to create these issues in the repository
2. **AI Analysis**: Ask Copilot to analyze and prioritize the issues
3. **Implementation**: Select an issue and have Copilot implement the solution
4. **Code Review**: Use Copilot to review the implementation
5. **Testing**: Generate tests for the implemented features
6. **Documentation**: Update documentation based on the changes

## Demo Script Example

```
# Create an issue using GitHub MCP server
"Create a GitHub issue for implementing weather emojis in the WeatherApp"

# Analyze the issue
"Analyze issue #2 and create an implementation plan"

# Implement the feature
"Implement the weather emoji feature from issue #2"

# Generate tests
"Create unit tests for the weather emoji functionality"

# Update documentation
"Update the README with information about the new emoji feature"

# Create pull request
"Create a pull request for the weather emoji implementation"
```
