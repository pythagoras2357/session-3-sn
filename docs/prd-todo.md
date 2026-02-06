# Product Requirements Document (PRD) - TODO App Upgrade

## 1. Overview

We are upgrading the basic TODO app to support due dates, priorities, and filters so users can better organize tasks. The current app only supports task title and completed status. This enhancement will add essential task management features while keeping the implementation simple and teachable, with no backend changes required. All data will remain in local storage.

---

## 2. MVP Scope

- **Due Date Field**: Add an optional `dueDate` field to each task
  - Format: ISO `YYYY-MM-DD`
  - Optional field (tasks can exist without due dates)
  - Invalid date values should be ignored (treated as absent)
  
- **Priority Field**: Add a `priority` field to each task
  - Values: `"P1"` (highest), `"P2"` (medium), `"P3"` (lowest)
  - Default value: `"P3"`
  - Enum constraint enforced
  
- **Filter Tabs**: Implement three filter views
  - **All**: Display all tasks (including completed)
  - **Today**: Display incomplete tasks due today
  - **Overdue**: Display incomplete tasks past their due date
  
- **Data Model Validation**:
  - `title`: Required field
  - `priority`: Required, must be one of `"P1" | "P2" | "P3"`, defaults to `"P3"`
  - `dueDate`: Optional, must be valid ISO `YYYY-MM-DD` format when present
  - `completed`: Boolean field (existing)
  
- **Storage**: Continue using local storage only (no backend or external storage integration)

---

## 3. Post-MVP Scope

- **Visual Overdue Highlighting**: Overdue tasks should be visually highlighted (e.g., displayed in red) to make them stand out
  
- **Priority Color Coding**: Display priority levels with color-coded badges
  - P1: Red badge
  - P2: Orange badge
  - P3: Gray badge
  
- **Task Sorting**: Implement automatic sorting of tasks with the following priority order:
  1. Overdue tasks first
  2. Then by priority (P1 → P2 → P3)
  3. Then by due date (ascending)
  4. Tasks without due dates appear last

---

## 4. Out of Scope

- **Notifications**: No push notifications, email reminders, or alerts
- **Recurring Tasks**: No support for repeating/recurring task patterns
- **Multi-User Features**: No user authentication, sharing, or collaboration features
- **Keyboard Navigation**: No special keyboard shortcuts or accessibility enhancements
- **External Storage**: No backend integration, cloud storage, or database persistence beyond local storage
- **Advanced Accessibility Features**: No screen reader optimizations or WCAG compliance requirements
