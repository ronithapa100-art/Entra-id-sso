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
<div class="mermaid">
sequenceDiagram
  participant U as User
  participant Z as Zoom (SP)
  participant SF as Salesforce (SP)
  participant AAD as Entra ID (IdP)

  U->>Z: Access Zoom (SP)
  Z-->>U: Redirect to IdP (SAML AuthnRequest)
  U->>AAD: Authenticate (MFA/Conditional Access)
  AAD-->>U: SAML Response (signed, SHA-256)
  U->>Z: Post SAML Response (ACS); session established

  Note over SF,AAD: Salesforce follows the same SAML pattern (ACS + Entity ID)
</div>

<script src="https://unpkg.com/mermaid@10.9.1/dist/mermaid.min.js"></script>
<script>mermaid.initialize({ startOnLoad: true });</script>


## Guides
- **Zoom Integration** — opens on GitHub:  
  https://github.com/ronithapa100-art/Entra-id-sso/blob/main/guides/zoom-integration.md
- **Salesforce Integration** — opens on GitHub:  
  https://github.com/ronithapa100-art/Entra-id-sso/blob/main/guides/salesforce-integration.md
- **Troubleshooting** — opens on GitHub:  
  https://github.com/ronithapa100-art/Entra-id-sso/blob/main/guides/troubleshooting.md

## Disclaimer
This case study is for educational/demo purposes only. Use a **test tenant** and never commit real secrets or company identifiers.
