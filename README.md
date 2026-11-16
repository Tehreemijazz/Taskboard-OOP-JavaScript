# Taskboard -- OOP JavaScript

A responsive, single-page task management dashboard built with **HTML,
CSS, and vanilla JavaScript**. The project demonstrates object-oriented
JavaScript concepts through a small taskboard application with projects,
tasks, assignments, comments, attachments, filters, and activity
tracking.

## Features

-   Multiple projects: Switch between Website Redesign, Mobile App
    v2, and an All Projects view.
-   Task management: Create, view, update, complete, reopen,
    duplicate, and delete tasks.
-   Task categories: Development, Testing, Documentation, and
    General.
-   Task details: Store a description, priority, status, due date,
    estimated hours, assignees, comments, attachments, and activity
    history.
-   Search and filters: Search task titles and descriptions; filter
    by status, priority, and assignee.
-   Project statistics: View total, completed, pending, and overdue
    tasks, plus estimated hours.
-   Overdue indication: Tasks with a past due date are highlighted
    unless completed.
-   Responsive layout: The interface adapts for smaller screens.
-   Theme support: Uses light and dark color variables and follows
    the operating system color preference, with a `data-theme` override
    available in CSS.

## Technologies Used

-   HTML5
-   CSS3 (CSS Grid, Flexbox, custom properties, media queries)
-   JavaScript (ES6+)
-   Native browser APIs: DOM, `FormData`, `<dialog>`, and
    `structuredClone()`

No framework, package installation, build step, or external runtime
dependency is required.

## Getting Started

1.  Download or clone this project.
2.  Open the project folder.
3.  Open `index.html` in a modern web browser.

You can also use the Live Server extension in Visual Studio Code to
run it locally.

> The application currently uses in-memory sample data. Changes are kept
> only while the page remains open and are reset when the page is
> refreshed. There is no backend or database connection.

## How to Use

1.  Select a project from the sidebar, or choose **All projects**.
2.  Use the search field to find tasks by title or description.
3.  Apply status, priority, or assignee filters. Select **Clear** to
    reset them.
4.  Select a task to open its details.
5.  From the task details, change its status or priority, assign or
    remove members, add a comment, add a sample attachment, complete or
    reopen it, duplicate it, or delete it.
6.  Select **New task** to create a task and choose its type, title,
    description, priority, due date, estimated hours, and assignees.
7.  Open the **Architecture** tab to read about the class structure and
    OOP concepts used in the project.

## Object-Oriented JavaScript Concepts

The project is organized into model, service, and UI sections.

### Classes and Encapsulation

-   `User`, `Comment`, and `Attachment` represent reusable data objects.
-   `Task` stores task data and behavior. Private class fields (such as
    `#id`, `#status`, and `#assignees`) protect internal state.
-   Getters and setters provide controlled access and validate values
    such as title, priority, status, and estimated hours.
-   Getters for collections return copies rather than exposing the
    internal arrays.

### Inheritance and Polymorphism

-   `DevelopmentTask` and `TestingTask` extend `Task` and override
    `effectiveHours()`.
-   `DocumentationTask` extends `Task` without changing its behavior.
-   The taskboard can work with different task types through the common
    task interface.

### Static Members

`Task` defines shared priority and status constants, a static ID
generator (`nextId()`), and a static summary method (`summarize()`).

### Composition

A task contains related objects such as assignees, comments,
attachments, and an `ActivityLog`. A project uses an `Observable` object
for event notifications rather than inheriting from it.

### Design Patterns

-   **Factory pattern:** `TaskFactory.create()` creates the appropriate
    task subclass. `TaskFactory.clone()` creates a separate task from a
    plain-data snapshot.
-   **Observer pattern:** `Project` notifies subscribers when project
    tasks change. `AppService` listens for those events and the UI
    refreshes.

### Other JavaScript Concepts

-   `call`, `apply`, and `bind` (the project demonstrates `bind` for the
    activity feed and `apply` for calculating the largest estimate).
-   Array methods including `map`, `filter`, `reduce`, `some`, and
    `forEach`.
-   Event delegation for handling task and dialog actions.
-   `FormData` for reading the new-task form.
-   `structuredClone()` for cloning plain task data.
-   Template literals for rendering interface sections.
-   Input validation and error handling.

## Project Structure

The project is intentionally kept in a single HTML file:

taskboard/
└── index.html

The file contains: - HTML markup for the sidebar, tabs, board,
architecture section, and dialog. - CSS styles and responsive layout
rules inside a `<style>` element. - JavaScript model classes,
`AppService`, rendering functions, and event listeners inside a
`<script>` element.

## Current Limitations

-   Sample users, projects, and tasks are created in JavaScript when the
    application starts.
-   Data is not saved to local storage, a server, or a database.
-   Attachments are sample records; the app does not upload or store
    actual files.
-   The application is a front-end demonstration and does not include
    authentication or multi-user synchronization.

## Possible Improvements

-   Persist projects and tasks using `localStorage` or a backend
    database.
-   Add real file upload and attachment previews.
-   Add task editing for title, description, due date, and estimated
    hours.
-   Add project and team member management.
-   Add automated tests for model and service behavior.

## Learning Purpose

This project is designed to practice object-oriented JavaScript,
including classes, private fields, getters and setters, inheritance,
polymorphism, composition, static members, factory and observer
patterns, and separation of concerns between application logic and DOM
rendering.
