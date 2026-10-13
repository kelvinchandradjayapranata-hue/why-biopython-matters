# 6. Limitations and Alternatives

## What Biopython is not

*(repository assessment, informed by the verified sources cited throughout)*

- **Not a substitute for domain knowledge.** The library handles data; interpreting it biologically remains the researcher's work.
- **Not a biological quality validator.** Biopython parses structure and content according to format rules — it does not certify that data are correct, complete, or biologically meaningful. The project's own documentation notes that GenBank/EMBL output "does not yet preserve every last bit of annotation," and that "many PDB files contain headers with incomplete or erroneous information."[5]
- **Not an AI system.** See document 05.
- **Not universal.** Each capability has boundaries, dependencies, and caveats — documented below.

Bracketed numbers refer to [7. References](07-references.md).

## Operational limitations (verified)

**Format edges.** Biopython does not guess formats; every `SeqIO` call names its format explicitly.[5] Some formats are read-only in practice (Swiss-Prot output is "not (yet) supported" for writing), some information is not preserved on round-trips, and alignment formats such as PHYLIP and Clustal are not supported by `index()`.[5]

**External software and licensing.** Several capabilities are interfaces rather than implementations: local BLAST, ClustalW, and EMBOSS must be installed separately[4][10]; secondary-structure assignment requires DSSP — which the tutorial notes requires obtaining a license, free for academic use — and residue-depth analysis requires MSMS[5]; BioSQL requires a database system and adapters, and some graphics require ReportLab.[4][10]

**Network dependence.** Entrez and online BLAST require internet access and compliance with the provider's requirements. The tutorial documents a mandatory email parameter, enforced rate limits (three queries per second, ten with an API key, "automatically enforced by Biopython"), and the possibility of blocked access for abusive usage.[5] NCBI's own usage-policy pages could not be directly re-verified during this build (bot protection); see the limitation recorded in [7. References](07-references.md).

**Environment requirements.** Python ≥3.10, NumPy as a required dependency, optional extras per feature, and a C compiler plus Python development headers if building from source.[3][10]

**API evolution.** Biopython deprecates and eventually removes interfaces — `Bio.pairwise2` was deprecated in release 1.80 in favor of `Bio.Align.PairwiseAligner` — so long-lived code needs periodic updates.[5][8][9] The project maintains a dedicated deprecation file precisely because this is expected practice, not an accident.[8] Pin versions; read release notes.[9] *(repository assessment)*

**Parsers track moving targets.** The formats themselves change. Biopython's README notes that when a data format changes, the parsing code can break — and "the parsing code in Biopython is sometimes updated faster than we can build Biopython releases," with the most recent parser obtainable by pulling the relevant files. The README cautions that such development-tree code "is not as well-tested as released code, and may contain new dependencies."[3]

## Scale and memory: what the documentation says

The tutorial documents different data-access patterns with different profiles: `parse()` streams records one at a time; `to_dict()` is described as the most flexible, most memory-demanding option; `index()` records file offsets and parses on demand; `index_db()` stores record information in an on-disk SQLite database rather than in memory.[5] Choosing among them is a data-scale decision.

This repository makes **no comparative performance claims** — no benchmarks were run for it, and none are cited. For context, large-scale genomics conventionally uses toolchains built on compiled libraries: pysam is "a python module for reading, manipulating and writing genomic data sets," wrapping the htslib C-API and providing access to the command-line functionality of samtools and bcftools.[18] That is a statement about ecosystem conventions, not a verdict on Biopython's speed. *(repository assessment)*

## Alternatives (verified self-descriptions)

| Tool | Scope (per its official documentation) |
|---|---|
| **pysam** | reads/writes genomic data sets via the htslib C-API; access to samtools/bcftools functionality[18] |
| **Biotite** | "bundles popular tasks in computational molecular biology into a uniform and fast Python library" — sequences, structures handled "in an intuitive NumPy-like way," database access, external-software interfaces[19] |
| **scikit-bio** | "a community-driven Python library for bioinformatics" — sequences, phylogenetic trees, community diversity metrics, ordination, multivariate statistics[20] |

These tools have different scope and design goals from Biopython and from one another; no drop-in replacement exists between them, and mixing tools in one workflow is normal. *(repository assessment)*

## Decision table

| If your task is… | A reasonable starting point is… | Because |
|---|---|---|
| Parsing sequence files/annotations (FASTA, GenBank, EMBL) | Biopython `SeqIO`[4][5] | Format coverage plus the records model |
| Extracting simple fields from a simple FASTA | plain Python may suffice | Little format semantics involved (document 03) |
| Aligned-read processing, variant calling, large BAM/CRAM-scale work | pysam-class htslib tooling[18] | Compiled library aimed at genomic files |
| Microbiome/ecology diversity statistics | scikit-bio[20] | Domain-specific metrics |
| NumPy-centric work, including structures | consider Biotite[19] | "NumPy-like" design |
| Mixed pipeline (retrieval → parse → ML) | a combination — Biopython upstream, a framework downstream (document 05)[15] | Tools compose |

## Closing

Biopython is appropriate when a workflow involves biological sequence or structure data in supported formats, standard annotations, or database retrieval — and when the trade-offs in document 03 are acceptable. It is the wrong tool when the task is model training, high-throughput genomic file processing, or anything outside its documented scope. The honest summary is the one this repository opened with: use depends on the research question, the data, the workflow, and the alternatives.

---

**Sources:** [3], [4], [5], [8], [9], [10], [15], [18], [19], [20] — see the annotated register in [7. References](07-references.md).
