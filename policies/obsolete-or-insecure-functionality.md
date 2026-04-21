OpenSSL Library policy for obsoleting cryptographic primitives and protocols
----------------------------------------------------------------------------

This formal policy outlines the OpenSSL Library’s framework for managing the
lifecycle of cryptographic primitives, protocols, and structural features. 
It ensures a "secure by default" posture while providing a predictable migration
path for the global ecosystem.

## Policy Objective
To maintain the integrity of the OpenSSL Library by systematically deprecating
and removing features that no longer meet modern cryptographic standards or
industry best practices.

## Triggers for end-of-life
Features enter the deprecation lifecycle when they meet one of two criteria:

* **Insecure:** Primitives or features with known practical attacks, or where 
  the "Work Factor" (computational effort to break) has decayed.
    * Any primitive with an effective security strength below **112 bits** 
      (OpenSSL Security Level 2) is considered insecure for modern use.
    * Protocol features that are exploitable by design.
* **Obsolete:** Features that remain cryptographically sound but have been 
  superseded by more secure or efficient alternatives.

## The end-of-life stages
Removal of cryptographic primitives and protocols happens through several stages
to conform to OpenSSL API guarantees.

### Stage 1: Industry Obsolete (Signal)
* **Status:** Feature is still available and enabled by default.
* **Trigger:** An industry standards body (IETF, NIST, etc.) publishes a
  "Deprecated" or "Historic" status, or a significant research paper 
  demonstrating a weakness (e.g., Logjam, CRIME) is published.
* **OpenSSL Action:** 
  * Documentation is updated to reflect industry obsoletion status.
  * Record a decision that defines when deprecation is planned.

### Stage 2: OpenSSL Deprecated (Transition)
* **Status:** Feature needs to be explicitly enabled.
* **Trigger:** It has been decided to formally deprecate the feature.
* **OpenSSL Action:**
  * Support for compile-time disabling the feature (`./config no-<feature>`) is
    added in a minor release.
  * Major release: Feature is compile-time disabled by default.
  * If applicable: Adding a migration path in the ossl-migration-guide.md.
  * Record a decision that defines when removal is planned.
  * For cryptographic algorithms:
     * Major release: Feature moved to the Legacy Provider.
     * Major (in severe cases: minor) release: Security Levels are adjusted to
       prohibit the feature at Level 2 or higher.
  * For other features:
    * Minor release: Compiler attributes (`OSSL_DEPRECATEDIN`) trigger
      warnings for developers.

### Stage 3: OpenSSL Obsolete (Removal)
* **Status:** Code is deleted.
* **Trigger:** A major OpenSSL release after deprecation (e.g., moving 
  from 3.x to 4.0).
* **OpenSSL Action:** 
  * Removal of source code, headers, and tests.
  * Notice in CHANGES.md.
