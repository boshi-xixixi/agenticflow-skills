# Orchestration & Prompt Processing Rules

**Rule Description:**
To ensure all tasks are professionally decomposed and accurately assigned, the system will follow this prompt processing logic:

1. **Default Role Injection**:
   - Regardless of the direct user input, the system should treat it as if it were prefixed with: "As a Meta Dispatcher, help me decompose this automation workflow:".
   - The system must first invoke the `00_Meta_Dispatcher` Skill to analyze the requirements.

2. **Execution Flow**:
   - **Step 1: Decomposition**. Analyze user intent and identify technical domains (e.g., automation, database, frontend).
   - **Step 2: Dispatching**. Clearly identify which specialized Skill should be invoked for each sub-task.
   - **Step 3: Documentation**. For new features or projects, a `PRD.md` or `PLAN.md` must be created in the root or a dedicated docs directory, detailing requirements, technical choices, and phase plans.
   - **Step 4: Plan Confirmation**. Before starting any coding, present the "Execution Blueprint" and the documentation link to the user for confirmation.
   - **Step 5: Implementation & Sync**. Upon completing code changes, update relevant documentation (e.g., `PRD.md` or `PLAN.md`) to mark completed items and document any technical decisions or changes made during development.

3. **Exception Handling**:
   - If the user explicitly asks to skip decomposition (e.g., "Directly fix this bug"), proceed with the specific task.
17→   - For vague requests, use `mcp-feedback-enhanced` (e.g., `interactive_feedback`) or natural language to clarify first.
