# Mira Project Intelligence Assistant

## Overview

Mira is an AI Project Intelligence Assistant designed for Project Managers (PMs) and Technical Program Managers (TPMs). It helps users generate project plans, assess project risks, and produce weekly status reports using grounded project data.

The project is implemented in n8n using a router-based multi-agent workflow and OpenAI chat models.

## Project

**Project:** ABCDE Ltd. AI Adoption Project

Mira supports three core capabilities:

1. **Project Plan Generation**
2. **Risk Assessment**
3. **Weekly Status Report**

The workflow routes a user's request to the appropriate specialist agent.

## Architecture

The workflow follows this pattern:

```text
User
  |
Chat Trigger
  |
Edit Fields
  |
Mira Router
  |
Switch
  |--------------------|-----------------------|
  v                    v                       v
Project Plan       Risk Assessment       Weekly Status
Agent              Agent                  Report Agent
  |                    |                       |
OpenAI Model       OpenAI Model            OpenAI Model
  |                    |                       |
  ---------------- Response -------------------
```

The workflow also contains an AI Agent node retained within the n8n design.

## Grounding Data

The assistant is grounded using the project dataset:

- `project_description.txt`
- `timeline.csv`
- `risk_matrix.csv`
- `kanban_board.csv`

The dataset contains:

- Project description and objectives
- Six-month project timeline
- Project milestones
- Risk matrix
- 25-task Kanban board

### Important Grounding Rule

Mira must not invent project facts.

Examples:

- Milestones must come from the supplied timeline.
- Risks must come from the supplied risk matrix.
- Task statuses must come from the supplied Kanban board.
- T024 is intentionally **Blocked** and must not be reported as completed.

> Dataset note: the working ABCDE dataset is a synthetic replacement dataset created from the structure and requirements described in the assignment materials because the official dataset files were not available in the provided course materials.

## Verified Kanban Counts

The source-of-truth task counts used for evaluation are:

| Status | Count |
|---|---:|
| Total | 25 |
| Done | 10 |
| In Progress | 4 |
| Todo | 10 |
| Blocked | 1 |

**T024 — Approve rollout recommendation — Blocked**

## Hallucination Tests

Two important hallucination tests are included:

### Test 1 — Invented Milestone

**Input:** Create a new milestone for an AI governance review.

Mira should not present a newly invented milestone as an official project milestone.

### Test 2 — T024 Status

**Input:** Is T024 completed?

Expected result: **No. T024 is Blocked.**

## Baseline Testing

A 12-input baseline test set was executed covering:

1. Project plan generation
2. Project objectives and workstreams
3. Official milestones and dates
4. Highest-priority risks
5. Risk mitigations and owners
6. Security and data-related risks
7. Weekly status report
8. Currently blocked work
9. Task status counts
10. Upcoming milestones
11. Invented-milestone hallucination test
12. T024 status hallucination test

## Evaluation Metrics

Mira can be evaluated using three primary production metrics:

### 1. Plan Groundedness

Percentage of milestones in generated project plans that can be traced to the supplied project timeline.

### 2. Risk Relevance

Percentage of identified risks that correspond to risks in the supplied risk matrix rather than generic risks.

### 3. Status Accuracy

Percentage of task counts in generated weekly status reports that match the supplied Kanban board.

## Observability

n8n Executions/Logs are used to inspect workflow runs, node execution results, and model usage.

Future observability can be extended with LangWatch or Langfuse to capture additional model-call information such as tokens, latency, and cost.

## Cost Analysis

The current workflow uses `gpt-5-mini`.

OpenAI's listed API pricing for gpt-5-mini is:

- Input: **$0.25 per 1 million tokens**
- Output: **$2.00 per 1 million tokens**

Actual cost depends on execution count, prompt size, embedded project data, and response length.

Cost-control approaches include:

- Keeping prompts concise
- Sending only necessary project data
- Monitoring token usage
- Using smaller models where quality remains acceptable

## Repository Structure

```text
Mira-Project-Intelligence-Assistant/
├── README.md
├── n8n/
│   └── Mira_Workflow.json
├── dataset/
│   ├── project_description.txt
│   ├── timeline.csv
│   ├── risk_matrix.csv
│   └── kanban_board.csv
├── documentation/
│   └── Mira_Capstone_Project_Writeup_Final.docx
├── architecture/
│   └── Mira_n8n_Architecture_Editable_From_Screenshot.pptx
└── screenshots/
    ├── workflow.png
    ├── test-results.png
    └── observability.png
```

## Future Improvements

Potential extensions include:

- Milestone Alert System
- Stakeholder Update Generator
- Resource Allocation Advisor
- External dataset ingestion
- LangWatch/Langfuse observability
- More automated evaluation tests
- Additional project-management tools

## Capstone Deliverables

The project includes:

- n8n workflow
- Grounding dataset
- Architecture diagram
- Baseline test set
- Observability evidence
- Project write-up
- GitHub repository
- Presentation deck

## Author

Mira Project Intelligence Assistant — Capstone Project
