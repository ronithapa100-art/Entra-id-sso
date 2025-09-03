# Troubleshooting & Lessons Learned

- **Invalid Signature / Certificate**: Confirm x509 validity and correct IdP metadata.
- **NameID issues**: Use `emailAddress` consistently between IdP and SP.
- **ACS mismatch**: Exactly match protocol/host/path/query; watch trailing slashes.
- **MFA loops**: Scope Conditional Access properly; exclude service accounts.
- **Clock skew**: Allow ~5 minutes in SAML time conditions.
- **Group-based access**: Prefer Entra security groups; document mappings.
- **Cert rotation**: Track expiry and automate metadata refresh where possible.
