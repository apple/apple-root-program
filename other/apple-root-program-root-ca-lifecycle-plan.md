# Apple Root Program Root CA Lifecycle and Replacement Plan

## What to do

Complete one row per Root CA Certificate your organization has included in the
Apple Root Program or has pending for new inclusion. Return the completed CSV as
a file linked in a comment on your CCADB inclusion case.

List every Root CA Certificate your organization has included in the Apple Root
Program. Seed from the public CA Certificate report on ccadb.org, and include
any Root CA Certificate still present that CCADB does not reflect. The goal is
one holistic view of all your included Root CA Certificates plus any pending for
inclusion. Do not include enterprise or private CA certificates that are not
associated with the Apple Root Program.

## Definitions

**Retirement** means removal of a Root CA Certificate from an Apple OS release.
Cessation of issuance is expected for every Root CA Certificate being retired:
no new subscriber certificates may be signed under that hierarchy on or after
the retirement date. The only exception is subscriber certificates signed under
a cross-signed hierarchy where the cross-signing Root CA Certificate is
separately included, or from the successor Root CA Certificate if it cross-signs
the one being replaced.

**SuccessorIncluded** (in a relative formula) means the date the successor Root
CA Certificate is verified in an Apple OS release (the ship date), not the date
Apple communicates inclusion to the CA Owner. The OS ship date is measurable and
observable in the ecosystem.

## Columns

| Column | Meaning |
| --- | --- |
| `RootCACertificateName` | Common name as shown in CCADB. |
| `SHA256Fingerprint` | SHA-256 fingerprint, 64 hex characters, no colons. |
| `AppleTrustPurposes` | Trust Purposes held or requested, using the names from ARP Policy 2.0 Appendix A: `Server Authentication`, `Legacy TLS`, `Secure Email`, `Legacy S/MIME`, `Client Authentication`, `Time Stamping`, `VMC`. Semicolon-separated when multiple apply (e.g. `Server Authentication; Secure Email`). |
| `LifecycleIntent` | `active` (no retirement plan), `replacement planned` (successor identified; name it in SuccessorSHA256 and state a RetirementTimeline), `retirement committed` (committing to removal; state a RetirementTimeline), or `net-new` (no predecessor; state a NewRootJustification). |
| `SuccessorSHA256` | SHA-256 of the successor Root CA Certificate, if any. `N/A` if none. |
| `RetirementTimeline` | An absolute date (`YYYY-MM-DD`) or a relative formula (`SuccessorIncluded + <N>d`, e.g. `SuccessorIncluded + 180d`). `N/A` for `active` or `net-new`. |
| `NewRootJustification` | For `net-new` only: one sentence stating the need. `N/A` for other intents. |
| `Notes` | Backstop dates, migration context, regulatory constraints, dependency on other root programs. `N/A` if none. |

Use `N/A` (not a blank field) for any column that does not apply to a given row.
This confirms the value was intentionally omitted rather than accidentally missed.

## Completeness rules

A return is complete when:

- At least one data row exists.
- Each row has a `RootCACertificateName`, valid `SHA256Fingerprint` (64 hex), non-empty `AppleTrustPurposes` using Appendix A names, and a `LifecycleIntent` from the allowed set.
- `retirement committed` rows state a `RetirementTimeline`.
- `net-new` rows state a `NewRootJustification`.
- Dates are valid `YYYY-MM-DD`; relative formulas match `SuccessorIncluded + <N>d`.
- Non-applicable fields contain `N/A`, not blank.

A `replacement planned` row without a `RetirementTimeline` is a warning (Apple
expects a timeline when a successor is known), not an error.

For relative formulas, Apple strongly encourages a backstop date in Notes (e.g.
"Backstop: 2031-12-31 if successor not included by then").

## Examples

```
RootCACertificateName,SHA256Fingerprint,AppleTrustPurposes,LifecycleIntent,SuccessorSHA256,RetirementTimeline,NewRootJustification,Notes
Example TLS Root CA G2,AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA,Server Authentication,active,N/A,N/A,N/A,Currently serving production TLS issuance
Example TLS Root CA G1,BBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBB,Server Authentication,retirement committed,AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA,2028-06-30,N/A,Successor already included; migrating subscribers
Example S/MIME Root CA G1,CCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCC,Secure Email,replacement planned,N/A,SuccessorIncluded + 180d,N/A,Backstop: 2031-12-31 if successor not included by then
Example TLS Root CA G3,DDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDD,Server Authentication,net-new,N/A,N/A,Dedicated single-purpose Server Authentication root for new issuance platform.,N/A
Example VMC Root CA G1,EEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEE,VMC,retirement committed,AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA,SuccessorIncluded + 365d,N/A,365d allows relying parties to transition to successor-issued VMCs
```

## After submitting

Ensure any retirement commitment is reflected in your published CP or CPS.
Apple may request confirmation of the section reference at a later phase.
