# Develop a 360° Customer View Portal for Gambling Company Operations

## 1. Problem Description

Build a **360° Customer View Dashboard** for a gambling company's operations team to access comprehensive customer information in one unified interface. The system aggregates data from multiple sources to provide a complete view of customer activity, compliance status, responsible gambling indicators, and financial transactions.

### Core Requirements:
- **Frontend**: Comprehensive dashboard with multiple data widgets and real-time updates
- **Backend**: RESTful API (.NET Core, Python Flask, or Node.js Express) for data aggregation
- **Data Aggregation**: Combine data from multiple microservices/databases
- **Real-Time Updates**: Live data for active gaming sessions and transactions
- **Customer Profile**: Demographics, verification status, account details
- **Gaming Activity**: Betting history, favorite games, win/loss statistics
- **Financial Overview**: Deposits, withdrawals, bonuses, current balance
- **Compliance & Risk**: KYC status, responsible gambling flags, suspicious activity alerts
- **Support History**: Customer service interactions and resolution status

### User Stories:
1. As an operations agent, I can search for a customer by ID, email, or username
2. As an operations agent, I can view customer's complete profile and account status
3. As an operations agent, I can see all recent gaming activity and betting patterns
4. As an operations agent, I can view financial transaction history and balance
5. As an operations agent, I can check KYC verification status and documents
6. As an operations agent, I can see responsible gambling indicators and limits
7. As an operations agent, I can view customer support ticket history
8. As a compliance officer, I can see risk flags and suspicious activity alerts
9. As a VIP manager, I can view high-value customer analytics and lifetime value
10. As an operations agent, I can see real-time active sessions and current bets

## 2. Hints

### Technical Implementation Hints:
- **Data Sources to Aggregate**:
  - Customer Service (profile, demographics, contact info)
  - Gaming Service (bets, game history, preferences)
  - Wallet Service (deposits, withdrawals, balance, bonuses)
  - KYC Service (verification status, documents, compliance)
  - Support Service (tickets, chats, resolutions)
  - Risk Service (fraud alerts, responsible gambling flags)
  
- **Dashboard Sections**:
  1. **Customer Header**: Photo, name, ID, status badges, quick actions
  2. **Account Overview**: Registration date, verification status, account tier
  3. **Current Activity**: Active sessions, ongoing bets, recent logins
  4. **Gaming Statistics**: Favorite games, total bets, win/loss ratio, RTP
  5. **Financial Summary**: Balance, lifetime deposits/withdrawals, bonus status
  6. **Compliance Panel**: KYC status, responsible gambling limits, cooling-off periods
  7. **Risk Indicators**: Fraud alerts, unusual patterns, self-exclusion status
  8. **Support Timeline**: Ticket history, chat logs, resolution status
  9. **Documents**: Uploaded KYC documents, statements, correspondence

- **Real-Time Features**:
  - WebSocket or Server-Sent Events for live updates
  - Current active gaming sessions
  - Real-time balance changes
  - Live bet placement notifications
  - Instant fraud alerts

- **Data Aggregation Strategy**:
  - Backend aggregator service calls multiple APIs
  - Cache customer data for performance (5-10 minute TTL)
  - Parallel API calls for faster loading
  - Fallback to cached data if service unavailable

### Quick Start Tips:
- Start with customer search and basic profile display
- Mock multiple microservices as separate endpoints
- Build one dashboard section at a time
- Use mock data for different customer types (VIP, flagged, new, etc.)
- Implement caching early to reduce redundant API calls
- Create reusable dashboard widgets/components
- Use charts library (Chart.js, Recharts) for gaming statistics
- Implement role-based access (operations vs. compliance vs. VIP manager)

### Sample Data Structure:

```typescript
// Aggregated Customer 360 View
{
  // Basic Info
  customerId: "CUS-123456",
  username: "john_player_77",
  email: "john@example.com",
  phone: "+1-555-0123",
  fullName: "John Smith",
  dateOfBirth: "1985-06-15",
  registrationDate: "2023-01-10",
  
  // Account Status
  accountStatus: "active" | "suspended" | "self_excluded" | "closed",
  verificationType: "basic" | "intermediate" | "enhanced",
  kycStatus: "verified" | "pending" | "rejected",
  vipTier: "bronze" | "silver" | "gold" | "platinum",
  
  // Gaming Activity
  gamingStats: {
    totalBets: 1547,
    totalWagered: 45230.50,
    totalWon: 42180.25,
    netPosition: -3050.25,
    favoriteGame: "Blackjack",
    lastGamePlayed: "2025-10-06T14:23:00Z",
    averageBetSize: 29.25,
    sessionCount: 312
  },
  
  // Financial Overview
  financial: {
    currentBalance: 1250.75,
    totalDeposits: 15000.00,
    totalWithdrawals: 12500.00,
    activeBonus: 50.00,
    lifetimeValue: 2500.00,
    lastDeposit: {
      amount: 500.00,
      method: "Credit Card",
      date: "2025-10-05T10:30:00Z"
    },
    pendingWithdrawals: []
  },
  
  // Compliance & Risk
  compliance: {
    kycVerified: true,
    proofOfAddressVerified: true,
    sourceOfFundsVerified: false,
    responsibleGamblingLimits: {
      dailyDepositLimit: 500,
      weeklyLossLimit: 1000,
      sessionTimeLimit: 120 // minutes
    },
    selfExclusionStatus: null,
    coolingOffPeriod: null
  },
  
  // Risk Flags
  riskFlags: [
    {
      type: "unusual_betting_pattern",
      severity: "medium",
      description: "Sudden increase in bet size",
      detectedAt: "2025-10-06T12:00:00Z"
    }
  ],
  
  // Support History
  supportHistory: [
    {
      ticketId: "TKT-9876",
      subject: "Withdrawal issue",
      status: "resolved",
      priority: "high",
      createdAt: "2025-10-04T09:15:00Z",
      resolvedAt: "2025-10-04T15:30:00Z"
    }
  ],
  
  // Active Sessions
  activeSessions: [
    {
      sessionId: "SES-456789",
      game: "Roulette",
      startedAt: "2025-10-06T14:00:00Z",
      currentBet: 25.00,
      sessionBalance: 150.00
    }
  ]
}
```

### Agent Mode Note:
If you are using the Agent mode and notice that the agent is working in the wrong directory, try to add the following line to your prompt:
```markdown
Work in the directory backend. When run terminal remember to change the right directory, for example: `cd challenges/360customer/backend && <command>`.
```
Change the directory to `frontend` when working on the frontend part.

## 3. Time Needed

**Estimated Duration: 90-120 minutes**

### Time Breakdown:
- **Setup & Planning** (15-20 minutes): Project structure, mock services design, dependencies
- **Backend Aggregation** (30-40 minutes):
  - Customer search endpoint
  - Data aggregation from multiple sources
  - Caching layer
  - Real-time data endpoints
- **Frontend Dashboard** (40-50 minutes):
  - Customer search interface
  - Dashboard layout with multiple widgets
  - Gaming statistics with charts
  - Financial overview
  - Compliance and risk panels
  - Support history timeline
- **Real-Time Features** (15-20 minutes):
  - WebSocket/SSE setup
  - Live session updates
  - Real-time balance changes

## 4. Extra Features (Bonus Challenges)

Quick additions for teams that finish early:

### Easy Additions (10-15 minutes each):
- **Export Customer Report**: Download PDF/CSV of customer data
- **Quick Actions**: Suspend account, reset password, send email
- **Customer Tags**: Add custom tags for categorization
- **Bookmark Customers**: Save frequently accessed customers
- **Activity Timeline**: Visual timeline of all customer events

### Medium Additions (15-25 minutes each):
- **Advanced Search**: Filter by VIP tier, registration date, status
- **Customer Comparison**: Compare metrics across multiple customers
- **Responsible Gambling Tools**: Set limits, trigger cooling-off periods
- **Document Viewer**: View KYC documents inline
- **Support Chat**: Initiate live chat with customer
- **Transaction Drill-Down**: Detailed view of specific transactions
- **Game Session Replay**: View historical game sessions

### Advanced Additions (25-40 minutes each):
- **Predictive Analytics**: Churn prediction, lifetime value forecasting
- **Fraud Detection Dashboard**: ML-based fraud probability scores
- **Cohort Analysis**: Compare customer segments and behaviors
- **Real-Time Notifications**: Push notifications for critical events
- **Audit Trail**: Complete history of who accessed customer data
- **Multi-Currency Support**: Handle international customers
- **Integration with CRM**: Sync with Salesforce or similar
- **Mobile App**: Responsive mobile version for field agents

### Why Perfect for Advanced Challenge:
- **Data Aggregation**: Learn to combine data from multiple sources
- **Complex UI**: Build sophisticated dashboard with many components
- **Real-Time Features**: Implement WebSocket or SSE for live data
- **Business Intelligence**: Visualize complex business metrics
- **Security & Compliance**: Handle sensitive customer data properly
- **Performance**: Optimize for large datasets and multiple API calls
- **Real-World Scenario**: Mirrors actual enterprise dashboards

### Success Criteria:
- ✅ Can search and retrieve customer by ID/email/username
- ✅ Dashboard displays all major customer data sections
- ✅ Gaming statistics show accurate calculations and charts
- ✅ Financial data aggregates correctly from multiple sources
- ✅ Compliance status and risk flags are clearly visible
- ✅ Real-time updates work for active sessions
- ✅ Support history displays chronologically
- ✅ Dashboard is responsive and performs well
- ✅ Caching reduces redundant API calls
- ✅ Error handling for failed data sources

### Testing Checklist:
- ✅ Search with valid customer ID
- ✅ Search with invalid/non-existent customer
- ✅ Test with VIP customer (high volume data)
- ✅ Test with flagged customer (risk alerts)
- ✅ Test with new customer (minimal data)
- ✅ Test with self-excluded customer
- ✅ Verify all dashboard sections load
- ✅ Test real-time updates (simulate active session)
- ✅ Verify financial calculations are accurate
- ✅ Test with one microservice down (fallback behavior)
- ✅ Test caching (should not call APIs repeatedly)
- ✅ Test on mobile viewport
- ✅ Verify role-based access (operations vs. compliance views)

### Performance Considerations:
- **Parallel API Calls**: Fetch data from multiple services simultaneously
- **Caching**: Cache aggregated customer data (5-10 minute TTL)
- **Lazy Loading**: Load sections on-demand rather than all at once
- **Pagination**: Paginate long lists (transactions, game history)
- **Debouncing**: Debounce search inputs to reduce API calls
- **CDN**: Serve static assets from CDN
- **Database Indexing**: Index customer ID, email, username fields

This challenge combines data aggregation, real-time features, complex business logic, and sophisticated UI design - perfect for learning enterprise-level dashboard development with performance optimization and compliance considerations!

## 5. Additional Resources

### Gambling Industry Compliance:
- [UK Gambling Commission Guidelines](https://www.gamblingcommission.gov.uk/)
- [Responsible Gambling Best Practices](https://www.begambleaware.org/)

### Real-Time Technologies:
- [WebSocket API](https://developer.mozilla.org/en-US/docs/Web/API/WebSocket)
- [Server-Sent Events](https://developer.mozilla.org/en-US/docs/Web/API/Server-sent_events)
- [Socket.io](https://socket.io/)

### Data Visualization:
- [Chart.js](https://www.chartjs.org/)
- [Recharts](https://recharts.org/)
- [D3.js](https://d3js.org/)

### Dashboard UI Frameworks:
- [Ant Design](https://ant.design/)
- [Material-UI](https://mui.com/)
- [Tailwind CSS](https://tailwindcss.com/)
