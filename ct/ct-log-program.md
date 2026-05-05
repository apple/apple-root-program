# Apple's Certificate Transparency Log Program

The goal of Apple's Certificate Transparency log program is to establish a set
of Certificate Transparency (CT) logs that are trusted on Apple's platforms to
provide Signed Certificate Timestamps (SCTs) for publicly trusted TLS server
authentication certificates.

## Program Policies and Requirements

### RFC 6962

To be considered for inclusion in Apple's Certificate Transparency log program,
a log conforming with RFC 6962 must:

- Implement CT as specified by RFC 6962.
- Not present two or more conflicting views of the Merkle Tree at different
  times and/or to different parties.
- Meet Apple's uptime requirement of 99%, as measured by Apple.
- Not specify a Maximum Merge Delay (MMD) which exceeds 24 hours.
- Incorporate a certificate that it created an SCT for within the MMD.
- Trust all root CA certificates included in Apple's trust store.

Logs may trust roots not included in Apple's trust store.

A log conforming with RFC 6962 may:

- Reject expired certificates.
- Reject revoked certificates.
- Reject leaf certificates which don't contain the id-kp-serverAuth Extended
  Key Usage (EKU).

Log operators must provide a minimum of 45 days' advance written notice to
<certificate-transparency-program@group.apple.com> of any changes to the
type(s) of leaf certificate(s) their log(s) accepts.

### Static CT API

To be considered for inclusion in Apple's Certificate Transparency log program,
a log conforming with the
[static-ct-api](https://c2sp.org/static-ct-api) C2SP specification must:

- Implement CT as specified by The Static Certificate Transparency API, v1.0.0.
- Not present two or more conflicting views of the Merkle Tree at different
  times and/or to different parties.
- Meet Apple's uptime requirement of 99%, as measured by Apple.
- Not specify a Maximum Merge Delay (MMD) which exceeds 1 minute.
- Incorporate a certificate that it created an SCT for within the MMD.
- Trust all root CA certificates included in Apple's trust store.

Logs may trust roots not included in Apple's trust store.

A log conforming with the static-ct-api C2SP specification may:

- Reject expired certificates.
- Reject revoked certificates.
- Reject leaf certificates which don't contain the id-kp-serverAuth Extended
  Key Usage (EKU).

Log operators must provide a minimum of 45 days' advance written notice to
<certificate-transparency-program@group.apple.com> of any changes to the
type(s) of leaf certificate(s) their log(s) accepts.

## States of Logs on Apple's Platforms

Logs that are included on Apple's platforms can be in one of the following
states:

### Pending

The log has requested inclusion in Apple's trusted log list, but hasn't been
accepted yet. A pending log doesn't count as "currently qualified" or "once
qualified."

### Qualified

The log has been accepted in Apple's program and set for distribution to
Apple's platforms. A qualified log counts as "currently qualified."

### Usable

SCTs from the log can be relied on to meet Apple's client CT policy. A usable
log counts as "currently qualified." Logs transition from qualified to usable
after a minimum of 74 days in the qualified state.

### Readonly

The log is trusted on Apple's platforms but is readonly, meaning the log has
stopped accepting certificate submissions. A readonly log counts as "currently
qualified."

### Retired

The log was trusted on Apple's platforms until the specific retirement
timestamp. A retired log counts as "once qualified" if the SCT in question was
issued before the retirement timestamp. A retired log doesn't count as
"currently qualified."

### Rejected

The log is not and will not be trusted on Apple's platforms. A rejected log
doesn't count as "currently qualified" or "once qualified."

## Inclusion Process

After a log is accepted into Apple's Certificate Transparency log program, a
monitoring period checks the log for compliance with Apple's policy. During
this time, the log state is "pending."

Apple can reject any log at its discretion. If this happens, the log state
becomes "rejected." If Apple finds no issues during the monitoring period, the
log can be accepted, at which time the log state becomes "qualified."

Apple monitors the log on an ongoing basis for compliance with log program
policies. A log's state during this time can be "qualified," "usable,"
"readonly," or "retired."

A log can be retired at any time, at Apple's discretion or as a result of
failure to comply with log program policies. The log's state then becomes
"retired."

## Apply for Inclusion

To apply for inclusion in Apple's CT log program, email
<certificate-transparency-program@group.apple.com> and include the following:

- The log's description, including:
  - the policy for accepting certificates, if any;
  - the policy for rejecting certificates for logging, if any;
  - a list of accepted root certificates by Subject DN and SHA-256 fingerprint;
    and
  - the specification (RFC 6962 or static-ct-api) with which the log conforms.
- The publicly accessible CT log server URL (HTTP).
- The log's public key (DER encoding of the SubjectPublicKeyInfo ASN.1
  structure).
- The log's MMD.
- The log's temporally sharded certificate expiry range including:
  - the `end_exclusive` value in ISO 8601 Date and Time in UTC format; and
  - the `start_inclusive` value in ISO 8601 Date and Time in UTC format.
- Contact information, including email addresses for two operator operations
  contacts and two operator representative contacts.
