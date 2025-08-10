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

1. **Implementation Phase**
   - Delegate to `plan-implementation-engineer` agent with the current phase details
   - Provide clear scope and deliverables for this specific phase
   - Ensure agent understands they should not proceed beyond the defined phase

2. **Validation Phase**
   - Delegate to `code-validator` agent to:
     - Run all tests and ensure they pass
     - Execute linters and static analysis (zero violations required)
     - Format code according to project standards
     - Update planning document marking phase complete
     - Commit clean code changes (exclude debug/temp files)

3. **Review Phase**
   - Once validation passes, delegate to appropriate code review agent:
     - For Go projects: use `go-code-reviewer` agent
     - For Python projects: use `python-code-reviewer` agent
     - Agent performs comprehensive code quality review
   - If review identifies issues requiring code changes:
     - Delegate back to `plan-implementation-engineer` to address review feedback
     - Return to validation phase, then review phase again
   - Repeat implementation → validation → review cycle until review approval

4. **Issue Resolution Cycle** (if validation fails)
   - If validation identifies bugs or test failures:
     - Delegate to `debugger` agent to diagnose issues
     - Delegate back to `plan-implementation-engineer` to apply fixes
     - Return to validation phase
   - Repeat until validation passes

5. **Phase Completion**
   - Only proceed to next phase after successful validation AND review approval
   - Ensure planning document accurately reflects completed work

### Final Validation

After all phases complete:
- Delegate to `product-evaluator` agent for comprehensive requirements validation
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

## Command Usage

```
Execute project implementation following established technical plan with iterative validation and quality control.
```
