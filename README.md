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







