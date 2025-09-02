# Zoom SSO with Entra ID — Case Study Guide (Demo)

> All values are placeholders. Do **not** publish real tenant/org details.

## Context
- **Service Provider (SP):** Zoom (vanity: `example.zoom.us`)
- **Identity Provider (IdP):** Microsoft Entra ID
- **Protocol:** SAML 2.0 (HTTP-Redirect, RSA-SHA256)

## Problem → Action → Result
**Problem:** Multiple sign-in methods and passwords caused friction and inconsistent security posture for Zoom.  
**Action:** Implemented SAML SSO with Entra ID:
- Created SAML enterprise app in Entra ID (`Zoom (Demo)`).
- Configured Zoom SSO with IdP URLs and x509 certificate.
- Standardized claims: `NameID=emailAddress`, attributes `email`, `givenname`, `surname`.
- Applied Conditional Access + MFA.
**Result:** Centralized authentication, fewer password resets, auditability via Entra logs.

## Configuration (high level)
- **IdP SSO URL:** `https://login.microsoftonline.com/YOUR_TENANT_ID/saml2`
- **IdP Issuer:** `https://sts.windows.net/YOUR_TENANT_ID/`
- **SP Entity ID:** `example.zoom.us`
- **ACS URL:** `https://example.zoom.us/saml/SSO`
- **Binding:** HTTP-Redirect
- **Signature Hash Algorithm:** SHA-256

## Attribute Mapping
- `NameID` → Email address
- `email` → `user.mail` (or `user.userprincipalname`)
- `givenname` → `user.givenname`
- `surname` → `user.surname`
- Optional: `groups` → for role mapping

## Rollout Plan
1. Pilot with a security group (e.g., `Zoom-SSO-Pilot`).
2. Monitor SAML response logs in Zoom + Sign-in logs in Entra.
3. Migrate remaining users; disable legacy sign-in methods.

## Validation & Troubleshooting
- Ensure vanity subdomain matches the ACS exactly.
- Compare certificate thumbprints; rotate before expiry.
- Inspect SAML assertions with a tracer; check time conditions.
