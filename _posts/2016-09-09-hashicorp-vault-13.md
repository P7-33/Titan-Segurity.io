---
title: 'HashiCorp Vault 1.3'
date: 2019-11-15T05:49:00+01:00
draft: false
---

![](https://www.datocms-assets.com/2885/1506458602-blog-vault-vertical-new.svg "Announcing HashiCorp Vault 1.3")  

We are excited to announce the public availability of HashiCorp Vault 1.3. Vault is a tool to provide secrets management, data encryption, and identity management for any infrastructure and application.

Vault 1.3 is focused on improving Vault's ability to serve as a platform for credential management workloads for services such as Active Directory and Kubernetes and support global multi-cloud operations with high performance, compliance-regulated workloads.

This release includes the following features:

*   **Entropy Augmentation _(Vault Enterprise only)_:** Allow Vault Enterprise to sample entropy from external cryptographic modules.
*   **Active Directory Check In/Check Out:** Allow Vault to manage check in/check out rotation for Active Directory credentials.
*   **Vault Debug:** A new CLI command to gather health metrics of Vault nodes.
*   **Path Filters _(Vault Enterprise only)_:** Implement path filters that permit controlling which namespace secrets are replicated to secondaries.
*   **Oracle Cloud Infrastructure (OCI) Support:** New auth methods, storage backends, and auto-unseal interfaces for Oracle Cloud Infrastructure.
*   **Improved Integrated Storage _(Beta)_:** Improved raft write performance, added support for non-voter nodes, along with UI support for: using raft storage, joining a raft cluster, and downloading and restoring a snapshot.

This release also includes additional new features, secure workflow enhancements, general improvements, and bug fixes. The Vault 1.3 [changelog](https://github.com/hashicorp/vault/blob/master/CHANGELOG.md) provides a full list of features, enhancements, and bug fixes.

[»](https://www.hashicorp.com/blog/vault-1-3/#entropy-augmentation) Entropy Augmentation
----------------------------------------------------------------------------------------

**Note: This is a Vault Enterprise feature**

Vault Enterprise 1.3 sees the introduction of entropy augmentation: a feature that allows Vault to sample entropy (or randomness for cryptographic operations) from an external source via the `seals` interface.

[Entropy](https://en.wikipedia.org/wiki/Entropy_(computing)), or statistical randomness, is critical in cryptography and important for protecting secrets within Vault. While the system entropy used by Vault ([which varies depending on where Vault is being run](https://golang.org/pkg/crypto/rand/)) is more than capable of operating in most threat models, there are some situations where additional entropy from hardware-based random number generators is desirable.

Entropy augmentation allows Vault Enterprise to supplement its system entropy with entropy from an external cryptography module. Designed to operate in environments where alignment with cryptographic regulations like [NIST SP800-90B](https://csrc.nist.gov/publications/detail/sp/800-90b/final) is required or when augmented entropy from external sources such as hardware true random number generators (TRNGs) or [quantum computing TRNGs](https://www.hashicorp.com/blog/quantum-security-and-cryptography-in-hashicorp-vault) are desirable, augmented entropy replaces system entropy when performing random number operations on critical security parameters (CSPs).

These CSPs have been selected from our [previous work in evaluating Vault for conformance with FIPS 140-2 guidelines for key storage and key transport](https://www.datocms-assets.com/2885/1510600487-vault_compliance_letter_fips_140-2.pdf) and include the following:

*   Vault's master key
*   Keyring encryption keys
*   Auto Unseal recovery keys
*   TLS private keys for inter-node and inter cluster communication (HA leader, raft, and replication)
*   Enterprise MFA TOTP token keys
*   JWT token wrapping keys
*   Root tokens
*   DR operation tokens

For more information on entropy augmentation, see our [learn guide](https://learn.hashicorp.com/vault/security/hsm-entropy) and the [system documentation](https://www.vaultproject.io/docs/enterprise/entropy-augmentation/index.html).

[»](https://www.hashicorp.com/blog/vault-1-3/#improved-integrated-storage-beta-) Improved Integrated Storage (Beta)
-------------------------------------------------------------------------------------------------------------------

Vault 1.3 sees a number of improvements to Vault’s integrated storage (also known as the Raft Storage Backend) and the transition of integrated storage to Beta.

This release includes the following new features:

*   **Non-Voter Nodes**: Storage nodes dedicated to streamlining performance.
*   **Recovery Mode**: Similar to Consul’s recovery mode, a secure emergency mode to directly manage Vault's storage.
*   **UI Improvements:** New UI to better manage integrated storage and to download/manage snapshots.
*   Improvements to integrated storage's backend systems to improve performance and stability.

Integrated storage is in the Beta phase, and as such we do not recommend or support using integrated storage for production workloads. We continue to work with the community on resolving bug fixes and testing, and plan on creating a reference architecture and fully supporting integrated storage as a storage backend for production systems in an upcoming Vault release.

For more information on integrated storage, see our [learn guide](https://learn.hashicorp.com/vault/beta/raft-storage) and the [system documentation](https://www.vaultproject.io/docs/configuration/storage/raft.html).

[»](https://www.hashicorp.com/blog/vault-1-3/#active-directory-check-in-check-out) Active Directory Check In / Check Out
------------------------------------------------------------------------------------------------------------------------

Starting in Vault 1.1, we began an evolution of features to improve privileged access management for static credential systems. Vault 1.3 continues this focus by adding new functionality to support Check In / Check Out management of Active Directory credentials.

Check In / Check Out is a new feature that allows Vault users to manage a set of AD credentials available within a system. This selection of AD Credentials can be shared within a team such that each team member can only be allowed to use one selected credential at a time, with credentials rotated as a user checked their credential back in.

For more information on AD Check In / Check Out, see our [learn guide](https://learn.hashicorp.com/vault/secrets-management/ad-secrets) and the [system documentation](https://www.vaultproject.io/docs/secrets/ad/index.html).

[»](https://www.hashicorp.com/blog/vault-1-3/#vault-debug) Vault Debug
----------------------------------------------------------------------

A constant goal of the Vault team is to improve the experience of deploying, configuring, and managing Vault. Vault 1.3 introduces new functionality towards this goal with the release of a new CLI command, `vault debug`.

Debug is a command that gathers metrics about a node’s health - including replication status, information about the host such as available memory, configuration state of the server, etc. Once gathered, this data is outputted to a tarball archive. These health metrics can then be shared with groups like HashiCorp Customer Success to support investigations in root cause analysis for issues.

Some of the data that `vault debug` accesses may be very sensitive. As such, Vault only gathers debug data from endpoints Vault users have access to via their ACL policies. If the user attempting to use `vault debug` does not have permission to access a certain endpoint for a particular target, its output will be omitted and a permissions error will be logged within the Audit Log.

The archive generated from `vault debug` outputted should be treated with care. Vault does not natively encrypt this archive, and we recommend users transmit this archive over encrypted channels when opting to share it.

For more information on `vault debug` see the [documentation](https://www.vaultproject.io/docs/commands/debug.html).

[»](https://www.hashicorp.com/blog/vault-1-3/#path-filters) Path Filters
------------------------------------------------------------------------

**Note: This is a Vault Enterprise feature**

In Vault 0.8 we introduced Mount Filters, a feature that allows for Vault Enterprise admins to select mounts (and thus secrets) that will not be forwarded in replication. Mount Filters has been successful in supporting enterprise governance and compliance workloads, in particular supporting compliance requirements such as GDPR that restrict the geographical movement of certain secrets.

With the introduction of namespaces in Vault 0.11, Vault Enterprise introduced a new way to segment secrets that does not map well with Mount Filters’ ability to manage the distribution of data across replicated clusters.

In Vault 1.3 we are releasing new functionality that enables Vault users to specify path filters. These path filters allow for mounts within namespaces to be filtered similar to existing mount filters, allowing for namespace admins to specify what secrets within a namespace will be omitted from performance replication.

For more information on path filters, see the [documentation](https://www.vaultproject.io/docs/enterprise/namespaces/index.html).

[»](https://www.hashicorp.com/blog/vault-1-3/#oracle-cloud-infrastructure-oci-integration) Oracle Cloud Infrastructure (OCI) Integration
----------------------------------------------------------------------------------------------------------------------------------------

Vault 1.3 sees the release of several new endpoints to support Oracle Cloud workloads. These features, developed as a contribution from the Oracle Cloud engineering team, include the following:

*   **[OCI Auth Method](https://www.vaultproject.io/docs/auth/oci.html):** An auth method for authenticating Oracle Cloud Infrastructure applications and users into Vault.
*   **[OCI Object Storage Backend](https://www.vaultproject.io/docs/configuration/storage/oci-object-storage.html):** Support for storing Vault data in within Oracle Cloud Infrastructure Object Storage.
*   **[OCI Auto Unseal](https://www.vaultproject.io/docs/configuration/seal/ocikms.html):** Auto Unseal a Vault Cluster using the Oracle Cloud Infrastructure Key Management System.

For more information see Oracle’s [announcement blog](https://blogs.oracle.com/cloud-infrastructure/announcing-oracle-cloud-infrastructure-plugins-for-hashicorp-vault).

[»](https://www.hashicorp.com/blog/vault-1-3/#other-features) Other Features
----------------------------------------------------------------------------

There are many new features in Vault 1.3 that have been developed over the course of the 1.2.x releases. We have summarized a few of the larger features below, and as always consult the [changelog](https://github.com/hashicorp/vault/blob/master/CHANGELOG.md) for full details:

*   **Improved KMIP Support:** Vault now supports KMIP operations for registering externally-derived keys to better support Vault serving as an external key management system for enterprise applications and systems. See the KMIP Server Secret engine [documentation](https://www.vaultproject.io/docs/secrets/kmip/index.html) for details.
*   **Stackdriver Metrics Sync:** Vault can now send metrics to [Stackdriver](https://cloud.google.com/stackdriver/). See the [configuration documentation](https://www.vaultproject.io/docs/config/index.html) for details.
*   **P384 Support:** Signing and verification is now supported with the P-384 (secp384r1) and P-521 (secp521r1) ECDSA curves in the Transit secret engine.
*   **AES128-GCM 96 Support**: Encryption and decryption is now supported in the transit secret engine via AES128-GCM96.

[»](https://www.hashicorp.com/blog/vault-1-3/#upgrade-details) Upgrade Details
------------------------------------------------------------------------------

Vault 1.3 introduces significant new functionality. As such, we provide both [general upgrade instructions](https://www.vaultproject.io/docs/upgrading/index.html) and a [Vault 1.3-specific upgrade](https://www.vaultproject.io/docs/upgrading/upgrade-to-1.3.0.html) page.

As always, we recommend upgrading and testing this release in an isolated environment. If you experience any issues, please report them on the [Vault GitHub issue tracker](https://github.com/hashicorp/vault/issues) or post to the [Vault mailing list](https://groups.google.com/forum/#!forum/vault-tool).

For more information about HashiCorp Vault Enterprise, visit [https://www.hashicorp.com/products/vault](https://www.hashicorp.com/products/vault). Users can download the open source version of Vault at [https://www.vaultproject.io](https://www.vaultproject.io/).

We hope you enjoy Vault 1.3!

  
  
from Hacker News https://ift.tt/2plEwED