# Agent team

For Mona's Project Pulse dashboard, I will use a four-agent custom team defined under the repository's agent folder and orchestrated through GitHub Copilot CLI in a Codespace.

## Custom agents

- Planner — Model: Claude Opus 4.7 (copilot)
  - Responsibility: researches the repo, reads relevant docs and code, identifies edge cases and dependencies, and produces an implementation plan with ordered steps, file assignments, and validation expectations.
  - Definition: .github/agents/planner.agent.md

- Orchestrator — Model: Claude Opus 4.7 (copilot)
  - Responsibility: coordinates the work across specialist agents, breaks the request into phases, assigns file scopes, runs tasks in parallel where safe, and verifies the integrated result before reporting back.
  - Definition: .github/agents/orchestrator.agent.md

- Coder — Model: GPT-5.5 (copilot)
  - Responsibility: implements the app logic and fixes bugs within the file scope assigned by the Orchestrator, and creates any required runnable app support such as a launch configuration for the Project Pulse dashboard.
  - Definition: .github/agents/coder.agent.md

- Designer — Model: Gemini 3.1 Pro (copilot)
  - Responsibility: focuses on the dashboard experience, including UX, accessibility, information hierarchy, responsive layout, and visual polish so the first view clearly reads as a Project Pulse frontend.
  - Definition: .github/agents/designer.agent.md

## Workflow note

GitHub Copilot CLI in a Codespace will orchestrate the project by having the Orchestrator delegate work to the Planner, Designer, and Coder in a structured, phase-based sequence while keeping file ownership clear and avoiding overlap.
