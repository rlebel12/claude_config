---
description: Execute project implementation with primary instance doing implementation and automatic validation for iterative refinement.
# model: opus
---

# Execute Command

Execute project implementation where you (primary Claude instance) handle implementation directly while leveraging specialized validators for iterative quality improvement.

## Process

### Project Setup

Start by prompting the user for:

1. **Problem Statement**: What specific problem or requirement needs to be addressed?
2. **Technical Plan**: The implementation plan (may be a document path, or ask user to provide/create one)

### Implementation Workflow

For each phase in the technical plan:

#### 1. **Research Phase** (when needed)
- **Delegate to code-research-specialist** when you need to:
  - Understand existing codebase architecture before implementation
  - Search for specific patterns, functions, or implementations
  - Explore unfamiliar code areas or dependencies
  - Understand integration points between systems
- Use research findings to inform your implementation approach

#### 2. **Implementation Phase**
- **You implement** the code directly, focusing on functional correctness
- Follow the language guidelines in CLAUDE.md for basic patterns

#### 3. **Sequential Refinement**
- **Automatically invoke appropriate language reviewer** based on code implemented
- **Apply reviewer feedback**:
  - Critical issues: Always fix
  - Important issues: Usually fix
  - Optional issues: Apply selectively based on value
- **Format code** using appropriate formatters

#### 4. **Parallel Validation**
- **Run in parallel** for efficiency:
  - Execute test suites
  - Run linters and static analysis
  - Any other validation tools
- Verify all parallel validation passes before proceeding

#### 5. **Final Review** (for complex projects)
- **Delegate to product-evaluator** for end-to-end validation against requirements
- If issues found, return to implementation phase for fixes

#### 6. **Phase Completion**
- Update planning document with completed work
- Commit clean, production-ready code
- Proceed to next phase or project completion

## Key Principles

- **Primary Implementation**: You handle all code implementation directly
- **Automatic Validation**: Always invoke language validators after implementation
- **Iterative Refinement**: Apply validator feedback before proceeding
- **Selective Fixes**: Prioritize critical and important improvements
- **Clean Commits**: Only commit refined, production-ready code

## Success Criteria

Project execution is complete when:

- All technical plan phases implemented with validation feedback applied
- All tests passing consistently  
- Code meets language-specific quality standards
- Product functionality validated against requirements
- Planning document reflects 100% completion

## Adaptive Complexity

### Simple Tasks (bug fixes, minor features)
- Implement → Validate → Test → Complete
- Skip complex orchestration for straightforward changes

### Complex Projects (major features, architecture changes)  
- Full phase-by-phase approach with comprehensive validation
- Research phase for unfamiliar areas
- Final product evaluation against requirements

Your role is to maintain context and conversational flow while ensuring code quality through automatic validation and selective refinement based on specialized feedback.
