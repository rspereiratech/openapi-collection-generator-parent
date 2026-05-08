# Security Policy

## Supported Versions

Security updates are provided for the latest minor release. Older versions may receive fixes on a best-effort basis.

| Version | Supported |
|---|---|
| 1.0.x   | :white_check_mark: |
| < 1.0   | :x: |

## Reporting a Vulnerability

If you discover a security vulnerability in **OpenAPI Collection Generator**, please report it privately. **Do not open a public GitHub issue.**

### How to Report

Email the maintainer at: **rspereiratech@gmail.com**

Include the following information:

- A description of the vulnerability and its potential impact
- Steps to reproduce (minimal OpenAPI spec, plugin configuration, commands)
- Affected version(s)
- Any known mitigations or workarounds
- Whether you intend to disclose publicly and on what timeline

### What to Expect

- **Acknowledgement** within 5 business days of your report.
- **Initial assessment** within 10 business days, including severity and remediation plan.
- **Fix and disclosure** coordinated with the reporter. We aim to release a patched version within 30 days of confirmation for high-severity issues.
- **Credit** in the release notes if you wish to be acknowledged.

## Scope

In scope:

- The Maven plugin and its modules (`core`, `postman`, `insomnia`, `maven-plugin`)
- Generated output that could expose sensitive data (e.g. credentials leaked into collections or environment files)
- Vulnerabilities in how the plugin parses or processes untrusted OpenAPI specifications

Out of scope:

- Vulnerabilities in third-party dependencies (please report upstream; we will track and update)
- Issues that require an attacker to already have local file system or build access
- Misconfigurations in the consumer's `pom.xml` or OpenAPI spec

## Security Best Practices for Users

- Avoid committing OpenAPI specs that contain real credentials, tokens, or production secrets.
- Review generated collection and environment files before importing into Postman or Insomnia, especially when sourced from external specs.
- Pin the plugin version in your `pom.xml` and update regularly.
- Run `mvn dependency:tree` periodically to audit transitive dependencies.

## Disclosure Policy

We follow **coordinated disclosure**. Once a fix is released, we will publish an advisory describing the issue, affected versions, and remediation steps.
