# UNTDED references — source corpus and provenance

Source documents and extracted provenance material for the UNTDED 2005
digitalization ([`untded/untded-2005`](https://github.com/untded/untded-2005)),
operated on behalf of **UN/CEFACT (UNECE)** and **ISO/TC 154**.

## Mandate

Per **ISO/TC 154 N1727** (resolutions of the 45th plenary, DIN Berlin,
2026-08-31/09-04): Resolution **P-2026-07** (JWG 9) encourages
*"exploring the use of an open-source platform to support the
maintenance and publication of ISO 7372"* — ISO 7372 being the
TDED/UNTDED standard. **P-2026-06** targets publication before October
2028; **P-2026-01** (JWG 1) addresses the stalled UN/EDIFACT Directory
publication with the UNECE Secretariat.

## Contents

| Path | What it is |
|---|---|
| `UNTDED2005.pdf` | Full original scan, 132 pp (damaged xref — render with `mutool`, not `pdftoppm`) |
| `ECE_TRADE_432E_CF-Rec1.pdf` | UNECE Recommendation No. 1 — United Nations Layout Key for Trade Documents (ECE/TRADE/432), the master form the directory's UNLK bridges reference |
| `ISO-3535-1977-preview.pdf` | Preview of ISO 3535:1977 — Forms design sheet and layout chart (referenced by the publication's references) |
| ~~`UNTDED2005_Redacted.pdf`~~ | The private working copy used for extraction — not distributed; the text layer it carried is fully covered by the original PDF above |
| `front-matter/` | 300 dpi renders + tesseract OCR of pp. 1–4, 9–19 (from the original) |
| `section-4.1-presentation.txt` | Text layer of section 4.1 — the printed change-tag legend |
| `edifact-D05B/` | Mirror of the UN/EDIFACT D.05B directory metadata used for cross-checking + the cross-check report: `segments.xml` (EDED-by-segment) and `codes.xml` (UNCL code values, short names — fetched 2026-09-07) |
| `AGENT-PROMPT-digitization.md` | The original digitization brief (provenance) |

## Attribution

The PDFs are the UN publication **ECE/TRADE/362** (also ISO 7372:2005),
© United Nations / UNECE, redistributed here with attribution for
standards-maintenance purposes on behalf of UN/CEFACT and ISO/TC 154.
The D.05B corpus mirrors the official UNECE publication via the
php-edifact/edifact-data mirror.
