# UN/EDIFACT D.01B UNCL (code lists)

Full-text UN Codes Library for directory release D.01B, mirrored from the
BSD-3-Clause conversion at fretlink/edi-parser
(`specification/references/D01B/simples/`). The underlying data is the
official UNECE publication.

## Why D.01B

The edition's own resource list (Foreword) names UN/EDIFACT D.02A. The
official UNCL zips (service.unece.org) are CDN-blocked for automation
and unarchived. Content-based discovery (2026-09-07) found no D.02A or
D.05B full-text mirror with the section-4.1.5 cross-references intact;
D.01B is the nearest complete release available under a clear license.
The join labels the vintage everywhere.

## What this carries that the D05B codes.xml does not

The short-names-only D05B mirror (`edifact-D05B/codes.xml`) is coverage
(which elements are coded, with how many values). These files carry the
full descriptions, including the section-4.1.5 cross-references:

- `[nnnn]` at the start of a qualifier code's description — the code's
  combined meaning equals TDED element nnnn (rule 1.3);
- `(nnnn)` — a related-TDED reference (rule 1.4 and narrative).

Verified: 3035 BB reproduces the publication's own rule-1.3 example
verbatim (`[3420] Bank employed by the buyer to make payment`).

## Attribution

UN/EDIFACT directories © UNECE. Conversion © fretlink/edi-parser contributors
(BSD-3-Clause). Mirrored here for standards-maintenance purposes on
behalf of UN/CEFACT and ISO/TC 154, consistent with the D05B mirror.
