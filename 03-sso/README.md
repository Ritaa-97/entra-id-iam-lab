# Project 3 — Single Sign-On (SSO) with Microsoft Entra ID and SAML

## Objective

Configure and document a Single Sign-On (SSO) authentication model using Microsoft Entra ID and Security Assertion Markup Language (SAML).

This project demonstrates how Microsoft Entra ID can act as an **Identity Provider (IdP)** and authenticate users before granting access to a SAML-enabled enterprise application.

The project also demonstrates group-based application assignment, SAML claims, SP-initiated authentication, and authentication troubleshooting using Microsoft Entra sign-in logs.

---

## Business Scenario

**Arkham Asylum Health** wants employees to use centralized identity and authentication when accessing organizational applications.

Instead of maintaining separate application credentials, employees authenticate through Microsoft Entra ID.

Centralized authentication allows the organization to:

* Manage user identities from a central directory
* Control application access through group membership
* Apply authentication policies consistently
* Reduce the need for separate application credentials
* Monitor authentication activity through Microsoft Entra sign-in logs
* Establish a foundation for stronger controls such as MFA and Conditional Access

---

## Environment

* Microsoft Entra ID
* Microsoft Entra admin center
* Microsoft Entra Enterprise Applications
* Microsoft Entra SAML Toolkit
* Microsoft Entra user identities
* Microsoft Entra groups
* SAML 2.0
* Microsoft Entra Sign-in Logs

---

## Authentication Model

The SAML authentication flow implemented in this project follows:

```text
User
  |
  v
Microsoft Entra SAML Toolkit
  |
  v
SAML Authentication Request
  |
  v
Microsoft Entra ID
  |
  v
User Authentication
  |
  v
SAML Assertion
  |
  v
Microsoft Entra SAML Toolkit
  |
  v
Authenticated Application Session
```

### Identity Provider

**Microsoft Entra ID** acts as the Identity Provider (IdP).

The IdP is responsible for authenticating the user and issuing the SAML assertion.

### Service Provider

**Microsoft Entra SAML Toolkit** acts as the Service Provider (SP).

The SP relies on Microsoft Entra ID to authenticate the user.

---

## Enterprise Application

The SSO demonstration application used in this project is:

**Microsoft Entra SAML Toolkit**

The application was configured as a SAML-based enterprise application in Microsoft Entra ID.

The application uses Microsoft Entra ID as its Identity Provider and the SAML Toolkit as the Service Provider.

---

## Group-Based Application Assignment

Access to the SAML Toolkit enterprise application was controlled through an existing Microsoft Entra security group:

`GRP-Dept-IT`

The group was assigned to the Microsoft Entra SAML Toolkit enterprise application.

This establishes the following access model:

```text
User
  |
  v
GRP-Dept-IT
  |
  v
Microsoft Entra SAML Toolkit
```

Group-based assignment allows application access to be managed through group membership rather than assigning users individually to the enterprise application.

---

## SAML Configuration

The Microsoft Entra SAML Toolkit was configured using SAML-based Single Sign-On.

### Entity ID

```text
https://samltoolkit.azurewebsites.net
```

### Assertion Consumer Service (ACS) URL

The Toolkit generated a unique ACS endpoint:

```text
https://samltoolkit.azurewebsites.net/SAML/Consume/22158
```

The ACS URL is the endpoint where the Service Provider receives the SAML assertion from Microsoft Entra ID.

### SP-Initiated Sign-On URL

The Toolkit generated the following SP-initiated login endpoint:

```text
https://samltoolkit.azurewebsites.net/SAML/Login/22158
```

This endpoint initiates the SAML authentication process from the Service Provider.

---

## Identity Provider Configuration

Microsoft Entra ID provided the following information to the SAML Toolkit:

* Microsoft Entra Login URL
* Microsoft Entra Identifier
* Microsoft Entra Logout URL
* Token-signing certificate

The raw token-signing certificate was downloaded from Microsoft Entra and uploaded into the SAML Toolkit configuration.

The certificate allows the Service Provider to validate the SAML assertion issued by Microsoft Entra ID.

---

## SAML Attributes and Claims

The SAML application was configured with standard identity claims.

| Claim                            | Source                   |
| -------------------------------- | ------------------------ |
| Unique User Identifier (Name ID) | `user.userprincipalname` |
| `emailaddress`                   | `user.mail`              |
| `givenname`                      | `user.givenname`         |
| `surname`                        | `user.surname`           |
| `name`                           | `user.userprincipalname` |

These claims allow identity information from Microsoft Entra ID to be passed to the SAML application as part of the authentication response.

---

## Test User

An existing Microsoft Entra test user within the assigned IT group was used to validate the SSO configuration.

The corresponding user was also registered within the SAML Toolkit using the matching Microsoft Entra identity.

This created the relationship:

```text
Microsoft Entra User
        |
        v
   GRP-Dept-IT
        |
        v
Enterprise Application
        |
        v
Microsoft Entra Authentication
        |
        v
SAML Assertion
        |
        v
SAML Toolkit User
```

No additional Microsoft Entra user was created specifically for the SSO test.

---

## SSO Testing

The SSO flow was tested using an SP-initiated authentication process.

### Test Procedure

1. Opened the Microsoft Entra SAML Toolkit.
2. Navigated to the SAML login page.
3. Selected **Log in**.
4. The Toolkit initiated authentication with Microsoft Entra ID.
5. Microsoft Entra authenticated the assigned test user.
6. Microsoft Entra issued the SAML authentication response.
7. The user was redirected back to the SAML Toolkit.
8. The Toolkit authenticated the user and displayed the application homepage.
9. Microsoft Entra Sign-in Logs were reviewed to verify the authentication event.

---

## Test Results

| Test                                   | Expected Result                                        | Status   |
| -------------------------------------- | ------------------------------------------------------ | -------- |
| SAML enterprise application configured | SAML configuration available                           | ✅ Passed |
| Group-based application assignment     | `GRP-Dept-IT` assigned to application                  | ✅ Passed |
| SAML Toolkit configuration             | Toolkit configured with Entra IdP information          | ✅ Passed |
| SAML claims configuration              | Required identity claims configured                    | ✅ Passed |
| SP-initiated SSO                       | User redirected through Microsoft Entra authentication | ✅ Passed |
| Application authentication             | Test user successfully authenticated into SAML Toolkit | ✅ Passed |
| Entra sign-in verification             | Successful Toolkit sign-in recorded in Entra logs      | ✅ Passed |

---

## Troubleshooting

### Initial Authentication Attempt

The initial authentication attempt did not complete successfully.

Microsoft Entra Sign-in Logs showed the authentication event as **Interrupted**.

The authentication details identified the cause as an expired password for the test user.

### Resolution

The test user's password was updated and the authentication process was performed again.

The SSO flow was then successfully completed.

A subsequent Microsoft Entra Sign-in Log showed:

**Application:** Microsoft Entra SAML Toolkit
**Status:** Success

This confirmed that the authentication issue was related to the test user's password state rather than the SAML configuration.

### Troubleshooting Approach

The issue was investigated using Microsoft Entra Sign-in Logs rather than changing the SAML configuration unnecessarily.

```text
SSO Test
   |
   v
Authentication Interrupted
   |
   v
Review Entra Sign-in Logs
   |
   v
Identify Password Expiration
   |
   v
Update Test User Password
   |
   v
Retest SSO
   |
   v
Successful Authentication
```

This demonstrates the use of identity-provider logging to troubleshoot authentication failures.

---

## Security Considerations

Centralized authentication provides a consistent authentication model and allows identity controls to be managed through Microsoft Entra ID.

Security considerations for this implementation include:

* Group-based application assignment
* Centralized authentication
* SAML assertion signing
* Token-signing certificate validation
* Identity claim control
* Authentication monitoring through sign-in logs
* Separation of administrative and test identities
* Password and authentication lifecycle management

No passwords, authentication tokens, client secrets, private keys, or other authentication credentials are stored in the GitHub repository.

Tenant-specific information should be sanitized before publishing the repository publicly.

Screenshots containing unnecessary tenant identifiers, usernames, IP addresses, request IDs, or other sensitive information should be redacted before publication.

---

## Evidence

The following evidence documents the implementation and validation of the SSO configuration.

| Evidence                                   | Description                                            |
| ------------------------------------------ | ------------------------------------------------------ |
| `01-basic-saml-configuration.png`          | Basic SAML configuration                               |
| `02-group-assignment.png`                  | Group-based application assignment                     |
| `03-entra-idp-configuration.png`           | Microsoft Entra Identity Provider configuration        |
| `04-saml-toolkit-configuration.png`        | SAML Toolkit configuration                             |
| `05-attributes-and-claims.png`             | SAML attributes and claims                             |
| `06-successful-sso.png`                    | Successful SAML Toolkit authentication                 |
| `07-successful-entra-sign-in.png`          | Successful Microsoft Entra sign-in                     |
| `08-troubleshooting-interrupted-login.png` | Initial interrupted authentication and troubleshooting |

---

## Skills Demonstrated

This project demonstrates practical experience with:

* Microsoft Entra ID
* Identity and Access Management (IAM)
* Enterprise Applications
* SAML 2.0
* Single Sign-On (SSO)
* Identity Provider (IdP) configuration
* Service Provider (SP) configuration
* SAML assertions
* SAML claims
* Name ID configuration
* Group-based application assignment
* User access management
* Token-signing certificates
* Authentication troubleshooting
* Microsoft Entra Sign-in Logs
* Security monitoring
* Authentication lifecycle management

---

## Outcome

The Microsoft Entra SAML Toolkit was successfully configured as a SAML enterprise application using Microsoft Entra ID as the Identity Provider.

A test user assigned through `GRP-Dept-IT` successfully authenticated through Microsoft Entra ID and accessed the SAML Toolkit.

The successful authentication was verified through both:

1. The SAML Toolkit application
2. Microsoft Entra Sign-in Logs

An initial authentication interruption was also investigated and resolved using Microsoft Entra Sign-in Logs.

The completed project demonstrates a practical SAML-based SSO implementation and provides a foundation for implementing additional IAM controls such as MFA, Conditional Access, application governance, and authentication monitoring.
