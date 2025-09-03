# Entra ID SSO Integration Demo (Zoom + Salesforce)

My role & context — I led an org-wide SSO rollout using Microsoft Entra ID as IdP for Zoom and Salesforce. Scope: **200 users**. I owned app registration, SAML assertion mapping, Conditional Access/MFA, pilot testing, and the phased production cutover.

This repository demonstrates how to configure **Microsoft Entra ID (Azure AD)** as the Identity Provider (IdP) for **Zoom** and **Salesforce** using **SAML 2.0** (and optionally OAuth/OIDC).
All values are **sanitized placeholders** — no company-specific or production data is included.

---

## 🌟 Project Highlights
- Implemented **organization-wide Single Sign-On (SSO)** across Zoom and Salesforce with **Entra ID**.
- Enabled Just-in-Time (JIT) provisioning** in Salesforce to streamline onboarding.
- Applied Conditional Access + MFA** at the IdP for defense-in-depth.
- Outcome: ~35% fewer login tickets over 60 days; onboarding time reduced from 2 days → 30 minutes (sanitized).

---
## Results (200 users, sanitized)

- **Scope:** Entra ID SSO across Zoom + Salesforce for **200 users**.
- **Onboarding speed:** **2 days → 30 minutes** (**~97% faster**).
  - **Time saved per user:** 15.5 hours
  - **Total saved:** 3,100 hours ≈ **388 workdays** (8h/day) ≈ **77.5 workweeks**
- **Helpdesk impact (60 days):** ~**35% fewer** login tickets
  - Baseline: **200 tickets** (1.0/user)
  - After: **130 tickets** (**70 fewer** total) → **0.65 tickets/user**
- **MFA coverage:** **200/200 users (100%)** via Conditional Access.



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

Decisions & trade-offs

NameID = emailAddress to align Salesforce & Zoom sign-in identities.

Salesforce ACS included the so= org ID to target the correct instance.

Conditional Access excluded break-glass/service accounts to avoid MFA loops; user groups governed app access.

Cert rotation: rotate IdP signing cert ~30 days before expiry; documented SP metadata updates.

Chose SAML because both apps have mature SAML patterns in our environment; fastest to implement safely.

---

## ⚠️ Disclaimer
For education/demo use only. Replace placeholders with your **test** values; never commit real secrets or org identifiers.
