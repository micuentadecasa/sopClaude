# Claude SOP Generator Configuration

## Project Overview
This project generates complete Standard Operating Procedures (SOPs) and implementation code for AI agents using a three-stage process. Each stage builds upon the previous one to create comprehensive agent documentation and code.

## How to Use This Project

### Quick Start
1. Create your use case in `input/use-case.md`
2. Run `./claude-sop` to generate everything automatically
3. Review outputs in the `output/` directory

### Individual Commands
- `./claude-define` - Stage 1: Define agent scope and scenarios
- `./claude-design` - Stage 2: Create Standard Operating Procedure  
- `./claude-build` - Stage 3: Generate implementation code
- `./claude-review` - Quality review of any completed stage
- `./claude-clear` - Clear all outputs to start fresh

### Command Options
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
├── prompts/                  # System prompts (don't modify)
├── claude-define*            # Stage 1 command
├── claude-design*            # Stage 2 command
├── claude-build*             # Stage 3 command
├── claude-review*            # Review command
├── claude-clear*             # Clear command
├── claude-sop*               # Master command
└── instructions.md           # Detailed usage instructions
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