# 1. What Is Biopython?

Biopython is a set of freely available Python tools for biological computation, developed since 1999 by an international team of volunteer contributors and maintained as a member project of the Open Bioinformatics Foundation.[1][3][4] The project describes itself as "a set of freely available tools for biological computation written in Python by an international team of developers," with the tagline "Python Tools for Computational Molecular Biology."[1]

> Bracketed numbers refer to the annotated source register in [7. References](07-references.md). Statements labeled **repository assessment** are this project's interpretation, not sourced facts.

## A library, not a language

Biopython is a library for the Python programming language. It is distributed as the `biopython` package (import name `Bio`) and installed with `pip`; NumPy is a required dependency and is installed automatically with it.[3][10] The current release is **1.88 (6 August 2026)**. It requires Python ≥3.10, and the project documents testing across Python 3.10 through 3.14 plus a 3.15 release candidate, as well as PyPy3.10; the README recommends Python 3.13.[1][3][10]

The distinction matters: Python provides the language, ecosystem, and general-purpose tooling; Biopython provides biology-aware data structures, parsers, and interfaces on top of it. It does not replace Python any more than a library replaces the language it is written in. *(repository assessment)*

## Provenance and project model

The project began in 1999 and published its application note in *Bioinformatics* in 2009.[4] Development is volunteer-run across an international contributor base, with releases, a regression test suite, release notes, and a documented deprecation process.[1][3][8][9] Recent releases — 1.86 in October 2025 and 1.88 in August 2026 — indicate continuing maintenance.[1][9]

## What it provides: a map, not a manual

- **Biological data types** — `Seq` (string-like sequences with biological operations), `SeqRecord` (sequences with identifiers, descriptions, annotations, and features), and `SeqFeature` objects describing sub-features and their locations.[4][6]
- **File format input/output** — `Bio.SeqIO` for sequence files and `Bio.AlignIO` for alignment files, across a large format catalog with per-format caveats.[4][5]
- **Sequence analysis** — pairwise and multiple alignment tooling under `Bio.Align` (see document 02 for the `pairwise2` deprecation note).[5][6]
- **Database retrieval** — modules for NCBI Entrez, ExPASy, KEGG, and other resources.[4][5]
- **Sequence search** — interfaces to BLAST, either through NCBI's online server or a local standalone installation, including parsing of XML output.[4]
- **Structural bioinformatics** — `Bio.PDB` for parsing and working with macromolecular structures (PDB, mmCIF and related formats).[4][5]
- **Phylogenetics and more** — `Bio.Phylo`, motifs, clustering, population genetics, phenotype data, graphical output (GenomeDiagram), and the shared BioSQL schema.[4][5][6]

Document 02 examines each of these with a consistent classification: implemented in Biopython, requiring external software, or requiring a network service.

## Position in the ecosystem

Biopython is one of several Python libraries for biological work, not the only option: Biotite, scikit-bio, and pysam each target overlapping but differently shaped problems — from structure and sequence handling to microbiome statistics to large-scale genomic files.[18][19][20] Document 06 compares them and offers decision guidance.

## Licensing — of Biopython, not of this repository

Biopython is released under the **"Biopython License Agreement."** Some files are "explicitly dual licensed under your choice" of the Biopython License Agreement or the BSD 3-Clause License, "with the intention of later offering all of Biopython under this dual licensing approach." The agreement grants "permission to use, copy, modify, and distribute this software and its documentation … for any purpose and without fee," with a warranty disclaimer and a restriction on using contributor names for endorsement.[7] PyPI lists the SPDX identifier `LicenseRef-Biopython-License-Agreement`.[10] The project's own site calls the license "extremely liberal and compatible with almost every license in the world."[1]

These terms apply to **Biopython itself**. This repository does not inherit Biopython's license; its own licensing terms are stated in the repository's [LICENSE](../LICENSE) and in the README's "License and attribution" section.

## Using and citing it

Biopython is designed both for software development and for "everyday scripts for common bioinformatics tasks."[4] If you use it in scientific work, the project asks that you cite the 2009 application note and/or one of the module-specific publications the project lists; the full citation is in [7. References](07-references.md).[2][10]

---

**Sources:** [1], [2], [3], [4], [5], [6], [7], [9], [10], [18], [19], [20] — see the annotated register in [7. References](07-references.md).
