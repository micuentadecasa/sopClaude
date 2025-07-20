# Design Error Handling Prompt

Create comprehensive error handling procedures for the agent based on the workflows and scenarios.

## Error Handling Procedures

### Error Classification

#### Level 1: Recoverable Errors
Errors the agent can handle autonomously:

**Error Type**: Input Validation Failure
- **Description**: User input doesn't meet requirements
- **Detection**: Validation rules in Step 1
- **Handling Procedure**:
  1. Log validation failure details
  2. Generate user-friendly error message
  3. Provide specific guidance on correct format
  4. Suggest examples
  5. Allow retry
- **Max Retries**: 3
- **Fallback**: Escalate to human after max retries

**Error Type**: Temporary External Service Failure
- **Description**: API timeout or temporary unavailability
- **Detection**: HTTP timeout or 5xx errors
- **Handling Procedure**:
  1. Log service failure
  2. Wait [exponential backoff]
  3. Retry request
  4. Use cached data if available
  5. Inform user of delay
- **Max Retries**: 5 with exponential backoff
- **Fallback**: Provide degraded service or queue for later

#### Level 2: Partial Failure Errors
Errors requiring degraded operation:

**Error Type**: Partial Data Availability
- **Description**: Some required data sources unavailable
- **Handling Procedure**:
  1. Identify available data sources
  2. Assess if minimum viable response possible
  3. Generate response with caveats
  4. Clearly mark degraded response
  5. Queue for full processing when available

#### Level 3: Critical Errors
Errors requiring immediate escalation:

**Error Type**: Security Violation
- **Description**: Detected security threat or policy violation
- **Handling Procedure**:
  1. Immediately halt processing
  2. Log full context with security marker
  3. Notify security team
  4. Respond with generic security message
  5. Block further requests from source

### Error Response Templates

#### User-Facing Error Messages

**Template 1: Validation Error**
```
I couldn't process your request because [specific issue].

What you provided: [user input excerpt]
What I need: [requirement]
Example: [valid example]

Please try again with the correct format.
```

**Template 2: Service Unavailable**
```
I'm having trouble accessing [service name] right now.

I'm actively retrying and will process your request as soon as possible.
Expected resolution time: [estimate]

You can:
- Wait for automatic retry
- Try again in [X] minutes
- Contact support if urgent
```

### Error Recovery Procedures

#### Automatic Recovery
Steps for self-healing:

1. **State Recovery**
   - Save state before risky operations
   - Implement checkpoint system
   - Restore from last good state

2. **Data Recovery**
   - Validate data integrity
   - Use backup sources
   - Reconstruct from logs if needed

#### Manual Recovery Procedures
For errors requiring human intervention:

1. **Error Queue Management**
   - Queue failed requests
   - Prioritize by impact/urgency
   - Provide admin interface

2. **Bulk Error Resolution**
   - Identify patterns in errors
   - Apply fixes in batches
   - Reprocess queued items

### Error Prevention Strategies

#### Proactive Validation
- Pre-validate inputs before processing
- Check system health before operations
- Verify external service availability

#### Circuit Breaker Pattern
- Monitor failure rates
- Temporarily disable failing services
- Provide fallback options
- Auto-recover when healthy

### Error Monitoring and Alerting

#### Metrics to Track
- Error rate by type
- Recovery success rate
- Mean time to recovery
- User impact metrics

#### Alert Thresholds
- Level 1: > 5% error rate
- Level 2: > 10% error rate or critical error
- Level 3: Security or data integrity issue

Create comprehensive error handling that ensures graceful degradation and clear communication.