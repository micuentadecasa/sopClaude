# Workflow CLAUDE.md Generator - Meta Prompt

You are an expert system architect tasked with creating a complete CLAUDE.md file system for any workflow-based process. Your goal is to analyze the provided workflow description and generate a fully functional CLAUDE.md file that includes integrated stage execution logic, progress tracking, command scripts, and validation systems.

## Your Task

1. **Analyze the Workflow**: Break down the provided workflow into logical stages
2. **Generate CLAUDE.md**: Create a complete CLAUDE.md file with all necessary components
3. **Design Stage Logic**: Define execution steps, validation, and progress tracking
4. **Create Supporting System**: Include command scripts, directory structures, and templates

## Analysis Framework

### Step 1: Workflow Analysis
When analyzing the input workflow, identify:

#### Core Components
- **Purpose**: What is the main objective of this workflow?
- **Inputs**: What information/documents are required to start?
- **Outputs**: What deliverables should be produced?
- **Stakeholders**: Who is involved in the process?
- **Dependencies**: What systems, tools, or resources are needed?

#### Stage Breakdown
- **Number of Stages**: How many logical phases are there? (typically 3-7 stages)
- **Stage Sequence**: What is the order of execution?
- **Stage Dependencies**: Which stages depend on previous completions?
- **Stage Outputs**: What specific deliverables does each stage produce?
- **Validation Points**: Where are quality checks and approvals needed?

#### Complexity Assessment
- **Simple Workflow**: Linear process with minimal dependencies (3-4 stages)
- **Medium Workflow**: Some branching and validation points (4-6 stages)
- **Complex Workflow**: Multiple paths, extensive validation, integrations (5-7+ stages)

### Step 2: Stage Design Patterns
For each identified stage, define:

#### Stage Structure
```
Stage N: [STAGE_NAME]
- Purpose: [What this stage accomplishes]
- Inputs: [Required inputs from previous stages or external sources]
- Tasks: [Specific tasks to be completed]
- Outputs: [Deliverables produced]
- Validation: [Quality checks and approval requirements]
- Success Criteria: [How to measure successful completion]
```

#### Common Stage Types
- **Intake/Analysis Stage**: Collect and analyze initial requirements
- **Design/Planning Stage**: Create plans, specifications, or designs
- **Implementation Stage**: Execute the main work or build deliverables
- **Review/Validation Stage**: Quality assurance and stakeholder approval
- **Deployment/Delivery Stage**: Final delivery and handoff

## CLAUDE.md Generation Template

Generate a complete CLAUDE.md file using this structure:

### Header Section
```markdown
# [WORKFLOW_NAME] - Integrated System

## Project Overview
[Brief description of the workflow and its value proposition]

## IMPORTANT: AI Agent Instructions

When the user runs `./[COMMAND_NAME]`, you should:

1. **Check Current State**: Read `tmp/[WORKFLOW_SLUG]-progress.json` to understand current progress
2. **Detect Stage**: Determine which stage to execute based on tracking files and command options
3. **Execute Stage**: Follow the appropriate stage instructions below
4. **Update Progress**: Update tracking files as tasks are completed
5. **Continue or Stop**: Move to next stage or complete based on configuration
```

### State Detection Logic
```markdown
### State Detection Logic

```javascript
// Read tmp/[WORKFLOW_SLUG]-progress.json to determine:
// - current_stage: which stage we're on (0=not started, 1=[stage1], 2=[stage2], etc.)
// - completed_stages: array of completed stage numbers
// - status: 'ready', 'in_progress', 'completed', 'error'

// If user passes --fresh: reset all progress and clear outputs
// If user passes --stage N: start from stage N
// If user passes --review: run review after completion
```
```

### Usage Instructions
```markdown
## How to Use This Project

### Quick Start
1. Create your [INPUT_TYPE] in `input/[INPUT_FILE]`
2. Run `./[COMMAND_NAME]` to generate everything automatically
3. Review outputs in the `output/` directory

### Command Options
- `./[COMMAND_NAME]` - Run all stages from current position
- `./[COMMAND_NAME] --review` - Run all stages plus quality review
- `./[COMMAND_NAME] --stage N` - Start from specific stage
- `./[COMMAND_NAME] --fresh` - Clear previous outputs before starting
- `./[COMMAND_NAME] --verbose` - Show detailed output
- `./[COMMAND_NAME] --quiet` - Minimal output
```

### Directory Structure
```markdown
## Directory Structure
```
[PROJECT_NAME]/
├── input/
│   └── [INPUT_FILE]              # Your [INPUT_TYPE] goes here
├── output/                       # All generated artifacts
[STAGE_DIRECTORIES]
├── prompts/                      # System prompts (referenced by stages)
├── tmp/                          # Progress tracking files
│   ├── [WORKFLOW_SLUG]-progress.json    # Overall progress state
[STAGE_TASK_FILES]
├── [COMMAND_NAME]*               # Single command to trigger this CLAUDE.md
├── claude-clear*                 # Clear command
└── CLAUDE.md                     # This file - contains all logic
```
```

### Input Requirements Section
Define the expected input format and requirements:

```markdown
## Input Requirements

### [INPUT_TYPE] Format
Your `input/[INPUT_FILE]` should include:
[INPUT_REQUIREMENTS_LIST]

### Example [INPUT_TYPE] Structure
```markdown
[EXAMPLE_INPUT_STRUCTURE]
```
```

### Stage Execution Logic
For each stage, generate:

```markdown
#### STAGE [N]: [STAGE_NAME]

**Trigger Conditions**:
- [TRIGGER_CONDITIONS]

**Execution Steps**:

1. **Update Progress**:
   ```json
   {
     "current_stage": [N],
     "status": "in_progress",
     "started_at": "timestamp"
   }
   ```

2. **[TASK_1_NAME]**:
   - [Task description and actions]
   - Mark "[TASK_1_ID]" task as completed in stage[N]-tasks.json

[ADDITIONAL_TASKS]

[N]. **Complete Stage [N]**:
   ```json
   {
     "current_stage": [N],
     "completed_stages": [[COMPLETED_STAGES_ARRAY]],
     "status": "stage[N]_complete"
   }
   ```
```

### Error Handling and Quality Control
```markdown
### Error Handling and Recovery

**If Task Fails**:
1. Mark task status as "error" in tracking file
2. Log error details
3. Allow user to retry or skip
4. Preserve completed work

**If Stage Interrupted**:
1. Current progress saved in tracking files
2. Can resume from last completed task
3. No need to restart entire stage

### Quality Control Framework
[QUALITY_CONTROL_PROCEDURES]
```

## Special Instructions for Complex Workflows

### Multi-Path Workflows
If the workflow has branching paths:
- Create conditional logic in stage execution
- Use decision trees for path selection
- Include merge points where paths reconvene

### Integration-Heavy Workflows
For workflows requiring external system integration:
- Create dedicated integration validation steps
- Include connection testing procedures
- Add fallback mechanisms for system failures

### Approval-Heavy Workflows
For workflows requiring multiple approvals:
- Create stakeholder notification systems
- Include approval tracking mechanisms
- Add escalation procedures for delayed approvals

## Output Requirements

Your generated CLAUDE.md must include:

### 1. Complete Project Structure
- Proper directory organization
- All necessary tracking files
- Command script specifications

### 2. Stage Execution Logic
- Clear trigger conditions
- Detailed execution steps
- Progress update mechanisms
- Error handling procedures

### 3. Validation Framework
- Quality checkpoints at each stage
- Success criteria definitions
- Review and approval processes

### 4. User Experience
- Clear usage instructions
- Helpful error messages
- Progress visibility
- Recovery procedures

### 5. Extensibility
- Configurable parameters
- Customization guidelines
- Integration points for additional tools

## Template Variables to Replace

When generating the CLAUDE.md, replace these variables:

- `[WORKFLOW_NAME]` - Full name of the workflow
- `[WORKFLOW_SLUG]` - URL-friendly slug version
- `[COMMAND_NAME]` - Executable command name (e.g., claude-workflow)
- `[PROJECT_NAME]` - Directory/project name
- `[INPUT_TYPE]` - Type of input document (e.g., requirements, specification)
- `[INPUT_FILE]` - Input file name (e.g., requirements.md)
- `[STAGE_DIRECTORIES]` - Directory structure for each stage
- `[STAGE_TASK_FILES]` - Task tracking files for each stage
- `[INPUT_REQUIREMENTS_LIST]` - List of input requirements
- `[EXAMPLE_INPUT_STRUCTURE]` - Example input format
- `[QUALITY_CONTROL_PROCEDURES]` - Quality control specific to workflow

## Best Practices for CLAUDE.md Generation

### 1. Maintain Consistency
- Use consistent naming conventions
- Follow the same pattern for all stages
- Ensure variable replacements are complete

### 2. Include Comprehensive Error Handling
- Account for partial completions
- Provide clear recovery procedures
- Include validation at every step

### 3. Design for User Experience
- Provide clear feedback and progress indicators
- Include helpful documentation
- Make commands intuitive and predictable

### 4. Ensure Scalability
- Design for workflows of varying complexity
- Allow for customization and extension
- Include performance considerations

---

# USE CASE TO PROCESS

**Instructions**: The workflow description below should be analyzed and converted into a complete CLAUDE.md system. Use the framework above to create all necessary components.

## Email Management Agent Workflow

### Description
An AI agent that automatically processes incoming emails, categorizes them by importance and type, drafts appropriate responses, and manages follow-up actions. The agent should integrate with email providers and task management systems to create a comprehensive email workflow automation.

### Primary Objectives
- Reduce email processing time by 70%
- Ensure important emails are never missed
- Maintain professional response quality
- Automate routine email tasks
- Integrate seamlessly with existing workflows

### Example Tasks

#### Task 1: Email Classification and Prioritization
- **Input**: Incoming email with sender, subject, content
- **Action**: Analyze email content and classify as:
  - Urgent (requires immediate response)
  - Important (requires response within 24 hours)
  - Informational (no response needed)
  - Newsletter/Marketing (archive or unsubscribe)
  - Spam (move to spam folder)
- **Output**: Classified email with priority score and suggested action

#### Task 2: Automated Response Generation
- **Input**: Classified email requiring response
- **Action**: Generate appropriate response based on:
  - Email content and context
  - Sender relationship and history
  - Response templates and tone guidelines
  - Company policies and procedures
- **Output**: Draft response ready for review/sending

#### Task 3: Meeting Scheduling
- **Input**: Email requesting meeting or containing scheduling information
- **Action**: 
  - Extract meeting details (date, time, attendees, topic)
  - Check calendar availability
  - Generate meeting invite or response
  - Add to calendar with appropriate details
- **Output**: Calendar entry and meeting response

#### Task 4: Action Item Extraction
- **Input**: Email containing tasks, deadlines, or follow-up items
- **Action**:
  - Identify actionable items and deadlines
  - Create tasks in project management system
  - Set reminders and notifications
  - Track completion status
- **Output**: Created tasks with proper categorization and deadlines

#### Task 5: Customer Support Routing
- **Input**: Customer support email
- **Action**:
  - Analyze issue type and complexity
  - Route to appropriate department/person
  - Generate initial response acknowledgment
  - Create support ticket if needed
- **Output**: Routed email with tracking information

#### Task 6: Invoice and Financial Processing
- **Input**: Email with invoices, receipts, or financial documents
- **Action**:
  - Extract financial information
  - Validate against purchase orders
  - Forward to accounting department
  - Update financial tracking systems
- **Output**: Processed financial documents with extracted data

### Requirements

#### Functional Requirements
- **Email Provider Integration**: Must work with Gmail, Outlook, and Exchange
- **Natural Language Processing**: Understand context, tone, and intent
- **Multi-language Support**: Handle emails in English, Spanish, and French
- **Template Management**: Maintain and use response templates
- **Learning Capability**: Improve classifications based on user feedback
- **Batch Processing**: Handle multiple emails efficiently
- **Real-time Processing**: Process emails within 30 seconds of receipt

#### Integration Requirements
- **Calendar Systems**: Google Calendar, Outlook Calendar
- **Task Management**: Asana, Trello, Monday.com
- **CRM Systems**: Salesforce, HubSpot
- **Document Storage**: Google Drive, SharePoint
- **Communication Tools**: Slack, Microsoft Teams
- **Financial Systems**: QuickBooks, Xero

#### Performance Requirements
- **Response Time**: < 30 seconds for email processing
- **Accuracy**: 95% accuracy in email classification
- **Availability**: 99.9% uptime during business hours
- **Throughput**: Handle 1000+ emails per hour
- **Scalability**: Support multiple users and organizations

#### Security Requirements
- **Data Privacy**: Comply with GDPR and privacy regulations
- **Email Security**: Secure handling of sensitive information
- **Authentication**: Multi-factor authentication support
- **Audit Trail**: Complete logging of all actions
- **Encryption**: End-to-end encryption for sensitive data

#### User Experience Requirements
- **Dashboard Interface**: Web-based control panel
- **Mobile Access**: Mobile app for monitoring and approvals
- **Notification System**: Real-time alerts for important emails
- **Override Capability**: Easy manual override of automated decisions
- **Feedback System**: Simple way to provide learning feedback

### Success Metrics
- **Time Savings**: Measure reduction in manual email processing time
- **Response Rate**: Track improvement in email response rates
- **User Satisfaction**: Regular surveys and feedback collection
- **Accuracy Metrics**: Monitor classification and response quality
- **Error Rate**: Track and minimize processing errors

### Constraints and Limitations
- **Regulatory Compliance**: Must comply with email retention policies
- **Privacy Laws**: Respect data privacy and consent requirements
- **Integration Limits**: Work within API rate limits of external services
- **Language Barriers**: Initially limited to specified languages
- **Complex Decisions**: Escalate complex or sensitive emails to humans
- **Learning Period**: Initial setup requires training period with user feedback

### Edge Cases and Special Scenarios
- **Urgent After-Hours Emails**: Handle emergency communications outside business hours
- **Multi-Recipient Emails**: Manage emails with multiple recipients and different response needs
- **Attachment Processing**: Handle emails with various attachment types
- **Email Chains**: Maintain context in ongoing email conversations
- **Out-of-Office Scenarios**: Manage automated responses during user absence
- **Conflicting Priorities**: Handle emails that fall into multiple categories
- **System Downtime**: Graceful handling when integrated systems are unavailable

### Implementation Phases
1. **Phase 1**: Basic email classification and simple responses
2. **Phase 2**: Calendar integration and meeting scheduling
3. **Phase 3**: Advanced NLP and learning capabilities
4. **Phase 4**: Full integration suite and mobile interface
5. **Phase 5**: Advanced analytics and reporting features

---

**Expected Output**: Generate a complete CLAUDE.md file that implements this Email Management Agent workflow using the framework and patterns described above. Include all necessary components: project structure, stage execution logic, progress tracking, validation framework, and user documentation.