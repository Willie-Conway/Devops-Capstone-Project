# DevOps Capstone Project

![Build Status](https://github.com/Willie-Conway/devops-capstone-project/actions/workflows/ci-build.yaml/badge.svg)


# 🚀 Lab: Agile Planning Using GitHub

⏳ **Estimated time needed:** 60 minutes

## 🌟 Welcome
Welcome to the hands-on **Agile Planning Using GitHub** lab! In this lab, you'll build a **Sprint Plan (Sprint 0)** for a **Customer Accounts Microservice** project.

**Project Goal:** Develop an account microservice with REST APIs to:
- ✨ Create
- 📖 Read
- 🔄 Update
- 🗑️ Delete
- 📜 List customer accounts

> **Note:** This lab uses **GitHub only** (no lab environment).

## 🎯 Objectives
By the end of this lab, you will:
- ✔️ Create a GitHub repository
- ✔️ Set up a GitHub Kanban board
- ✔️ Develop a user story template
- ✔️ Add and prioritize user stories
- ✔️ Refine a product backlog
- ✔️ Build a sprint plan

## 📸 Screenshot Requirements
You'll need to save these screenshots:

| File Name                         | Description                          |
|-----------------------------------|--------------------------------------|
| `planning-repository-done.png`    | GitHub repo created                  |
| `planning-storytemplate-done.png` | User story template                  |
| `planning-userstories-done.png`   | 7 user stories added                 |
| `planning-productbacklog-done.png`| Backlog triaged                      |
| `planning-labels-done.png`        | Stories labeled & refined            |
| `planning-kanban-done.png`        | Final sprint backlog                 |

**Screenshot Shortcuts:**
- **Mac:** `Shift + Cmd + 3` (full screen) or `Shift + Cmd + 4` (area)
- **Windows:** `Alt + Print Screen` → Paste into image editor

## 🛠️ Exercises

### Exercise 1: Create GitHub Repository
1. Use [this template](https://github.com/ibm-developer-skills-network/aolwx-devops-capstone-template) (click "Use this template")
2. Name: `devops-capstone-project` (set to **Public**)
3. **Evidence:** Save repo URL + `planning-repository-done.png`

---

### Exercise 2: Create Kanban Board
Set up board with 7 columns:
1. New issues
2. Icebox ❄️
3. Product Backlog 📋
4. Sprint Backlog 🏃
5. In progress 🔄
6. Review/QA ✔️
7. Done ✅

---

### Exercise 3: User Story Template
Create `.github/ISSUE_TEMPLATE/user-story.md`:

```markdown
**As a** [role]  
**I need** [function]  
**So that** [benefit]  

### Details and Assumptions
* [document what you know]  

### Acceptance Criteria  
```gherkin
Given [context]  
When [action]  
Then [outcome]
```



**Evidence:** `planning-storytemplate-done.png`

---

### Exercise 4: Product Backlog
Create 7 user stories:
1. Set up dev environment
2. Read an account
3. Update an account
4. Delete an account
5. List accounts
6. Containerize with Docker 🐳
7. Deploy to Kubernetes ☸️

**Evidence:** `planning-userstories-done.png`

---

### Exercise 5: Triage Issues
- Move 5 stories to **Product Backlog**
- Move 2 stories (Docker/K8s) to **Icebox** ❄️

**Evidence:** `planning-productbacklog-done.png`

---

### Exercise 6: Refine Backlog
1. Add details/acceptance criteria
2. Create `technical debt` label (yellow)
3. Apply labels:
   - `enhancement` (customer features)
   - `technical debt` (e.g., setup)
4. Rank by priority

**Evidence:** `planning-labels-done.png`

---

### Exercise 7: Sprint Plan
1. Create 3 sprints (1 week each)
2. Assign 5 stories to **Sprint 1**
3. Add story points (3=S, 5=M, 8=L, 13=XL)
4. Move to Sprint Backlog

**Evidence:** `planning-kanban-done.png`

# Lab: 🏦 Account Microservice - RESTful API with TDD

## 🔍 Lab Overview
**Develop a RESTful Service Using Test-Driven Development**  
*Estimated time: 90 minutes*

### 🎯 Objectives
- Follow Agile plan from Kanban board
- Implement REST API endpoints using TDD
- Achieve 95%+ test coverage
- Conduct sprint review

## ⚠️ Important Notes
- **Ephemeral environment**: Cloud IDE may reset - push changes to GitHub!
- **Security**: Never store secrets in code
- **GitHub PAT**: Required for pushing changes (repo+write permissions)

## 🛠️ Setup Instructions

### 1️⃣ Initialize Environment
```bash
export GITHUB_ACCOUNT=your_username
git clone https://github.com/$GITHUB_ACCOUNT/devops-capstone-project.git
cd devops-capstone-project
bash ./bin/setup.sh
exit  # Must reopen terminal!
```

### 2️⃣ Validate Setup
```bash
which python        # Should show venv path
python --version   # Verify Python 3.9+
```

### 3️⃣ Install Dependencies
```bash
pip install -r requirements.txt
```
### 🧪 TDD Workflow
#### 🔴 Write Failing Test
```python
# tests/test_routes.py
def test_get_account(client):
    response = client.get("/accounts/1")
    assert response.status_code == 200
```
### 🟢 Implement Minimal Code
```python
# service/routes.py
@app.route("/accounts/<int:id>", methods=["GET"])
def get_account(id):
    account = Account.find(id)
    return jsonify(account.serialize()), 200
```

### 🔁 Run Tests
```bash
nosetests --with-coverage --cover-package=service
```

### 📊 Coverage Verification
```bash
coverage report -m  # CLI report
coverage html       # HTML report
open htmlcov/index.html
```

### 📋 Required Endpoints

| Method | Endpoint         | Description        |
|--------|------------------|--------------------|
| GET    | /accounts/<id>   | Get single account |
| PUT    | /accounts/<id>   | Update account     |
| DELETE | /accounts/<id>   | Delete account     |
| GET    | /accounts        | List all accounts  |


### 📸 Evidence Checklist

1. **`tests-passing.png`** - All tests green

2. **`coverage-report.png`** - Coverage ≥95%

3. **`api-working.png`** - curl/Postman demo

### 📂 Project Structure

```bash
.
├── service/
│   ├── models.py     # DB models
│   └── routes.py     # API endpoints
├── tests/
│   └── test_routes.py # Unit tests
├── requirements.txt
└── bin/setup.sh      # Setup script
```

### 💡 Pro Tips

- Use mocks in tests:
  ```python
  from unittest.mock import patch
  ```

  - Test edge cases:
    ```python
    def test_get_nonexistent_account(client):
    response = client.get("/accounts/999")
    assert response.status_code == 404
    ```

    - Commit often to avoid losing work
    
# 🚀 REST API Guidelines Review

This document summarizes the REST API design for your lab, including testable behaviors, HTTP status codes, and implementation hints for endpoints. Use it as a cheat sheet during development and test writing! ✅

---

## 📌 RESTful API Endpoints

| 🛠️ Action | 🔢 Method | 🔁 URL Endpoint         | 📦 Return Code    | 🧾 Body                     |
|----------|------------|------------------------|-------------------|----------------------------|
| List     | `GET`      | `/accounts`            | `200 OK`          | Array of accounts `[{}]`   |
| Create   | `POST`     | `/accounts`            | `201 CREATED`     | A new account `{}`         |
| Read     | `GET`      | `/accounts/{id}`       | `200 OK` or `404` | Account as JSON `{}`       |
| Update   | `PUT`      | `/accounts/{id}`       | `200 OK` or `404` | Updated account as JSON    |
| Delete   | `DELETE`   | `/accounts/{id}`       | `204 NO CONTENT`  | Empty string `""`          |

🧠 **Note:** These standard behaviors enable consistent testing and API usage. If no accounts exist, always return `[]` with `200 OK` instead of a `404`.

---

## 🔢 HTTP Status Codes

| 📟 Code | 🧾 Status              | 📖 Description                            |
|--------|------------------------|--------------------------------------------|
| 200    | `HTTP_200_OK`          | ✅ Request successful                       |
| 201    | `HTTP_201_CREATED`     | 🆕 Resource successfully created            |
| 204    | `HTTP_204_NO_CONTENT`  | 🗑️ Resource deleted / no body in response   |
| 404    | `HTTP_404_NOT_FOUND`   | 🚫 Resource not found                       |
| 405    | `HTTP_405_METHOD_NOT_ALLOWED` | ❌ Method not allowed on endpoint  |
| 409    | `HTTP_409_CONFLICT`    | ⚠️ Conflict with the current state          |

These codes are available via:
```python
from service.common import status
````

---

## 🧪 Sample Unit Tests

### 🔍 Test: Read Account

```python
def test_get_account(self):
    response = self.client.get("/accounts/1")
    self.assertEqual(response.status_code, status.HTTP_200_OK)
    data = response.get_json()
    self.assertEqual(data["id"], 1)
```

### 📝 Test: Update Account

```python
def test_update_account(self):
    updated = {"name": "New Name", "address": "New Address"}
    response = self.client.put("/accounts/1", json=updated)
    self.assertEqual(response.status_code, status.HTTP_200_OK)
    data = response.get_json()
    self.assertEqual(data["name"], "New Name")
```

### ❌ Test: Delete Account

```python
def test_delete_account(self):
    response = self.client.delete("/accounts/1")
    self.assertEqual(response.status_code, status.HTTP_204_NO_CONTENT)
```

### 📜 Test: List All Accounts

```python
def test_list_accounts(self):
    response = self.client.get("/accounts")
    self.assertEqual(response.status_code, status.HTTP_200_OK)
    data = response.get_json()
    self.assertIsInstance(data, list)
```

### 🆕 Test: Create Account

```python
def test_create_account(self):
    new_account = {"name": "Jane Doe", "address": "123 Elm St"}
    response = self.client.post("/accounts", json=new_account)
    self.assertEqual(response.status_code, status.HTTP_201_CREATED)
    data = response.get_json()
    self.assertEqual(data["name"], "Jane Doe")
```

---

## 💡 TDD Workflow Tips

* ✅ **Write the test first** (Red)
* 🧑‍💻 **Write the code to pass the test** (Green)
* ♻️ **Refactor if needed**
* 💥 Use the constants like `status.HTTP_200_OK`
* 🔄 Use `.get()`, `.post()`, `.put()`, `.delete()` on `self.client` for endpoint tests

---

## ⚙️ `setup.cfg` Configuration for `nosetests`

```ini
[nosetests]
verbosity=2
with-spec=1
spec-color=1
with-coverage=1
cover-erase=1
cover-package=service
```

🎉 Now, running `nosetests` will include color, spec-style output, and coverage!

---

## 📸 Submission Checklist

* ✅ Screenshot of `setup.cfg`: `rest-setupcfg-done.jpg` / `.png`
* ✅ Screenshot of Kanban board (Story in Done): `rest-techdebt-done.jpg` / `.png`

---

# 🚀 Lab: Develop a RESTful Service Using Test-Driven Development (TDD)

Welcome to the **DevOps Capstone Lab** focused on developing a secure and test-driven RESTful service using Flask! This guide outlines everything you need, from environment setup to deployment, in a clear, emoji-enhanced format 😄.

---

## 🔐 Note: Important Security Information

- Always handle sensitive data securely.
- Never commit secrets or API keys into version control.
- Ensure all APIs have proper validation and error handling.

---

## 🛠️ Initialize Development Environment

1. Clone the repository.
2. Set up your virtual environment:
    ```bash
    python3 -m venv venv
    source venv/bin/activate
    ```
3. Install dependencies:
    ```bash
    pip install -r requirements.txt
    ```

---

## 📦 Project Overview

This project implements a RESTful service with full CRUD operations for managing **accounts**, built using **Flask** and tested with **nose** using TDD principles.

---

## 📘 REST API Guidelines Review

- Use appropriate HTTP status codes.
- Use JSON for all responses.
- Follow RESTful conventions:
  - `GET /accounts` → List all accounts
  - `GET /accounts/<id>` → Read an account
  - `POST /accounts` → Create an account
  - `PUT /accounts/<id>` → Update an account
  - `DELETE /accounts/<id>` → Delete an account

---

## 🧪 Exercise 1: Implement Your First User Story

Start with the "Create an Account" story. Use TDD:
1. Write a failing test.
2. Implement the feature.
3. Make it pass.
4. Refactor.
5. Maintain 95%+ test coverage.

---

## 🧭 Reference: RESTful Service

Refer to `service/routes.py` and `tests/test_routes.py` for routing logic and test cases. Always write your test **before** implementing the logic!

---

## 🧰 Exercise 2: Create a REST API with Flask

Implement the remaining user stories: **Read, List, Update, Delete**

### 🧾 Read an Account
**Test**
```python
def test_get_account(self):
    """It should Read a single Account"""
    account = self._create_accounts(1)[0]
    resp = self.client.get(f"{BASE_URL}/{account.id}")
    self.assertEqual(resp.status_code, status.HTTP_200_OK)
    self.assertEqual(resp.get_json()["name"], account.name)
````

**Route**

```python
@app.route("/accounts/<int:account_id>", methods=["GET"])
def get_accounts(account_id):
    account = Account.find(account_id)
    if not account:
        abort(status.HTTP_404_NOT_FOUND)
    return account.serialize(), status.HTTP_200_OK
```

---

### 📃 List All Accounts

**Test**

```python
def test_get_account_list(self):
    """It should Get a list of Accounts"""
    self._create_accounts(5)
    resp = self.client.get(BASE_URL)
    self.assertEqual(resp.status_code, status.HTTP_200_OK)
    self.assertEqual(len(resp.get_json()), 5)
```

**Route**

```python
@app.route("/accounts", methods=["GET"])
def list_accounts():
    accounts = Account.all()
    return jsonify([a.serialize() for a in accounts]), status.HTTP_200_OK
```

---

### ✏️ Update an Account

**Test**

```python
def test_update_account(self):
    """It should Update an existing Account"""
    account = AccountFactory()
    resp = self.client.post(BASE_URL, json=account.serialize())
    new_account = resp.get_json()
    new_account["name"] = "Updated Name"
    resp = self.client.put(f"{BASE_URL}/{new_account['id']}", json=new_account)
    self.assertEqual(resp.status_code, status.HTTP_200_OK)
    self.assertEqual(resp.get_json()["name"], "Updated Name")
```

**Route**

```python
@app.route("/accounts/<int:account_id>", methods=["PUT"])
def update_accounts(account_id):
    account = Account.find(account_id)
    if not account:
        abort(status.HTTP_404_NOT_FOUND)
    account.deserialize(request.get_json())
    account.update()
    return account.serialize(), status.HTTP_200_OK
```

---

### 🗑️ Delete an Account

**Test**

```python
def test_delete_account(self):
    """It should Delete an Account"""
    account = self._create_accounts(1)[0]
    resp = self.client.delete(f"{BASE_URL}/{account.id}")
    self.assertEqual(resp.status_code, status.HTTP_204_NO_CONTENT)
```

**Route**

```python
@app.route("/accounts/<int:account_id>", methods=["DELETE"])
def delete_accounts(account_id):
    account = Account.find(account_id)
    if account:
        account.delete()
    return "", status.HTTP_204_NO_CONTENT
```

---

## 💡 Hints and Solutions

Find detailed breakdowns, hints, and solutions for each user story in the `docs/` folder or reference materials.

---

## 🧪 Exercise 3: Run the REST Service

Start the development server:

```bash
flask run
```

Run tests:

```bash
nosetests --with-coverage
```

---

## ✅ Exercise 4: Sprint Review

1. Verify acceptance criteria are met.
2. Confirm test coverage ≥ 95%.
3. Review your Kanban board for completeness.
4. Capture screenshots of progress.

---

## 🏁 Conclusion

🎉 You've now completed the full lifecycle of building and testing a RESTful service using Flask and TDD! Pat yourself on the back!

> 🚧 Keep exploring by adding auth, pagination, or filtering!

---

## 📎 Screenshots for Evidence

* `read-accounts.jpg`
* `list-accounts.jpg`
* `update-accounts.jpg`
* `delete-accounts.jpg`

---

## 🧠 Bonus: Error Handling

Test edge cases like unsupported methods or invalid routes:

```python
def test_method_not_allowed(self):
    """It should not allow an illegal method call"""
    resp = self.client.delete(BASE_URL)
    self.assertEqual(resp.status_code, status.HTTP_405_METHOD_NOT_ALLOWED)
```



# Lab: 🧾 Account REST API - Sprint 1 ✅

Welcome to the **Account Microservice**! This service supports full CRUD operations for managing customer accounts. Below is a breakdown of functionality, tests, and routes implemented in Sprint 1.

---

## 🚀 Features Implemented

### 1. ✅ Create an Account
- **Route:** `POST /accounts`
- **Demo Command:**
```bash
  curl -i -X POST http://127.0.0.1:5000/accounts \
  -H "Content-Type: application/json" \
  -d '{"name":"John Doe","email":"john@doe.com","address":"123 Main St.","phone_number":"555-1212"}'
````

* **Screenshot:** `rest-create-done.jpg`

---

### 2. 🔄 Update an Account

* **Route:** `PUT /accounts/<id>`
* **Functionality:** Modify an existing account by providing updated fields.
  
* **Demo Command:**

  ```bash
  curl -i -X PUT http://127.0.0.1:5000/accounts/1 \
  -H "Content-Type: application/json" \
  -d '{"name":"John Doe","email":"john@doe.com","address":"123 Main St.","phone_number":"555-1111"}'
  ```
* **Screenshot:** `rest-update-done.jpg`

#### 🧪 Test Case

```python
def test_update_account(self):
    """It should Update an existing Account"""
    test_account = AccountFactory()
    resp = self.client.post(BASE_URL, json=test_account.serialize())
    self.assertEqual(resp.status_code, status.HTTP_201_CREATED)

    new_account = resp.get_json()
    new_account["name"] = "Something Known"

    resp = self.client.put(f"{BASE_URL}/{new_account['id']}", json=new_account)
    self.assertEqual(resp.status_code, status.HTTP_200_OK)

    updated_account = resp.get_json()
    self.assertEqual(updated_account["name"], "Something Known")
```

#### 🛠 Flask Route

```python
@app.route("/accounts/<int:account_id>", methods=["PUT"])
def update_accounts(account_id):
    """Update an Account"""
    app.logger.info(f"Request to update an Account with id: {account_id}")
    account = Account.find(account_id)
    if not account:
        abort(status.HTTP_404_NOT_FOUND, f"Account with id [{account_id}] could not be found.")
    account.deserialize(request.get_json())
    account.update()
    return account.serialize(), status.HTTP_200_OK
```

---

### 3. 🗑️ Delete an Account

* **Route:** `DELETE /accounts/<id>`
* **Demo Command:**

  ```bash
  curl -i -X DELETE http://127.0.0.1:5000/accounts/1
  ```
* **Screenshot:** `rest-delete-done.jpg`

#### 🧪 Test Case

```python
def test_delete_account(self):
    """It should Delete an Account"""
    account = self._create_accounts(1)[0]
    resp = self.client.delete(f"{BASE_URL}/{account.id}")
    self.assertEqual(resp.status_code, status.HTTP_204_NO_CONTENT)
```

#### 🛠 Flask Route

```python
@app.route("/accounts/<int:account_id>", methods=["DELETE"])
def delete_accounts(account_id):
    """Delete an Account"""
    app.logger.info(f"Request to delete an Account with id: {account_id}")
    account = Account.find(account_id)
    if account:
        account.delete()
    return "", status.HTTP_204_NO_CONTENT
```

---

### 4. ❌ Method Not Allowed

* **Route:** `DELETE /accounts`
* **Demo:** Sending an invalid method to an unsupported route.

#### 🧪 Test Case

```python
def test_method_not_allowed(self):
    """It should not allow an illegal method call"""
    resp = self.client.delete(BASE_URL)  # DELETE not allowed on /accounts
    self.assertEqual(resp.status_code, status.HTTP_405_METHOD_NOT_ALLOWED)
```

---

## 📷 Sprint Demo Artifacts

| Action | Screenshot             |
| ------ | ---------------------- |
| Create | `rest-create-done.jpg` |
| List   | `rest-list-done.jpg`   |
| Read   | `rest-read-done.jpg`   |
| Update | `rest-update-done.jpg` |
| Delete | `rest-delete-done.jpg` |

---

## 🧭 Reflections: Sprint Retrospective

### ✅ What went well?

* Full CRUD endpoints tested and validated.
* REST service ran smoothly during local demo.

### ❗ What could be improved?

* Initial test data setup was manual — can be streamlined.
* Better error handling could be implemented.

### 🔁 What to change next sprint?

* Add automated CI test runs for PRs.
* Explore pagination or filtering on list endpoint.

---

## 🛠 Tech Stack

* Flask 🐍
* Pytest 🧪
* curl 🌐
* SQLAlchemy 🛢️
* Docker (optional) 🐳
---

# 🌀 Sprint Retrospective: Capstone Project Sprint 1

## ✅ What Went Right
- 🚀 Successfully implemented **CRUD operations** for the Account microservice.
- 🧪 All **tests passed**, ensuring high code quality and functionality.
- 🤝 Smooth **collaboration with the product owner** during the sprint review.
- 📚 Clear and detailed **documentation** guided development and testing effectively.

---

## ⚠️ What Went Wrong
- 🤔 Initial confusion around handling **HTTP status codes** correctly.
- 🐞 Spent more time than expected debugging **update and delete endpoints**.
- 🧭 Could have **planned testing earlier** to catch bugs before implementation.

---

## 🔄 What to Improve Next Sprint
- 🧪 Write **more comprehensive tests before coding** new features.
- 🧠 Allocate time upfront for **API design discussions** and clarity.
- ⚙️ **Automate deployment and integration** steps for faster feedback.
- ⏱️ Schedule **regular check-ins** to detect and resolve issues early.

---

## 📝 Final Thoughts
Reflecting on your sprint helps you improve as a developer and teammate. Keep these lessons in mind for Sprint 2! 💡


> “Agile is not a destination—it’s a journey of continuous improvement.” 🚶‍♂️


# Lab: 🚀 Sprint 2 Planning — Capstone Project

🕒 **Estimated Time Needed:** 30 minutes

Welcome to **Sprint 2 Planning**! With Sprint 1 successfully wrapped up 🎉, it’s time to level up our microservice by adding **continuous integration** and **security enhancements**.

---

## 🎯 Objectives

In this sprint, you will:

- 📝 Create stories for Sprint 2  
- 🗂️ Add them to your **Kanban board**  
- 🏷️ Apply appropriate **labels** and **estimates**  
- 📋 Build and prioritize your **Sprint Backlog**

---

## 📸 Screenshot Requirements

📷 Throughout this lab, you'll need to take screenshots (`.jpg` or `.png`) to document your progress. Use built-in OS tools:

- **Mac**: `⇧ + ⌘ + 3` or `⇧ + ⌘ + 4`
- **Windows**: `Alt + Print Screen`, then paste into Paint or Snipping Tool

---

## 📦 New Requirements from Management

Management has requested:

- 🤖 **Automated CI** using GitHub Actions  
- 🛡️ **Security upgrades** including security headers and CORS policy  

---

## 🧩 User Stories for Sprint 2

### ✅ Story 1: Automate Continuous Integration Checks

**Title:** Need the ability to automate continuous integration checks  
**As a** Developer  
**I need** automation to build and test every pull request  
**So that** I don't rely on manual testing

#### 🧠 Assumptions
- Use **GitHub Actions** for automation
- Include **linting** and **unit testing**
- Use **`postgres:alpine`** as the DB image
- Add a **build status badge** to the `README.md`

#### ✅ Acceptance Criteria (Gherkin)
```gherkin
Given code is ready to be merged  
When a pull request is created  
Then GitHub Actions should run linting and unit tests  
And the badge should show that the build is passing
````

* 📌 **Label:** `technical debt`
* 📏 **Estimate:** `Small (3)`
* 🚦 **Status:** Move to **Sprint Backlog** (ranked 1st)

---

### 🔐 Story 2: Add Security Headers and CORS Policies

**Title:** Need to add security headers and CORS policies
**As a** service provider
**I need** security headers and CORS in place
**So that** my site is protected from attacks

#### 🧠 Assumptions

* Use `Flask-Talisman` for **security headers**
* Use `Flask-CORS` for **CORS policies**

#### ✅ Acceptance Criteria (Gherkin)

```gherkin
Given the site is secured  
When a REST API request is made  
Then secure headers and a CORS policy should be returned
```

* 📌 **Label:** `security`
* 📏 **Estimate:** `Medium (5)`
* 🚦 **Status:** Move to **Sprint Backlog** (ranked 2nd)

---

## 🗂️ Finalizing the Sprint Backlog

* ✅ Add both stories to **Sprint 2**
* 🔢 Rank story 1 (CI automation) **first**
* 🔢 Rank story 2 (Security) **second**
* 🖼️ Take a screenshot of your Kanban board as `sprint2-plan.jpg` or `sprint2-plan.png`

---

## 🏁 Conclusion

🎉 **Congratulations!** You've completed your Sprint 2 planning. Your team is now ready to:

* 🚀 Start building automation
* 🔐 Secure your microservice
* ✅ Improve development workflow

> “Planning is bringing the future into the present so that you can do something about it now.” – Alan Lakein


### 🚀 Exercise 1: Pick Up the First Story

⏱ **Estimated Time:** 10 minutes  
📋 **Objective:** Start working on your first story by properly updating the kanban board.

---

### 📌 Your Task

Before you begin coding, follow these steps:

1. 🧭 Navigate to your **kanban board**.
2. 🔍 Find the **first story** at the top of the **Sprint Backlog**:
   > **"Need the ability to automate continuous integration checks"**
3. 👉 Move the story to the **In Progress** column.
4. 🙋 Assign the story to **yourself**.
5. 📖 Open and **read the full contents** of the story.

---

### 🧾 Story Details

> **Title:** Need the ability to automate continuous integration checks  
> 
> **As a** Developer  
> **I need** automation to build and test every pull request  
> **So that** I do not have to rely on manual testing of each request, which is time-consuming

### 🔍 Assumptions

- ⚙️ GitHub Actions will be used for the automation workflow  
- 🧪 Workflow must include **code linting** and **testing**  
- 🐘 The Docker image used for the database should be `postgres:alpine`  
- 🏷 A GitHub Actions **badge** should be added to the `README.md` to reflect the build status

---

### ✅ Acceptance Criteria (Gherkin)

```gherkin
Given code is ready to be merged  
When a pull request is created  
Then GitHub Actions should run linting and unit tests  
And the badge should show that the build is passing
````

---

### 🏁 Results

✅ The story should now:

* Be visible in the **In Progress** column
* Be assigned to **you**
* Be **fully reviewed** so you're ready to begin development

---

### 📸 Don't Forget: Screenshot Reminder

🖼 Take a screenshot of your kanban board after assigning and moving the story. Save it as:

```
sprint2-story-inprogress.jpg
```


Here's a well-structured `README.md` with appropriate sections, helpful emojis, and your GitHub Actions build badge included.

---



## 📦 Workflow Overview

This project uses GitHub Actions to automate the following CI pipeline:

1. ✅ **Checkout the code**
2. 📥 **Install Python dependencies**
3. 🧼 **Lint the code with Flake8**
4. 🧪 **Run unit tests with Nose**
5. 📊 **Display build status with a badge**

---

### ⚙️ GitHub Actions Workflow Configuration

The workflow file is located at:  
`.github/workflows/ci-build.yaml`

### 🐳 Build Job Configuration

```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    container: python:3.9-slim
    services:
      postgres:
        image: postgres:alpine
        ports:
          - 5432:5432
        env:
          POSTGRES_PASSWORD: pgs3cr3t
          POSTGRES_DB: testdb
        options: >-
          --health-cmd pg_isready
          --health-interval 10s
          --health-timeout 5s
          --health-retries 5
````

### 📥 Steps to Run

```yaml
    steps:
      - name: Checkout
        uses: actions/checkout@v2

      - name: Install dependencies
        run: |
          python -m pip install --upgrade pip wheel
          pip install -r requirements.txt

      - name: Lint with flake8
        run: |
          flake8 service --count --select=E9,F63,F7,F82 --show-source --statistics
          flake8 service --count --max-complexity=10 --max-line-length=127 --statistics

      - name: Run unit tests with nose
        run: nosetests
        env:
          DATABASE_URI: "postgresql://postgres:pgs3cr3t@postgres:5432/testdb"
```

---

### 🧪 Testing & Coverage

* **Testing Tool:** `nose`
* **Linter:** `flake8`
* **Coverage:** Automatically integrated via `nose` configuration in `setup.cfg`

---

### 🏷️ Badge

The badge above 👆 automatically updates with the latest build status of your default branch (`main`).
It’s a great way to communicate your project’s CI health! ✅

---

### 📸 Evidence (Screenshots to Submit)

* `ci-workflow-done.jpg` – Workflow run from GitHub Actions
* `ci-badge-done.jpg` – README showing the CI badge
* `ci-kanban-done.jpg` – Kanban board showing story in "Done" column

---

## ✅ Final Steps

✔️ Create a Pull Request
✔️ Merge once the checks pass
✔️ Celebrate! 🎉

---

> Replace `<OWNER>` in the badge URL with your actual GitHub username to activate the badge!


# 🛡️ Add Security to Your RESTful Service

Welcome to the **"Add Security to Your RESTful Service"** hands-on lab! In this lab, you'll enhance your Flask microservice to improve its security posture using HTTP security headers and CORS policies.

---

## ⏱️ Estimated Time

**60 minutes**

---

## 🎯 Objectives

By the end of this lab, you will:

✅ Take the next story from the Sprint Backlog  
🔐 Add `Flask-Talisman` for security headers  
🌐 Add `Flask-CORS` to enable cross-origin requests  
👀 View the results of your security enhancements  
📥 Make a pull request and merge after CI tests pass  
🗂️ Move the story to the ✅ **Done** column on your kanban board  

---

## 🧰 Tools & Libraries

- 🐍 Flask  
- 🛡️ [Flask-Talisman](https://github.com/GoogleCloudPlatform/flask-talisman) – Automatically adds security headers like HSTS, CSP, and X-Frame-Options  
- 🔄 [Flask-CORS](https://flask-cors.readthedocs.io/en/latest/) – Enables CORS in your Flask app

---

## 🏗️ Setup Instructions

1. 🔃 Pull the latest story from your Sprint Backlog  
2. 🏗️ Create a new branch:  
```bash
   git checkout -b add-security-headers
```

3. ➕ Add packages to your `requirements.txt`:

```txt
   Flask-Talisman
   Flask-Cors
```

4. 📦 Install the new dependencies:

   ```bash
   pip install -r requirements.txt
   ```

5. 📝 Update your `service/__init__.py` or wherever your app is created:

   ```python
   from flask_talisman import Talisman
   from flask_cors import CORS

   app = Flask(__name__)

   Talisman(app)
   CORS(app)
   ```

---

## 🔎 Validation Steps

After making your changes:

✅ Run your unit tests locally or via `make test`
✅ Check headers via browser dev tools or `curl -I http://localhost:5000`
✅ Confirm CORS headers like `Access-Control-Allow-Origin` are present
✅ Commit changes:

```bash
git add .
git commit -m "🔐 Added security headers and CORS policies"
```

---

## 🚀 Push & Pull Request

📤 Push your branch:

```bash
git push origin add-security-headers
```

📋 Create a pull request on GitHub
✅ Wait for CI to pass
🔁 Merge when ready

---

## 🧾 Evidence to Submit

📸 Take screenshots of the following and save them as:

* ✅ `security-headers-terminal.png` – terminal showing security headers present
* ✅ `ci-pipeline-passed.png` – CI pipeline success in GitHub Actions
* ✅ `security-readme-badge.png` – (optional) README with updated security note
* ✅ `kanban-security-done.png` – Kanban board with story in **Done**

---

## ⚠️ Notes on Environment

☁️ Your Cloud IDE is **ephemeral** (short-lived).
Make sure to:

* 🔄 Re-run setup after each reset:

  ```bash
  export GITHUB_ACCOUNT=your_github_account
  git clone https://github.com/$GITHUB_ACCOUNT/devops-capstone-project.git
  cd devops-capstone-project
  bash ./bin/setup.sh
  exit
  ```

* ✅ Open a new terminal and verify Python is using the virtual environment:

  ```bash
  which python
  python --version
  ```

---

## 💬 Summary

With these changes, your RESTful service is now:

🔒 Secured with HTTP headers
🌐 Accessible with CORS
🛠️ Integrated into CI/CD
📈 Documented and validated!

👏 Great job making your service more production-ready!


---

### 📖 Exercise 1: Pick Up the Next Story

Welcome to **Exercise 1** of your DevOps Sprint! It's time to grab the next story from your **Sprint Backlog** and begin working. This step sets the stage for improving the security of your RESTful microservice.

---

### ✅ Your Task

Follow these steps to kick off development:

1️⃣ Open your **Kanban board** (e.g., Trello, GitHub Projects, or Jira).  
2️⃣ Find the story titled:

> 📝 **"Need to add security headers and CORS policies"**

3️⃣ 🛠️ Move the story to the **In Progress** column.  
4️⃣ 🙋 Assign the story to yourself.  
5️⃣ 📚 Open the story and **read its full contents**.

---

### 📌 Story Details

### 🎯 Title:  
**Need to add security headers and CORS policies**

### 👤 As a:
Service provider

### 🧩 I need:
My service to use **security headers** and **CORS policies**

### 🛡️ So that:
My website is not vulnerable to **CORS attacks**

---

### 💭 Assumptions

- ✅ `Flask-Talisman` will be used for adding **security headers**
- ✅ `Flask-CORS` will be used for managing **cross-origin resource sharing**

---

### 📋 Acceptance Criteria

| #️⃣ | Given | When | Then |
|----|-------|------|------|
| 1️⃣ | The site is secured | A REST API request is made | Secure headers and a valid CORS policy are returned |

---

### 🏁 Results

Once complete, your **Kanban board** should reflect:

- ✅ Story in **In Progress** column  
- ✅ Story **assigned to you**  
- ✅ Story content **reviewed and understood**

---

### 🔜 Next Step

You're now ready to:

➡️ Proceed to **Exercise 2**: Observe the Current Behavior  
This will help you compare the response **before and after** implementing Flask-Talisman!

🧠 Pro Tip: Screenshot your Kanban board with the story in **In Progress** — you'll need it later!

---

💡 *"Start with clarity. Deliver with security."*


Here’s a complete `README.md` in **Markdown format with emojis** that documents **Exercise 4: Add Security Headers** as part of your DevOps Capstone Lab workflow:


### 🔐 Exercise 4: Add Security Headers

In this exercise, you'll begin improving the security of your microservice by adding **Flask-Talisman**, which injects essential HTTP security headers into your REST API responses.

---

### 🧠 Objective

Apply security best practices to your Flask application by:

- ✅ Adding `Flask-Talisman` to your `requirements.txt`
- ✅ Installing the dependency
- ✅ Modifying your Flask app to include Talisman
- ✅ Validating the expected security headers using automated tests

---

### 🛠️ Your Task

### 📦 1. Add Flask-Talisman to `requirements.txt`
At the bottom of the file, add:
```txt
Flask-Talisman
````

---

### 📥 2. Install Requirements

Use the following command in your terminal:

```bash
pip install -r requirements.txt
```

---

### 🧩 3. Update the Flask App

Open the file:

```
./service/__init__.py
```

Then, do the following:

#### 🔁 Import Talisman

Add this import:

```python
from flask_talisman import Talisman
```

#### 🧬 Create Talisman Instance

After your Flask app is created, add:

```python
talisman = Talisman(app)
```

This wraps your Flask app with Talisman, enabling automatic security headers 🚀

---

### 🧪 4. Run Unit Tests

Test only your routes:

```bash
nosetests tests/test_routes.py
```

✅ Your **security headers test** should now **pass**
❌ Other route tests may **fail** due to enforced HTTPS (we'll fix this in Exercise 5)

---

### 🧾 Results

You should observe:

* ✅ `test_security_headers` **passes**
* ❌ Other tests may fail due to 302 redirects or missing HTTPS handling

No worries — you're on the right path! 🎯
We'll adjust Talisman to disable forced HTTPS during tests in the next exercise.

---

### 💬 Commit Your Work

Once this step is complete, don't forget to save your progress:

```bash
git commit -am "Added security headers"
```

---

### 🔜 Next Up

➡️ [Exercise 5: Disable Forced HTTPS](#) — Fix your broken tests so they pass during local testing.

---

🧠 *“Secure early, test always, and deploy with confidence.”*


### 🌐 Exercise 7: Add CORS Policies

Now that your microservice is secure with HTTP headers via Flask-Talisman, it's time to allow **Cross-Origin Resource Sharing (CORS)** using Flask-Cors — enabling your frontend or other services to interact with your API!

---

### ✅ Objectives

- ✍️ Write a unit test to validate CORS headers
- 📦 Add `Flask-Cors` to your project
- 🔧 Enable CORS in your Flask app
- 🧪 Run tests and verify success
- 📸 Capture evidence for screenshots

---

### 🧪 Step 1: Write the Test Case

Add the following to `tests/test_routes.py`:

```python
def test_cors_security(self):
    """It should return a CORS header"""
    response = self.client.get('/', environ_overrides=HTTPS_ENVIRON)
    self.assertEqual(response.status_code, status.HTTP_200_OK)
    # Check for the CORS header
    self.assertEqual(response.headers.get('Access-Control-Allow-Origin'), '*')
````

🧨 This test will **fail initially** because Flask hasn't been configured with CORS yet.

---

### 📦 Step 2: Add Flask-Cors

Update `requirements.txt`:

```txt
Flask-Cors
```

Then install the new dependency:

```bash
pip install -r requirements.txt
```

---

### 🔧 Step 3: Enable CORS in Your App

Edit `service/__init__.py`:

1. Import the library:

   ```python
   from flask_cors import CORS
   ```

2. Enable CORS **after Talisman is initialized**:

   ```python
   CORS(app)
   ```

This will allow cross-origin requests from **any domain** (using `*` wildcard).

---

### ✅ Step 4: Run All Tests

Run all tests again to verify:

```bash
nosetests
```

✅ Now **all tests should pass**, including your new `test_cors_security`.

---

### 💾 Step 5: Commit Your Changes

```bash
git commit -am "Added CORS headers"
```

---

### 🧪 Exercise 8: Validate CORS Headers

Let’s manually confirm that your service returns CORS headers!

---

### 🚀 Step 1: Start the Service

In one terminal, run:

```bash
honcho start
```

---

## 🔍 Step 2: Use curl to Check Headers

In a second terminal:

```bash
curl -I localhost:5000
```

You should see output like this:

```
HTTP/1.1 302 FOUND
Server: gunicorn
Date: Thu, 13 Oct 2022 20:18:54 GMT
Content-Type: text/html; charset=utf-8
Location: https://localhost:5000/
Access-Control-Allow-Origin: *
Permissions-Policy: browsing-topics=()
X-Frame-Options: SAMEORIGIN
X-Content-Type-Options: nosniff
Content-Security-Policy: default-src 'self'; object-src 'none'
Referrer-Policy: strict-origin-when-cross-origin
```

✅ Confirm the presence of the `Access-Control-Allow-Origin: *` header.

---

### 🛑 Step 3: Stop the Service

In the first terminal, stop the service by pressing:

```
Ctrl+C
```

(You might need to press it twice.)

---

### 🚀 Exercise 8 Continued: Make a Pull Request

You’ve now implemented and verified CORS headers — let’s commit, push, and make a PR.

---

### 🔄 Step 1: Confirm All Changes Are Committed

```bash
git status
```

If anything is uncommitted, do:

```bash
git add .
git commit -m "Added CORS headers"
```

---

### ☁️ Step 2: Push to Remote

```bash
git push -u origin <your-branch-name>
```

---

### 🔁 Step 3: Open a Pull Request

1. Go to your GitHub repo
2. Click **Compare & pull request**
3. Add a meaningful title and description
4. Click **Create pull request**

🎉 GitHub Actions will now run your tests automatically.

---

### 📸 Step 4: Take Screenshots for Submission

* `security-code-done.jpg`: Screenshot of `service/__init__.py`
* `security-headers-done.jpg`: Screenshot of terminal showing the curl output
* `security-kanban-done.jpg`: Screenshot of your Kanban board with the story in **Done**

---

### 🏁 Conclusion

Well done! 🎉 You've:

* ✅ Enabled CORS policies using Flask-Cors
* 🧪 Verified via tests and curl
* 🚀 Opened a pull request with CI
* 📸 Captured evidence for your submission

You're ready to move on to **Sprint 3** where you’ll tackle Docker, Kubernetes, and Tekton CD pipelines.

---












