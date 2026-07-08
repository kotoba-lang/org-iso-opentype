# kotoba-lang/org-iso-opentype

Zero-dep portable `.cljc` implementation of TrueType/OpenType (SFNT) —
ISO/IEC 14496-22 Open Font Format. Named `org-iso-opentype` (ISO/IEC-numbered
spec, consistent with `org-iso-jpeg`/`org-iso-isobmff`/`org-iso-pdf` in the
same batch).

Extracted from `kotoba-lang/kasane` (kasane.ttf, ADR-2606272100). Offset-based
hand parser over the table directory + head/maxp/name tables. R0 extracts the
table set, head metrics (units-per-em, the fixed magicNumber for validation),
glyph count, and family name — CFF/glyf outline parsing is a follow-up.
Consumed by `org-w3-woff`, which reassembles a WOFF-wrapped SFNT and
delegates here for the same metadata.

## Usage

```clojure
(require '[opentype.core :as opentype])

(opentype/parse sfnt-bytes)
;; => {:sfnt-version :num-tables :tables :magic :magic-ok?
;;     :units-per-em :num-glyphs :family}
```

## Test

```sh
clojure -M:test
```
