# Portfolio: Entra ID SSO (Zoom + Salesforce)

Use these bullets verbatim (or tweak numbers) on your resume and LinkedIn.
Replace bracketed values with your own metrics.

## Resume Bullets
- Led **organization-wide Single Sign-On (SSO)** rollout by integrating **Microsoft Entra ID** with **Zoom** and **Salesforce**, securing access for **[N] users** across **[X] departments**; cut login-related tickets by **~[30–50]%**.
- Implemented **Just-in-Time (JIT) provisioning** in Salesforce with attribute/role mapping, reducing new-user onboarding time from **[T1] → [T2]** and eliminating manual account creation.
- Hardened authentication with **Conditional Access + MFA**, standardized **SAML 2.0 (RSA-SHA256)**, and enforced **group-based access**; improved auditability and reduced risk of credential reuse.
- Built an operational runbook for **certificate rotation** and SAML metadata refresh; prevented outages by rotating certs **[X] weeks** before expiry.
- Partnered with Security and IT Ops to pilot, monitor, and phase rollout; achieved **[>99%]** successful sign-in rate post cutover.

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
