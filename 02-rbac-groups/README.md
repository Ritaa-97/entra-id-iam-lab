# Role-Based Access Control (RBAC)

## Objective

Implement a group-based access control model in Microsoft Entra ID that assigns application access based on an employee's department rather than assigning access directly to individual users.

## Business Scenario

Arkham Asylum Health requires a structured approach to application access. Employees should receive access appropriate to their department while minimizing unnecessary direct user assignments.

The access model uses Microsoft Entra security groups to centralize access management and support least-privilege principles.

## Environment

- Microsoft Entra ID
- Microsoft Entra admin center
- Security groups
- Enterprise applications
- Group-based application assignment

## Access Model

The RBAC model follows:

Department
↓
Security Group
↓
Enterprise Application
↓
User Access

Employees are assigned to department security groups. The department groups are then assigned to the applications required by that department.

This approach reduces the need for individual application assignments and provides a more manageable access governance structure.

## Department Security Groups

| Department | Security Group | Members |
|---|---|---:|
| IT | GRP-Dept-IT | 25 |
| Clinical Operations | GRP-Dept-ClinicalOperations | 20 |
| Finance | GRP-Dept-Finance | 15 |
| Human Resources | GRP-Dept-HR | 15 |
| Compliance | GRP-Dept-Compliance | 10 |
| Sales | GRP-Dept-Sales | 10 |
| Executive | GRP-Dept-Executive | 5 |
| **Total** | | **100** |

The workforce consists of 99 bulk-provisioned users and one manually provisioned test user, Ava Johnson. Ava was assigned to the IT department group.

## Application Access Model

| Department | Security Group | Application | Access Model |
|---|---|---|---|
| IT | GRP-Dept-IT | Arkham IT Portal | Group-based |
| Clinical Operations | GRP-Dept-ClinicalOperations | Arkham Clinical Portal | Group-based |
| Finance | GRP-Dept-Finance | Arkham Finance Portal | Group-based |
| Human Resources | GRP-Dept-HR | Arkham HR Portal | Group-based |
| Compliance | GRP-Dept-Compliance | Arkham Compliance Portal | Group-based |
| Sales | GRP-Dept-Sales | Arkham Sales Portal | Group-based |
| Executive | GRP-Dept-Executive | Arkham Executive Portal | Group-based |

## Implementation

Department security groups were created in Microsoft Entra ID using:

- Group type: Security
- Membership type: Assigned

Users were added to the security group corresponding to their department.

The department security groups were then assigned to their corresponding enterprise applications.

Individual users were not directly assigned to the applications.

## Access Validation

Ava Johnson was used as the test user for IT access validation.

Validation confirmed:

Ava Johnson
↓
GRP-Dept-IT
↓
Arkham IT Portal

The user was a member of the IT security group, while the IT security group was assigned to the Arkham IT Portal.

This demonstrates that application access is inherited through group membership rather than being directly assigned to the user.

## Security Control

### Risk

Directly assigning application access to individual users can create:

- Access sprawl
- Inconsistent permissions
- Difficult access reviews
- Increased administrative overhead
- Potential access remaining after departmental changes

### Control

Department-based security groups are used as the access control layer between users and applications.

### Expected Benefit

Centralized group-based access makes permissions easier to manage, review, modify, and revoke.

## Testing

| Test | Expected Result | Status |
|---|---|---|
| Department groups created | Seven security groups exist | Pass |
| Users assigned to department groups | Users belong to appropriate department group | Pass |
| Application group assignment | Applications assigned to department groups | Pass |
| Direct application assignment | Users are not directly assigned to applications | Pass |
| IT access validation | Ava receives IT application access through group membership | Pass |
| Group-based access model | User → Group → Application relationship confirmed | Pass |

## Evidence

Screenshots documenting the RBAC implementation include:

- Department security group membership
- Compliance group application assignment
- Finance group application assignment
- IT group application assignment
- Ava Johnson IT group membership
- Application Users and groups configuration

## Security Considerations

The project uses fictional employee identities and simulated applications.

No passwords, access tokens, client secrets, private keys, or other authentication credentials should be included in the repository.

Tenant-specific information should be sanitized before publishing the repository publicly.

## Outcome

A department-based RBAC model was implemented in Microsoft Entra ID using security groups and group-based enterprise application assignments.

The resulting model provides a centralized approach to application access and establishes the foundation for future Joiner-Mover-Leaver, access review, and IAM audit activities.
