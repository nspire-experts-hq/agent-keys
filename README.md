# agent-keys

**Public key sets for NSPIRE platform agent credentials. Everything in this repository is public by
design and none of it is a secret.**

| File | What it is |
|---|---|
| `jwks.json` | the JSON Web Key Set used to verify agent service tokens |

A JWKS holds **public** keys. It is published so that the service verifying a token can fetch the key
that checks its signature — which is the normal way this is done, and the reason this repository is
public rather than private. The corresponding **private** signing keys are not here, are not in any
repository, and never will be.

## If a key here changes

Replacing a key is a **rotation**. During one, this file holds **two** keys at once: tokens signed
with the old key keep verifying while new tokens are signed with the new one, and the old key is
removed only after the last token signed with it has expired. That overlap is what makes a rotation
not an outage.

## This repository holds nothing else

No credentials, no configuration, no application code. One file, one job.
