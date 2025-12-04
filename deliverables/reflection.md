# Module 7: Assignment: Maintaining Secure Systems with SBOMs and Patching


This assignment consists on maintaining and verifying the security of the Ubuntu system that powers the GitHub Codespace environment. Rather than analyzing application code, the work centers on generating system-level SBOMs, identifying vulnerabilities in installed packages, applying updates with apt, and validating the system’s improved security.

## SBOM and Vulnerability Report

SBOM was generated using Syft for the Ubuntu system in the Codespace. The SBOM was then scanned with Grype to identify vulnerabilities in installed packages.

Total number of packages identified:  256
Number of vulnerabilities by severity: 1 critical, 12 high, 1598 medium, 196 low, 24 negligible

### CVE
**CVE-2025-23166 Summary**

CVE-2025-23166 is caused by improper exception handling in the C++ method `SignTraits::DeriveBits()`, which may call `ThrowException()` incorrectly when processing user-supplied input in a background thread. This results in an uncaught exception that can crash the entire Node.js process.
Because cryptographic operations often handle untrusted external data, an attacker could exploit this flaw to remotely force a denial-of-service by crashing a Node.js runtime.


### How does maintaining updated packages illustrate complete mediation?
Complete mediation requires that every access and every system component be continuously verified rather than trusted based on past checks. Keeping packages updated ensures that the underlying code performing those checks is not using known-vulnerable or outdated implementations. By regularly applying patches, the system maintains its ability to enforce security decisions correctly at every access.

### Why is generating a new SBOM after patching essential to assurance?
Assurance depends on having verifiable evidence that a system is in a trusted. Generating a new SBOM after patching creates an accurate inventory of all installed components, reflecting the system as it actually exists after updating. This allows vulnerability scanners and auditors to confirm that the intended changes occurred and that no outdated or risky components remain after update is made.

### What risks persist when organizations delay system updates?
Delaying updates leaves systems running software with known vulnerabilities that attackers can easily search for and exploit. Once a vulnerability becomes public, attackers quickly learn how to take advantage of it, making unpatched systems especially vulnerable.
The longer updates are postponed, the greater the chance of the vulnerability being exploited, leading to potential data breaches, service disruptions, and loss of trust.

### How does this exercise embody the secure design lifecycle principle?
This exercise demonstrates that security is not a one-time configuration step but an ongoing process of measurement, improvement, and verification. By generating SBOMs, scanning for vulnerabilities, applying patches, and validating changes, the workflow mirrors how secure systems evolve across their lifecycle.
