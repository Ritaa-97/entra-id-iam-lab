# Joiner-Mover-Leaver (JML) Identity Lifecycle

## Objective

Demonstrate Joiner-Mover-Leaver (JML) identity lifecycle management in Microsoft Entra ID, including user provisioning, department-based access changes, and account deprovisioning.

## Business Scenario

Arkham Asylum Health uses Microsoft Entra ID to manage employee identities and department-based application access. This project simulates the identity lifecycle of a fictional employee through onboarding, internal transfer, and offboarding.

## Environment

- Microsoft Entra ID
- Security groups for department-based access
- Group-based application assignments
- Arkham Asylum Health simulated environment

## JML Model

**Joiner:** Create user → Assign department group → Grant application access

**Mover:** Update department/role → Remove previous group → Assign new department group → Update application access

**Leaver:** Disable account → Remove group membership → Remove application access

## Joiner

Created **Harley Quinn** as a Clinical Operations Analyst and assigned her to `GRP-Dept-ClinicalOperations`, providing access to the Arkham Clinical Portal.

## Mover

Transferred Harley Quinn from Clinical Operations to Compliance by updating her job title and department, removing her previous group membership, and assigning `GRP-Dept-Compliance`.

Her application access changed from the **Arkham Clinical Portal** to the **Arkham Compliance Portal**.

## Leaver

Disabled Harley Quinn's Entra account and removed her remaining department group membership, resulting in no application assignments.

## Security Controls

- Role-based access through security groups
- Least-privilege access based on department
- Removal of previous access during department transfers
- Account disablement during offboarding
- Removal of group and application access

## Evidence

### Joiner

- [Joiner user creation](./evidence/01-joiner-user-creation.png)
- [Joiner group assignment](./evidence/02-joiner-group-assignment.png)

### Mover

- [Mover before](./evidence/03-mover-before.png)
- [Mover after](./evidence/04-mover-after.png)

### Leaver

- [Leaver account disabled](./evidence/05-leaver-account-disabled.png)
- [Leaver access removed](./evidence/06-leaver-access-removed.png)

## Outcome

Successfully demonstrated a complete JML lifecycle in Microsoft Entra ID, including identity provisioning, role-based access changes, and secure employee offboarding.
