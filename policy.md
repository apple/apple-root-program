# Apple Root Program Policy

**Version 2.0**

**Effective TBD, 2026**

## Introduction

Apple uses public key infrastructure (PKI) to secure and enhance the experience of Apple users.
Apple operating systems and applications (such as Safari and Mail) use a common store for Root CA Certificates; see [https://support.apple.com/103272](https://support.apple.com/103272) and [https://support.apple.com/103255](https://support.apple.com/103255).
Apple requires certification authority (CA) Owners to meet certain criteria, as documented herein.

*Note*: The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in [BCP 14](https://www.rfc-editor.org/info/bcp14).

## Definitions

**Baseline Requirements**: Industry-standard requirements published by the CA/Browser Forum or other standards bodies that govern the issuance and management of publicly-trusted certificates.
Specific Baseline Requirements applicable to each Trust Purpose are defined in [Appendix A](#appendix-a-trust-purposes).

**CA Owner**: The organization or legal entity that is either represented in the subject DN of the CA certificate or in possession or control of the corresponding private key capable of issuing new certificates, if not the same organization or legal entity directly represented in the subject DN of the certificate.
This definition includes CA Owners whose CA certificates are not directly included in this root program but chain to those that are.

**Current Version**: For audit criteria, the version in effect at the beginning of the audit period. For other requirements, the version in effect at the time of assessment or compliance.

**Detailed Controls Report (DCR)**: For WebTrust audits, the report produced by the auditor documenting the CA's controls.
For ETSI audits, equivalent documentation mapping controls to requirements and processes demonstrating how those controls meet the requirements.

**Trust Purpose**: A designated use case for certificates as defined in [Appendix A](#appendix-a-trust-purposes), such as Server Authentication, Secure Email, or Code Signing.

## Table of Contents

1. [Program Requirements](#1-program-requirements)
   * [1.1 Audit Requirements](#11-audit-requirements)
   * [1.2 Audit Engagement Requirements](#12-audit-engagement-requirements)
   * [1.3 Standards and Policy Document Compliance Requirements](#13-standards-and-policy-document-compliance-requirements)
   * [1.4 Communication Requirements](#14-communication-requirements)
   * [1.5 Inclusion Requirements](#15-inclusion-requirements)
   * [1.6 Due Diligence Requirements](#16-due-diligence-requirements)
   * [1.7 Subordinate CA Requirements](#17-subordinate-ca-requirements)
2. [Policy Requirements](#2-policy-requirements)
   * [2.1 General](#21-general)
   * [2.2 TLS Trust Purposes](#22-tls-trust-purposes)
3. [Incidents](#3-incidents)
4. [Root Inclusion Submission Process](#4-root-inclusion-submission-process)
5. [Root Program Management](#5-root-program-management)
   * [5.1 Constraints](#51-constraints)

[Appendix A: Trust Purposes](#appendix-a-trust-purposes)

## Change Log

| Version | Date | Change Description |
| :------ | :--- | :----------------- |
| 2.0 | 2026-MM-DD | Converted to Markdown format. Introduced versioning and change log. Restructured policy organization. Added VMC trust purpose. Separated SSL Baseline and Network Security audit criteria. Added lifecycle event reporting requirements. Required annual detailed controls report attestation (effective 2027-07-01). Required Markdown CP/CPS format and single trust purpose scoping per CP/CPS (effective 2027-07-01). Required single-purpose subordinate CAs for certificates issued after 2026-07-01. Required minimum RSA 4096-bit or ECDSA 384-bit for new root inclusions. Required support for specified domain validation methods. Added conflict resolution clause for overlapping requirements. Added change of control and ownership notification requirements. Streamlined requirements by referencing CCADB Policy where applicable. |
| 1.0 | 2023-08-15 | Last version before versioning was introduced |

## 1. Program Requirements

### 1.1 Audit Requirements

CA Owners MUST meet the audit obligations for all Trust Purposes (as defined in Appendix A) for which they are enabled within the Apple Root Program.

CA Owners MUST provide audit reports in the Common CA Database (CCADB).

*Note*: The presence of qualifications in an audit report is not, by itself, considered reason to remove a CA Owner from the Apple Root Program. The purpose of audits is to honestly and thoroughly assess a CA Owner's compliance with requirements which are necessary to assure a secure and stable ecosystem. Audit findings, including qualifications, can help to identify opportunities for improvement, whether for individual CA Owners or for the wider industry as a whole.

#### 1.1.1 All CA Owners

All CAs MUST be audited at least annually against the version in effect at the beginning of the audit period of at least one of the below:

* WebTrust (Preferred)
  * "WebTrust Principles and Criteria for Certification Authorities"
* ETSI (Accepted on a case-by-case basis)
  * "ETSI EN 319 411-1" LCP, NCP, or NCP+

#### 1.1.2 TLS CA Owners

CAs capable of issuing TLS certificates MUST be audited at least annually against the version in effect at the beginning of the audit period of at least one of the below sets of criteria:

* WebTrust
  * Preferred:
    * "WebTrust Principles and Criteria for Certification Authorities";
    * "WebTrust Principles and Criteria for Certification Authorities - SSL Baseline"; and
    * "WebTrust Principles and Criteria for Certification Authorities - Network Security"
  * Accepted:
    * "WebTrust Principles and Criteria for Certification Authorities"; and
    * "WebTrust Principles and Criteria for Certification Authorities - SSL Baseline with Network Security"
* ETSI (Accepted on a case-by-case basis)
  * "ETSI EN 319 411-1" LCP and (DVCP or OVCP); or
  * "ETSI EN 319 411-1" NCP and EVCP

#### 1.1.3 EV TLS CA Owners

CAs capable of issuing EV TLS certificates MUST be audited at least annually against the version in effect at the beginning of the audit period of at least one of the below sets of criteria:

* WebTrust (Preferred)
  * Preferred:
    * "WebTrust Principles and Criteria for Certification Authorities";
    * "WebTrust Principles and Criteria for Certification Authorities - SSL Baseline";
    * "WebTrust Principles and Criteria for Certification Authorities - Network Security"; and
    * "WebTrust Principles and Criteria for Certification Authorities - Extended Validation SSL"
  * Accepted:
    * "WebTrust Principles and Criteria for Certification Authorities";
    * "WebTrust Principles and Criteria for Certification Authorities - SSL Baseline with Network Security"; and
    * "WebTrust Principles and Criteria for Certification Authorities - Extended Validation SSL"
* ETSI (Accepted on a case-by-case basis)
  * "ETSI EN 319 411-1" NCP and EVCP

#### 1.1.4 S/MIME CA Owners

CAs capable of issuing S/MIME certificates MUST be audited at least annually against the version in effect at the beginning of the audit period of at least one of the below sets of criteria:

* WebTrust (Preferred)
  * "WebTrust Principles and Criteria for Certification Authorities";
  * "WebTrust Principles and Criteria for Certification Authorities - Network Security"; and
  * "WebTrust Principles and Criteria for Certification Authorities - S/MIME"
* ETSI (Accepted on a case-by-case basis)
  * "ETSI TS 119 411-6" LCP, NCP, or NCP+

#### 1.1.5 VMC CA Owners

CAs capable of issuing VMC certificates MUST be audited at least annually against the version in effect at the beginning of the audit period of at least one of the below sets of criteria:

* WebTrust
  * "WebTrust Principles and Criteria for Certification Authorities";
  * "WebTrust Principles and Criteria for Certification Authorities - Network Security"; and
  * "WebTrust Principles and Criteria for Certification Authorities - Verified Mark Certificates"

#### 1.1.6 Lifecycle Event Reporting

CA Owners MUST ensure all keys intended for use in a CA Certificate are included in lifecycle reports as part of their annual auditing procedures. When Lifecycle Events have occurred during an audit period, they MUST be addressed either in:

* the annual audit report(s) supplied to the Apple Root Program; or
* separate reports supplied to the Apple Root Program within 90 days of the Event concluding.

Such reporting MUST minimally cover the following Lifecycle Events:

* for keys intended for use in a Root CA Certificate and keys intended for use in a CA Certificate not operated by the CA Owner:
  * Key Generation Ceremony
* for keys intended for use in a CA Certificate:
  * Key Backup, Storage, and Recovery
  * Key Transport
  * Key Destruction

### 1.2 Audit Engagement Requirements

#### 1.2.1 Auditor Annual Training

CA Owners MUST ensure auditors involved in external audit engagements undergo and/or have undergone annual training specific to the subject matter assessed within the Audit Criteria outlined in [Section 1.1](#11-audit-requirements).

*Note*: CA Owners and auditors are encouraged to reach out to the Apple Root Program with questions and for recommendations.
By way of example, if the auditor has undergone training to review the changes made to the Audit Criteria they're assessing, that would meet this requirement.
CA Owners are not required to share with Apple the evidence used to verify Auditor Annual Training compliance.

#### 1.2.2 Firm and Auditor Qualifications

CA Owners MUST ensure audits comply with the firm and auditor qualification requirements specified in CCADB Policy Section 5.3.

*Note*: Audit statements MUST include auditor qualification documentation as required by CCADB Policy Section 5.3.1.

#### 1.2.3 Additional Requirements or Obligations

Apple reserves the right to require a CA Owner to complete additional audit engagements, appoint or reject an auditor, or require submission of a detailed controls report to Apple.

#### 1.2.3.1 Detailed Controls Report

A detailed controls report documents a CA Owner's certification authority system, design, controls, verification methods, scope boundaries, and operating effectiveness.

Effective 2027-07-01, for every annual audit, the CA Owner MUST:

1. Ensure the auditor produces a detailed controls report.
2. Ensure the auditor contract allows for the detailed controls report to be shared with Apple.
3. Review the report before attestation letter finalization.
4. Provide written attestation to Apple by adding a Case Comment to the 'CASE PROGRESS' tab of the CCADB "Add/Update Root Request" case for that audit confirming review and accuracy of the detailed controls report.

Apple MAY require the CA Owner to provide Apple with a copy of each recent detailed controls report.
When requested, the CA Owner MUST provide them to Apple within 30 days.

*Note 1*: For WebTrust audits, this is the Detailed Controls Report (DCR).
For ETSI audits, it is equivalent documentation mapping controls to requirements.

*Note 2*: Additional audit engagements and auditor appointment/rejection typically apply to future audits.

#### 1.2.4 Incidents

CA Owners MUST ensure audit reports include incident information as required by the [CCADB Policy](https://www.ccadb.org/policy).

### 1.3 Standards and Policy Document Compliance Requirements

CA Owners MUST strictly adhere to:

* the current version of the [CCADB Policy](https://www.ccadb.org/policy), including but not limited to:
  * Annual self-assessment requirements (CCADB Policy Section 6.4)
  * Cross-certificate EKU requirements (CCADB Policy Section 6.3)
  * CRL disclosure and availability requirements (CCADB Policy Section 6.2)
  * Incident reporting guidelines (CCADB Policy Section 6.1)
  * Audit statement content requirements (CCADB Policy Section 5.2)
  * Firm and auditor qualification requirements (CCADB Policy Section 5.3);
* their policy documents as disclosed in the CCADB; and
* the Baseline Requirements specified in Appendix A for their designated Trust Purpose(s).

When new versions of the [CCADB Policy](https://www.ccadb.org/policy) are published without a future Effective Date, CA Owners MUST adhere to the new version within 14 days of its publication.

**Conflict Resolution:**
Where this policy imposes requirements that are more restrictive than CCADB Policy or applicable Baseline Requirements (such as minimum key sizes for new root inclusions, required domain validation methods, or CP/CPS formatting), CA Owners MUST comply with the more restrictive requirements specified in this policy.

CA Owners uncertain about which requirement applies should contact the Apple Root Program for clarification before taking action.

#### 1.3.1 Policy Document Requirements

CA Owners MUST incorporate and commit to compliance with the Baseline Requirements applicable to their designated Trust Purpose(s) in their CP/CPS document.

Effective 2027-07-01, all policy documents MUST adhere to the following:

1. **Format:** Documents MUST be a combined Certificate Policy and Certification Practice Statement (CP/CPS) in MarkDown format with .md file extension.
The Markdown file is the authoritative version in CCADB.
CA Owners MAY publish additional formats for convenience.

2. **Content Integrity:** Each CP/CPS document MUST be self-contained with respect to the CA Owner's specific practices and procedures.
The CP/CPS MUST describe the CA Owner’s practices for meeting applicable requirements, including any CA‑specific or additional requirements.
The CP/CPS MUST NOT rely on incorporation by reference to external operational standards.
Even if an operational standard permits incorporation by reference, this policy supersedes that allowance.

4. **Trust Purpose Scoping:**

   * Each CP/CPS document MUST be scoped to a single Trust Purpose (as defined in Appendix A).
   * The Trust Purpose and required EKU(s) MUST be stated in Section 1.4 of the CP/CPS.
   * A Root CA Certificate hierarchy supporting multiple Trust Purposes MUST provide a distinct CP/CPS document for each Trust Purpose.
   * Multiple Root CA Certificate hierarchies MAY reference the same CP/CPS document if they share the same Trust Purpose.

### 1.4 Communication Requirements

* CA Owners MUST maintain up to date contact details in the CCADB.
* CA Owners are accountable for keeping up to date on discussions in and implementing any changes necessary to conform with changes communicated via the following:
   * CA communications from Apple (typically via CCADB)
   * [CA/Browser Forum Public Discussion List](https://groups.google.com/a/groups.cabforum.org/g/public)
   * [CA/Browser Forum Server Certificate Working Group](https://groups.google.com/a/groups.cabforum.org/g/servercert-wg)
   * [CA/Browser Forum Validation Subcommittee](https://groups.google.com/a/groups.cabforum.org/g/validation)
   * [CA/Browser Forum Network Security Working Group](https://groups.google.com/a/groups.cabforum.org/g/netsec)
   * [CA/Browser Forum SMIME Certificate Working Group](https://groups.google.com/a/groups.cabforum.org/g/smcwg-public)
   * [CCADB Public Discussion List](https://groups.google.com/a/ccadb.org/g/public)
* CA Owners MUST notify Apple if they anticipate any change in control or ownership of any CA Certificate (whether directly included or subordinate thereto).
    The acquiring CA MUST disclose its ownership, jurisdiction, continuity of audits with independent WebTrust/ETSI auditor confirmation that all evidence since root signing is retained, and its plans for managing legacy roots and key material.
    Continued inclusion requires Apple approval and is not transferable.
* CA Owners MUST receive approval from Apple prior to issuing a Subordinate CA Certificate to any entity which is not the CA Owner.

### 1.5 Inclusion Requirements

* CA Owners and their Root CA Certificates MUST provide broad value to Apple's users.
* CA Owners applying for inclusion in the Apple Root Program are expected to meet all applicable Program and Policy requirements prior to submitting an application.
* CA Owners MUST strictly limit the number of Root CA Certificates per CA Owner, especially those capable of issuing multiple types of certificates.
* CA Owners MUST complete all fields required in the CCADB Root Inclusion Request Case.
* Root Inclusion Requests will only be accepted for Root CA hierarchies dedicated to a single Trust Purpose (as defined in Appendix A) with a single combined CP/CPS document in MarkDown format (.md file extension).
* Root Inclusion Requests MUST only contain Root CA Certificates which have a minimum key size of RSA 4096-bit or ECDSA 384-bit.

### 1.6 Due Diligence Requirements

The Apple Root Program reserves the right to require additional clarifying information to resolve ambiguities that arise during routine due diligence.
CA Owners MUST respond to such requests within 14 calendar days.
If a CA Owner requires additional time, they MUST notify Apple within the initial 14-day period with an estimated completion date and get Apple approval for the extension.

### 1.7 Subordinate CA Requirements

Subordinate CA Certificates created after 2026-07-01 MUST be dedicated to a single Trust Purpose as defined in [Appendix A](#appendix-a-trust-purposes), regardless of whether the hierarchy supports multiple Trust Purposes.

*Note*: This requirement is consistent with and may overlap with requirements in applicable CA/Browser Forum Baseline Requirements.

## 2. Policy Requirements

*Note*: For effective dates related to certificate issuance, the requirement is enforced for certificates issued on or after the specified date at 00:00:00 UTC.

### 2.1 General

* Root CA Owners SHOULD be aware that issuance of a precertificate or certificate chaining up to an included CA Certificate constitutes authorization by the Root CA Owner for that certificate.
* Root CA Owners SHOULD be aware that participation in the Apple Root Program constitutes a Root Certificate distribution agreement, as referenced in Section 9.9 of the TLS Baseline Requirements or S/MIME Baseline Requirements, between the Root CA Owner and Apple.

#### 2.1.1 CA Disclosure

CA Owners MUST disclose all CA Certificates in the CCADB as required by the CCADB Policy, including the requirement that CRL URLs be available for successful retrieval every 4 hours under normal operating conditions.

*Note*: CA Certificates not disclosed in the CCADB MAY not function on Apple Devices.
It is RECOMMENDED that CA Owners disclose CA Certificates in the CCADB at least 14 days before beginning to issue from the CA Certificate.

#### 2.1.2 CRLs

CA Owners MUST populate CRL information in the CCADB as required by the CCADB Policy.

#### 2.1.3 Single-Purpose Root CAs

CA Owners applying to the Apple Root Program MUST submit only Root CA Certificates dedicated to a single Trust Purpose as defined in [Appendix A](#appendix-a-trust-purposes).
All subordinate CA Certificates in these hierarchies MUST contain only the EKU(s) specified in [Appendix A](#appendix-a-trust-purposes) for the designated Trust Purpose.

*Note*: Root CA Certificates included before this policy version that support multiple Trust Purposes MAY continue operating.
Apple reserves the right to require transition to single-purpose operation.

### 2.2 TLS Trust Purposes

For Server Authentication and Legacy TLS Trust Purposes:

CA Owners MUST support at least one of the following domain validation methods from the TLS Baseline Requirements:
* 3.2.2.4.7 DNS Change
* 3.2.2.4.18 Agreed-Upon Change to Website v2
* 3.2.2.4.19 Agreed-Upon Change to Website - ACME
* 3.2.2.4.20 TLS Using ALPN

TLS CA Owners SHOULD be aware that TLS subscriber certificates MUST comply with the [Apple Certificate Transparency Policy](https://support.apple.com/en-us/103214) to be accepted for connection establishment on Apple devices.

## 3. Incidents

Failure to comply with this policy in any way is considered an incident.
CA Owners MUST follow the [CCADB Incident Reporting Guidelines](https://www.ccadb.org/cas/incident-report) for all incidents.

## 4. Root Inclusion Submission Process

To begin the submission process, request access to the CCADB and create a Root Inclusion Request Case in the CCADB.
Once all minimum requirements are met, submit the Root Inclusion Request case in CCADB.
CA Owners will be contacted if any additional information is required, and when consideration of the Root Inclusion Request is complete.
For more information on the CCADB, please see [https://www.ccadb.org/cas](https://www.ccadb.org/cas).

## 5. Root Program Management

Apple accepts and removes Root CA Certificates and CA Owners as it deems appropriate at its sole discretion.
Apple prioritizes Root Inclusion Requests as it deems appropriate at its sole discretion.

### 5.1 Constraints

The Apple Root Program MAY apply additional constraints to CA Certificates and their hierarchies under exceptional circumstances.
These constraints MAY include, but are not limited to, any of the following:

* leaf certificates issued before, after, or between configured date(s) will not validate
* the maximum allowed validity period for leaf certificates is constrained
* the set of policy OIDs asserted in leaf certificates is constrained to a subset of the policy OIDs otherwise allowed for the CA Certificate's designated Trust Purpose
* the domain names and/or top-level domains for which leaf certificates will validate is constrained to a subset of what is otherwise allowed for the CA Certificate's designated Trust Purpose

## Appendix A: Trust Purposes

The Apple Root Program recognizes the following Trust Purposes:

| Trust Purpose | Required EKU(s) | Baseline Requirements |
|---------------|-----------------|----------------------|
| Server Authentication | id-kp-serverAuth (1.3.6.1.5.5.7.3.1) | TLS BR |
| Legacy TLS | id-kp-serverAuth (1.3.6.1.5.5.7.3.1)<br>id-kp-clientAuth (1.3.6.1.5.5.7.3.2) | TLS BR |
| Secure Email | id-kp-emailProtection (1.3.6.1.5.5.7.3.4) | S/MIME BR |
| Legacy S/MIME | id-kp-emailProtection (1.3.6.1.5.5.7.3.4)<br>id-kp-clientAuth (1.3.6.1.5.5.7.3.2) | S/MIME BR |
| Client Authentication | id-kp-clientAuth (1.3.6.1.5.5.7.3.2) | CA-defined (subject to Apple approval) |
| Time Stamping | id-kp-timeStamping (1.3.6.1.5.5.7.3.8) | RFC 3161 and CA-defined (subject to Apple approval) |
| VMC | id-kp-BrandIndicatorforMessageIdentification (1.3.6.1.5.5.7.3.31) | VMC Requirements |

**Baseline Requirements Definitions:**

* **TLS BR**: CA/Browser Forum Baseline Requirements for the Issuance and Management of Publicly-Trusted TLS Server Certificates
* **EV Guidelines**: CA/Browser Forum Guidelines for the Issuance and Management of Extended Validation Certificates
* **S/MIME BR**: CA/Browser Forum Baseline Requirements for the Issuance and Management of Publicly-Trusted S/MIME Certificates
* **VMC Requirements**: AuthIndicator Working Group Minimum Security Requirements for Issuance of Mark Certificates

**Additional Notes:**

* For all Trust Purposes, subordinate CA Certificates MUST contain only the EKU(s) specified for that Trust Purpose.
Subscriber (end-entity) certificates MAY contain any subset of the permitted EKU(s).
* For Trust Purposes with multiple required EKUs, CA Owners MAY provide one CP/CPS document per EKU.
* For "Server Authentication" and "Legacy TLS," CA Owners issuing Extended Validation certificates MUST also comply with EV Guidelines.
* For "Legacy S/MIME," the id-kp-clientAuth EKU MUST be used only for S/MIME-related client authentication as permitted by the S/MIME Baseline Requirements.
* Root CA Certificates included before this policy version that support multiple Trust Purposes MAY continue operating under existing configurations.
Apple reserves the right to require transition to single-purpose operation.
