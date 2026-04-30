# Apple's Certificate Transparency Policy

**Version 1.0**

**Published: April 21, 2025**

Publicly trusted Transport Layer Security (TLS) server authentication certificates must meet
Apple's Certificate Transparency (CT) policy to be evaluated as trusted on Apple platforms.

Certificates that fail to comply with our policy will result in a failed TLS connection, which
can break an app's connection to Internet services or Safari's ability to seamlessly connect.

## Policy Requirements

Apple's policy requires at least two Signed Certificate Timestamps (SCT) issued from a CT log
-- once-approved[^1] or currently approved[^1] at the time of check -- and either:

- At least two SCTs from currently approved CT logs with one SCT presented via TLS extension
  or OCSP Stapling; or
- At least one embedded SCT from a currently approved log and at least the number of SCTs from
  once or currently approved logs, based on validity period as detailed in the table below.

At least one SCT must be issued from a log compliant with RFC 6962.

**The number of embedded SCTs required is based on certificate lifetime[^2]:**

| Certificate Lifetime | # of SCTs from Distinct Logs | Maximum # of SCTs per Log Operator Counting Toward SCT Requirement |
| :------------------- | :--------------------------- | :----------------------------------------------------------------- |
| 180 days or less     | 2                            | 1                                                                  |
| 181 to 398 days      | 3                            | 2                                                                  |

## CT Logs

Download the current [CT Log list](https://valid.apple.com/ct/log-list/current_log_list.json)
and [CT Log list schema](https://valid.apple.com/ct/log-list/log_list_schema.json) in JSON format.

For CT log status definitions, please refer to
[Apple's Certificate Transparency log program](https://support.apple.com/103703).

---

[^1]: A certificate's validity period (or lifetime) is defined in line with RFC 5280, Section
4.1.2.5, as "the period of time from notBefore through notAfter, inclusive."

[^2]: Validity period is measured with a day being equal to 86,400 seconds. Any time greater
than this indicates an additional day of validity.
