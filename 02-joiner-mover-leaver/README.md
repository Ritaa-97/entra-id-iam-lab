# Project 2 — Joiner, Mover, Leaver (JML)

## Objective 

Simulate the employee identity lifecycle within Microsoft Entra ID by implementing Joiner, Mover, and Leaver scenarios for Arkham Asylum Health 

## Business Scenario 

Arkham Asylum Health requires a controlled identity lifecycle process to ensure employees receive appropriate access when they join the organization, have access updated when they change jobs or department, and have access removed when they leave the organization. 

## Environment 

- Microsoft Entra ID
- Arkham Asylum Health Fictional Workforce
- GitHub
- Stimulated HR Employee Data 

## Joiner Scenario 

A new employee joining Arkham Asylum Heath requires an identity to be created in Microsoft Entra ID with the appropriate employment attributes and baseline access. 

##Joiner Test Employee 

| Attributes | Value | 
|---|---|
| Employee ID | EMP101 |
| Display Name | Bruce Wayne | 
| Department | Compliance | 
| Job Title | Compliance Analyst | 
| Office Location | Austin, TX | 
| Hire Date | September 15, 2026 | 
| Usage Location | United States | 
| Initial Access | Compliance-App | 

## Expected Outcome 
The new employee identity should be created in Microsoft Entra ID with the expected identity and employment attributes. Baseline access should be aligned with the employee's department and job function.
