# Project 2 — Role-Based Access Control (RBAC)

## Objective

Implement a group-based access control model in Microsoft Entra ID that assigns application access based on an employee's department.

## Business Scenario

Arkham Asylum Health requires a structured approach to application access. Employees should receive access appropriate to their department while minimizing unnecessary direct user assignments.

Department security groups are used to centralize application access and support consistent access management.

## Environment

- Microsoft Entra ID
- Microsoft Entra admin center
- Security groups
- Enterprise applications
- Group-based application assignment
- Simulated healthcare workforce

## RBAC Model

The access model follows:

**Department → Security Group → Enterprise Application → User Access**

Employees are assigned to department security groups. Department groups are then assigned to the applications required by each department.

This approach reduces the need for direct user-to-application assignments and provides a centralized access management model.

## Department Security Groups

| Department | Security Group | Employees |
|---|---|---:|
| IT | GRP-Dept-IT | 25 |
| Clinical Operations | GRP-Dept-ClinicalOperations | 20 |
| Finance | GRP-Dept-Finance | 15 |
| Human Resources | GRP-Dept-HumanResources | 15 |
| Compliance | GRP-Dept-Compliance | 10 |
| Sales | GRP-Dept-Sales | 10 |
| Executive | GRP-Dept-Executive | 5 |
| **Total** | | **100** |

All department groups were created as Microsoft Entra security groups with assigned membership.

**Note:** The group membership total exceeds the workforce count because Ava Johnson and Bruce Wayne were added as test users to the IT and Compliance groups respectively.

## Application Access Model

| Department | Security Group | Enterprise Application |
|---|---|---|
| IT | GRP-Dept-IT | Arkham IT Portal |
| Clinical Operations | GRP-Dept-ClinicalOperations | Arkham Clinical Portal |
| Finance | GRP-Dept-Finance | Arkham Finance Portal |
| Human Resources | GRP-Dept-HumanResources | Arkham HR Portal |
| Compliance | GRP-Dept-Compliance | Arkham Compliance Portal |
| Sales | GRP-Dept-Sales | Arkham Sales Portal |
| Executive | GRP-Dept-Executive | Arkham Executive Portal |

## Implementation

Department security groups were created in Microsoft Entra ID and populated with employees according to their department.

The department groups were then assigned to their corresponding enterprise applications.

The implementation uses group-based application assignment rather than assigning applications individually to each employee.

## Testing

Ava Johnson was used as the validation user for the IT access model.

The expected access relationship is:

**Ava Johnson → GRP-Dept-IT → Arkham IT Portal**

| Test | Expected Result | Status |
|---|---|---|
| Department groups created | Seven department groups available | Passed |
| Group membership | Employees assigned to appropriate groups | Passed |
| Group-to-application assignment | IT group assigned to IT Portal | Passed |
| User access relationship | Ava Johnson receives access through group membership | Passed |

## Security Control

### Risk

Direct application assignments to individual users can make access difficult to manage and review as employees change departments or responsibilities.

### Control

Department security groups are used as the access control layer between users and enterprise applications.

### Expected Benefit

Group-based access provides a centralized and repeatable method for managing application permissions and supports future access review and lifecycle management activities.

## Evidence

Evidence supporting the implementation is available in the [`evidence`](./evidence/) folder.

- [01-enterprise-applications.png](./evidence/01-enterprise-applications.png) — Enterprise applications configured in Microsoft Entra ID
- [02-department-security-groups.png](./evidence/02-department-security-groups.png) — Department security groups
- [03-it-group-membership.png](./evidence/03-it-group-membership.png) — IT department group membership
- [04-group-application-assignment.png](./evidence/04-group-application-assignment.png) — IT group-to-application assignment

## Outcome

A department-based RBAC model was implemented using Microsoft Entra ID security groups and enterprise applications.

The resulting model establishes a centralized foundation for managing application access based on department membership.

## Skills Demonstrated

**Microsoft Entra ID | RBAC | Security Groups | Group-Based Access | Enterprise Applications | Access Management | IAM Controls**
