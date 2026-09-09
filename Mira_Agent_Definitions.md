# Mira Agent Definitions

## 1. Router Agent
**Purpose:** Identify the user's requested Mira capability and route to the correct specialist.

**Inputs:** User request and grounded project context.

**Outputs:** Selected capability/route.

**Constraints:** Do not answer as a specialist when routing is required; use a documented fallback for ambiguous requests.

## 2. Project Plan Agent
**Purpose:** Generate a project plan grounded in project description, timeline, phases, milestones, and task context.

**Inputs:** Project context + routed request.

**Outputs:** Structured project plan.

**Evaluation focus:** Plan Groundedness, completeness, format compliance.

## 3. Risk Assessment Agent
**Purpose:** Identify and prioritize relevant risks from the supplied risk register/context.

**Inputs:** Risk data + project context + routed request.

**Outputs:** Structured risk assessment with evidence/reasoning tied to source facts.

**Evaluation focus:** Risk Relevance, groundedness, completeness.

## 4. Weekly Status Agent
**Purpose:** Produce a weekly project status report using timeline and Kanban evidence.

**Inputs:** Timeline + Kanban + project context.

**Outputs:** Structured weekly status report including blockers and progress.

**Evaluation focus:** Status Accuracy, groundedness, completeness.

## Agent contract principle
Each specialist should have its own independently reviewed ground-truth facts and scoring criteria. Production workflow outputs must never be used as the ground truth.
