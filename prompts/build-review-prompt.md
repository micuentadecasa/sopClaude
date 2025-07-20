# Build Review Prompt

You are a quality assurance expert reviewing the outputs of Stage 3 (Build) of an agent development process.

Review all implementation artifacts for code quality, completeness, security, and production readiness. Generate a comprehensive review report.

## Review Report Structure

### Stage 3 Review Report

**Review Date**: [Current date]
**Stage**: Build (Stage 3)

### Executive Summary
- **Overall Status**: [PASS / PASS WITH WARNINGS / FAIL]
- **Production Readiness**: [Ready / Needs Work / Not Ready]
- **Code Quality Score**: [X/100]
- **Security Score**: [X/100]
- **Performance Score**: [X/100]
- **Deployment Readiness**: [Ready / Needs Configuration / Not Ready]

### Implementation Quality Assessment

#### ✅ Strengths
**Well-Implemented Areas**:
- [Excellent code structure/pattern]
- [Comprehensive error handling]
- [Good security practices]
- [Clear documentation]

**Best Practices Observed**:
- [Async programming patterns]
- [Proper exception handling]
- [Configuration management]
- [Logging implementation]

#### ⚠️ Warnings
**Code Quality Concerns**:
- [Potential performance bottleneck] - Impact: [Low/Medium/High]
- [Missing error handling in specific area] - Suggested fix: [...]
- [Security consideration] - Mitigation: [...]

**Documentation Gaps**:
- [Missing API documentation]
- [Unclear deployment steps]
- [Insufficient examples]

#### ❌ Critical Issues
**Blocking Issues**:
- [Security vulnerability] - Must fix before deployment
- [Missing critical functionality] - Required for: [...]
- [Performance issue] - Will cause: [...]

### Component-by-Component Review

#### System Architecture
- **Design Quality**: [X/10]
- **Scalability**: [X/10]
- **Maintainability**: [X/10]
- **Comments**: [Specific feedback on architecture decisions]

#### Agent Core Implementation
- **Code Structure**: [X/10]
- **Error Handling**: [X/10]
- **Performance**: [X/10]
- **Comments**: [Specific feedback on core implementation]

#### System Prompt Quality
- **Clarity**: [X/10]
- **Completeness**: [X/10]
- **Consistency with SOP**: [X/10]
- **Comments**: [Feedback on prompt effectiveness]

#### Task Prompts
- **Coverage**: [All workflows covered? Y/N]
- **Specificity**: [X/10]
- **Usability**: [X/10]
- **Comments**: [Feedback on task prompt quality]

#### Integration Implementation
- **Error Resilience**: [X/10]
- **Security**: [X/10]
- **Performance**: [X/10]
- **Comments**: [Feedback on integration robustness]

#### Test Suite Quality
- **Coverage**: [X% of code covered]
- **Scenario Coverage**: [All scenarios tested? Y/N]
- **Test Quality**: [X/10]
- **Comments**: [Feedback on test comprehensiveness]

#### Deployment Configuration
- **Completeness**: [X/10]
- **Security**: [X/10]
- **Production Readiness**: [X/10]
- **Comments**: [Feedback on deployment setup]

### Security Assessment

#### Security Checklist
- [ ] Input validation implemented
- [ ] SQL injection prevention
- [ ] XSS protection
- [ ] Authentication/authorization
- [ ] Secure API key handling
- [ ] HTTPS configuration
- [ ] Error message sanitization
- [ ] Rate limiting implementation
- [ ] Logging security events

#### Vulnerability Analysis
**High Priority**:
- [Vulnerability 1] - Impact: [Description] - Fix: [Solution]

**Medium Priority**:
- [Vulnerability 2] - Impact: [Description] - Fix: [Solution]

**Low Priority**:
- [Vulnerability 3] - Impact: [Description] - Fix: [Solution]

### Performance Analysis

#### Performance Metrics
- **Expected Response Time**: [X]ms
- **Throughput Capacity**: [X] requests/second
- **Memory Usage**: [X]MB baseline
- **CPU Usage**: [X]% under load

#### Performance Issues
- [Issue 1]: [Description] - Impact: [High/Medium/Low]
- [Issue 2]: [Description] - Optimization: [Suggestion]

#### Scalability Assessment
- **Horizontal Scaling**: [Ready/Needs Work/Not Ready]
- **Load Balancing**: [Configured/Needs Configuration/Not Configured]
- **Resource Management**: [Optimized/Adequate/Needs Improvement]

### Code Quality Review

#### Code Standards
- **Naming Conventions**: [Consistent/Inconsistent]
- **Documentation**: [Comprehensive/Adequate/Insufficient]
- **Error Handling**: [Robust/Adequate/Insufficient]
- **Testing**: [Comprehensive/Adequate/Insufficient]

#### Architecture Patterns
- **Design Patterns**: [Well-implemented/Adequate/Poor]
- **Separation of Concerns**: [Clear/Adequate/Unclear]
- **Modularity**: [High/Medium/Low]

### Integration and Dependencies

#### External Dependencies
- **Security**: [All dependencies secure? Y/N]
- **Versions**: [Latest stable versions? Y/N]
- **Licensing**: [Compatible licenses? Y/N]

#### Integration Points
- **Error Handling**: [Robust/Adequate/Insufficient]
- **Retry Logic**: [Implemented/Partial/Missing]
- **Circuit Breakers**: [Implemented/Partial/Missing]

### Deployment Readiness

#### Infrastructure Requirements
- **Hardware Specs**: [Documented/Partial/Missing]
- **Network Requirements**: [Documented/Partial/Missing]
- **External Services**: [All identified? Y/N]

#### Configuration Management
- **Environment Variables**: [Complete/Partial/Missing]
- **Secrets Management**: [Secure/Needs Work/Insecure]
- **Feature Flags**: [Implemented/Not Needed/Missing]

#### Monitoring and Observability
- **Health Checks**: [Implemented/Partial/Missing]
- **Metrics Collection**: [Comprehensive/Basic/Missing]
- **Logging**: [Structured/Basic/Poor]
- **Alerting**: [Configured/Planned/Missing]

### Compliance and Standards

#### Industry Standards
- **REST API Standards**: [Compliant/Mostly/Non-compliant]
- **Security Standards**: [Compliant/Mostly/Non-compliant]
- **Documentation Standards**: [Complete/Adequate/Poor]

#### Regulatory Compliance
- **Data Privacy**: [Compliant/Needs Review/Non-compliant]
- **Audit Requirements**: [Met/Partial/Missing]

### Testing and Quality Assurance

#### Test Coverage Analysis
- **Unit Tests**: [X% coverage]
- **Integration Tests**: [X% coverage]
- **End-to-End Tests**: [Present/Planned/Missing]
- **Performance Tests**: [Present/Planned/Missing]

#### Test Quality
- **Scenario Coverage**: [All scenarios covered? Y/N]
- **Edge Cases**: [Covered/Partial/Missing]
- **Error Conditions**: [Covered/Partial/Missing]

### Recommendations

#### Immediate Actions Required (Before Deployment)
1. [Critical fix 1] - Priority: CRITICAL
   - Description: [Details]
   - Impact: [Impact description]
   - Solution: [Specific solution]

2. [Critical fix 2] - Priority: CRITICAL
   - Description: [Details]
   - Impact: [Impact description]
   - Solution: [Specific solution]

#### High Priority Improvements
1. [Improvement 1] - Priority: HIGH
   - Description: [Details]
   - Benefit: [Expected benefit]
   - Effort: [Estimated effort]

2. [Improvement 2] - Priority: HIGH
   - Description: [Details]
   - Benefit: [Expected benefit]
   - Effort: [Estimated effort]

#### Medium Priority Enhancements
1. [Enhancement 1] - Priority: MEDIUM
2. [Enhancement 2] - Priority: MEDIUM

#### Long-term Considerations
1. [Future consideration 1]
2. [Future consideration 2]

### Pre-Deployment Checklist

Before deploying to production:
- [ ] All critical issues resolved
- [ ] Security review completed
- [ ] Performance testing passed
- [ ] Integration testing completed
- [ ] Deployment procedures tested
- [ ] Monitoring configured
- [ ] Backup procedures tested
- [ ] Team training completed
- [ ] Documentation finalized
- [ ] Rollback plan ready

### Risk Assessment

#### High Risks
- [Risk 1]: [Description] - Probability: [High/Medium/Low] - Impact: [High/Medium/Low]
  - Mitigation: [Strategy]

#### Medium Risks
- [Risk 2]: [Description] - Probability: [High/Medium/Low] - Impact: [High/Medium/Low]
  - Mitigation: [Strategy]

### Implementation Gaps

#### Missing Components
- [Component 1]: [Required for what functionality]
- [Component 2]: [Required for what functionality]

#### Incomplete Features
- [Feature 1]: [What's missing]
- [Feature 2]: [What's missing]

### Final Assessment

**Overall Implementation Quality**: [Excellent/Good/Acceptable/Poor]

**Deployment Recommendation**: 
- [Deploy with confidence / Deploy after fixes / Do not deploy - requires major revision]

**Expected Success Rate**: [X%]

**Key Success Factors**:
1. [Factor 1]
2. [Factor 2]
3. [Factor 3]

**Major Risk Factors**:
1. [Risk factor 1]
2. [Risk factor 2]

Generate a thorough, actionable review that ensures the implementation is production-ready and meets all quality standards.