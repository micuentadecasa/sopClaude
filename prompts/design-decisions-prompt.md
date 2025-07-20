# Design Decision Trees Prompt

Based on the main workflow SOP and scenarios, create detailed decision trees for all key decision points in the agent's operation.

## Decision Trees Documentation

### Master Decision Tree
Create the top-level decision tree that routes to specific handlers:

```
[Initial Input]
    |
    ├─ Is input valid?
    │   ├─ No → [Error Handler]
    │   └─ Yes → Continue
    │       |
    │       ├─ What type of request?
    │       │   ├─ Type A → [Decision Tree A]
    │       │   ├─ Type B → [Decision Tree B]
    │       │   └─ Type C → [Decision Tree C]
    │       └─ ...
```

### Decision Tree A: [Specific Process Name]
```
[Input Type A]
    |
    ├─ Check condition 1
    │   ├─ True → Action 1
    │   └─ False → Check condition 2
    │       ├─ True → Action 2
    │       └─ False → Action 3
```

### Decision Tree B: [Specific Process Name]
[Create similar detailed tree]

## Decision Logic Documentation

For each decision point, document:

### Decision: [Decision Name]
**Input Variables**:
- Variable 1: [Type, range, description]
- Variable 2: [Type, range, description]

**Decision Logic**:
```
IF (condition1 AND condition2) THEN
    → Path A: [Description]
ELIF (condition3 OR condition4) THEN
    → Path B: [Description]
ELSE
    → Path C: [Default path]
```

**Edge Cases**:
- If [edge case 1]: [How to handle]
- If [edge case 2]: [How to handle]

## Complex Decision Patterns

### Multi-Factor Decisions
For decisions requiring multiple inputs:

**Decision Matrix**:
| Factor 1 | Factor 2 | Factor 3 | Result |
|----------|----------|----------|---------|
| High     | Yes      | Type A   | Action 1|
| High     | No       | Type A   | Action 2|
| Low      | Yes      | Type B   | Action 3|
| ...      | ...      | ...      | ...     |

### Weighted Decisions
For decisions with scoring:

**Scoring Criteria**:
- Criterion 1: Weight 40%
- Criterion 2: Weight 30%
- Criterion 3: Weight 30%

**Thresholds**:
- Score > 80: High confidence path
- Score 50-80: Medium confidence path
- Score < 50: Low confidence/manual review

## Decision Optimization

### Fast-Path Decisions
Identify decisions that can be made quickly:
- [Decision 1]: Check only [condition] for 80% of cases
- [Decision 2]: Use cached result if available

### Complex Decision Handling
For decisions requiring extensive processing:
- Break into sub-decisions
- Cache intermediate results
- Provide progress feedback

Create comprehensive decision trees that cover all paths through the agent's logic.