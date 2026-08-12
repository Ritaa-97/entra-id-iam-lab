# Project 3 — Single Sign-On (SSO)

## Objective

Configure and document a Single Sign-On (SSO) authentication model using Microsoft Entra ID and an enterprise application.

The project demonstrates how users authenticate through Microsoft Entra ID before accessing an enterprise application.

## Business Scenario

Arkham Asylum Health wants employees to use centralized identity and authentication when accessing organizational applications.

Instead of maintaining separate application credentials, users authenticate through Microsoft Entra ID.

## Environment

- Microsoft Entra ID
- Microsoft Entra admin center
- Enterprise applications
- Microsoft Entra user identities
- Single Sign-On

## Authentication Model

The authentication flow follows:

User
↓
Microsoft Entra ID
↓
Authentication
↓
MFA
↓
Enterprise Application
↓
Application Access

Microsoft Entra ID serves as the centralized identity provider for the application.

## Enterprise Application

The existing Arkham Compliance Portal will be used as the SSO demonstration application.

Application:

`Arkham Compliance Portal`

The application was previously configured for group-based access through:

`GRP-Dept-Compliance`

## Implementation

The enterprise application will be configured to use Microsoft Entra ID for authentication.

The SSO configuration will be documented without exposing passwords, authentication secrets, tokens, client secrets, or other sensitive information.

## Authentication Testing

The following scenarios will be tested:

| Test | Expected Result | Status |
|---|---|---|
| Application configured for SSO | SSO configuration available | Pending |
| Authorized user authentication | User successfully authenticates | Pending |
| Application access | Authorized user can access application | Pending |
| Unauthorized user access | User without application assignment cannot access application | Pending |
| MFA authentication | MFA requirement is demonstrated where configured | Pending |

## Security Considerations

Centralized authentication provides a consistent authentication experience and allows identity controls to be managed through Microsoft Entra ID.

No passwords, tokens, client secrets, private keys, or other authentication credentials will be stored in the GitHub repository.

Tenant-specific information should be sanitized before publishing the repository publicly.

## Evidence

Screenshots documenting the SSO implementation and testing will be stored in the `evidence` folder.

Evidence will include:

- Enterprise application SSO configuration
- Authentication configuration
- Successful authentication test
- Application access validation
- Unauthorized access test where applicable

## Outcome

The project will demonstrate centralized authentication through Microsoft Entra ID and establish the foundation for stronger authentication controls such as MFA and Conditional Access.
