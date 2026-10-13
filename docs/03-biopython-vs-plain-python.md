# 3. Biopython vs. Plain Python

Three different things are often conflated in this comparison:

1. **Python** — a general-purpose programming language with its standard library.
2. **Biopython** — a domain-specific library written in Python for biological computation.[1]
3. **Your own code** — whatever you write yourself, with or without Biopython.

The comparison that matters is between reimplementing the needed functionality yourself in plain Python and delegating it to Biopython's tested, documented components. *(repository assessment)* Bracketed numbers refer to [7. References](07-references.md).

## What plain Python gives you

- **Zero additional dependencies.** Nothing to install, pin, or upgrade.
- **Complete control and transparency.** All behavior in a script is behavior you wrote and can read end to end.
- **No library version to manage.** No deprecation notices, no release-note reading, no compatibility matrix.
- **Genuinely sufficient capability for simple tasks.** Extracting record identifiers from a modest FASTA file, for example, is basic line-by-line string handling.

*(repository assessment, building on the formats and caveats documented in [5])*

## What Biopython adds

- **Parsers for specification-heavy formats.** GenBank flat files, EMBL records, mmCIF structures, and FASTQ quality encodings carry non-trivial structure and edge cases; the library's parsers are maintained as the community formats evolve.[4][5]
- **A consistent object model.** `Seq`, `SeqRecord`, and `SeqFeature` give every part of a workflow the same representation of sequences, annotations, and features — instead of one dictionary shape per script.[4]
- **Predictable conventions.** Biopython does not guess file formats ("we don't try and guess the file format for you!"), which keeps behavior explicit.[5]
- **Interoperation.** Standard objects and NumPy — a required dependency of Biopython itself — let results flow into the wider Python scientific ecosystem.[10][12]
- **Inherited maintenance.** Releases, a regression test suite, release notes, and a documented deprecation process mean format changes and interface evolution are tracked upstream, not by you.[3][8][9]

## What adopting it costs

- **A dependency chain.** Biopython requires Python ≥3.10 and NumPy; some features need optional extras, such as ReportLab for parts of `Bio.Graphics` or database adapters for BioSQL.[10]
- **Version management.** Library APIs evolve — `Bio.pairwise2` was deprecated in release 1.80 in favor of `Bio.Align.PairwiseAligner` — so code needs occasional attention as deprecations accumulate.[5][8]
- **A learning curve.** Using the library well means learning its object model and conventions.
- **Abstraction overhead.** For trivial tasks, configuring the library can be heavier than a short hand-written script. *(repository assessment)*

## The maintenance trade-off

Hand-written code has no upstream: it never breaks because a library upgraded — but it also never improves when a file format changes. Library-based code inherits the project's maintenance — but also its evolution, including deprecations.[5][8] Both directions are real, and neither dominates in every situation. Biopython's own repository is candid that parsers track a moving target: when a data format changes, the parsing code can break — and "the parsing code in Biopython is sometimes updated faster than we can build Biopython releases."[3] *(repository assessment, based on [3][8])*

## A simple decision sketch

| Situation | Plain Python may suffice | Biopython is the stronger fit |
|---|---|---|
| Small scripts, simple formats (e.g., pull IDs from FASTA) | ✅ | overkill |
| Specification-heavy formats (GenBank, EMBL, mmCIF) | risky to hand-roll | ✅ |
| Annotations/features must be preserved | — | ✅ (`SeqRecord`/`SeqFeature`)[4] |
| No dependencies allowed at all | ✅ | not possible |
| Data feeding further Python tooling | — | ✅ (standard objects, NumPy)[10][12] |

Fuller tool-selection guidance, including non-Biopython libraries, is in document 06.

## Bottom line

Biopython is not always the better choice. It earns its place when format complexity, annotation handling, or reuse across projects makes reimplementation expensive. Plain Python remains entirely appropriate — and often preferable — when the task is small, the format is simple, or dependencies must be avoided.

---

**Sources:** [1], [3], [4], [5], [8], [9], [10], [12] — see the annotated register in [7. References](07-references.md).
