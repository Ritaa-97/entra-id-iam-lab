# Identity Provisioning 

## Objective 

Create and provision a simulated workforce of 100 fictional employees in Microsoft Entra ID.
## Business Scenario 

Arkham Asylum Health requires a centralized identity platform to manage employees across multiple departments and support standardized identity and access management processes 

## Environment  

- Microsoft Entra ID
- Microsoft Entra Admin Center
- Bulk User Provisioning
- CSV-based identity data 

## Employee Population

The 100 simulated employees are distributed across departments as follow: 
- IT: 25 employees
- Clinical Operations: 20 Employees
- Finance: 15 Employees
- Human Resources : 15
- Compliance: 10 employees
- Sales: 10 employees
- Executive: 5 employees
**Total: 100 Employees**

## Employee Attributes

The simulated employee dataset contains attributes used to establish and manage employee identities:

- Employee ID — unique organizational identifier
- First Name
- Last name
- Display Name
- User Principal Name (UPN)
- Department _ supports future access decisions
- Job Title - identifies the employee's roles
- Manager - supports identity life cycle scenarios 
- Location
- Access Tier
- Initial Access

  ## Identity Provisioning Approach

  Arkham Asylum Health uses Microsoft Entra ID as its centralized identity platform. Two provisioning approaches are demonstrated in this lab:
  1. Manual User Provisioning
  2. Bulk User Provisioning
  
  Manual provisioning demonstrates the process of creating and validating an individual employee identity.
  Bulk provisioning demonstrates how identity creation can be scaled across a larger workforce using structured CSV data.

  The provisioning workflow is:
  
    HR Employee Data
            ↓
    Attribute Mapping
            ↓
    Identity Provisioning
            ↓
    Microsoft Entra ID
            ↓
    Identity Validation

  ## Manual Usr Provisioning
  A single fictional employee was manually provisioned in Microsoft Entra ID to validate the individual identity creation process before performing bulk provisioning.
  The test identity, Ava Johnson (EMP001), was created using attributes from the simulated HR employee dataset.
  The manually provisioned identity was validated for:
  - Display Name: Ava Johnson
  - Employee ID: EMP001
  - User Principal Name (UPN)
  - Department: IT
  - Job Title: Help Desk Analyst
  - Employee Type: Full-Time
  - Employee Hire Date: September 1, 2026
  - Office Location: Austin, TX
  - Company Name: Arkham Asylum Health
  - Usage Location: United States
  - Account Status: Enabled
 
  ## Manual Provisioning Evidence
  The following evidence documents the manual identity provisioning and validation process:
  - [Manual user validation](evidence/01-manual-user-validation.png)
  - [Manual provisioning result](evidence/02-manual-provisioning-result.png)
  - [Manual provisioning configuration](evidence/03-manual-provisioning-configuration.png)
  

 
## Provisioning Result 

**Status:** Passed

The Entra user profile was reviewed after creation to confirm that the expected identity and employment attributes were successfully populated.
 
## Bulk User Provisioning 

After validating the manual provisioning process, Microsoft Entra ID bulk creation is used to provision the remaining stimulated workforce using structured CSV data. 
the Bulk Provisioning process includes: 

- Preparing employee data
- Mapping source attribute to Microsoft Entra fields
- Validating the provisioning CSV
- Uploading the CSV to Microsoft Entra ID
- Reviewing the Bulk operation Results
- Validating provisioned attributes

## Bulk Provisioning Result

**Status:** Passed
The bulk provisioning operation successfully created the remaining simulated employee identities in Microsoft Entra ID.
The resulting user population was reviewed in the Entra Admin Center to confirm that the expected identities were created and available in the directory.

### Bulk Provisioning Evidence
The following evidence documents the bulk provisioning and validation process:

- [Bulk provisioning result](evidence/04-bulk-provisioning-result.png)
- [Bulk user attribute validation](evidence/05-bulk-user-attribute-validation.png)

  ##Testing
  | Test | Expected Result | Status|
  |---|---|---|
  | 100 Users Submitted | 100 Users processed | Pending|
  | User Creation | User Created successfully | Pending
  | UPN validation | Valid tenant UPN | Pending |
  | Employee ID validation | Unique IDs | Pending |
  | Department validation | Correct department assigned | Pending |
  | Manual user creation | User successfully created in Entra ID | Pass |
  | Attribute consistency | Manual user matches schema structure | Pending |
  

  ## Security Considerations

  All employees in this project are fictional.
  No real employee, patient, password, or sensitive healthcare information

  ## Evidence
  Screenshots will be captured and documented at each stage of the implementation to provide evidence of successful identity provisioning in Microsoft Entra ID

  The following screenshots will be included:
  - Bulk User Import Process (CSV upload screen in Microsoft Entra Admin Center)
  - Successful Processing summary showing number of user created
  - Sample Usr profile from Entra ID demonstrating attribute mapping (Employee ID, Department, Job Title, UPN)
  - Directory User list conforming all 100 accounts exists
  - Manual User test creation workflow in Entra Admin center
  - Validation of Unique Employee ID assignment across all Users
 
  Each screenshot will be labeled and stored in the /evidence/identity-provisioning/ directory within the GitHub repository to ensure compliance, audit readiness, and full traceability of the provisioning process.

  
