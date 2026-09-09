# ADR-001 — Router Orchestration

## Status
Accepted

## Context
Mira must support multiple project-intelligence capabilities while keeping responsibilities explicit and evaluations traceable.

## Decision
Use a router-based multi-agent workflow. A routing component classifies the request and sends it to the relevant specialist agent.

### Specialist responsibilities
- **Project Plan Agent** — project-plan generation.
- **Risk Assessment Agent** — risk assessment.
- **Weekly Status Agent** — weekly status reporting.

The architecture should remain within the course requirement of 3–5 agents and should document any additional utility/router agent.

## Rationale
- Clear separation of concerns.
- Easier agent-level evaluation and ground truth.
- Lower risk of mixing incompatible response formats.
- Easier observability and debugging by capability.

## Trade-offs
A router adds orchestration complexity and can misroute ambiguous requests. Routing should therefore be tested independently and fallback behavior documented.

## Verification
Confirm the exported workflow and live n8n canvas match this decision before submission.
