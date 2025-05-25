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


# 📅 Lab 3: Sprint 2 Planning

Welcome to the **Sprint 2 Planning** lab! In this lab, you'll organize, prioritize, and plan your development work for the second sprint of your project using Agile practices.

---

## 🎯 Objectives

* Review user stories and backlog items for Sprint 2
* Prioritize work based on business value and complexity
* Break down stories into actionable tasks
* Assign tasks to team members (if applicable)
* Define sprint goals and deliverables
* Create/update your sprint backlog in your Agile tool (e.g., GitHub Projects, Jira)

---

## 🔧 Prerequisites

* Basic understanding of Agile and Scrum methodologies
* Familiarity with your project’s user stories and backlog
* Access to your Agile planning tool (e.g., GitHub Projects, Jira)

---

## 📝 Lab Overview

You will:

1. **Review backlog items** planned for Sprint 2
2. **Prioritize and select stories** to complete during Sprint 2
3. **Break down stories into smaller tasks** for easier tracking and execution
4. **Estimate effort** (story points or time) for each story or task
5. **Assign tasks** to developers (if working in a team)
6. **Set sprint goals** that define what the sprint will achieve
7. **Update your sprint board or project board** to reflect your Sprint 2 plan

---

## 🔨 Step 1: Review and Prioritize Backlog

* Look at all user stories in your backlog
* Prioritize based on business impact and dependencies
* Remove or defer any stories that don’t fit the sprint scope

---

## 🛠️ Step 2: Break Down Stories into Tasks

* For each user story, create detailed tasks
* Tasks should be manageable and clear
* Example: For a "User login" story, tasks might include "Create login API," "Design login UI," "Write unit tests"

---

## 📊 Step 3: Estimate Effort

* Assign story points or time estimates to tasks or stories
* Use planning poker, T-shirt sizing, or your preferred estimation method

---

## 🤝 Step 4: Assign and Commit

* Assign tasks to team members based on skills and availability
* Commit to what the team can realistically complete in the sprint

---

## 🎯 Step 5: Set Sprint Goals

* Define clear goals that reflect the sprint's expected outcome
* Example: "Implement user authentication and profile management"

---

## 💻 Step 6: Update Agile Board

* Move stories/tasks to the Sprint 2 column or equivalent in your tool
* Ensure everyone has visibility of the sprint plan

---

## 📑 Evidence

* Take a screenshot of your updated sprint board showing Sprint 2 backlog and goals
* Optionally, export or share your sprint backlog as a PDF or CSV

---

## 🎉 Congratulations!

You have successfully planned Sprint 2 and are ready to start focused, prioritized development work!

---


