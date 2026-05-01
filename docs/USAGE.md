# Usage Guide

This document explains how to use MyApp after it has been installed and started.

## Table of Contents

1. [Logging In](#1-logging-in)
2. [Dashboard Overview](#2-dashboard-overview)
3. [Managing Tasks](#3-managing-tasks)
4. [Managing Team Members](#4-managing-team-members)
5. [Notifications](#5-notifications)
6. [Keyboard Shortcuts](#6-keyboard-shortcuts)

---

## 1. Logging In

Navigate to `http://localhost:3000` (or your deployed URL) and log in with your credentials.

If you seeded the database with sample data, the default admin account is:

| Field | Value |
|---|---|
| Email | `admin@example.com` |
| Password | `Admin1234!` |

> **Note:** Change the default password immediately in a production environment.

---

## 2. Dashboard Overview

The dashboard shows a summary of all tasks grouped by status:

```
┌─────────────────────────────────────────────────────┐
│  MyApp Dashboard                      👤 Admin ▾     │
├───────────────┬────────────────┬────────────────────┤
│   TO DO (5)   │ IN PROGRESS (3)│     DONE (12)       │
│               │                │                     │
│ ▸ Fix login   │ ▸ Add CSV exp  │ ▸ Setup CI/CD ✓     │
│ ▸ Write docs  │ ▸ Dark mode    │ ▸ Auth module ✓     │
│ ...           │ ...            │ ...                 │
└───────────────┴────────────────┴────────────────────┘
```

Use the **Filter** bar at the top to filter tasks by:
- Assignee
- Priority (Low / Medium / High / Critical)
- Due date range
- Label / tag

---

## 3. Managing Tasks

### Creating a Task

1. Click **+ New Task** in the top-right corner
2. Fill in the form:
   - **Title** *(required)*
   - **Description** — supports Markdown
   - **Assignee** — select a team member
   - **Priority** — Low, Medium, High, or Critical
   - **Due Date**
3. Click **Save**

### Updating a Task

1. Click on any task card to open the detail view
2. Edit the fields inline
3. Changes are saved automatically

### Changing Task Status

Drag and drop the task card between the **To Do**, **In Progress**, and **Done** columns, or use the status dropdown inside the task detail view.

### Deleting a Task

1. Open the task detail view
2. Click the **⋮ More Options** menu (top-right of the detail panel)
3. Select **Delete Task**
4. Confirm the deletion in the dialog

> **Warning:** Task deletion is permanent and cannot be undone.

---

## 4. Managing Team Members

### Inviting a Member

1. Go to **Settings → Team**
2. Click **Invite Member**
3. Enter their email address and select a role:
   - **Viewer** — can view tasks only
   - **Member** — can create and update tasks
   - **Admin** — full access including settings
4. Click **Send Invitation**

The invited user will receive an email with a link to join.

### Removing a Member

1. Go to **Settings → Team**
2. Find the member in the list
3. Click **Remove** next to their name
4. Confirm in the dialog

> Removing a member does not delete their existing tasks — those will become unassigned.

---

## 5. Notifications

MyApp sends email notifications when:

- A task is assigned to you
- A task you are assigned to changes status
- A comment is added to a task you are assigned to
- A task you own is overdue

You can manage notification preferences in **Settings → Notifications**.

---

## 6. Keyboard Shortcuts

| Shortcut | Action |
|---|---|
| `N` | Create new task |
| `F` | Focus the filter bar |
| `Esc` | Close modal / detail panel |
| `?` | Show keyboard shortcut help |
| `Ctrl + Z` | Undo last action |
| `Ctrl + Shift + Z` | Redo |
