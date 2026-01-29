# MVP

- Epic: Task Due Date
  - Story: Add due date field to task
    - Acceptance Criteria:
      - A due date input is available when creating and editing a task.
      - The input accepts ISO format `YYYY-MM-DD`.
      - The due date is optional; tasks can be saved without a due date.
      - When present and valid, the due date is persisted in local storage with the task.
  - Story: Validate ISO YYYY-MM-DD input
    - Acceptance Criteria:
      - Non-ISO or invalid dates (e.g., `2025-13-40`) are treated as invalid.
      - Invalid due dates do not block saving the task; they are ignored (treated as absent).
      - The app remains stable when invalid input is entered (no crashes).
  - Story: Ignore invalid due dates
    - Acceptance Criteria:
      - If an invalid date is entered, no `dueDate` value is stored for the task.
      - Tasks with invalid/absent `dueDate` are excluded from Today and Overdue filters.
      - Other task fields are saved as expected.

- Epic: Task Priority
  - Story: Add priority enum P1|P2|P3
    - Acceptance Criteria:
      - The priority field presents options `P1`, `P2`, `P3` only.
      - Selected priority is persisted with the task in local storage.
      - Creating and editing tasks allows changing the priority.
  - Story: Set default priority to P3
    - Acceptance Criteria:
      - If the user does not select a priority, the task is saved with `P3`.
      - Existing tasks without an explicit priority load/display as `P3`.
  - Story: Display priority in task list
    - Acceptance Criteria:
      - Each task shows its priority label (`P1`, `P2`, or `P3`) in the list view.
      - Display does not require color-coding in MVP; text label is sufficient.

- Epic: Filtering Views
  - Story: Implement All view
    - Acceptance Criteria:
      - All tasks are visible, including completed and incomplete.
      - Tasks with and without due dates appear in this view.
  - Story: Implement Today view for incomplete tasks
    - Acceptance Criteria:
      - Shows tasks with a valid `dueDate` equal to the current calendar date.
      - Includes only incomplete tasks; completed tasks are excluded.
      - Tasks without a valid `dueDate` do not appear.
  - Story: Implement Overdue view for incomplete tasks
    - Acceptance Criteria:
      - Shows tasks with a valid `dueDate` earlier than today.
      - Includes only incomplete tasks; completed tasks are excluded.
      - Tasks without a valid `dueDate` do not appear.

- Epic: Local Persistence
  - Story: Persist tasks in local storage
    - Acceptance Criteria:
      - Creating, editing, completing, and deleting tasks updates data stored in browser local storage.
      - Persisted fields include: `title`, `priority`, `dueDate` (when valid), and completion status.
      - Persistence operations succeed without requiring a backend.
  - Story: Load tasks from local storage on startup
    - Acceptance Criteria:
      - On app load, tasks are read from local storage and rendered.
      - If no tasks are stored, the app initializes with an empty list without errors.

- Epic: Basic Validation
  - Story: Require title on task creation
    - Acceptance Criteria:
      - A task cannot be saved without a non-empty `title`.
      - When `title` is present, it is persisted and displayed in lists and details.

# Post-MVP

- Epic: Overdue Highlighting
  - Story: Visually highlight overdue tasks in list
    - Acceptance Criteria:
      - Incomplete tasks with `dueDate` earlier than today are visually distinguished (e.g., red treatment) from other tasks.
      - Highlighting applies consistently across views that display overdue tasks.

- Epic: Task Sorting
  - Story: Sort overdue tasks first
    - Acceptance Criteria:
      - Task lists order overdue incomplete tasks before all other tasks.
  - Story: Sort by priority P1→P3
    - Acceptance Criteria:
      - Within the same overdue/non-overdue grouping, tasks are ordered by priority: `P1` before `P2` before `P3`.
  - Story: Sort by due date ascending
    - Acceptance Criteria:
      - Within the same priority, tasks with earlier `dueDate` appear before later `dueDate`.
  - Story: Place undated tasks last
    - Acceptance Criteria:
      - Tasks without a `dueDate` appear after all tasks with a valid `dueDate`.
      - Ordering of undated tasks among themselves is unspecified in PRD and may default to creation/display order.
