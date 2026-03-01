# Lab 02: Zero Trust Policy Profile

## 1. ZTA Component Definitions

### Policy Engine (PE)
The Policy Engine is the decision-making component of a Zero Trust Architecture. It evaluates every access request by analyzing multiple security signals such as user identity, assigned role, device security status, and contextual risk factors. Based on predefined organizational policies, it determines whether access should be allowed, denied, or require additional verification. The Policy Engine does not directly grant access — it makes the logical decision.

### Policy Administrator (PA)
The Policy Administrator acts as the coordinator that carries out the decision made by the Policy Engine. When access is approved, the PA generates secure session credentials or tokens and configures the necessary systems to allow communication. If access is denied, it ensures the user session is blocked. It essentially translates policy decisions into technical actions.

### Policy Enforcement Point (PEP)
The Policy Enforcement Point is the component that sits between the user and the protected resource. It enforces the final decision provided by the Policy Engine. If access is authorized, it permits traffic to the HR database. If access is denied, it blocks the connection attempt. It ensures that no user can bypass policy controls.

---

## 2. Core Principle Application

**Chosen Principle:** Verify Explicitly  

**Explanation:**
The Policy Engine enforces the principle of "Verify Explicitly" by requiring multiple independent verification checks before granting access to sensitive HR employee PII data. Instead of trusting a user simply because they are inside the corporate network, the system validates identity, device security posture, and contextual information for every access attempt.

**Specific Example:**
If an HR Benefits Coordinator attempts to access the employee PII database at the Golden State Water Treatment Facility, the Policy Engine evaluates:

- Whether the user successfully authenticated using multi-factor authentication (MFA)
- Whether the user’s account is assigned an approved HR role
- Whether the device is compliant with company security policies (encryption enabled and endpoint protection active)
- Whether the login attempt matches normal working hours

Only when all verification checks pass does the Policy Engine approve access. If any signal fails — such as the device lacking required security software — access is denied even if the username and password are correct.

---

## 3. Simplified Policy Table

| Policy Requirement (Signal) | Condition to be Met by User | Action if Condition is Met |
|----------------------------|----------------------------|----------------------------|
| User Identity Verification | User must authenticate using MFA and hold an approved HR role in directory services | Grant Access |
| Device Security Posture | Device must have full-disk encryption enabled and active endpoint protection software | Grant Access |
| Access Context Validation | Login must originate from approved geographic region and within business hours (6 AM – 7 PM) | Grant Access |

*If any condition is not met → Deny Access*

---

## 4. Git Repository Metadata

- **Project:** Lab 02 - Zero Trust Policy  
- **Filename:** ZT-Policy-Profile.md  
- **Commit Message:** Complete Zero Trust Policy Profile for Lab 02
- **GitHub URL:** https://github.com/Hashem811/github-protfolio/new/main
- **Due Date:** February 27, 2026
