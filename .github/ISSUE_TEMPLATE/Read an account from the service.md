### **2. Read an Account from the Service**

---

| name                        | about                                                                                         | title                                  | labels   | assignees |
|-----------------------------|-----------------------------------------------------------------------------------------------|----------------------------------------|----------|-----------|
| Read an Account from the Service | Implement functionality to retrieve a customer account from the service.                    | "[FEATURE] Read an Account from the Service" |          |           |

<br>

> [!IMPORTANT]  
> **Regarding 'Feature Description' and 'Acceptance Criteria':**  
> Always use the same syntax!!! Consistency is key.  
> It ensures better clarity and easier testing.  
> Use Gherkin-Syntax.  
> For example:  
> 
> Given [some context]  
> When [certain action is taken]  
> Then [the outcome of action is observed]  

<br>

## **Feature Description:**

**Feature**: Read Customer Account

**As a** customer service agent  
**I need** to retrieve a customer account from the service using an account ID  
**So that** I can view customer details like name and address.

<br><br>

## **Details and Assumptions:**

- Accounts are identified by a unique customer ID.  
- The service must return the account details (name, address, email).  
- Error handling must be implemented for invalid IDs.

<br><br>

## **Acceptance Criteria:**

```gherkin
Given that a customer account exists with valid details  
When I request the account using a valid customer ID  
Then the system should return the correct customer details  
And the status code should be "200 OK"
```

