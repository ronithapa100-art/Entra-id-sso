# Entra ID SSO Integration Demo (Zoom + Salesforce)

This repository demonstrates how to configure **Microsoft Entra ID (Azure AD)** as the Identity Provider (IdP) for **Zoom** and **Salesforce** using **SAML 2.0** (and optionally OAuth/OIDC).
All values are **sanitized placeholders** — no company-specific or production data is included.

---

## 🌟 Project Highlights
- Implemented **organization-wide Single Sign-On (SSO)** across Zoom and Salesforce with **Entra ID**.
- Enabled **Just-in-Time (JIT) provisioning** in Salesforce to streamline onboarding.
- Applied **Conditional Access + MFA** at the IdP for defense-in-depth.
- Outcome (example): **~40% fewer** login-related helpdesk tickets; faster onboarding.

---

## 📂 Repo Contents
```
.
├─ README.md
├─ docs/
│  └─ architecture.mmd
├─ guides/
│  ├─ zoom-integration.md
│  ├─ salesforce-integration.md
│  └─ troubleshooting.md
├─ config/
│  ├─ salesforce-saml-config-sample.xml
│  └─ zoom-saml-config-sample.xml
├─ SECURITY.md
├─ DISCLAIMER.md
├─ LICENSE (MIT)
└─ .gitignore
```

---

## 🔐 Safe Placeholder Values
- **Tenant ID** → `YOUR_TENANT_ID`
- **Domains** → `example.com`, `example.my.salesforce.com`, `example.zoom.us`
- **IdP Issuer** → `https://sts.windows.net/YOUR_TENANT_ID/`
- **IdP SAML URL** → `https://login.microsoftonline.com/YOUR_TENANT_ID/saml2`
- **Certificates** → `<REDACTED_CERTIFICATE>`

---

## 🛠️ Technical Overview
- **Protocol:** SAML 2.0 with RSA-SHA256
- **Binding:** HTTP-Redirect
- **Claims:**
  - `NameID` → `emailAddress`
  - Attributes: `email`, `givenname`, `surname`, `groups` (optional)
- **Salesforce:** JIT provisioning supported
- **Zoom:** Vanity subdomain & SAML attributes

See `docs/architecture.mmd` for the full auth flow.

---

## 📚 Lessons Learned
- Keep **ACS/Entity IDs** exact; mismatches cause silent failures.
- Plan **certificate rotation**; refresh SP metadata in advance.
- Align **UPN vs. Email** mapping to avoid JIT issues in Salesforce.
- Tune **Conditional Access** to prevent MFA loops.
- Use a SAML tracer to inspect assertions and timestamps (`NotBefore/NotOnOrAfter`).

---

## ⚠️ Disclaimer
For education/demo use only. Replace placeholders with your **test** values; never commit real secrets or org identifiers.
