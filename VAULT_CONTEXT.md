# Vault Context

This file provides the product context needed to evaluate HashiCorp Vault UIs.

## What Vault Is

Vault is a secrets management and encryption platform. It controls access to tokens, passwords, certificates, API keys, and other secrets. It provides a unified interface to secrets while maintaining tight access control and recording a detailed audit log.

Vault exists in two deployment models:
- **HCP Vault Dedicated** — HashiCorp-managed clusters hosted on HashiCorp Cloud Platform (HCP). Infrastructure is managed by HashiCorp; the customer manages configuration, policies, and secrets.
- **Vault Enterprise / Community (self-hosted)** — Customer manages everything, including infrastructure, upgrades, and high availability.

The UI being evaluated is typically the **HCP Vault Dedicated** experience unless stated otherwise.

## Core Concepts

### Secrets Engines
Plugins that store, generate, or encrypt data. Each is mounted at a path (e.g., `secret/`, `pki/`, `transit/`). Common engines:
- **KV (Key-Value):** Static secrets — the most common engine. v1 (no versioning) and v2 (versioned).
- **PKI:** Issues X.509 certificates dynamically. Used for mTLS, service mesh, internal CAs.
- **Transit:** Encryption-as-a-service. Encrypts/decrypts data without exposing keys.
- **Database:** Generates dynamic, short-lived database credentials on demand.
- **AWS / Azure / GCP:** Generates dynamic cloud credentials for infrastructure access.

### Auth Methods
How users and machines prove identity to Vault. Each method is mounted at a path. Common methods:
- **Token:** Default. Every auth method ultimately produces a token.
- **OIDC / JWT:** Federated identity (SSO). Primary method for human users in HCP.
- **AppRole:** Machine-to-machine auth for CI/CD and automation.
- **Kubernetes:** Pods authenticate using their service account token.
- **AWS / Azure / GCP IAM:** Machines authenticate using cloud identity.

**Design implication:** The UI should not assume human interaction. The majority of Vault traffic is machine-to-machine.

### Policies
HCL documents that define what paths a token can access and what operations it can perform (read, write, delete, list, sudo). Policies are deny-by-default.

**Design implication:** A user viewing a page may not have permission to perform the actions shown. The UI must handle permission boundaries gracefully — hiding or disabling inaccessible actions, never showing errors after the fact.

### Tokens
Every authenticated entity gets a token with a TTL (time-to-live), attached policies, and optional metadata. Tokens can be:
- **Service tokens:** Persistent, stored by Vault, can create child tokens.
- **Batch tokens:** Lightweight, not stored, cannot be revoked individually. Used at scale.

### Leases
Most dynamic secrets have a lease — a TTL after which the secret is revoked. Leases can be renewed. If not renewed, Vault revokes the credential (e.g., deletes the database user).

**Design implication:** Temporal context matters everywhere. "This credential expires in 12 minutes" is critical operational information.

## Critical Operations & States

### Seal / Unseal
Vault starts in a **sealed** state — it has encrypted data but cannot decrypt it. Unsealing requires a threshold of key shares (Shamir's Secret Sharing) or an auto-unseal mechanism (KMS).

- **Sealed = fully inoperable.** No reads, no writes, no auth. This is an emergency state.
- **Auto-unseal (HCP default):** Uses a cloud KMS. The cluster unseals automatically on restart.

**Design implication:** Seal status is the single most important health indicator. A sealed cluster is a production outage. On any surface responsible for communicating system health or availability, seal state must be unmissable.

### Replication
Vault Enterprise supports two replication modes:
- **Performance replication:** Read replicas for geographic distribution. Writes go to primary.
- **Disaster recovery (DR) replication:** Hot standby. Promotes to primary if the primary fails.

### Snapshots
Point-in-time backup of the entire Vault state. Critical for disaster recovery. HCP manages automated snapshots, but users should know when the last snapshot was taken.

## Common Vault Workflows

1. **Store and retrieve a static secret** — Mount KV engine → Write secret at a path → Read secret by path.
2. **Generate dynamic database credentials** — Configure database engine → Create a role with TTL → Application requests credentials → Vault creates temporary DB user → Credentials expire and Vault revokes the user.
3. **Issue a TLS certificate** — Configure PKI engine with a CA → Create a role → Request certificate for a domain → Vault issues short-lived cert.
4. **Encrypt application data (Transit)** — Configure transit engine → Create encryption key → Application sends plaintext → Vault returns ciphertext. Keys never leave Vault.
5. **Set up CI/CD authentication** — Enable AppRole auth → Create role with policies → Retrieve Role ID + Secret ID → Pipeline authenticates → Gets short-lived token to read secrets.

## Terminology Quick Reference

| Term | Meaning |
|---|---|
| **Mount / mount path** | Where a secrets engine or auth method is enabled (e.g., `secret/`, `auth/approle/`) |
| **Policy** | Access control document. Deny-by-default. Written in HCL. |
| **Token** | Auth credential. Has TTL, policies, and metadata. |
| **Lease** | TTL on a dynamic secret. Renewable. Auto-revoked on expiry. |
| **Seal / Unseal** | Encryption lock on the Vault. Sealed = fully inoperable. |
| **Namespace** | Tenant isolation boundary. HCP clusters operate within a namespace. |
| **JTBD** | Job To Be Done — the user's actual goal, not the feature they're clicking. |
| **HCL** | HashiCorp Configuration Language — used for policies and Terraform configs. |
| **IaC** | Infrastructure as Code — managing infrastructure via config files (Terraform). |
| **mTLS** | Mutual TLS — both client and server authenticate via certificates. |
| **KMS** | Key Management Service — cloud provider service for managing encryption keys. |
| **Shamir's Secret Sharing** | Algorithm that splits a key into N shares, requiring K of N to reconstruct. Used for manual unseal. |

## What This Means for Evaluation

- **Seal status must be unmissable.** If you can't tell whether the cluster is sealed within 1 second of landing on the page, that's a Critical finding.
- **Machine users dominate.** Most Vault interactions are automated. The UI should support and accelerate automation setup, not assume manual operation.
- **Temporal context is essential.** Secrets expire. Tokens expire. Leases expire. Certificates expire. If the UI shows something without its TTL or expiration, it's missing critical information.
- **Permissions shape what's visible.** Not every user can see or do everything. The UI should degrade gracefully based on policy, not show errors after action attempts.
- **Security posture is always relevant.** Every screen is a potential audit surface. Ask: "Can a Governance & Compliance Owner get what they need from this view?"
