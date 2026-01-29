# Product Requirements Document (PRD) - TODO App Upgrade (MVP and Post‑MVP)

## 1. Overview

We are upgrading the basic TODO app (currently supporting only title and completed) to include due dates, simple priorities, and basic filters so users can better organize tasks while keeping the implementation lean and teachable. The MVP will remain frontend-only with local storage and no backend changes. Post‑MVP adds visual overdue highlighting and deterministic sorting.

---

## 2. MVP Scope

- Add `dueDate` (optional), format ISO `YYYY-MM-DD`; invalid values ignored (treated as absent).
- Add `priority` enum: `P1 | P2 | P3` with default `P3`.
- Add filters: **All**, **Today**, **Overdue**.
  - **All** view includes completed tasks.
  - **Today** and **Overdue** show only incomplete tasks.
- Keep storage local only (no backend or external storage).
- `title` is required; basic validation present.

---

## 3. Post-MVP Scope

- Visually highlight overdue tasks so they stand out (e.g., red treatment).
- Sorting rules: overdue first → priority (P1→P3) → due date ascending → undated last.

---

## 4. Out of Scope

- Notifications.
- Recurring tasks.
- Multi-user features.
- Keyboard navigation / advanced accessibility features.
- Backend changes and external storage (MVP remains local-only).
