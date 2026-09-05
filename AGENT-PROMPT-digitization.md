# Agent brief: UNTDED 2005 digitalization (YAML SSOT, TypeScript/Ruby only)

You are a fresh agent. Read `/Users/mulgogi/src/isoiecjtc5/CLAUDE.md` first for
repo context. Do not touch anything outside the paths named below.

## Mission

Digitalize the UNTDED (United Nations Trade Data Elements Directory, 2005
edition) from a scanned PDF into a machine-readable, validated dataset whose
**first target consumer is UNECE / UN/CEFACT** — the goal is a machine-readable
UNTDED that UN/CEFACT could adopt (and that ISO/TC 154 can table into
JTC 5 DPP semantic work as the data-element base).

## Inputs (read-only, never delete or modify)

- `/Users/mulgogi/src/isoiecjtc5/untded/UNTDED2005_Redacted.pdf` — working copy, 132 pages, **scanned, no text layer**
- `/Users/mulgogi/src/isoiecjtc5/untded/UNTDED2005.pdf` — full original (21 MB; cross-check pages that are blank/redacted in the working copy)
- OCR tools available: `tesseract` (CLI). Vision-model assist is possible via
  this environment's Read-tool→CDN→`mcp__4_5v_mcp__analyze_image` flow for
  hard pages. **NO Python anywhere in the pipeline** (do not use or extend
  `tools/convert-to-md.py` for this task).

## Hard constraints

1. **YAML is the single source of truth (SSOT).** Every data element lives in
   YAML. All other formats (CSV, JSON, JSON Schema, HTML index) are derived,
   generated outputs — never hand-edited.
2. **Implementation languages: TypeScript or Ruby. No Python.**
3. **Ruby option:** model classes with `lutaml-model` only — declare typed
   attributes + mappings; (de)serialization exclusively through the
   framework. NEVER hand-roll `to_h`/`from_h`/`to_json`/`from_json`.
   **TypeScript option:** types + runtime validation (zod) with JSON Schema
   generation.
4. Tests use real instances/files — no mocks, no doubles.RSpec or vitest.
5. Reversibility: nothing destructive; all output goes under
   `/Users/mulgogi/src/isoiecjtc5/untded-digital/`.

## Data model to develop

Design a typed model for a trade data element directory. Fields (adjust after
inspecting real pages; document decisions):

- `tag` — 4-digit UNTDED element number (e.g. `1001`)
- `name_en` / `name_fr` (UNTDED is bilingual)
- `description`
- `representation` — class (an..35 / n2 / a3 …), format, length constraints
- `status` (e.g. deprecated/active in 2005 edition)
- `code_list` — reference + codes when the element has an enumerated code list
- `edifact` — linkage to UN/EDIFACT data element / composite references
- `notes`
- `provenance` — `{ pdf: UNTDED2005_Redacted.pdf, page: <int>, ocr_confidence: high|medium|low }`

Partition YAML by document structure (per UNTDED part/chapter), e.g.
`data/elements/1000-1099.yaml`. Low-confidence entries go to a review queue
(`review-queue.yaml`) — never silently guessed.

## Deliverables

```
untded-digital/
├── README.md            # method, coverage map (pages → files), known gaps
├── model/               # data model (Ruby lutaml-model classes or TS + zod)
├── data/                # YAML SSOT (the elements)
├── bin or script/       # `validate` (load all YAML through the model),
│                       # `export` (regenerate derived CSV/JSON/HTML)
├── test or spec/        # RSpec/vitest, real data files
└── derived/             # generated outputs (regenerable)
```

## Method (sample-first)

1. Render 2–3 representative pages (dense table page, code-list page, header
   page) at high DPI; run tesseract; eyeball accuracy; decide per-page OCR
   strategy (tesseract-first + vision-model verification for problem pages).
2. Build the data model against those real samples; wire validate/export.
3. Scale through all 132 pages; track coverage in README; flag every
   uncertain cell into the review queue with provenance.
4. Final check: `validate` passes; export regenerates byte-identical; README
   states coverage percentage and every known gap.

## Success criteria

- 100 % of pages processed (each element captured or explicitly queued for
  review with page provenance).
- `validate` green; no YAML bypasses the model; derived outputs regenerable.
- A UN/CEFACT-minded reader can consume the dataset without reading the PDF.
