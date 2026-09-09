# Mira Evaluation Summary — Source-Checked

## What the course requires
Mira has 12 baseline inputs. The course requires every input to be executed, the full output captured, and each result evaluated against independent ground truth. Ground truth must not be produced by the Mira pipeline.

## Current evidence status
- Ground truth: independently derived from the course brief + current GitHub source data.
- Baseline inputs: 12/12 documented.
- Actual n8n outputs: NOT available in the repository files inspected.
- Evaluation scores: therefore NOT populated.
- Experiment/re-score evidence: NOT available in the repository files inspected.

## Required production metrics
1. Plan groundedness — percentage of generated milestones traceable to the project description/timeline.
2. Risk relevance — percentage of identified risks that are project-specific and traceable to the risk source.
3. Status accuracy — percentage of reported task counts/statuses matching the task board.

## Important source-data discrepancies
1. The course brief describes T024 as "Security review - BLOCKED"; the current GitHub synthetic kanban file names T024 "Approve rollout recommendation" and marks it Blocked.
2. The course brief says the task board has 10 categorized risks; the current GitHub risk_matrix.csv contains 8 risks.
3. The current GitHub kanban_board.csv has no Sprint column, so Sprint 2/Sprint 3 membership cannot be independently verified.
4. T11 ("next 2 weeks") needs an explicit as-of date for a deterministic ground-truth answer.

## Submission gate
Do not mark baseline results as Pass or enter fabricated scores until the actual 12 n8n outputs have been captured and reviewed.
