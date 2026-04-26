# IAAA

* Identity - unique acc(email id etc) that represents a person.

* Authentication - prove that identity(passwords, OTP).

* Authorisation - what the identity can do.

* Accountability - recording or logging who did what, when and where

The level starts from identity and continues till last A. Any level cannot be skipped.

## Broken Access Control

When server cannot properly enforce "Who can access what". Like IDOR, if changing and id `?id=7 → ?id=6` lets u see other users contents, then access control is broken. This shows horizontal privelge excalation and vertical privelege escalation.

## Authentication failure



    username enumeration
    weak/guessable passwords (no lockout/rate limits)
    logic flaws in the login/registration flow
    insecure session or cookie handling

these are the reasons attacker can login to ur account or bind it.

## logging failures

good logging can underpin accountability, failures like missing authentication events.

# Application Design Flaws

