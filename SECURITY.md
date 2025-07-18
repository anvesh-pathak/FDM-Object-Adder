# Security Policy

## Supported Versions

| Version | Supported          |
| ------- | ------------------ |
| 1.0.x   | :white_check_mark: |

## Reporting a Vulnerability

If you discover a security vulnerability in FDM Object Adder, please report it by sending an email to [anvpatha@cisco.com](mailto:anvpatha@cisco.com).

**Please do not report security vulnerabilities through public GitHub issues.**

When reporting a vulnerability, please include:

- Type of issue (e.g. buffer overflow, SQL injection, cross-site scripting, etc.)
- Full paths of source file(s) related to the manifestation of the issue
- The location of the affected source code (tag/branch/commit or direct URL)
- Any special configuration required to reproduce the issue
- Step-by-step instructions to reproduce the issue
- Proof-of-concept or exploit code (if possible)
- Impact of the issue, including how an attacker might exploit the issue

## Response Timeline

- **Initial Response**: Within 48 hours
- **Status Update**: Within 7 days
- **Resolution**: Based on severity and complexity

## Security Best Practices

When using this tool:

1. **Use dedicated service accounts** for FDM authentication
2. **Limit network access** to FDM management interfaces
3. **Regularly update dependencies** using `pip install -U -r requirements.txt`
4. **Review input files** before processing to avoid malicious content
5. **Use HTTPS only** for FDM connections (built-in default)

## Vulnerability Disclosure

We will acknowledge receipt of vulnerability reports and work with researchers to investigate and address issues. We aim to:

- Confirm the problem and determine affected versions
- Audit code to find similar problems
- Prepare fixes for all affected versions
- Release patches as quickly as possible
