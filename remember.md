# sopClaude Project - Quick Reference

## What This Project Does

### 🎯 Main Purpose
This project is a **meta-system for creating workflow automation systems**. It has two main components:

1. **Email Management Agent SOP Generator** - A working example that generates complete Standard Operating Procedures for email automation
2. **Universal Workflow Generator** - A meta-prompt system that can create CLAUDE.md files for ANY workflow-based process

### 🧠 The Big Idea
Instead of manually creating workflow documentation and automation systems, this project:
- Analyzes workflow descriptions
- Automatically generates complete CLAUDE.md systems
- Creates stage-by-stage execution logic
- Includes progress tracking and validation
- Provides command-line interfaces for execution

## Key Files & Components

### 📁 Current System (Email Management Agent)
- **`CLAUDE.md`** - Complete integrated system for SOP generation (3 stages: Define → Design → Build)
- **`input/use-case.md`** - Email management agent requirements and examples
- **`output/`** - Generated artifacts organized by stage
- **`tmp/`** - Progress tracking files (JSON format)
- **`claude-sop`** - Command to run the workflow

### 🔧 Meta-System (Workflow Generator)
- **`prompt.md`** - Meta-prompt that can generate CLAUDE.md files for any workflow
- Contains comprehensive framework for workflow analysis
- Includes templates for stage creation, progress tracking, and validation
- Uses Email Management Agent as example/reference

## How to Use

### 🚀 Using the Current System (Email Management)
```bash
# Run the complete email SOP generation
./claude-sop

# Start fresh (clear previous outputs)
./claude-sop --fresh

# Start from specific stage
./claude-sop --stage 2

# Run with review at the end
./claude-sop --review
```

### 🏗️ Creating New Workflow Systems
1. **Open Claude Code in plan mode**
2. **Copy the entire `prompt.md` content** as your prompt
3. **Replace the Email Management Agent section** with your workflow description
4. **Let Claude generate** a complete CLAUDE.md system for your workflow
5. **Implement the generated system** in a new directory

## Current State & What's Working

### ✅ Completed
- **Stage 1 Complete**: Agent scope definition and scenarios (6 scenarios created)
- **Stage 2 In Progress**: SOP design with main workflow and decision trees
- **Meta-prompt System**: Fully functional prompt.md for generating new workflow systems

### 📂 Generated Outputs (Email Management)
- `output/stage1-define/agent-scope.md` - Clear agent boundaries and capabilities
- `output/stage1-define/scenarios/` - 6 detailed scenarios with success criteria
- `output/stage2-design/sop/main-workflow.md` - Complete 6-phase workflow
- `output/stage2-design/sop/decision-trees.md` - Decision logic and flow charts

### 🎯 Quality Scores
- Stage 1 Review: 92/100 (Excellent)
- All scenarios rated 88-96/100
- System ready for Stage 3 (Implementation)

## Key Concepts

### 🔄 Three-Stage Pattern - The "Why" Behind Each Stage

#### **Stage 1: DEFINE** - Scope, scenarios, requirements analysis
**🎯 Why this stage exists**: Before building anything, you need crystal-clear understanding of WHAT you're building and WHO it's for.

**Specific Steps & Reasoning**:
1. **Read Use Case** 
   - *Why*: Parse and understand the raw requirements to establish foundation
   - *Purpose*: Convert user language into system understanding
   
2. **Generate Agent Scope** 
   - *Why*: Set clear boundaries on what the system WILL and WON'T do
   - *Purpose*: Prevent scope creep and unrealistic expectations
   - *Outputs*: Clear capabilities, limitations, success criteria
   
3. **Create Scenarios** 
   - *Why*: Convert abstract requirements into concrete, testable examples
   - *Purpose*: Ensure system handles real-world situations effectively
   - *Outputs*: 5-10 detailed scenarios with inputs, actions, and expected outputs
   
4. **Stage 1 Review** 
   - *Why*: Quality gate to catch issues before they become expensive to fix
   - *Purpose*: Validate completeness and feasibility before proceeding

#### **Stage 2: DESIGN** - Workflows, procedures, decision trees
**🎯 Why this stage exists**: Transform the "WHAT" from Stage 1 into the "HOW" - detailed procedures that can be followed.

**Specific Steps & Reasoning**:
1. **Create Main Workflow** 
   - *Why*: Define the step-by-step process for handling core functionality
   - *Purpose*: Ensure consistent, repeatable operations
   - *Outputs*: Detailed 6-phase workflow with timing and SLAs
   
2. **Generate Decision Trees** 
   - *Why*: Handle complex logic and branching scenarios systematically
   - *Purpose*: Ensure consistent decision-making across all cases
   - *Outputs*: Visual flowcharts and logic paths for edge cases
   
3. **Design Error Handling** 
   - *Why*: Plan for when things go wrong (they always do)
   - *Purpose*: Graceful degradation and recovery procedures
   - *Outputs*: Error procedures, escalation paths, fallback mechanisms
   
4. **Define Integrations** 
   - *Why*: Specify exactly how to connect with external systems
   - *Purpose*: Ensure seamless data flow and system interoperability
   - *Outputs*: API specifications, data formats, connection requirements
   
5. **Optimize SOP** 
   - *Why*: Combine all design elements into a streamlined, actionable document
   - *Purpose*: Create the "single source of truth" for implementation
   - *Outputs*: Consolidated, optimized Standard Operating Procedure
   
6. **Stage 2 Review** 
   - *Why*: Validate that procedures are complete, logical, and implementable
   - *Purpose*: Catch design flaws before expensive implementation phase

#### **Stage 3: BUILD** - Implementation code, tests, deployment guides
**🎯 Why this stage exists**: Convert the "HOW" from Stage 2 into working, deployable software and systems.

**Specific Steps & Reasoning**:
1. **Create System Architecture** 
   - *Why*: Define technical structure before writing code
   - *Purpose*: Ensure scalable, maintainable implementation
   - *Outputs*: Technical specifications, component design, technology choices
   
2. **Generate System Prompt** 
   - *Why*: Create the "brain" instructions for AI components
   - *Purpose*: Ensure AI behavior aligns with designed procedures
   - *Outputs*: Core agent instructions based on optimized SOP
   
3. **Create Task Prompts** 
   - *Why*: Provide specific instructions for different scenario types
   - *Purpose*: Handle specialized cases with appropriate context
   - *Outputs*: Scenario-specific prompt files for different situations
   
4. **Generate Core Implementation** 
   - *Why*: Create the actual working code that executes workflows
   - *Purpose*: Transform procedures into executable software
   - *Outputs*: Main agent class with workflow logic (Python/other languages)
   
5. **Create Integration Code** 
   - *Why*: Build connectors to external systems identified in Stage 2
   - *Purpose*: Enable real-world functionality beyond isolated processing
   - *Outputs*: API connectors, data transformers, system interfaces
   
6. **Generate Test Suite** 
   - *Why*: Verify that implementation actually works as designed
   - *Purpose*: Catch bugs and ensure quality before deployment
   - *Outputs*: Comprehensive test coverage for all scenarios
   
7. **Create Deployment Guide** 
   - *Why*: Enable others to successfully implement the system
   - *Purpose*: Bridge from development to production use
   - *Outputs*: Step-by-step production setup instructions
   
8. **Stage 3 Review** 
   - *Why*: Final quality gate before release
   - *Purpose*: Ensure everything is production-ready and well-documented

#### **🧠 The Logic of Sequential Stages**
- **Stage 1 → Stage 2**: Can't design procedures without clear requirements
- **Stage 2 → Stage 3**: Can't build software without detailed specifications  
- **Each Stage Review**: Prevents compounding errors and ensures quality
- **Progress Tracking**: Enables resumption if interrupted, maintains accountability

### 📊 Progress Tracking System
- JSON-based state management
- Task-level granularity
- Resume/restart capabilities
- Quality validation at each stage

### 🎛️ Command System
- Single command execution (`./claude-[workflow]`)
- Command-line options (--fresh, --stage, --review)
- Clear user feedback and error handling

## Example Use Cases for Meta-System

The `prompt.md` can generate CLAUDE.md systems for:

### 📋 Business Processes
- **Document Review Workflows** - Legal, compliance, technical reviews
- **Project Management** - Requirements → Design → Implementation → Delivery
- **Content Creation** - Research → Draft → Review → Publish
- **Quality Assurance** - Test planning → Execution → Reporting

### 🔧 Technical Processes
- **Software Development** - Requirements → Architecture → Code → Testing
- **Data Processing** - Collection → Cleaning → Analysis → Reporting
- **System Deployment** - Planning → Testing → Deployment → Monitoring

### 🏢 Administrative Workflows
- **Hiring Process** - Job posting → Screening → Interviews → Onboarding
- **Purchase Orders** - Request → Approval → Procurement → Delivery
- **Customer Onboarding** - Registration → Setup → Training → Support

## Quick Commands Reference

```bash
# Email Management System
./claude-sop --fresh              # Start completely fresh
./claude-sop --stage 2            # Resume from stage 2
./claude-sop --review             # Include quality review
./claude-clear                    # Clear all outputs

# Check progress
cat tmp/sop-progress.json         # View current state
cat tmp/stage1-tasks.json         # View stage 1 task status
```

## Troubleshooting

### ❌ Common Issues
- **Command not found**: Run `chmod +x claude-*` to make scripts executable
- **Missing input**: Ensure `input/use-case.md` exists with workflow description
- **Incomplete outputs**: Check for errors in terminal output
- **Poor quality**: Make input more detailed and specific

### 🔍 Debugging
- Check `tmp/` files for progress state
- Review generated files in `output/` directories
- Look for error messages in command output
- Verify input file format matches requirements

## Next Steps & Ideas

### 🚀 Immediate Opportunities
1. **Complete Stage 3** - Generate implementation code for email management
2. **Test Meta-System** - Create a new workflow system using prompt.md
3. **Add More Examples** - Document review, project management workflows
4. **Create Templates** - Common workflow patterns and structures

### 🎯 Advanced Features
- **Visual Workflow Designer** - GUI for creating workflow descriptions
- **Integration Marketplace** - Pre-built integrations for common tools
- **Analytics Dashboard** - Track workflow performance and optimization
- **Collaborative Features** - Multi-user workflow development

## Files to Remember

### 🔑 Critical Files
- **`CLAUDE.md`** - The brain of the current system
- **`prompt.md`** - Meta-prompt for creating new systems
- **`input/use-case.md`** - Current workflow definition
- **`tmp/sop-progress.json`** - Current execution state

### 📚 Documentation
- **`remember.md`** - This file (you're reading it!)
- **`output/*/review/*.md`** - Quality assessments for each stage
- **`output/stage1-define/agent-scope.md`** - System capabilities and boundaries

---

## 💡 Pro Tips

1. **Always use --fresh** when testing major changes
2. **Review stage outputs** before proceeding to next stage
3. **Customize prompts** in `prompts/` directory for specific needs
4. **Use the meta-system** to create workflows for your own processes
5. **Keep input descriptions detailed** for better output quality

**Remember**: This isn't just an email automation generator - it's a framework for creating ANY structured workflow automation system! 🚀