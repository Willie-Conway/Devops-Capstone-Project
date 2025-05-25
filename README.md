# DevOps Capstone Project

![Build Status](https://github.com/Willie-Conway/devops-capstone-project/actions/workflows/ci-build.yaml/badge.svg)

# 📅 Lab 1: Agile Planning Using GitHub

Welcome to the **Agile Planning** lab! In this exercise, you’ll learn how to use GitHub’s Agile tools — Issues, Labels, Milestones, and Projects — to plan and track your work effectively.

---

## 🎯 Objectives

* Create GitHub Issues to track user stories and tasks
* Use Labels to categorize and prioritize work
* Group Issues into Milestones for release planning
* Use GitHub Projects (Kanban boards) to manage workflow visually
* Move stories across columns to reflect progress

---

## 🔧 Prerequisites

* A GitHub account
* Basic familiarity with GitHub repositories and issues

---

## 📝 Step 1: Create Issues for User Stories

1. Go to your GitHub repository’s **Issues** tab.
2. Click **New issue**.
3. Enter the title and description for a user story or task.
4. Submit the issue.

💡 *Tip:* Use clear, actionable titles and detailed descriptions for each issue.

---

## 🏷️ Step 2: Add Labels

* Create and assign labels like:

  * `story` (for user stories)
  * `bug`
  * `enhancement`
  * `priority: high` / `priority: low`

* To add labels:

  * Click on an issue
  * Select **Labels** on the right sidebar
  * Choose or create the appropriate label

---

## 🎯 Step 3: Create Milestones

* Navigate to the **Milestones** tab under Issues.
* Create a milestone representing a release or sprint (e.g., `Sprint 1`, `Release 1.0`).
* Assign issues to this milestone to track their progress towards completion.

---

## 📊 Step 4: Create and Use a Project (Kanban Board)

1. Go to the **Projects** tab.
2. Create a new project using the **Kanban (Basic)** template.
3. Set up columns such as:

   * To Do
   * In Progress
   * Done
4. Add your issues as cards to the project board.
5. Drag and drop issues between columns as work progresses.

---

## 🔄 Step 5: Track and Update

* Regularly update issue status by moving cards across the board.
* Close issues when done.
* Update milestones to reflect sprint or release progress.

---

## ✅ Evidence

* Take a screenshot of your GitHub Project board showing issues in different columns.
* Save it as `agile-planning-kanban.png`.

---

## 💡 Tips for Effective Agile Planning

* Keep issues small and manageable.
* Prioritize stories clearly using labels and milestones.
* Use the project board daily to reflect current progress.
* Link pull requests to issues for traceability.

---

## 🎉 Congratulations!

You’ve successfully set up an Agile planning workflow using GitHub’s built-in tools. This will help your team stay organized and focused on delivering value incrementally.

---

# 🛠️ Lab 2: Develop a RESTful Service Using Test-Driven Development (TDD)

Welcome to the **Test-Driven Development (TDD)** lab! In this lab, you will build a RESTful API by writing tests first and then implementing code to make those tests pass. This approach ensures higher quality, better design, and fewer bugs.

---

## 🎯 Objectives

* Understand the principles of Test-Driven Development
* Write unit tests for REST API endpoints before implementation
* Develop a simple RESTful service to manage resources (e.g., accounts, users)
* Run tests continuously to validate code correctness
* Practice refactoring with confidence after tests pass

---

## 🔧 Prerequisites

* Basic knowledge of RESTful APIs
* Familiarity with Python or your chosen programming language
* Understanding of unit testing frameworks (e.g., `unittest`, `pytest`, `nose`)
* Development environment setup (IDE, terminal)

---

## 📝 Lab Overview

You will follow these steps:

1. **Write failing tests first** for the REST API endpoints you want to implement.
2. **Implement the minimal code** to make the tests pass.
3. **Refactor your code** to improve structure while ensuring tests still pass.
4. **Repeat the cycle** for each new feature or endpoint.

---

## 🔨 Step 1: Write Tests for API Endpoints

* Define tests for common RESTful operations:

  * GET (list and single resource)
  * POST (create resource)
  * PUT/PATCH (update resource)
  * DELETE (remove resource)

* Use your testing framework to define expected input/output and behaviors.

---

## 💻 Step 2: Implement API Endpoints

* Build the RESTful service (e.g., Flask, Django, FastAPI).
* Implement the endpoints gradually, running tests after each addition.
* Ensure your endpoints return appropriate HTTP status codes and JSON responses.

---

## ✅ Step 3: Run Tests Continuously

* Use your test runner (e.g., `nose`, `pytest`) to execute tests.
* Fix any failing tests by adjusting your implementation.
* Confirm all tests pass before moving forward.

---

## 🔄 Step 4: Refactor Your Code

* Clean up your implementation for readability, performance, and maintainability.
* Ensure tests still pass after refactoring.

---

## 📚 Helpful Commands

* Run tests:

  ```bash
  nosetests -v --with-spec --spec-color
  ```
* Run the REST API server (example for Flask):

  ```bash
  flask run
  ```

---

## 🎉 Lab Complete!

You’ve now built a RESTful service using the TDD approach — ensuring a robust, well-tested application.

---

## 📑 Evidence

* Capture the terminal output of your passing test run. Save it as `test-results.txt`.
* Screenshot your running REST API responding to requests, if possible.

---

## 💡 Tips for Success

* Keep tests small and focused on one behavior.
* Write clear, descriptive test names.
* Use mocks/stubs if needed for external dependencies.
* Run tests frequently to catch regressions early.

---



