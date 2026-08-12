# Project 3 — Single Sign-On (SSO)

## Objective

Configure Single Sign-On (SSO) using **Microsoft Entra ID** and **SAML 2.0**.

## Environment

* Microsoft Entra ID
* Enterprise Applications
* Microsoft Entra SAML Toolkit
* SAML 2.0
* Microsoft Entra Sign-in Logs

## Implementation

* Created the **Microsoft Entra SAML Toolkit** enterprise application.
* Configured SAML **Entity ID, ACS URL, and Sign-on URL**.
* Configured SAML attributes and claims.
* Assigned the application to `GRP-Dept-IT`.
* Registered a matching test user in the SAML Toolkit.
* Configured the Entra token-signing certificate.
* Tested SP-initiated SSO.

## Authentication Flow

**User → SAML Toolkit → Microsoft Entra ID → Authentication → SAML Assertion → SAML Toolkit → Access Granted**

## Testing

| Test                       | Result   |
| -------------------------- | -------- |
| SAML configuration         | ✅ Passed |
| Group-based assignment     | ✅ Passed |
| SSO authentication         | ✅ Passed |
| Application access         | ✅ Passed |
| Entra sign-in verification | ✅ Passed |

## Troubleshooting

The initial authentication attempt was interrupted because the test user's password had expired.

The issue was identified using **Microsoft Entra Sign-in Logs**. After updating the user's password, the SSO test was successful.

## Evidence

## Evidence

Screenshots documenting the SSO implementation and validation are stored in the `evidence` folder.

- [01-saml-configuration.png](./evidence/01-saml-configuration.png) — Microsoft Entra SAML configuration
- [02-group-assignment.png](./evidence/02-group-assignment.png) — Group-based application assignment
- [03-saml-toolkit-configuration.png](./evidence/03-saml-toolkit-configuration.png) — SAML Toolkit configuration
- [04-attributes-claims.png](./evidence/04-attributes-claims.png) — SAML attributes and claims
- [05-successful-sso.png](./evidence/05-successful-sso.png) — Successful SSO authentication
- [06-sign-in-success.png](./evidence/06-sign-in-success.png) — Successful Microsoft Entra sign-in
- [07-troubleshooting.png](./evidence/07-troubleshooting.png) — Initial authentication troubleshooting

## Skills Demonstrated

**Microsoft Entra ID | IAM | SAML 2.0 | SSO | Enterprise Applications | Group-Based Access | SAML Claims | Authentication Troubleshooting | Sign-in Logs**

## Outcome

Successfully implemented and validated **SAML-based SSO using Microsoft Entra ID**, including troubleshooting an authentication failure using Entra sign-in logs.
