# Project Pulse dashboard implementation plan

## Goal

Build a lightweight static Project Pulse dashboard for Mona's team so contributors can quickly understand active projects, ownership, status, recent activity, priority, and short summary information in a clean, readable layout.

## Planned workstreams

### 1. Planning and alignment

- Confirm the expected output and file set: `app/index.html`, `app/styles.css`, `app/project-data.json`, and `.vscode/launch.json`.
- Define the dashboard's core information model and layout requirements.
- Establish the handoff between the Designer and Coder so visual decisions and code structure stay aligned.

### 2. Data and structure setup

- Define the project data format in `app/project-data.json` using a top-level `projects` array.
- Each project should include at least `name`, `owner`, `status`, `recentActivity`, and `priority`.
- Confirm the HTML structure in `app/index.html` will support project cards, badges, summary text, and a clear dashboard heading.

### 3. Visual design execution

- Use the Designer to guide layout, hierarchy, spacing, accessibility, and visual polish.
- Create a dashboard that reads as a real Project Pulse product view instead of a generic placeholder page.
- Ensure the page uses strong contrast, readable type, clear status treatment, and responsive behavior for contributor-friendly scanning.

### 4. Frontend implementation

- Use the Coder to implement the static dashboard files and wire the data source into the rendered project cards.
- Build semantically structured markup in `app/index.html` with CSS hooks that match `app/styles.css`.
- Keep the code simple, deterministic, and easy to validate.

### 5. Runtime launch support

- Define a VS Code launch configuration in `.vscode/launch.json` named `Run Project Pulse Dashboard`.
- Configure the launch target to serve the `app/` directory and open `index.html` so the dashboard loads directly instead of the directory listing.

## File assignments

- `app/index.html`
  - Owns the dashboard structure, title, project card layout, and semantic content.
  - Designer provides the layout and visual hierarchy; Coder implements the final markup.

- `app/styles.css`
  - Owns the dashboard styling, spacing, typography, card visuals, badges, and responsive behavior.
  - Designer drives the design system; Coder implements the CSS and class hooks.

- `app/project-data.json`
  - Owns the source project data used to populate the dashboard.
  - Coder implements the data structure and content; Planner confirms the required fields.

- `.vscode/launch.json`
  - Owns the local preview configuration for the app.
  - Coder creates the run configuration after the HTML and folder layout are confirmed.

## Designer responsibilities

The Designer is responsible for:

- project dashboard information hierarchy
- card layout and readability
- status styling and visual emphasis
- accessibility and contrast decisions
- responsive polish for a clean contributor-first dashboard
- making the first screen clearly look like Project Pulse

## Coder responsibilities

The Coder is responsible for:

- creating the static app files
- implementing the HTML structure and CSS application
- wiring project data into the dashboard view
- ensuring no broken references between files
- creating `.vscode/launch.json` so the project runs properly in VS Code

## Dependencies

- `app/project-data.json` must be defined before the dashboard cards can be rendered consistently.
- `app/index.html` depends on the final HTML structure and class names used in `app/styles.css`.
- `app/styles.css` depends on the HTML structure and CSS hook names selected by the Designer and agreed to by the Coder.
- `.vscode/launch.json` depends on the app being organized under `app/` with a valid `index.html` entry point.
- Validation depends on all three app files and the launch configuration being present and internally consistent.

## Parallel work decisions

- Parallel work is appropriate for the early phase when the Designer is defining the card and layout system while the Coder is preparing the data model in `app/project-data.json`.
- The HTML and CSS work should not be fully parallelized after the initial design direction is agreed; the class names and layout hooks must be matched to avoid drift.
- The launch configuration can be created in parallel with the final HTML/CSS pass once the `app/` structure and `index.html` entry point are confirmed.
- The Planner should keep the work sequence explicit so the Orchestrator can avoid overlapping file ownership in a way that creates merge conflicts or inconsistent structure.

## Validation expectations

The work is considered successful when:

- the dashboard opens from the VS Code launch configuration named `Run Project Pulse Dashboard`
- the browser loads `app/index.html` directly instead of a directory listing
- the page title and dashboard heading clearly show `Project Pulse`
- project cards render using data from `app/project-data.json`
- each card displays key project fields such as owner, status, recent activity, and priority
- status badges and priority styling are visually distinct and readable
- the page is responsive and retains usable spacing at smaller widths
- no broken asset references exist between `index.html`, `styles.css`, and `project-data.json`
- the final result reflects the Designer's UX goals and the Coder's implementation quality within the expected static app scope

## Recommended execution sequence

1. Planner confirms scope and file ownership.
2. Designer defines the dashboard structure and visual treatment.
3. Coder creates the data file and static app files.
4. Coder adds `.vscode/launch.json` for preview.
5. Orchestrator validates the final result and reports completion.
