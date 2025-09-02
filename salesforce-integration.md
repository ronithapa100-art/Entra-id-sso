# Salesforce SSO with Entra ID — Case Study Guide (Demo)

> Use a **Sandbox** for testing. Values below are placeholders.

## Context
- **Service Provider (SP):** Salesforce (`example.my.salesforce.com`)
- **Identity Provider (IdP):** Microsoft Entra ID
- **Protocol:** SAML 2.0 with RSA-SHA256; **JIT provisioning** enabled

## Problem → Action → Result
**Problem:** Manual user onboarding and inconsistent login experience across apps.  
**Action:** Implemented SAML SSO with JIT in Salesforce:
- Entra ID SAML enterprise app targeting Salesforce (Entity ID `https://saml.salesforce.com`).
- Configured Salesforce SAML SSO with IdP Issuer, SSO URL, and certificate.
- Mapped `NameID=emailAddress`; added optional claims for role/profile mapping.
- Enabled JIT provisioning to create users on first SSO.
**Result:** Faster onboarding, consistent MFA-backed sign-in, reduced admin overhead.

## Configuration (high level)
- **Entity ID:** `https://saml.salesforce.com`
- **SSO URL (IdP):** `https://login.microsoftonline.com/YOUR_TENANT_ID/saml2`
- **ACS URL:** `https://example.my.salesforce.com?so=00DXXXXXXX`
- **Signing Algorithm:** RSA-SHA256
- **JIT:** Enabled (Standard)

## Attribute Mapping
- `NameID` → Email address (`user.mail` or `user.userprincipalname`)
- Optional attributes for Profile/Permission Set routing: `department`, `role`, `groups`

## Rollout Plan
1. Sandbox validation → small pilot in production.
2. Map Profiles/Permission Sets to groups; test least-privilege.
3. Communicate cutover with clear fallback and helpdesk runbook.

## Validation & Troubleshooting
- Verify `so=` org ID in the ACS URL.
- If using Federation ID, ensure it matches the mapped claim.
- Align domains when multiple My Domains exist.
