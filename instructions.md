# Claude SOP Generator - Instructions

## Overview
This system transforms your use cases into production-ready AI agent Standard Operating Procedures (SOPs) using a three-stage process. Each stage builds upon the previous one to create comprehensive agent documentation and implementation.

## Quick Start

### 1. Install Claude Code
```bash
npm install -g @anthropic-ai/claude-code
```

### 2. Setup Your Use Case
Create a file `input/use-case.md` with your agent description:

```markdown
# My Agent Use Case

## Description
[Describe what your agent should do]

## Example Tasks
- Task 1: [Description]
- Task 2: [Description]
- Task 3: [Description]

## Requirements
- [List specific requirements]
- [Integration needs]
- [Constraints]
```

### 3. Run the Three Stages

#### Stage 1: Define
```bash
./claude-define
```
This analyzes your use case and generates:
- Agent scope and boundaries
- Concrete scenarios with success criteria
- Capability definitions
- Quality review report

Output location: `output/stage1-define/`

#### Stage 2: Design
```bash
./claude-design
```
This creates the Standard Operating Procedure:
- Step-by-step workflows
- Decision trees
- Error handling procedures
- Integration specifications

Output location: `output/stage2-design/`

#### Stage 3: Build
```bash
./claude-build
```
This generates the implementation:
- System architecture
- Agent prompts
- Implementation code
- Test framework

Output location: `output/stage3-build/`

## Additional Commands

### Review Progress
```bash
./claude-review
```
Run quality checks on any completed stage.

### Start Fresh
```bash
./claude-clear
```
Removes all outputs and resets progress for a new project.

## Directory Structure
```
sopClaude/
├── input/
│   └── use-case.md      # Your use case goes here
├── output/              # All generated artifacts
│   ├── stage1-define/   # Definition outputs
│   ├── stage2-design/   # SOP outputs
│   └── stage3-build/    # Implementation outputs
└── prompts/             # System prompts (don't modify)
```

## Example Use Case

Here's a sample `input/use-case.md` for an email agent:

```markdown
# Email Management Agent

## Description
An AI agent that automatically categorizes, prioritizes, and drafts responses to emails based on content and sender importance.

## Example Tasks
- Task 1: Categorize incoming emails (urgent, important, newsletter, spam)
- Task 2: Draft appropriate responses based on email type
- Task 3: Schedule emails for optimal sending times
- Task 4: Extract action items and create tasks

## Requirements
- Integration with email providers (Gmail, Outlook)
- Natural language understanding
- Calendar integration for scheduling
- Task management system integration
```

## Tips for Best Results

1. **Be Specific**: The more detailed your use case, the better the output
2. **Include Examples**: Concrete examples help generate better scenarios
3. **List Constraints**: Mention any limitations or requirements upfront
4. **Review Each Stage**: Check outputs before proceeding to the next stage
5. **Iterate**: You can always run `claude-clear` and refine your use case

## Troubleshooting

### Command not found
Make sure you've made the scripts executable:
```bash
chmod +x claude-*
```

### No output generated
- Check that `input/use-case.md` exists
- Ensure Claude Code is installed and working
- Review any error messages in the terminal

### Want to modify outputs
You can manually edit any generated files before running the next stage. The system will use your edited versions as input.

## Output Examples

### Stage 1 Output
- `agent-scope.md`: Defines what the agent will and won't do
- `scenarios/`: Concrete use cases with expected outcomes
- `review/stage1-review.md`: Quality assessment

### Stage 2 Output
- `sop/main-workflow.md`: Step-by-step procedures
- `sop/decision-trees.md`: Logic flow diagrams
- `integrations.md`: External system requirements

### Stage 3 Output
- `architecture/system-design.md`: Component structure
- `prompts/system-prompt.md`: Main agent instructions
- `implementation/`: Working code examples

## Advanced Usage

### Customizing Prompts
Advanced users can modify the prompts in `prompts/` directory to customize the output style or add specific requirements.

### Integration with Your Project
The generated outputs are designed to be directly usable in your projects. The implementation code can be adapted to your specific programming language and framework.

## Support

For issues or questions:
1. Check the review reports in each stage's output
2. Ensure your use case is well-defined
3. Try running `claude-clear` and starting fresh
4. Review the generated artifacts for any error messages

Happy SOP generating!