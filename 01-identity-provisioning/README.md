# Identity Provisioning 

## Objective 

Create and Provision Simulated workforce of 100 fictional employees in Microsoft Entra ID
## Business Scenario 

Arkham Asylum Health requires a centralized identity platform to manage employees across multiple departments and support standardized identity and access management processes 

##Environment  

-Microsoft Entra ID
-Microsoft Entra Admin Center
-Bulk User Provisioning 
CSV-based identity data 

##Employee Population

The 100 simulated employees are distributed across departments as follow: 
- IT: 25 employees
- Clinical Operations: 20 Employees
- Finance: 15 Employees
- Compliance: 10 employees
- Sales: 10 employees
- Executive Leadership: 5 employees

##Employee Attributes

The Simulated employee dataset contains: 
- Employee Id
- First Name
- Last name
- Display Name
- User Principal Name
- Department
- Job Title
- Manager
- Location
- Access Tier
- Initial Access

  ##Implementation

  Users were provisioned in Microsoft Entra ID two methods:
  - Bulk provisioning via CSV import for the primary workforce of 100 user
  - Manual provisioning of a single test user to validate identity creation
 
  The manual User was created directly in the Microsoft Entra Admin Center

  ##Testing
  | Test | Expected Result | Status|
  |---|---|---|
  | 100 Users Submitted | 100 Users processed | Pending|
  | User Creation | User Created successfully | Pending
  | UPN validation | Valid tenant UPN | Pending |
  | Employee ID validation | Unique IDs | Pending |
  | Department validation | Correct department assigned | Pending |
  | Manual user creation | User successfully created in Entra ID | Pending |
  | Attribute consistency | Manual user matches schema structure | Pending |
  

  ##Security Considerations

  All employees in this project are fictional.
  No real employee, patient, password, or sensitive healthcare information

  ##Evidence
  Screenshots will be captured and documented at each stage of the implementation to provide evidence of successful identity provisioning in Microsoft Entra ID

  The following screenshots will be included:
  - Bulk User Import Process (CSV upload screen in Microsoft Entra Admin Center)
  - Successful Processing summary showing number of user created
  - Sample Usr profile from Entra ID demonstrating attribute mapping (Employee ID, Department, Job Title, UPN)
  - Directory User list conforming all 100 accounts exists
  - Manual User test creation workflow in Entra Admin center
  - Validation of Unique Employee ID assignment across all Users
 
  Each screenshot will be labeled and stored in the /evidence/identity-provisioning/ directory within the GitHub repository to ensure compliance, audit readiness, and full traceability of the provisioning process.

  
