---
description: Orchestrates iterative project execution using specialized subagents with built-in validation and quality control.
# model: opus
---

# Execute Command

Orchestrates iterative project execution using specialized subagents with built-in validation and quality control.

## Process

Use the following process to guide project execution.

### Beginning the Planning Process

Start by prompting the user for:

1. **Problem Statement**: What specific problem or requirement needs to be addressed?
2. **Technical Plan**: The implementation plan (may be a document path, or ask user to provide/create one)

### Iterative Execution Cycle

For each phase in the technical plan:

0. **Research and Exploration Phase** (when needed)

   - **Always delegate to codebase exploration agent when**:
     - Need to understand existing codebase architecture before implementation
     - Searching for specific patterns, functions, or implementations
     - Exploring unfamiliar code areas or dependencies
     - Understanding integration points between systems
   - Provide specific research objectives and expected deliverables
   - Use research findings to inform implementation approach

1. **Implementation Phase**

   - Delegate to plan execution agent with the current phase details
   - Provide clear scope and deliverables for this specific phase
   - Ensure agent understands they should not proceed beyond the defined phase
   - **If implementation requires code exploration**: delegate to exploration agent first

2. **Validation Phase**

   - Delegate to testing and quality assurance agent to:
     - Run all tests and ensure they pass
     - Execute linters and static analysis (zero violations required)
     - Format code according to project standards
     - Update planning document marking phase complete
     - Commit clean code changes (exclude debug/temp files)

3. **Review Phase**

   - **Multi-area projects**: Delegate to multiple specialized reviewers in parallel:
     - Frontend changes: delegate to appropriate reviewer for frontend tech stack
     - Backend changes: delegate to language-specific code reviewer
     - Database changes: include in backend review with schema focus
     - API changes: coordinate reviews across frontend/backend boundaries
   - **Single-area projects**: Delegate to appropriate code review agent:
     - For Go projects: use Go-specialized code reviewer
     - For Python projects: use Python-specialized code reviewer
   - Agent performs comprehensive code quality review
   - **Consolidate feedback** from multiple reviewers when applicable
   - If review identifies issues requiring code changes:
     - Delegate back to plan execution agent to address review feedback
     - Return to validation phase, then review phase again
   - Repeat implementation → validation → review cycle until review approval

4. **Issue Resolution Cycle** (if validation fails)

   - If validation identifies bugs or test failures:
     - Delegate to debugging specialist agent to diagnose issues
     - Delegate back to plan execution agent to apply fixes
     - Return to validation phase
   - Repeat until validation passes

5. **Phase Completion**
   - Only proceed to next phase after successful validation AND review approval
   - Ensure planning document accurately reflects completed work

### Final Validation

After all phases complete:

- Delegate to product quality assurance agent for comprehensive requirements validation
- Agent will test against original problem statement and requirements
- If evaluation fails, return to appropriate implementation phase for corrections

### Success Criteria

Project execution is complete when:

- All technical plan phases implemented, validated, and reviewed
- All tests passing consistently
- Code quality standards met through rigorous review process
- Product evaluation confirms all requirements satisfied
- Planning document reflects 100% completion

## Key Principles

- **Phase-by-Phase**: Never implement multiple phases simultaneously
- **Quality Gates**: Validation and review must both pass before advancing
- **Review Standards**: Code must meet professional quality standards through expert review
- **Documentation**: Keep planning document updated throughout
- **Clean Commits**: Only commit production-ready code
- **User Requirements**: Final validation against original problem statement

## Delegation Strategy

### When to Delegate Research

- **Always delegate** when you need to explore or understand existing code
- Use codebase exploration agent for research and understanding
- Delegate research **before** implementation when working with unfamiliar systems
- Provide specific search criteria and research objectives

### Multi-Area Review Delegation

- **Identify project scope** early: frontend, backend, database, API, infrastructure
- **Delegate to multiple reviewers** when changes span multiple areas
- Run reviews **in parallel** for efficiency
- **Consolidate feedback** from all reviewers before proceeding
- Ensure **cross-boundary consistency** (e.g., API contracts match frontend usage)

### Agent Selection by Function

- **Codebase exploration**: Use research specialist for understanding existing code
- **Plan execution**: Use implementation specialist for focused development
- **Quality assurance**: Use testing specialist for validation and standards
- **Code review**: Use language-specific reviewers (Go specialist for Go, Python specialist for Python, etc.)
- **Issue diagnosis**: Use debugging specialist for problem resolution
- **Product validation**: Use QA specialist for requirements verification

## Command Usage

```
Execute project implementation following established technical plan with iterative validation and quality control.
```
