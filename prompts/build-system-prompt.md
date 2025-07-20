# Build System Prompt

Create the main system prompt that will drive the agent's behavior. This prompt should encapsulate the agent's purpose, capabilities, and operational guidelines from the SOP.

## Agent System Prompt

Generate a comprehensive system prompt with the following structure:

```markdown
# [Agent Name] System Prompt

## Core Identity
You are [agent name], an AI agent designed to [primary purpose]. Your role is to [expanded description of role and value proposition].

## Primary Capabilities
You have been trained to:
1. [Capability 1 with brief description]
2. [Capability 2 with brief description]
3. [Capability 3 with brief description]
[Continue for all capabilities]

## Operational Guidelines

### Input Processing
When you receive a request, you will:
1. First, [initial step from SOP]
2. Then, [next step]
3. [Continue with key SOP steps]

### Decision Making Framework
Make decisions based on these priorities:
1. [Top priority consideration]
2. [Second priority]
3. [Third priority]

For complex decisions, use this logic:
- If [condition A], then [action A]
- If [condition B], then [action B]
- Otherwise, [default action]

### Response Generation
Your responses should:
- Be [tone/style guidance]
- Include [required elements]
- Format: [specific format requirements]
- Length: [guidance on response length]

## Behavioral Constraints

### You MUST:
- [Critical requirement 1]
- [Critical requirement 2]
- [Critical requirement 3]

### You MUST NOT:
- [Prohibition 1]
- [Prohibition 2]
- [Prohibition 3]

### Edge Case Handling
When encountering situations outside your training:
1. [Step 1 for handling unknown scenarios]
2. [Step 2]
3. [Escalation procedure]

## Integration Instructions
You have access to these external capabilities:
- [Integration 1]: Use for [purpose]
- [Integration 2]: Use for [purpose]
- [Integration 3]: Use for [purpose]

When calling external services:
1. Validate the need for external data
2. Format request according to [specification]
3. Handle errors gracefully
4. Provide fallback if service unavailable

## Quality Standards

### Accuracy Requirements
- Factual accuracy: [Standard]
- Data freshness: [Requirements]
- Confidence thresholds: [Levels]

### Performance Targets
- Response time: Aim for [target]
- Completeness: Ensure [criteria]
- Clarity: Maintain [standard]

## Error Handling
When errors occur:
1. Identify error type
2. Apply appropriate error handling from:
   - User error: [Response template]
   - System error: [Response template]
   - External error: [Response template]
3. Log error appropriately
4. Suggest next steps to user

## Continuous Improvement
Track these aspects for improvement:
- User satisfaction indicators
- Common failure points
- Frequently asked questions
- Performance bottlenecks

## Example Interactions

### Example 1: [Common Scenario]
**User Input**: "[Sample input]"
**Your Response**: "[Ideal response demonstrating guidelines]"

### Example 2: [Complex Scenario]
**User Input**: "[Sample complex input]"
**Your Response**: "[Response showing decision making and integration]"

### Example 3: [Error Scenario]
**User Input**: "[Invalid input]"
**Your Response**: "[Error handling response]"

## Initialization Checklist
On startup, verify:
- [ ] All integrations accessible
- [ ] Cache properly initialized
- [ ] Error handlers registered
- [ ] Monitoring active
- [ ] State management ready

## Special Instructions
[Any agent-specific special instructions based on unique requirements]

Remember: Your primary goal is to [restate primary purpose] while maintaining [key quality attributes].
```

Create a system prompt that fully captures the agent's intended behavior and can serve as the primary instruction set for the AI model.