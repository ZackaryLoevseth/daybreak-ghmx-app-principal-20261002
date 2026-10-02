# Restricted GitHub App fixture

Disposable researcher-owned fixture for testing one GitHub App installation with
repository permissions limited to `Metadata: read` and `Contents: write`.

The protected workflow never checks out or executes mutable repository content.
Its only protected effect is an HMAC of one fixed marker using a synthetic
environment secret, written as a commit-status description.

Routes:

- `ghmx-app-direct-allowed`: same-App direct positive control while the policy
  allows `repository_dispatch`.
- `ghmx-app-direct-denied`: same-App direct negative after the policy is changed
  to allow only `workflow_dispatch`.
- `ghmx-app-relay`: same App reaches the protected reusable workflow through an
  untargeted relay while the restrictive policy remains unchanged.

