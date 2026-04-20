OpenSSL policy for obsoleting cryptographic primitives and protocols
--------------------------------------------------------------------

This formal policy outlines the OpenSSL Project’s framework for managing the
lifecycle of cryptographic primitives, protocols, and structural features. 
It ensures a "secure by default" posture while providing a predictable migration
path for the global ecosystem.

## 1. Policy Objective
To maintain the integrity of the OpenSSL library by systematically deprecating
and removing features that no longer meet modern cryptographic standards or
industry best practices.

## 2. Triggers for end-of-life
Features enter the deprecation lifecycle when they meet one of two criteria:

* **Insecure:** Primitives or features with known practical attacks, or where 
  the "Work Factor" (computational effort to break) has decayed.
    * Any primitive with an effective security strength below **112 bits** 
      (OpenSSL Security Level 2) is considered insecure for modern use.
    * Protocol features that are exploitable by design.
* **Obsolete:** Features that remain mathematically sound but have been 
  superseded by more secure or efficient alternatives.

## 3. The end-of-life stages
Removal of cryptographic primitives and protocols happens through several stages
to conform to OpenSSL API guarantees.

### Stage 1: Industry Obsolete (Signal)
* **Status:** Feature is still available and enabled by default.
* **Trigger:** An industry standards body (IETF, NIST, etc.) publishes a
  "Deprecated" or "Historic" status, or a significant research paper 
  demonstrating a weakness (e.g., Logjam, CRIME) is published.
* **OpenSSL Action:** 
  * Documentation is updated to reflect industry obsoletion status.
  * Record a decision that defines when deprecation is allowed.

### Stage 2: OpenSSL Deprecated (Transition)
* **Status:** Feature is moved to the **Legacy Provider**.
* **Trigger:** A new major or minor OpenSSL release.
* **OpenSSL Action:**:
    * Minor release: Compiler attributes (`OSSL_DEPRECATEDIN`) trigger
      warnings for developers.
    * Minor release: Support for compile-time disabling the feature 
      (`./config no-<feature>`).
    * Major release: Feature is compile-time disabled by default
    * Major release: Feature moved to the Legacy Provider.
    * Major release: Security Levels are adjusted to prohibit the feature at
      Level 2 or higher.
    * Record a decision that defines when removal is allowed.
    * If applicable: Adding a migration path in the ossl-migration-guide.md.

### Stage 3: OpenSSL Obsolete (Removal)
* **Status:** Code is deleted.
* **Trigger:** A major OpenSSL release after deprecation (e.g., moving 
  from 3.x to 4.0).
* **OpenSSL Action:** 
  * Removal of source code, headers, and tests.
  * Notice in CHANGES.md.

## 4. Specific Criteria for Protocol Features
Structural features (extensions, compression, etc.) are evaluated differently
than mathematical primitives:

1.  **Information Leakage:** Any feature that leaks plaintext length or metadata
    (e.g., **TLS Compression**) is moved immediately to Stage 2.
2.  **Forward Secrecy:** Features that rely on static keying material (e.g., 
    **Static RSA**) are marked Obsolete and moved to Stage 2.
3.  **Side-Channel Resistance:** If a feature cannot be implemented in
    "constant-time" on modern hardware, it is prioritized for Stage 3 removal.

> **Emergency Override:** The OpenSSL Foundation Board of Directors reserves the
> right to bypass Stages 1 and 2 for "Zero-Day" catastrophic breaks, disabling
> the feature in a minor security patch.
