# Contributing

Thanks for your interest! This specification is a **work in progress**, and input at
every level is genuinely welcome: typo fixes, wording clarifications, technical
objections, alternative bindings, implementation experience - all of it. Don't hesitate
to open an issue even for a half-formed thought; discussion is the point of publishing
this as a draft.

## Where discussion happens

- **GitHub issues** - questions, comments, proposals, disagreements. No template
  required; just say what you mean.
- **Pull requests** - for concrete text changes, small or large. A PR that sparks a
  discussion and gets reworked is a success, not a failure.

## How to reference the spec

To keep comments unambiguous, please cite:

- **Sections** by their § number, e.g. *§7.1 (the rewrite rule)* or *§11.2 (HTTP status
  mapping)*.
- **Normative requirements** by their N-number, e.g. **N7** (they live in §6, one anchor
  per requirement, so `…/requirements.html#n7` deep-links).
- **Conformance points** by their CP-number, e.g. **CP-14** (§17, anchors `#cp-14` etc.).

## How to cite the spec *inside* the spec

Two rules, both learned the hard way — v0.3 shipped with four references that
pointed at sections which do not exist, and nothing caught them:

- **Cite a subsection as `xref:page.adoc#anchor[§n.n]`**, never as bare prose
  `§n.n`, wherever the target has an anchor. Add one if it does not.
- **Never put a § number in link text that the `xref:` does not resolve to.**
  `xref:annex-b-dutch-gf.adoc[Annex B §B.7]` resolves the *page*, so Antora
  passes it even when §B.7 does not exist. The subsection number in the link
  text buys none of the xref's safety.

**Run `tools/check-refs.sh` before opening a PR.** It resolves every prose
`§n.n` against the headings that actually exist and is the half of the
reference gate Antora does not cover. `tools/traceability.sh` reports the
requirement → conformance-point → track closure; a requirement scored by
neither must be listed in `tools/traceability-exceptions.txt` with a reason.
Both also run in CI on every push and pull request
(`.github/workflows/validate.yml`).

## Bumping the version

Most version literals come from attributes in `antora.yml`
(`spec-version`, `spec-status`, `spec-date`), which `index.adoc` interpolates.
Four sites cannot, and must be bumped by hand together:

| Site | Why it cannot be an attribute |
| --- | --- |
| `antora.yml`'s own `version:` | The Antora component version. It carries the **minor** version only (`0.3`) — a patch release replaces its predecessor in place, so there is no version selector and no stale URLs. Bump it only for a minor release. |
| `package.json`'s `version` | Outside Antora's attribute scope. |
| `README.md` | GitHub Markdown; no attribute expansion. |
| `rest-facade.adoc`'s `"spec_version": "0.3"` | Inside a `[source,json]` block. Substituting there needs `subs="attributes+"`, which makes the example non-copy-pasteable. It is also **deliberately `major.minor`**: the field reports the wire contract a gateway implements, and patch releases do not change it — see §7a.2. Leave it alone for a patch release. |

## What to edit

The **AsciiDoc pages under `modules/ROOT/pages/` are the source of truth.** Edit those.
Please don't edit any exported artifact (HTML, DOCX, PDF renderings that may circulate) —
they are generated from, or superseded by, these pages.

A note on requirement language: the key words MUST / SHOULD / MAY follow RFC 2119, and
where a requirement names an IHE profile, the profile is a **proposed binding** - the
obligation is normative, the named profile is open to review (see *Reader's guide and
terminology*). Challenging a proposed binding is an entirely legitimate contribution.

## Diagrams

Diagrams are authored in **PlantUML**. To change one:

1. Edit the source in `diagrams/*.puml`.
2. Re-render the PNG with PlantUML (not shipped in this repo; download
   `plantuml.jar` from https://plantuml.com/download):

   ```sh
   java -jar plantuml.jar -tpng -o ../modules/ROOT/images diagrams/*.puml
   ```

3. Commit both the `.puml` source and the re-rendered PNG in
   `modules/ROOT/images/` together.

## Licensing of contributions

This specification is dedicated to the public domain under
[CC0 1.0 Universal](LICENSE). By contributing you agree that your contribution is
published under the same terms.
