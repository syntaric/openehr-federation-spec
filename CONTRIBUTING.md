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
