# Design Optimization Prompt

Review all the SOP components (main workflow, decision trees, error handling) and create an optimized, consolidated version that eliminates redundancies and improves efficiency.

## Optimization Analysis and Consolidated SOP

### Optimization Opportunities Identified

#### 1. Redundancy Elimination
**Found Redundancies**:
- [Duplicate process 1] appears in [locations]
- [Duplicate validation] occurs in [steps]
- [Repeated API calls] in [workflows]

**Consolidation Strategy**:
- Create shared functions for [common processes]
- Implement single validation point at [location]
- Cache API results for reuse

#### 2. Workflow Streamlining
**Bottlenecks Identified**:
- [Sequential process] that could be parallelized
- [Unnecessary wait points] in workflow
- [Over-complex decision trees] that can be simplified

**Optimization Actions**:
- Parallelize [specific steps]
- Remove [unnecessary checkpoints]
- Simplify decision logic using [approach]

### Optimized Main Workflow

## Streamlined SOP v2.0

### Quick-Path Workflows
For common scenarios (80% of cases):

**Fast Path A**: [Most common scenario]
1. Quick validation check
2. Direct routing to handler
3. Cached response if available
4. Single API call if needed
5. Return result

**Fast Path B**: [Second most common]
[Similar streamlined steps]

### Standard Workflow (Optimized)
For remaining 20% of cases:

#### Phase 1: Intelligent Input Processing
- Combined validation and classification
- Early exit for invalid inputs
- Smart routing based on patterns

#### Phase 2: Parallel Processing
Execute simultaneously:
- Branch A: [Process 1]
- Branch B: [Process 2]
- Branch C: [Process 3]

Wait for all to complete, then merge results.

#### Phase 3: Unified Output Generation
- Single output formatter
- Consistent error handling
- Standardized logging

### Optimized Decision Logic

#### Simplified Decision Tree
```
[Input] → [Pattern Matcher]
    ├─ Pattern A (60%) → Fast Handler A
    ├─ Pattern B (25%) → Fast Handler B
    └─ Complex (15%) → Full Decision Tree
```

#### Decision Caching
Cache these decisions for reuse:
- User preference decisions (TTL: 24h)
- Classification results (TTL: 1h)
- Routing decisions (TTL: 5m)

### Performance Optimizations

#### Resource Management
1. **Connection Pooling**
   - Maintain persistent connections to frequent APIs
   - Pool size: [recommended size]
   - Timeout: [recommended timeout]

2. **Request Batching**
   - Batch similar requests every [X] seconds
   - Maximum batch size: [Y]
   - Priority queue for urgent requests

3. **Precomputation**
   - Precompute common responses
   - Warm cache on startup
   - Background refresh for stale data

#### Memory Optimization
- Limit in-memory cache to [size]
- Use lazy loading for large datasets
- Implement cache eviction policy

### Monitoring and Metrics

#### Performance KPIs
Track these optimized metrics:
- Average response time: Target < [X]ms
- Cache hit rate: Target > [Y]%
- Parallel processing utilization: Target > [Z]%

#### Optimization Validation
Measure improvement:
- Before: [baseline metrics]
- After: [expected metrics]
- Improvement: [percentage gains]

### Implementation Priority

#### Quick Wins (Week 1)
1. Implement response caching
2. Add pattern-based fast paths
3. Consolidate duplicate validations

#### Medium Term (Week 2-3)
1. Set up connection pooling
2. Implement parallel processing
3. Optimize decision trees

#### Long Term (Month 2)
1. Advanced caching strategies
2. Machine learning for pattern detection
3. Predictive pre-processing

### Rollback Plan
If optimizations cause issues:
1. Feature flag for each optimization
2. Gradual rollout (10% → 50% → 100%)
3. Automated rollback triggers
4. Keep non-optimized path available

Generate a consolidated, optimized SOP that maintains all functionality while significantly improving performance.