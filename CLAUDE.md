# Claude SOP Generator - Integrated System

## Project Overview
This project generates complete Standard Operating Procedures (SOPs) and implementation code for AI agents using a three-stage process. Each stage builds upon the previous one to create comprehensive agent documentation and code.

## IMPORTANT: AI Agent Instructions

When the user runs `./claude-sop`, you should:

1. **Check Current State**: Read `tmp/sop-progress.json` to understand current progress
2. **Detect Stage**: Determine which stage to execute based on tracking files and command options
3. **Execute Stage**: Follow the appropriate stage instructions below
4. **Update Progress**: Update tracking files as tasks are completed
5. **Continue or Stop**: Move to next stage or complete based on configuration

### State Detection Logic

```javascript
// Read tmp/sop-progress.json to determine:
// - current_stage: which stage we're on (0=not started, 1=define, 2=design, 3=build)
// - completed_stages: array of completed stage numbers
// - status: 'ready', 'in_progress', 'completed', 'error'

// If user passes --fresh: reset all progress and clear outputs
// If user passes --stage N: start from stage N
// If user passes --review: run review after completion
```

## How to Use This Project

### Quick Start
1. Create your use case in `input/use-case.md`
2. Run `./claude-sop` to generate everything automatically
3. Review outputs in the `output/` directory

### Command Options
- `./claude-sop` - Run all stages from current position
- `./claude-sop --review` - Run all stages plus quality review
- `./claude-sop --stage 2` - Start from specific stage
- `./claude-sop --fresh` - Clear previous outputs before starting
- `./claude-sop --verbose` - Show detailed output
- `./claude-sop --quiet` - Minimal output

## Directory Structure
```
sopClaude/
├── input/
│   └── use-case.md           # Your use case description goes here
├── output/                   # All generated artifacts
│   ├── stage1-define/        # Agent definition and scenarios
│   ├── stage2-design/        # Standard Operating Procedures
│   └── stage3-build/         # Implementation code
├── prompts/                  # System prompts (referenced by stages)
├── tmp/                      # Progress tracking files
│   ├── sop-progress.json     # Overall progress state
│   ├── stage1-tasks.json     # Stage 1 task tracking
│   ├── stage2-tasks.json     # Stage 2 task tracking
│   └── stage3-tasks.json     # Stage 3 task tracking
├── claude-sop*               # Single command to trigger this CLAUDE.md
├── claude-clear*             # Clear command
└── CLAUDE.md                 # This file - contains all logic
```

## Input Requirements

### Use Case Format
Your `input/use-case.md` should include:
- **Description**: Clear explanation of what the agent should do
- **Example Tasks**: 5-10 concrete examples with inputs/outputs
- **Requirements**: Functional, integration, performance, and security needs
- **Constraints**: Limitations and special considerations
- **Success Metrics**: How to measure effectiveness

### Example Use Case Structure
```markdown
# Agent Name

## Description
[What the agent does and why it's valuable]

## Example Tasks
### Task 1: [Task Name]
- **Input**: [Specific input format]
- **Action**: [What the agent does]
- **Output**: [Expected result]

[Continue with more tasks...]

## Requirements
- **Functional**: [What it must do]
- **Integration**: [External systems]
- **Performance**: [Speed, accuracy, throughput]
- **Security**: [Privacy, compliance, safety]

## Constraints
- [Limitation 1]
- [Limitation 2]
```

## Output Structure

### Stage 1: Define
- `agent-scope.md` - Defines what the agent will/won't do
- `scenarios/` - Individual scenario files with success criteria
- `review/stage1-review.md` - Quality assessment

### Stage 2: Design
- `sop/main-workflow.md` - Step-by-step procedures
- `sop/decision-trees.md` - Logic flow diagrams
- `sop/error-handling.md` - Error procedures
- `sop/optimized-sop.md` - Streamlined final version
- `integrations.md` - External system specifications
- `review/stage2-review.md` - Quality assessment

### Stage 3: Build
- `architecture/system-design.md` - Technical architecture
- `prompts/system-prompt.md` - Main agent instructions
- `prompts/task-prompts/` - Specific task instructions
- `implementation/agent-core.py` - Main implementation
- `implementation/integrations.py` - External connections
- `tests/test-suite.py` - Comprehensive test framework
- `deployment-guide.md` - Production deployment guide
- `review/stage3-review.md` - Final quality assessment

## Customization

### Modifying Prompts
Advanced users can customize the prompts in `prompts/` to:
- Change output format or style
- Add specific requirements or constraints
- Adjust for different programming languages
- Include additional quality checks

### Integration with Your Workflow
The generated outputs are designed to be:
- **Directly usable** in your projects
- **Technology agnostic** (can adapt to different languages)
- **Production ready** with proper error handling
- **Well documented** for easy maintenance

## Best Practices

### Use Case Writing
1. **Be Specific**: Include concrete examples with real data
2. **Cover Edge Cases**: Mention unusual or error scenarios
3. **Define Success**: Clear metrics for what "working" means
4. **List Integrations**: All external systems the agent needs
5. **Set Constraints**: Mention limitations upfront

### Iterative Development
1. Start with a simple use case
2. Run the full pipeline
3. Review the outputs
4. Refine your use case based on learnings
5. Run `./claude-clear` and regenerate

### Quality Assurance
1. Always run `./claude-review` after completion
2. Check each stage's review report
3. Address any critical issues before proceeding
4. Test the generated code in a safe environment

## Common Issues and Solutions

### Command Not Found
```bash
chmod +x claude-*  # Make scripts executable
```

### Missing Input File
Create `input/use-case.md` with your agent description

### Incomplete Outputs
- Check for error messages in the terminal
- Ensure Claude Code is properly installed
- Verify internet connection for API calls

### Poor Quality Outputs
- Make your use case more detailed and specific
- Include more concrete examples
- Clearly define requirements and constraints

---

# INTEGRATED STAGE EXECUTION LOGIC

## Stage Detection and Execution

When executing `./claude-sop`, follow this logic:

### 1. Pre-Execution Setup

1. **Read Progress State**:
   ```
   Check tmp/sop-progress.json for:
   - current_stage
   - completed_stages
   - status
   - options (from command line)
   ```

2. **Parse Command Options**:
   - `--fresh`: Reset progress and clear outputs
   - `--stage N`: Start from specific stage
   - `--review`: Run review after completion
   - `--verbose`: Show detailed output
   - `--quiet`: Minimal output

3. **Validate Prerequisites**:
   - Check input/use-case.md exists
   - Create output directories if needed
   - Update sop-progress.json with current options

### 2. Stage Execution Logic

#### STAGE 1: DEFINE AGENT SCOPE AND SCENARIOS

**Trigger Conditions**:
- current_stage < 1 OR --stage 1 OR --fresh
- OR stage1-tasks.json shows incomplete tasks

**Execution Steps**:

1. **Update Progress**:
   ```json
   {
     "current_stage": 1,
     "status": "in_progress",
     "started_at": "timestamp"
   }
   ```

2. **Read Use Case**:
   - Load input/use-case.md
   - Parse requirements, examples, constraints
   - Mark "read_use_case" task as completed in stage1-tasks.json

3. **Generate Agent Scope**:
   - Use prompts/define-scope-prompt.md as guidance
   - Create output/stage1-define/agent-scope.md
   - Include: purpose, capabilities, limitations, success criteria
   - Mark "generate_scope" task as completed

4. **Create Scenarios**:
   - Use prompts/define-scenarios-prompt.md as guidance
   - Generate 5-10 scenario files in output/stage1-define/scenarios/
   - Each scenario: input, expected behavior, success criteria
   - Mark "create_scenarios" task as completed

5. **Stage 1 Review**:
   - Use prompts/define-review-prompt.md as guidance
   - Create output/stage1-define/review/stage1-review.md
   - Check completeness, clarity, feasibility
   - Mark "stage1_review" task as completed

6. **Complete Stage 1**:
   ```json
   {
     "current_stage": 1,
     "completed_stages": [1],
     "status": "stage1_complete"
   }
   ```

#### STAGE 2: DESIGN STANDARD OPERATING PROCEDURE

**Trigger Conditions**:
- Stage 1 complete AND (current_stage < 2 OR --stage 2)
- OR stage2-tasks.json shows incomplete tasks

**Execution Steps**:

1. **Update Progress**:
   ```json
   {
     "current_stage": 2,
     "status": "in_progress"
   }
   ```

2. **Create Main Workflow**:
   - Use prompts/design-workflow-prompt.md
   - Read stage1 outputs for context
   - Create output/stage2-design/sop/main-workflow.md
   - Include: step-by-step procedures, decision points
   - Mark "create_workflow" task as completed

3. **Generate Decision Trees**:
   - Use prompts/design-decisions-prompt.md
   - Create output/stage2-design/sop/decision-trees.md
   - Visual flowcharts and logic paths
   - Mark "create_decision_trees" task as completed

4. **Design Error Handling**:
   - Use prompts/design-errors-prompt.md
   - Create output/stage2-design/sop/error-handling.md
   - Recovery procedures, escalation paths
   - Mark "create_error_handling" task as completed

5. **Define Integrations**:
   - Use prompts/design-integrations-prompt.md
   - Create output/stage2-design/integrations.md
   - API specifications, data formats
   - Mark "create_integrations" task as completed

6. **Optimize SOP**:
   - Use prompts/design-optimize-prompt.md
   - Combine all SOP documents into optimized version
   - Create output/stage2-design/sop/optimized-sop.md
   - Mark "optimize_sop" task as completed

7. **Stage 2 Review**:
   - Use prompts/design-review-prompt.md
   - Create output/stage2-design/review/stage2-review.md
   - Mark "stage2_review" task as completed

8. **Complete Stage 2**:
   ```json
   {
     "current_stage": 2,
     "completed_stages": [1, 2],
     "status": "stage2_complete"
   }
   ```

#### STAGE 3: BUILD IMPLEMENTATION ARTIFACTS

**Trigger Conditions**:
- Stage 2 complete AND (current_stage < 3 OR --stage 3)
- OR stage3-tasks.json shows incomplete tasks

**Execution Steps**:

1. **Update Progress**:
   ```json
   {
     "current_stage": 3,
     "status": "in_progress"
   }
   ```

2. **Create System Architecture**:
   - Use prompts/build-architecture-prompt.md
   - Create output/stage3-build/architecture/system-design.md
   - Technical specifications, component design
   - Mark "create_architecture" task as completed

3. **Generate System Prompt**:
   - Use prompts/build-system-prompt.md
   - Create output/stage3-build/prompts/system-prompt.md
   - Core agent instructions based on optimized SOP
   - Mark "create_system_prompt" task as completed

4. **Create Task Prompts**:
   - Use prompts/build-task-prompts.md
   - Create files in output/stage3-build/prompts/task-prompts/
   - Specific prompts for each scenario type
   - Mark "create_task_prompts" task as completed

5. **Generate Core Implementation**:
   - Use prompts/build-implementation-prompt.md
   - Create output/stage3-build/implementation/agent-core.py
   - Main agent class with workflow logic
   - Mark "create_implementation" task as completed

6. **Create Integration Code**:
   - Use prompts/build-integrations-prompt.md
   - Create output/stage3-build/implementation/integrations.py
   - External system connectors
   - Mark "create_integrations_impl" task as completed

7. **Generate Test Suite**:
   - Use prompts/build-tests-prompt.md
   - Create output/stage3-build/tests/test-suite.py
   - Comprehensive test coverage
   - Mark "create_tests" task as completed

8. **Create Deployment Guide**:
   - Use prompts/build-deployment-prompt.md
   - Create output/stage3-build/deployment-guide.md
   - Production setup instructions
   - Mark "create_deployment" task as completed

9. **Stage 3 Review**:
   - Use prompts/build-review-prompt.md
   - Create output/stage3-build/review/stage3-review.md
   - Final quality assessment
   - Mark "stage3_review" task as completed

10. **Complete Stage 3**:
    ```json
    {
      "current_stage": 3,
      "completed_stages": [1, 2, 3],
      "status": "completed",
      "completed_at": "timestamp"
    }
    ```

### 3. Error Handling and Recovery

**If Task Fails**:
1. Mark task status as "error" in tracking file
2. Log error details
3. Allow user to retry or skip
4. Preserve completed work

**If Stage Interrupted**:
1. Current progress saved in tracking files
2. Can resume from last completed task
3. No need to restart entire stage

### 4. Review Execution (Optional)

If `--review` flag is used:
1. Run comprehensive review across all stages
2. Generate output/overall-review.md
3. Highlight issues, suggestions, improvements
4. Provide quality score and recommendations

---

## Advanced Usage

### Parallel Development
You can work on multiple agents by:
1. Creating separate directories for each agent
2. Running the commands in each directory
3. Comparing and learning from different approaches

### Integration with CI/CD
The commands can be integrated into automated workflows:
```bash
# In your CI pipeline
./claude-sop --quiet
if [ $? -eq 0 ]; then
    echo "SOP generation successful"
    # Continue with deployment
else
    echo "SOP generation failed"
    exit 1
fi
```

## Support and Feedback

### Getting Help
1. Check `instructions.md` for detailed usage information
2. Review example use case in `input/use-case.md`
3. Run `./claude-sop --help` for command options

### Improving Quality
- The more detailed your use case, the better the output
- Include edge cases and error scenarios
- Specify integration requirements clearly
- Define success metrics precisely

## Version Information
- **Generator Version**: 1.0.0
- **Claude Code Required**: Latest version
- **Python Version**: 3.9+ (for generated code)
- **Dependencies**: Listed in generated requirements.txt

## Legal and Compliance
- Generated code includes security best practices
- Follows industry standards for error handling
- Includes audit logging and compliance features
- Review security considerations before production use

Happy SOP generation! 🚀