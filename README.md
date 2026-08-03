# KYE Protocol™ — JSON Schemas

The patent-safe **schema surface** of KYE Protocol™: the published JSON Schema
(2020-12) definitions for every artefact the protocol exposes externally —
entities, delegations, decisions, evidence packs, replay proofs, attestations,
and the payments overlay under [`payments/`](payments/).

This repository is a **mirror**. It is generated from the `public/schemas` tree
of the KYE Protocol master repository and re-synced on change; edits made here
are overwritten. Report problems via
[Discussions](https://github.com/KYE-Protocol/Discussions).

## Canonical URIs

Each schema's `$id` is its canonical, resolvable URI on `kyeprotocol.com` —
not a path in this repository:

```
https://kyeprotocol.com/schemas/proof-bundle.json
```

Reference schemas by `$id`. This mirror exists so the same bytes are clonable,
diffable and archivable without depending on the website being up; the `$id`
remains the identity.

## What is here — and what is deliberately not

These schemas define **shape**: field names, types, formats, required-ness,
identifier patterns, and enumerated vocabulary. That is the interoperability
contract, and it is fully public.

They do **not** define **mechanism**. The algorithms behind the fields — how a
score is computed, how a bundle is canonicalised before hashing, how entries
are linked, how thresholds map to outcomes — are not published here or
anywhere else in the open. A schema tells you that a decision carries a signed
evidence reference; it does not tell you how that evidence is constructed.
This split is deliberate and permanent, not an omission to be filled in later.

## Verifying

Any JSON Schema 2020-12 validator works. With
[ajv](https://ajv.js.org/):

```bash
git clone https://github.com/KYE-Protocol/schemas
cd schemas
npx ajv-cli validate --spec=draft2020 -s proof-bundle.json -d your-payload.json
```

Illustrative payloads for these schemas are published separately at
[KYE-Protocol/examples](https://github.com/KYE-Protocol/examples). The
identifier grammar used throughout
(`kye:<class>:<trust-domain>:<subclass>:<local>`) is at
[KYE-Protocol/id-format](https://github.com/KYE-Protocol/id-format), and the
controlled vocabulary at
[KYE-Protocol/vocabulary](https://github.com/KYE-Protocol/vocabulary).

## Licence

Apache-2.0 — see [LICENSE](LICENSE). KYE™, KYE Protocol™ and the KYE product
names are trademarks of KYE Protocol; the licence covers the schema files, not
the marks.
