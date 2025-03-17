### **3. Update an Account in the Service**

---

| name                        | about                                                                                           | title                                    | labels   | assignees |
|-----------------------------|-------------------------------------------------------------------------------------------------|------------------------------------------|----------|-----------|
| Update an Account in the Service | Implement functionality to update an existing customer account in the service.               | "[FEATURE] Update an Account in the Service" |          |           |

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

**Feature**: Update Customer Account

**As a** customer service agent  
**I need** to be able to update an existing customer account's information  
**So that** I can keep the customer's details accurate and up-to-date.

<br><br>

## **Details and Assumptions:**

- Customer information (e.g., address, email) can be modified.  
- Only authorized users should be able to update accounts.  
- The system should return a success message after the update.

<br><br>

## **Acceptance Criteria:**

```gherkin
Given that a customer account exists with outdated details  
When I update the account with new, valid details  
Then the system should save the updated information  
And return a "200 OK" response confirming the update
```
