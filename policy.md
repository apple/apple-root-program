# Apple Root Certificate Program

*Note*: This version comes into effect August 15, 2023.

Apple uses public key infrastructure (PKI) to secure and enhance the experience for Apple users.
Apple operating systems and applications (such as Safari and Mail) use a common store for root certificates; see <https://support.apple.com/kb/HT209143> and <https://support.apple.com/kb/HT212865>.
Apple requires certification authority (CA) providers to meet certain criteria, as documented herein.

## 1. Program Requirements

### 1.1 Audit Requirements

CA providers may fall into one or more of the below categories and must meet the obligations related to all certificate purposes for which they are enabled within the Apple Root Program.

CA providers must provide audit reports in the Common CA Database (CCADB).

*Note*: The presence of qualifications in an audit report is not, by itself, considered reason to remove a CA provider from the Apple Root Program.
The purpose of audits is to honestly and thoroughly assess a CA provider's compliance with requirements which are necessary to assure a secure and stable ecosystem.
Audit findings, including qualifications, can help to identify opportunities for improvement, whether for individual CA providers or for the wider industry as a whole.

#### 1.1.1 All CA Providers

CA providers must ensure their CAs are audited against the current version of at least one of the below criteria at least annually:
*   (Preferred) "WebTrust Principles and Criteria for Certification Authorities"
*   (Accepted on a case-by-case basis) "ETSI EN 319 411-1" LCP, NCP, or NCP+

#### 1.1.2 TLS CA Providers

CA providers must ensure their Transport Layer Security (TLS) enabled root CAs and all subordinate CAs capable of issuing TLS certificates are audited against the current version of at least one of the below sets of criteria at least annually:

*   (Preferred) "WebTrust Principles and Criteria for Certification Authorities" and "WebTrust Principles and Criteria for Certification Authorities -- SSL Baseline with Network Security"
*   (Accepted on a case-by-case basis) "ETSI EN 319 411-1" LCP and (DVCP or OVCP)
*   (Accepted on a case-by-case basis) "ETSI EN 319 411-1" NCP and EVCP

#### 1.1.3 EV TLS CA Providers

CA providers must ensure their Extended Validation (EV) enabled root CAs and all subordinate CAs capable of issuing EV TLS certificates are audited against the current version of at least one of the below sets of criteria at least annually:

*   (Preferred) "WebTrust Principles and Criteria for Certification Authorities", "WebTrust Principles and Criteria for Certification Authorities -- SSL Baseline with Network Security", and "WebTrust Principles and Criteria for Certification Authorities -- Extended Validation SSL"
*   (Accepted on a case-by-case basis) "ETSI EN 319 411-1 NCP" and EVCP

#### 1.1.4 S/MIME CA Providers

Effective December 1, 2024, CA providers must ensure their S/MIME enabled root CAs and all subordinate CAs capable of issuing S/MIME certificates **have been** and will continue to be audited against the current version of at least one of the below sets of criteria at least annually:

*   (Preferred) "WebTrust Principles and Criteria for Certification Authorities" and "WebTrust Principles and Criteria for Certification Authorities -- S/MIME"
*   (Accepted on a case-by-case basis) "ETSI TS 119 411-6" LCP, NCP, or NCP+

To further clarify expectations:

*   An initial audit period must begin no later than September 1, 2023.
*   An initial audit period must begin no earlier than the effective date of a CA provider's published CP/CPS which confirms the CA provider's compliance with the current version of the CA/Browser Forum Baseline Requirements for the Issuance and Management of Publicly-Trusted S/MIME Certificates.
*   An initial audit period must end no later than September 1, 2024.
*   The initial audit period must include a minimum of 60 days.
*   A complete period-of-time audit report must be published no later than December 1, 2024.
    *   Where applicable, CA providers must not delay their S/MIME audit beyond the audit cycle established for their other, extant CAs in the Apple Root Program.
*   Beginning September 1, 2023, S/MIME CA providers must deliver contiguous audit reports annually.
    *   In order to align audit periods following this initial audit period, S/MIME CA providers may adjust audit periods as desired, which may result in overlap between the initial audit period and future audit periods.

*Note*: Apple expects its S/MIME CA providers to be proactively seeking to comply with the CA/Browser Forum Baseline Requirements for the Issuance and Management of Publicly-Trusted S/MIME Certificates.
In order to ensure minimal disruption to currently included S/MIME CA providers, and in order to enable uninterrupted issuance of S/MIME certificates by these CA providers as the S/MIME Baseline Requirements come into effect, Apple expects audits to be conducted sufficiently early in the lifecycle of the Requirements to provide confidence that pre-existing CA providers have successfully transitioned their S/MIME CA systems into a compliant state.

#### 1.1.5 Lifecycle Event Reporting

CA providers must ensure all keys intended for use in a CA Certificate are included in lifecycle reports as part of their annual auditing procedures.
When Lifecycle Events have occurred during an audit period, they must be addressed either in:

*   the annual audit report(s) supplied to the Apple Root Program; or
*   separate reports supplied to the Apple Root Program within 90 days of the Event concluding.

Such reporting must minimally cover the following Lifecycle Events:

*   for keys intended for use in a Root CA Certificate and keys intended for use in a CA Certificate not operated by the CA provider:
    *   Key Generation Ceremony
*   for keys intended for use in a CA Certificate:
    *   Key Backup, Storage, and Recovery
    *   Key Transport
    *   Key Destruction

### 1.2 Audit Engagement Requirements

#### 1.2.1 Auditor Annual Training

CA providers must ensure auditors involved in external audit engagements undergo and/or have undergone annual training specific to the subject matter assessed within the Audit Criteria outlined in section 1.1.

*Note*: CA providers and auditors are encouraged to reach out to the Apple Root Program with questions and for recommendations.
By way of example, if the auditor has undergone training to review the changes made to the Audit Criteria they're assessing, that would meet this requirement.
CA providers are not required to share with Apple the evidence used to verify Auditor Annual Training compliance.

#### 1.2.2 Firm and Auditor Qualifications

CA providers must ensure audits used to comply with this policy are performed by entities licensed or otherwise permitted to provide assurance services in the country(ies) where the assessment is performed, for the entirety of the audit engagement's duration.

*Note*: CA providers are not required to share with Apple the evidence used to verify Firm and Auditor Qualifications meet these requirements.
*   WebTrust
    *   Firms must:
        *   be enrolled in the WebTrust Program (managed by CPA Canada);
        *   be registered as a legal entity in good standing;
        *   be registered as an accountancy or auditing firm in good standing with a corresponding national accounting body, which is a member of IFAC; and
        *   have no outstanding legal or professional indicators that an audit could not be performed.
    *   Signing Partners and QA Partners must:
        *   be members in good standing with a national accounting body, which is a member of IFAC;
        *   have experience in the entire process of Certification Authority assessment; and
        *   have up-to-date knowledge in Public Key Infrastructure, Information Security Management, and management system assessment.
    *   Field staff should be members in good standing with a national accounting body, which is a member of IFAC and must:
        *   maintain IT specialist certification (e.g., CISA, CISM, etc.); and
        *   be familiar with the requirements established by the CA/Browser Forum and the WebTrust Principles and Criteria associated with the assessment being performed.
*   ETSI
    *   Conformity Assessment Bodies must be accredited for the certification of trust services according to:
        *   "EN ISO/IEC 17065\"; and
        *   "ETSI EN 319 403 V2.2.2 (2015-08)" or "ETSI EN 319 403-1 V.2.3.1 (2020-06)" or later.
    *   Audits must be performed and audit reports written taking into consideration:
        *   "ETSI TS 119 403-2 V1.2.4 (2020-11)" or later; and
        *   requirements established by the CA/Browser Forum associated with the assessment being performed.
    *   Auditors and all personnel performing audits, reviews, or certification decisions must be:
        *   registered members of the Conformity Assessment Body in their specific role; and
        *   familiar with the requirements established by the CA/Browser Forum associated with the assessment being performed.

#### 1.2.3 Additional Requirements or Obligations

*   Apple reserves the right to require a CA provider to complete additional audit engagements.
*   Apple reserves the right to appoint or reject an auditor for a CA provider.
*   Apple reserves the right to require a detailed controls report from a CA provider.
    *   A detailed controls report provides a thorough description of a CA provider's certification authority system and design as well as their implementation and operating effectiveness of PKI controls.
    *   A detailed controls report may be a single report or a collection of artifacts which together provide the requisite information.

*Note*: Due to how audit engagements are structured, additional audit engagements, the appointment or rejection of an auditor, and a detailed controls report are actions that would typically apply to a future audit.

#### 1.2.4 Incidents

CA providers must ensure that audit reports include information regarding all incidents, as described and defined below under Section 3 "Incidents" and as required by section 5.1 of the CCADB Policy (<https://www.ccadb.org/policy>).

### 1.3 Standards and Policy Document Compliance Requirements

#### 1.3.1 All CA Providers

CA providers must strictly adhere to their Certificate Policy (CP) and/or Certification Practices Statement (CPS) document(s) as disclosed within the CCADB (and not marked as "Deleted").

*Note*: This extends to all policy documents the CA provider publishes in relation to its CAs included in the Apple Root Program, such as TSPS documents.

CA providers must strictly adhere to the current version of the CCADB Policy (<https://www.ccadb.org/policy>).

#### 1.3.2 TLS CA Providers

TLS CA providers must constantly maintain compliance with the current version of the CA/Browser Forum Baseline Requirements Certificate Policy for the Issuance and Management of Publicly-Trusted Certificates (TLS Baseline Requirements).

TLS CA providers must incorporate and commit to compliance with the current version of the CA/Browser Forum's Baseline Requirements in their CP and/or CPS documents.

#### 1.3.3 EV TLS CA Providers

EV TLS CA providers must constantly maintain compliance with the current version of the CA/Browser Forum Guidelines For The Issuance And Management Of Extended Validation Certificates (EV Guidelines).

EV TLS CA providers must incorporate and commit to compliance with the current version of the CA/Browser Forum's EV Guidelines in their CP and/or CPS documents.

#### 1.3.4 S/MIME CA Providers

Effective September 1, 2023, S/MIME CA providers must constantly maintain compliance with the current version of the CA/Browser Forum Baseline Requirements for the Issuance and Management of Publicly-Trusted S/MIME Certificates (S/MIME Baseline Requirements).

*Note*: This also requires that end-entity S/MIME certificates must be issued from a CA Certificate compliant with the S/MIME Baseline Requirements.

Effective September 1, 2023, S/MIME CA providers must incorporate and commit to compliance with the current version of the CA/Browser Forum's S/MIME Baseline Requirements in their CP and/or CPS documents.

### 1.4 Communication Requirements

*   CA providers must maintain up to date contact details in the CCADB.
*   CA providers are accountable for keeping up to date on discussions in and implementing any changes necessary to conform with changes communicated via the following:
    *   CA communications from Apple (typically via CCADB)
    *   CA/Browser Forum Public Discussion List (<https://lists.cabforum.org/mailman/listinfo/public>)
    *   CA/Browser Forum Server Certificate Working Group (<https://lists.cabforum.org/mailman/listinfo/servercert-wg>)
    *   CA/Browser Forum Validation Subcommittee (<https://lists.cabforum.org/mailman/listinfo/validation>)
    *   CA/Browser Forum Networking Security Working Group (<https://lists.cabforum.org/mailman/listinfo/netsec>)
    *   CA/Browser Forum SMIME Certificate Working Group (<https://lists.cabforum.org/mailman/listinfo/smcwg-public>)
    *   CCADB Public Discussion List (<https://groups.google.com/a/ccadb.org/g/public>)
*   CA providers must notify Apple if they anticipate any change in control or ownership of any CA Certificate (whether directly included or subordinate thereto).
    Inclusion is not transferable without prior approval by Apple.

### 1.5 Inclusion Requirements
*   CA providers applying for inclusion in the Apple Root Program are expected to meet all applicable Program and Policy requirements prior to submitting an application.
*   CA providers must strictly limit the number of Root CA Certificates per CA provider, especially those capable of issuing multiple types of certificates.
*   CA providers and their Root CA Certificates must provide broad value to Apple's users.
*   CA providers must complete all fields required in the CCADB Root Inclusion Request Case.

## 2. Policy Requirements

*Note*: For effective dates related to certificate issuance, the requirement is enforced for certificates issued on or after the specified date at 00:00:00 UTC.

### 2.1 General

*   CA providers should be aware that issuance of a precertificate or certificate chaining up to an included CA Certificate constitutes authorization by the CA provider for that certificate.
*   CA providers should be aware that participation in the Apple Root Program as a CA provider constitutes a Root Certificate distribution agreement, as referenced in Section 9.9 of the TLS Baseline Requirements, between CA providers and Apple.

#### 2.1.1 CA Disclosure

Effective April 1, 2022, CA providers must disclose in the CCADB all CA Certificates which chain up to their CA Certificate(s) included in the Apple Root Program.

#### 2.1.2 Full CRLs

Effective October 1, 2022, CA providers must populate the CCADB fields under "Pertaining to Certificates Issued by This CA" with either the CRL Distribution Point for the "Full CRL Issued By This CA" or a "JSON Array of Partitioned CRLs" on Root and Intermediate Certificate records, within 7 days of the corresponding CA issuing its first certificate.
This requirement applies to each included CA Certificate and each CA Certificate chaining up to an included CA Certificate in the Apple Root Program.

*   When populating the "JSON Array of Partitioned CRLs" with multiple CRL URLs, CA providers must ensure that each CRL contains a critical Issuing Distribution Point extension and the distributionPoint field of the extension must include a UniformResourceIdentifier.
    *   The value of the UniformResourceIdentifier must exactly match a URL, from which the CRL was accessed, present in the "JSON Array of Partitioned CRLs" field in the CCADB record associated with the Issuing CA Certificate.
*   When populating the "Full CRL Issued By This CA" with a single CRL URL, the CRL should not contain an Issuing Distribution Point extension.
*   Under normal operating conditions, the CRL URLs provided by CAs in this section must be available such that Apple systems are able to successfully retrieve the current CRL every 4 hours.

#### 2.1.3 Single-purpose Root CAs

Effective April 15, 2024, all CA providers applying to the Apple Root Program must submit only Root CA Certificates dedicated to a single purpose.
Valid certificate purposes are:

*   TLS
    *   All CA Certificates subordinate to the applicant Root CA Certificate must
        *   contain the `extendedKeyUsage` extension which must contain only
            *   the `id-kp-serverAuth` OID; or
            *   the `id-kp-serverAuth` OID and the `id-kp-clientAuth` OID; and
        *   not contain the same public key as any other certificate which asserts any other `extendedKeyUsage` OIDs.
*   S/MIME
    *   All CA Certificates subordinate to the applicant Root CA Certificate must
        *   contain the `extendedKeyUsage` extension and the `extendedKeyUsage` extension must contain only
            *   the `id-kp-emailProtection` OID; or
            *   the `id-kp-emailProtection` OID and the `id-kp-clientAuth` OID; and
        *   not contain the same public key as any other certificate which asserts any other `extendedKeyUsage` OIDs.
*   Client Authentication
    *   All CA Certificates subordinate to the applicant Root CA Certificate must
        *   contain the `extendedKeyUsage` extension, and the `extendedKeyUsage` extension must contain the `id-kp-clientAuth` OID, and the `extendedKeyUsage` extension must not contain:
            *   the `id-kp-serverAuth` OID;
            *   the `id-kp-emailProtection` OID; nor
            *   the `id-kp-timeStamping` OID; and
        *   not contain the same public key as any other certificate which asserts any other `extendedKeyUsage` OIDs.
*   Timestamping
    *   All CA Certificates subordinate to the applicant Root CA Certificate must
        *   contain the `extendedKeyUsage` extension and the `extendedKeyUsage` extension must contain only the `id-kp-timeStamping` OID; and
        *   not contain the same public key as any other certificate which asserts any other `extendedKeyUsage` OIDs.

*Note*: In a future version of the Apple Root Program Policy, it is expected that already-included Root CA Certificates which do not comply with the above guidance will be removed from the Apple Root Program.

### 2.2 TLS

*   Effective August 15, 2024, TLS CA providers must support at least one of the following domain validation methods from the TLS Baseline Requirements:
    *   3.2.2.4.7 DNS Change
    *   3.2.2.4.18 Agreed-Upon Change to Website v2
    *   3.2.2.4.19 Agreed-Upon Change to Website - ACME
    *   3.2.2.4.20 TLS Using ALPN

### 2.3 S/MIME

*   Effective April 1, 2022, S/MIME certificates must:
    *   include the `emailProtection` EKU
    *   include at least one subjectAlternativeName `rFC822Name` value containing an email address
    *   not have a validity period greater than 1185 days
    *   use a signature hash algorithm of greater than or equal strength to SHA-256 (see section 7.1.3.1 and 7.1.3.2 of the CA/B Forum's TLS Baseline Requirements).
    *   meet the following key size requirements:
        *   For RSA key pairs, the modulus size must be at least 2048 bits when encoded and its size in bits must be evenly divisible by 8.
        *   For ECDSA key pairs, the key must represent a valid point on the NIST P-256, NIST P-384 or NIST P-521 named elliptic curve.

## 3. Incidents

Failure to comply with the above requirements in any way is considered an incident.
CA providers must report such incidents to the Apple Root Program at <certificate-authority-program@apple.com> with a full incident report.
This report can be shared directly or as a link from a public disclosure (e.g. Bugzilla).

Of paramount importance for CA providers when submitting incident reports and participating in all follow-up discussion are:

*   a demonstration of quality in investigation and depth of knowledge in the root cause analysis, including analyzing for variants;
*   timeliness and transparency in responding to questions; and
*   thoroughness and specificity in the identification and implementation of remediation tasks.

## 4. Submission Process

To begin the submission process, request access to the CCADB and create a Root Inclusion Request Case in the CCADB.
Once complete, e-mail <certificate-authority-program@apple.com> with the details of your Root Inclusion Request Case.
CA providers will be contacted if any additional information is required, and when consideration of the Root Inclusion Request is complete.
For more information on the CCADB, please see [https://www.ccadb.org/cas](https://www.ccadb.org/cas/).

## 5. Root Acceptance

Apple accepts and removes Root CA Certificates and CA providers as it deems appropriate at its sole discretion.
Apple prioritizes Root Inclusion Requests as it deems appropriate at its sole discretion.
