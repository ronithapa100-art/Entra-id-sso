# Portfolio: Entra ID SSO (Zoom + Salesforce)

Use these bullets verbatim (or tweak numbers) on your resume and LinkedIn.
Replace bracketed values with your own metrics.

## Resume Bullets
- Led **organization-wide SSO** using **Microsoft Entra ID** for **Zoom** and **Salesforce**, securing access for **200 users**; reduced login-related tickets by **~35%** over 60 days.
- Cut onboarding time from **2 days → 30 minutes (~97% faster)** by standardizing SAML 2.0 mappings and enabling Salesforce **JIT provisioning**; saved **3,100 total hours** (~**388 workdays**).
- Enforced **Conditional Access + MFA** across the estate; achieved **100% coverage (200/200 users)** with group-based access and documented break-glass exclusions.
- Implemented a **certificate rotation** runbook (rotate ~30 days before expiry) and SP metadata update steps to avoid outages.

## Interview Talking Points (STAR)
- **Situation:** Users had multiple passwords and inconsistent security across SaaS apps.
- **Task:** Centralize auth, improve UX, and enforce MFA without disrupting productivity.
- **Action:** Designed SAML SSO via Entra ID, configured Zoom & Salesforce, mapped claims, enabled JIT, and applied Conditional Access. Ran a pilot, analyzed logs, and phased to production.
- **Result:** Faster sign-ins, fewer tickets (~[40%] reduction), consistent policy enforcement, and measurable onboarding time savings.

## Metrics You Can Track (and mention)
- Helpdesk tickets: before/after cutover
- Average time to onboard a new user
- % of users protected by MFA
- Cert rotation lead time; number of incidents avoided
- Sign-in success rate; time-to-resolution of SSO issues

## Keywords (ATS-friendly)
`Microsoft Entra ID`, `Azure AD`, `SAML 2.0`, `SSO`, `MFA`, `Conditional Access`, `SCIM`, `JIT Provisioning`, `Salesforce`, `Zoom`, `IdP`, `SP`, `RBAC`, `Identity Lifecycle`, `x509`, `Certificate Rotation`

---

See the full demo and guides in this repo:
- `README.md`
- `guides/zoom-integration.md`
- `guides/salesforce-integration.md`
- `docs/architecture.mmd`
