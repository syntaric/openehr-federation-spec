# Proposal for Federation Tier with AQL

A specification for a **Federation Tier** in openEHR querying: it lets a client run an
AQL query across **multiple distributed CDRs** as though they were a single repository.
The federation is keyed on each node's **local `ehr_id`** - patient identity is resolved
*outside* AQL (proposed binding: IHE PIXm/XCPD/mCSD, with the Dutch Generic Functions as
a regional alternative), and each node then receives **standard, non-federated AQL**
scoped to its resolved `ehr_id`. The gateway is a transparent façade: a client never
needs federation-specific syntax to run a basic patient query.

> **Status: working draft, v0.2.** This is very much a work in progress, circulated by
> the openEHR Federation Working Group for comment. Feedback of every kind is welcome —
> from typo fixes to fundamental disagreement with the model. See
> [CONTRIBUTING.md](CONTRIBUTING.md).

## Rendered site

The spec is published with [Antora](https://antora.org/) via GitHub Pages:

**https://syntaric.github.io/openehr-federation-spec/**

## Building locally

Requires Node.js (18+).

```sh
npm install
npm run build
```

Then open `build/site/index.html` in a browser.

## Repository layout

```
antora.yml                    Antora component descriptor (component: federation-aql, v0.2)
antora-playbook.yml           Antora playbook (local build and CI use the same one)
modules/ROOT/pages/           The specification, one AsciiDoc page per section - this is
                              the source of truth; edit these
modules/ROOT/images/          Rendered diagrams (PNG)
modules/ROOT/nav.adoc         Site navigation
diagrams/                     PlantUML sources for the diagrams
.github/workflows/publish.yml Builds the site and deploys it to GitHub Pages on push to main
```

## Provenance

This revision supersedes *Proposal for Federation Tier with AQL* (openEHR Federation
Working Group, 2025-08-20). What changed, and why, is catalogued in
[Changes from the 2025-08-20 proposal](modules/ROOT/pages/changes-from-2025-08-20.adoc).

## Contributing

Contributions are welcome - issues, pull requests, and discussion alike. Please read
[CONTRIBUTING.md](CONTRIBUTING.md) for how to reference the spec (§ numbers, N#
requirements, CP# conformance points) and how diagram changes work.

## License

[Creative Commons Zero v1.0 Universal (CC0)](LICENSE) - public domain dedication.
