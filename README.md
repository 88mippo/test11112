# Security Policy

## Reporting a Vulnerability

The Ghostfolio project team and community take the security of our application and the privacy of our users very seriously. If you discover a security vulnerability, we appreciate your help in disclosing it to us responsibly.

**Please DO NOT open a public GitHub Issue to report a security vulnerability.**

Instead, please report vulnerabilities by emailing our core team directly at **security@ghostfol.io** or by submitting a private security advisory on GitHub.

### Please include the following details in your report:
* A description of the vulnerability and its potential impact.
* Detailed steps to reproduce the issue (including proof-of-concept scripts, code snippets, or screenshots where applicable).
* The affected component, API endpoint, or application version.
* Any potential mitigations or fixes you might have identified.

## Vulnerability Response Process

1. **Acknowledgment:** We will acknowledge receipt of your vulnerability report within 48 hours.
2. **Assessment:** Our team will investigate and verify the reported issue to determine its severity and scope.
3. **Fix & Patch:** Once confirmed, we will prepare a fix. Critical security patches are prioritized for release.
4. **Public Disclosure:** After a fix has been deployed and released, we will credit you in the release notes (unless you prefer to remain anonymous) and publish a security advisory.

## Security Best Practices for Self-Hosting

If you are self-hosting Ghostfolio, we strongly recommend following these guidelines:
* **Keep Updated:** Always run the latest stable Docker container tag or version release.
* **Environment Variables:** Secure your `.env` file and ensure sensitive variables (such as `JWT_SECRET_KEY`) use strong, randomly generated keys.
* **Reverse Proxy:** Run Ghostfolio behind a secure reverse proxy (e.g., Nginx, Traefik, Caddy) with SSL/TLS encryption enabled (`HTTPS`).
* **Database Access:** Restrict external network access to your PostgreSQL database instance.
