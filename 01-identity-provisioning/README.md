# Project 1 — Identity Provisioning

## Objective

Create and provision a simulated workforce of 100 fictional employees in Microsoft Entra ID.

## Business Scenario

Arkham Asylum Health requires a centralized identity platform to manage employees across multiple departments and support standardized identity and access management processes.

## Environment

- Microsoft Entra ID
- Microsoft Entra admin center
- Bulk user provisioning
- CSV-based identity data

## Employee Population

The simulated workforce consists of 100 employees across seven departments:

| Department | Employees |
|---|---:|
| IT | 25 |
| Clinical Operations | 20 |
| Finance | 15 |
| Human Resources | 15 |
| Compliance | 10 |
| Sales | 10 |
| Executive | 5 |
| **Total** | **100** |

## Implementation

Two identity provisioning methods were demonstrated:

1. Manual user provisioning
2. Bulk user provisioning

Manual provisioning was used to validate the identity creation process using Ava Johnson (EMP001). After validation, the remaining simulated workforce was provisioned using Microsoft Entra ID bulk creation and structured CSV data.

Key identity attributes included:

- Employee ID
- Display Name
- User Principal Name (UPN)
- Department
- Job Title
- Manager
- Location
- Access Tier

## Testing

| Test | Expected Result | Status |
|---|---|---|
| Manual user creation | Identity created successfully | Passed |
| Attribute validation | Expected attributes populated | Passed |
| Bulk provisioning | Remaining users created successfully | Passed |
| Directory validation | Provisioned users available in Entra ID | Passed |
| Employee ID validation | Unique employee identifiers maintained | Passed |

## Results

100 fictional employee identities were successfully provisioned into Microsoft Entra ID.

Manual provisioning was validated before bulk provisioning to confirm the expected identity attributes and provisioning process.

## Evidence

### Manual Provisioning

- [01-manual-user-validation.png](./evidence/01-manual-user-validation.png) — Manual user validation
- [02-manual-provisioning-result.png](./evidence/02-manual-provisioning-result.png) — Manual provisioning result
- [03-manual-provisioning-configuration.png](./evidence/03-manual-provisioning-configuration.png) — Manual provisioning configuration

### Bulk Provisioning

- [04-bulk-provisioning-result.png](./evidence/04-bulk-provisioning-result.png) — Bulk provisioning result
- [05-bulk-user-attribute-validation.png](./evidence/05-bulk-user-attribute-validation.png) — Bulk user attribute validation

## Security Considerations

All identities used in this project are fictional. No real employee, patient, password, credential, or sensitive healthcare information is included.

## Lessons Learned

The project demonstrated the importance of validating identity data before account creation. Manual validation followed by bulk provisioning helped establish a consistent and scalable identity provisioning process.

## Skills Demonstrated

**Microsoft Entra ID | Identity Provisioning | Bulk User Management | CSV Provisioning | Attribute Mapping | Identity Validation | IAM Controls | Audit Evidence**







  
