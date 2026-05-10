# 🤝 Contribution Guidelines for Northwind Elementary

First of all, thank you for investing your time in contributing to this project! To maintain high software quality, ensure a scalable architecture, and provide a smooth collaboration experience, please adhere to the following standards and workflows.

## 🌿 Git Workflow & Branching

We follow a simplified GitHub Flow to ensure continuous integration:

* **Main Branch:** The `main` branch must *always* be in a runnable and stable state.
* **Short-lived Branches:** Create a new branch for every feature or bug fix. Use descriptive prefixes (e.g., `feature/post-grade` or `bugfix/identity-login`).
* **Pull Requests (PRs):** All changes must be submitted via PRs. Direct commits to `main` are not allowed.
* **Reviews:** A PR must be reviewed and approved by another team member before merging.
* **Quality Gate:** Ensure the code compiles, the application runs locally, and all unit tests pass before requesting a review.

## 📝 Commit Messages

Commit messages are used for future release notes and tracking. We follow the **Conventional Commits** standard. They must be meaningful and descriptive.

🔴 **Bad:** > fixed stuff
> update code

🟢 **Good:** > feat(assessment): implement PostGrade logic
> fix(people): resolve null reference in Student model

## 🛠️ Coding Standards 

Consistency across the codebase is essential for maintainability and long-term scalability. All code (classes, methods, variables, database schemas, and documentation) **must be in English**.

* **The Boy Scout Rule:** "Always leave the code a little cleaner than you found it." If you see a small technical debt while working on a slice, fix it.

### ⚙️ Backend (C# & .NET 10)
We follow industry-standard C# conventions:
* **Modular Isolation:** Each module is the sole owner of its database schema. Cross-schema JOINs should be treated as an architectural violation unless explicitly justified. Cross-module communication must be handled through shared `.Contracts` projects or in-memory events using MediatR.
* **REPR Pattern:** Endpoints must follow the Request-EndPoint-Response (REPR) pattern. Keep endpoint handlers clean of validation logic by leveraging .NET 10's native support for Data Annotations.
* **Naming Conventions:**
  * `PascalCase`: For classes, records, method names, public members, and namespaces.
  * `camelCase`: For local variables and private fields (optionally prefixed with `_`).
  * `Interfaces`: Must always start with "I" (e.g., `IAcademicService`).
* **Clean Code Principles:**
  * **SRP (Single Responsibility Principle):** Each class or endpoint should have only one reason to change.
  * **Dependency Injection:** Prefer Constructor Injection as the default method in the backend.
  * **Asynchronous Programming:** Use `async/await` for all I/O bound operations (database calls, external APIs).
  * **No Magic Numbers:** Replace raw numbers or hardcoded strings with named constants or enums (e.g., `MAX_STUDENTS_PER_GRADE`).

### 🅰️ Frontend (Angular 21 & TypeScript)
* **Architecture:** Strictly use **Standalone Components**. Do not introduce `NgModules`.
* **State Management & Zoneless:** Prefer **Angular Signals** for reactive state and data binding. By leveraging Signals, we are building a strictly **Zoneless application** (without `zone.js`), aligning with the future of the framework.
* **Dependency Injection:** Prefer the `inject()` function over traditional constructor injection to maintain a clean and consistent syntax across Standalone Components.
* **Naming Conventions:**
  * `kebab-case`: For file names and component selectors (e.g., `student-list.component.ts`).
  * `camelCase`: For variables, functions, and properties.
  * `PascalCase`: For classes, interfaces, and types.

## 🧪 Testing & Quality

* **Unit Tests:** Every new feature should include its corresponding unit tests in the `tests/` directory (using xUnit for .NET and Vitest for Angular).
* **Formatting:** We use a shared `.editorconfig`. Ensure your IDE (VS Code, Rider, or Visual Studio) applies the same indentation and brace rules automatically on save.
* **No Commented-out Code:** Never commit commented-out code blocks. If code is no longer needed, delete it. Git remembers the history.

## 🆘 Seeking Help & Reporting Issues

When you encounter a bug or need help, please open an Issue following these rules:

1. **Be Precise:** Describe the *expected* vs. *actual* behavior clearly.
2. **Provide Context:** Mention the specific file, slice, and line number where the issue occurs.
3. **NO Photos of Screens:** Always copy-paste the raw text of the error log, or provide a high-resolution screenshot directly from your OS. **Prefer copy-pasted logs or proper screenshots instead of low-quality monitor photos.**
