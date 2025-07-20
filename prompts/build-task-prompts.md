# Build Task Prompts

Based on the SOP workflows and decision trees, create specific task prompts for each major operation the agent needs to perform.

## Task-Specific Prompts Generation

Analyze the workflows and create individual prompts for each distinct task type:

### Task Prompt Structure Template

For each task, generate a prompt following this structure:

```markdown
# Task: [Task Name]

## Task Context
This prompt is activated when: [Trigger conditions]
Expected input format: [Format specification]
Expected output format: [Format specification]

## Task Instructions

### Step-by-Step Process
1. [Detailed step 1]
2. [Detailed step 2]
3. [Continue with all steps]

### Decision Points
At [decision point]:
- If [condition A]: [Specific action]
- If [condition B]: [Specific action]
- Otherwise: [Default action]

### Required Validations
Before proceeding, ensure:
- [ ] [Validation 1]
- [ ] [Validation 2]
- [ ] [Validation 3]

### Output Generation
Generate output that includes:
- [Required element 1]
- [Required element 2]
- [Optional element 1] (if applicable)

### Error Scenarios
Handle these potential errors:
- [Error type 1]: [Handling instruction]
- [Error type 2]: [Handling instruction]

### Quality Criteria
Ensure output meets:
- [Quality standard 1]
- [Quality standard 2]

### Example
**Input**: [Example input]
**Output**: [Example output]
```

## Required Task Prompts

Based on the SOP, generate prompts for these tasks:

### Core Tasks

#### TASK_PROMPT_VALIDATION
For validating and classifying input

#### TASK_PROMPT_ROUTING
For determining the appropriate processing path

#### TASK_PROMPT_SIMPLE_RESPONSE
For handling straightforward requests

#### TASK_PROMPT_COMPLEX_ANALYSIS
For requests requiring deep analysis

#### TASK_PROMPT_INTEGRATION_CALL
For managing external service interactions

#### TASK_PROMPT_ERROR_RESPONSE
For generating user-friendly error messages

#### TASK_PROMPT_BATCH_PROCESSING
For handling multiple items efficiently

### Specialized Tasks

#### TASK_PROMPT_[SPECIFIC_FUNCTION_1]
Based on unique agent capabilities

#### TASK_PROMPT_[SPECIFIC_FUNCTION_2]
Based on unique agent capabilities

### Integration-Specific Tasks

#### TASK_PROMPT_[INTEGRATION_1]_QUERY
For interacting with specific external system

#### TASK_PROMPT_[INTEGRATION_2]_UPDATE
For updating external system

### Administrative Tasks

#### TASK_PROMPT_STATUS_CHECK
For health monitoring and status reporting

#### TASK_PROMPT_AUDIT_LOG
For creating audit trail entries

#### TASK_PROMPT_METRICS_REPORT
For generating performance metrics

## Task Chaining Instructions

Define how tasks connect:

### Task Flow Mappings
```
VALIDATION → ROUTING → [SPECIFIC_TASK] → OUTPUT_GENERATION
                    ↓
                ERROR_RESPONSE (if validation fails)
```

### Context Passing
Between tasks, pass:
- Original request ID
- Validation results
- Previous task outputs
- Error accumulator
- Performance metrics

## Task Optimization Guidelines

### Caching Strategy
For each task, specify:
- Cacheable results: [What can be cached]
- Cache key generation: [How to create keys]
- Cache TTL: [Time to live]

### Parallel Execution
Tasks that can run in parallel:
- [Task A] and [Task B]
- [Task C] and [Task D]

### Fast-Path Conditions
When to skip to simplified processing:
- [Condition 1]: Use [Fast Task X]
- [Condition 2]: Use [Fast Task Y]

## Task Testing Scenarios

For each task, provide test cases:

### Positive Test Cases
1. **Standard Input**: [Input] → [Expected output]
2. **Edge Case**: [Input] → [Expected output]

### Negative Test Cases
1. **Invalid Input**: [Input] → [Expected error]
2. **Timeout Scenario**: [Input] → [Expected behavior]

### Performance Test Cases
1. **High Volume**: [Scenario] → [Performance target]
2. **Complex Processing**: [Scenario] → [Performance target]

Generate comprehensive task prompts that can be individually invoked for specific operations.