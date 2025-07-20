# Design Integrations Prompt

Based on the agent scope and workflows, create detailed integration specifications for all external systems the agent needs to interact with.

## Integration Specifications

### Integration Overview

**Total Integrations Required**: [Number]
**Critical Integrations**: [List most important]
**Optional Integrations**: [Nice-to-have list]

### Integration Details

For each integration, provide:

## Integration 1: [System Name]

### Overview
- **Purpose**: Why this integration is needed
- **Type**: API / Database / File System / Message Queue / etc.
- **Criticality**: Critical / Important / Optional
- **Vendor**: [Provider name]

### Technical Specifications

#### Connection Details
- **Protocol**: REST API / GraphQL / SOAP / gRPC / etc.
- **Authentication**: OAuth2 / API Key / JWT / Basic Auth
- **Base URL**: [Production URL]
- **Rate Limits**: [Requests per minute/hour]
- **Timeout**: [Recommended timeout in seconds]

#### API Endpoints Required

**Endpoint 1**: [GET/POST/etc] /path/to/endpoint
- **Purpose**: [What this does]
- **Request Format**:
  ```json
  {
    "field1": "type",
    "field2": "type"
  }
  ```
- **Response Format**:
  ```json
  {
    "result": "type",
    "data": []
  }
  ```
- **Error Codes**: [List common errors]

**Endpoint 2**: [Continue for all endpoints...]

### Data Mapping

#### Inbound Data Transformation
```
External Field → Agent Field
system.userId → user.id
system.emailAddr → user.email
```

#### Outbound Data Transformation
```
Agent Field → External Field
response.content → api.message_body
response.priority → api.urgency_level
```

### Integration Workflow

1. **Pre-Integration Checks**
   - Verify credentials valid
   - Check service health
   - Validate input data

2. **Integration Steps**
   - Step 1: [Authenticate]
   - Step 2: [Prepare request]
   - Step 3: [Send request]
   - Step 4: [Process response]
   - Step 5: [Transform data]

3. **Post-Integration Actions**
   - Log transaction
   - Update cache
   - Trigger next workflow

### Error Handling

**Common Errors and Mitigations**:
- **401 Unauthorized**: Refresh token and retry
- **429 Rate Limited**: Implement backoff, use queue
- **500 Server Error**: Retry with exponential backoff
- **Timeout**: Increase timeout, implement async pattern

### Performance Optimization

#### Caching Strategy
- **What to Cache**: [List cacheable data]
- **Cache TTL**: [Time-to-live for each type]
- **Cache Invalidation**: [When to refresh]

#### Batch Operations
- **Batchable Operations**: [List what can be batched]
- **Batch Size**: [Optimal batch size]
- **Batch Timing**: [When to trigger batches]

### Security Considerations

#### Data Security
- **Sensitive Fields**: [List fields to encrypt/mask]
- **Data Retention**: [How long to store]
- **Audit Requirements**: [What to log]

#### Access Control
- **Permissions Required**: [List permissions]
- **Scope Limitations**: [What agent cannot access]

### Testing Requirements

#### Integration Tests
- Test successful connection
- Test error scenarios
- Test rate limiting
- Test data transformation
- Test timeout handling

#### Mock Data
Provide sample data for testing:
```json
{
  "test_scenario_1": { ... },
  "test_scenario_2": { ... }
}
```

### Monitoring and Alerts

#### Key Metrics
- Success rate
- Average response time
- Error rate by type
- Data volume processed

#### Alert Conditions
- Connection failures > 3 in 5 minutes
- Response time > 5 seconds
- Error rate > 10%

## Integration Priority Matrix

| Integration | Priority | Complexity | Implementation Order |
|-------------|----------|------------|---------------------|
| System A    | Critical | Low        | 1                   |
| System B    | Critical | High       | 2                   |
| System C    | Important| Medium     | 3                   |

Create comprehensive integration specifications that developers can use to implement robust connections.