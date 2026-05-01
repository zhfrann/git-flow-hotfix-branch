# Changelog

All notable changes to MyApp are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [Unreleased]

### Added
- Dark mode support
- CSV export for task lists

---

## [1.2.1] - 2024-04-10

### Fixed
- **HOTFIX**: Fixed critical bug where task deletion removed the wrong record when multiple tasks shared the same due date
- **HOTFIX**: Resolved authentication token expiry not refreshing properly on long sessions

---

## [1.2.0] - 2024-03-28

### Added
- Email notification system for task assignments and status changes
- Priority levels: Low, Medium, High, Critical

### Changed
- Improved dashboard loading speed by 40% through query optimisation
- Updated task card UI for better readability

### Fixed
- Fixed pagination issue on the task list page when filtering by assignee

---

## [1.1.1] - 2024-02-14

### Fixed
- **HOTFIX**: Patched XSS vulnerability in task description field
- Fixed date picker not respecting user timezone settings

---

## [1.1.0] - 2024-01-20

### Added
- Team member management: invite, remove, and set roles
- Task comments and activity feed

### Changed
- Migrated database from SQLite to PostgreSQL

---

## [1.0.0] - 2023-12-01

### Added
- Initial release
- Task CRUD (Create, Read, Update, Delete)
- User authentication (register, login, logout)
- Basic dashboard with task overview
