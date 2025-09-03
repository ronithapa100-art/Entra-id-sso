---
title: Entra ID SSO (Zoom + Salesforce) — Demo Case Study
description: Portfolio-ready case study showing Entra ID SSO with Zoom & Salesforce (sanitized).
---


# Entra ID SSO (Zoom + Salesforce) — Demo Case Study

This site summarizes how to integrate **Microsoft Entra ID** with **Zoom** and **Salesforce** for **SAML 2.0** Single Sign-On. All values are sanitized placeholders.

## Highlights
- Org-wide SSO with Entra ID as IdP
- Zoom + Salesforce integrations with SAML 2.0 (RSA-SHA256, HTTP-Redirect)
- JIT user provisioning in Salesforce
- Conditional Access + MFA at the IdP
- Troubleshooting playbook and sample configs


## Architecture
![SSO flow: Entra ID (IdP) with Zoom & Salesforce (SAML 2.0)](architecture.pdf)




## Guides
- **Zoom Integration** — opens on GitHub:  
  https://github.com/ronithapa100-art/Entra-id-sso/blob/main/guides/zoom-integration.md
- **Salesforce Integration** — opens on GitHub:  
  https://github.com/ronithapa100-art/Entra-id-sso/blob/main/guides/salesforce-integration.md
- **Troubleshooting** — opens on GitHub:  
  https://github.com/ronithapa100-art/Entra-id-sso/blob/main/guides/troubleshooting.md

## Disclaimer
This case study is for educational/demo purposes only. Use a **test tenant** and never commit real secrets or company identifiers.
