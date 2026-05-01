# # Search Feature Guide

This document provides an overview of how to use the search and advanced filtering capabilities in MyApp. These features are designed to help teams locate tasks quickly and efficiently.

## Overview

The search functionality is integrated directly into the main dashboard and allows you to find tasks based on specific text, as well as filter results by criteria such as status, priority, and assignee.

---

## Using Search in the Dashboard (UI)

The search and filter bar is located at the top of the MyApp Dashboard.

* **Quick Access:** Press the `F` keyboard shortcut to immediately focus the cursor on the filter bar.
* **Text Search:** Type any keyword to find matches within the task **Title** or **Description**.
* **Status Filtering:** You can filter tasks based on their current column: **To Do**, **In Progress**, or **Done**.
* **Priority Filtering:** View tasks based on their priority level: **Low**, **Medium**, **High**, or **Critical**.
* **Assignee Filtering:** Narrow down the task list to see work currently assigned to a specific team member.

---

## Search API Reference

The text search and filtering features are fully supported by the MyApp REST API. Searching is performed through the standard task retrieval endpoint by adding query parameters.

### `GET /tasks`

Retrieves a list of tasks with search and filter parameters applied.

**Query Parameters:**

| Parameter | Type | Description |
|---|---|---|
| `q` | string | Full-text search keyword to match titles and descriptions. |
| `status` | string | Filter by task status: `todo`, `in_progress`, `done`. |
| `priority` | string | Filter by priority: `low`, `medium`, `high`, `critical`. |
| `assignee` | string | Filter by the user ID of the task assignee. |

**Example Request:**

To search for tasks containing the keyword "login" that are "in_progress" and have a "high" priority:

```http
GET /api/v1/tasks?q=login&status=in_progress&priority=high
