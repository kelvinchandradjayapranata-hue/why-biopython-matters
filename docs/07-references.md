# 7. References

This is the annotated source register for the whole repository. Every bracketed number used in the documents resolves to an entry below. All sources were inspected directly during preparation of this repository on **2026-10-13** unless a status explicitly says otherwise. Version statements reflect the state of the sources on that date.

## How to cite Biopython

The project's documentation instructs users: "If you use Biopython in a scientific publication, please cite the application note" — Cock et al. 2009 ([4] below) — and/or one of the module-specific publications the project lists for individual components ([2]). Full reference:

> Cock P.J.A., Antao T., Chang J.T., Chapman B.A., Cox C.J., Dalke A., Friedberg I., Hamelryck T., Kauff F., Wilczyński B., de Hoon M.J.L. **Biopython: freely available Python tools for computational molecular biology and bioinformatics.** *Bioinformatics* 25(11):1422–1423, 2009. DOI: 10.1093/bioinformatics/btp163.

## A. Primary Biopython sources

### [1] Biopython — project website
- URL: https://biopython.org/
- Type: Official project website. Accessed: 2026-10-13. Status: ✅ Directly inspected.
- Supports: definition of Biopython ("a set of freely available tools for biological computation written in Python by an international team of developers"; tagline "Python Tools for Computational Molecular Biology"); Open Bioinformatics Foundation membership; current release **1.88, released 6 August 2026**; license description ("extremely liberal and compatible with almost every license in the world"); links to tutorial, API docs, wiki, cookbook.

### [2] Biopython Documentation (project wiki)
- URL: https://biopython.org/wiki/Documentation
- Type: Official documentation index. Accessed: 2026-10-13. Status: ✅ Directly inspected.
- Supports: the Tutorial and Cookbook "contain the bulk of Biopython's documentation"; citation instruction quoted above; existence of module-specific publications for components including Bio.PDB, Bio.Cluster, GenomeDiagram, the FASTQ format, and Bio.Phylo/PAML (titles/authors not recorded here — not verified); deprecation-policy documentation exists.

### [3] Biopython source repository — README
- URL: https://github.com/biopython/biopython
- Type: Official repository. Accessed: 2026-10-13. Status: ✅ Directly inspected.
- Supports: "Official git repository for Biopython"; supported/tested Python versions (3.10–3.14 and a 3.15 release candidate at the time of the README; PyPy3.10 v7.3.17 or later; recommends Python 3.13); NumPy as a required dependency installed automatically via pip; beta/unreleased-code caveats; the README's candid note that when a data format changes the parsing code can break, and that "the parsing code in Biopython is sometimes updated faster than we can build Biopython releases" (the most recent parser is obtainable by pulling the relevant files); repository activity signals as of the access date (stars, commits, open issues — time-sensitive, not used as quality claims).

### [4] Cock et al. 2009 — Biopython application note
- URL (inspected copy): https://pmc.ncbi.nlm.nih.gov/articles/PMC2682512/
- Cock P.J.A., Antao T., Chang J.T., Chapman B.A., Cox C.J., Dalke A., Friedberg I., Hamelryck T., Kauff F., Wilczyński B., de Hoon M.J.L. "Biopython: freely available Python tools for computational molecular biology and bioinformatics." *Bioinformatics* 25(11):1422–1423, 2009. DOI: 10.1093/bioinformatics/btp163 · PMID: 19304878 · PMCID: PMC2682512.
- Accessed: 2026-10-13. Status: ✅ Directly inspected (full text via PMC).
- Supports: project inception (1999); design rationale for `Seq`, `SeqRecord`, and `SeqFeature`; SeqIO/AlignIO scope; BLAST interface (NCBI online server **or** local standalone installation) and XML output parsing; wrappers for ClustalW and EMBOSS; database modules (NCBI Entrez, ExPASy, InterPro, KEGG, SCOP); `Bio.PDB`; phylogenetic tools ("supports phylogenetic tools using the NEXUS interface (Maddison et al., 1997) or the Newick standard tree format"); a population-genetics module (wrappers for GENEPOP; coalescent simulation via SIMCOAL2; Fst-outlier selection detection; the module name `Bio.PopGen` is per [6], not used in the paper); the paper's own scope caveat ("The features described herein are only a subset"). Historical note: module statements reflect 2009 and are used mainly for architecture and provenance.

### [5] Biopython Tutorial and Cookbook (current, version 1.88)
- URL: https://biopython.org/docs/latest/Tutorial/index.html
- Chapters inspected directly: Sequence Input/Output (`chapter_seqio.html`); Pairwise alignments using pairwise2 (`chapter_pairwise2.html`); Accessing NCBI's Entrez databases (`chapter_entrez.html`); Going 3D: The PDB module (`chapter_pdb.html`); Phylogenetics with Bio.Phylo (`chapter_phylo.html`).
- Accessed: 2026-10-13. Status: ✅ Directly inspected (five chapters; the tutorial index's table of contents is also used for chapter-existence claims).
- Supports: `SeqIO` function semantics (`parse`, `read`, `write`, `to_dict`, `index`, `index_db`, `convert`); explicit-format requirement ("we don't try and guess the file format for you!"); format names and caveats (FASTA, FASTQ, GenBank `gb`/`gp`, EMBL, Swiss-Prot read-only for writing, twoBit, tab; alignment formats not indexable; GenBank/EMBL output "does not yet preserve every last bit of annotation"); `pairwise2` deprecation banner ("Please note that Bio.pairwise2 was deprecated in Release 1.80") and the pointer to `Bio.Align.PairwiseAligner`; Entrez E-utilities function list and interface requirements (mandatory email since June 1, 2010; 3 queries/second, 10 with API key, enforced by Biopython; NCBI usage guidance); `Bio.PDB` parsing (`PDBParser`, `MMCIFParser`, `MMCIF2Dict`), Structure/Model/Chain/Residue/Atom architecture, supported structure formats (PDB, mmCIF/PDBx — "the standard PDB archive format" since 2014 — BinaryCIF, MMTF, PQR, PDBML), parsing caveats ("Sometimes a PDB file cannot be unambiguously interpreted"; "many PDB files contain headers with incomplete or erroneous information"), and external dependencies for some analyses (DSSP with its license note; MSMS); the `Bio.Phylo.PAML` interface (PAML, "a suite of programs for phylogenetic analysis by maximum likelihood"; codeml, baseml, and yn00 "are implemented").

### [6] Biopython API documentation (version 1.88)
- URLs: https://biopython.org/docs/latest/api/index.html; https://biopython.org/docs/latest/api/Bio.html; https://biopython.org/docs/latest/api/Bio.pairwise2.html
- Accessed: 2026-10-13. Status: ✅ Directly inspected. Caveat: the `Bio` package listing was truncated at its tail during inspection; the subpackage/submodule inventory recorded here covers the visible portion.
- Supports: current module inventory (subpackages/submodules such as `Bio.Align`, `Bio.SeqIO`, `Bio.Entrez`, `Bio.PDB`, `Bio.Phylo`, `Bio.PopGen`, `Bio.motifs`, `Bio.pairwise2`); warning classes (including `BiopythonDeprecationWarning`); note that `Bio.pairwise2`'s API page carries no deprecation notice even though the tutorial and release notes record the deprecation (see [5], [8]).

### [7] Biopython LICENSE.rst (repository default branch)
- URL: https://raw.githubusercontent.com/biopython/biopython/master/LICENSE.rst
- Accessed: 2026-10-13. Status: ✅ Directly inspected. Caveat: read from the repository's default (development) branch; applies to Biopython itself, **not** to this repository, whose own licensing is stated in its [LICENSE](../LICENSE).
- Supports: Biopython is "currently released under the 'Biopython License Agreement'"; some files are "explicitly dual licensed under your choice" of the Biopython License Agreement or the BSD 3-Clause License, "with the intention of later offering all of Biopython under this dual licensing approach"; permission grant ("with or without modifications and for any purpose and without fee"); disclaimer of warranties; contributor-name restriction. The BSD 3-Clause section carries a "Copyright (c) 1999-2025, The Biopython Contributors" line.

### [8] Biopython DEPRECATED.rst (repository default branch)
- URL: https://raw.githubusercontent.com/biopython/biopython/master/DEPRECATED.rst
- Accessed: 2026-10-13. Status: ✅ Directly inspected. Caveat: development-branch file; it may document changes beyond the released 1.88 version, and is used here only for the statements below.
- Supports: this file "provides documentation for modules in Biopython that have been moved or deprecated in favor of other modules"; "The Bio.pairwise2 module was deprecated in Release 1.80" (no removal release specified); examples of the project's deprecation/removal practice (e.g., `Bio.SubsMat` deprecated 1.78, removed 1.80; `Bio.Align.Generic` deprecated in Release 1.57, removed in Release 1.69).

### [9] Biopython NEWS.rst (repository default branch)
- URL: https://raw.githubusercontent.com/biopython/biopython/master/NEWS.rst
- Accessed: 2026-10-13. Status: ⚠️ Directly inspected with caveat: the fetched excerpt was truncated; only the visible portion is recorded here.
- Supports: release dates (release 1.86 dated 28 October 2025); "A new pairwise sequence aligner is available in Bio.Align" in release 1.72 (21 June 2018) "as an alternative to the existing pairwise sequence aligner in Bio.pairwise2"; historical `pairwise2` maintenance notes.

### [10] PyPI — biopython 1.88
- URL: https://pypi.org/project/biopython/
- Accessed: 2026-10-13. Status: ✅ Directly inspected.
- Supports: latest version 1.88 released Aug 6, 2026; requires Python ≥3.10; SPDX license expression `LicenseRef-Biopython-License-Agreement`; NumPy required and auto-installed; optional dependencies (ReportLab for `Bio.Graphics`; matplotlib for `Bio.Phylo` plotting; networkx plus pygraphviz or pydot; rdflib; PostgreSQL/MySQL adapters for BioSQL); external tools referenced as potentially useful (standalone NCBI BLAST, EMBOSS, ClustalW); C compiler and Python development headers needed to build from source.

### [11] Bio.SeqIO wiki page
- URL: https://biopython.org/wiki/SeqIO
- Accessed: 2026-10-13. Status: ⚠️ Inspected with caveat: the page itself states the authoritative format list lives in the code docstrings, and it may lag behind releases. Used in this repository only for interface conventions corroborated elsewhere ([5]) and for the qualitative statement that the format catalog is large and asymmetric per format.

## B. Related tools and context

### [12] NumPy — website
- URL: https://numpy.org/
- Accessed: 2026-10-13. Status: ✅ Directly inspected.
- Supports: "The fundamental package for scientific computing with Python"; N-dimensional arrays; numerical computing tools; ecosystem statements ("NumPy lies at the core of a rich ecosystem of data science libraries"; "forms the basis of powerful machine learning libraries like scikit-learn and SciPy"). Version at access: 2.5.0 (2026-06-21).

### [13] pandas — landing page
- URL: https://pandas.pydata.org/
- Accessed: 2026-10-13. Status: ✅ Directly inspected.
- Supports: pandas is "a fast, powerful, flexible and easy to use open source data analysis and manipulation tool, built on top of the Python programming language." Version at access: 3.0.6 (Sep 17, 2026).

### [14] pandas — About page
- URL: https://pandas.pydata.org/about/
- Accessed: 2026-10-13. Status: ✅ Directly inspected.
- Supports: "pandas aims to be the fundamental high-level building block for doing practical, real world data analysis in Python"; "A fast and efficient **DataFrame** object for data manipulation with integrated indexing". Note: the page does not mention `Series`; this repository makes no claim about it.

### [15] PyTorch — website
- URL: https://pytorch.org/
- Accessed: 2026-10-13. Status: ✅ Directly inspected.
- Supports: framework self-description and feature areas: "Production Ready" (TorchScript, TorchServe), "Distributed Training" (`torch.distributed`), "Robust Ecosystem" (computer vision, NLP), "Cloud Support"; latest stable requires Python 3.10 or later (stable version 2.7.0 at access). Used only to establish PyTorch as a machine-learning/deep-learning framework distinct from Biopython.

### [16] AlphaFold Protein Structure Database — EMBL-EBI & Google DeepMind
- URL: https://alphafold.ebi.ac.uk/
- Accessed: 2026-10-13. Status: ✅ Directly inspected. Caveat: the page states prediction counts inconsistently ("over 260 million" in one section, "over 200 million" elsewhere); this repository therefore cites no count.
- Supports: AlphaFold is "an AI system developed by Google DeepMind that predicts a protein's 3D structure from its amino acid sequence"; it "regularly achieves accuracy competitive with experiment"; CASP14 ranking; the page's own note that "the system still has some limitations"; the database is developed by Google DeepMind and EMBL-EBI; data availability under CC-BY-4.0.

### [17] Jumper et al. 2021 — AlphaFold publication
- Jumper J., Evans R., Pritzel A., Green T., Figurnov M., Ronneberger O., Tunyasuvunakool K., … Silver D., Vinyals O., Senior A.W., Kavukcuoglu K., Kohli P., Hassabis D. "Highly accurate protein structure prediction with AlphaFold." *Nature* 596(7873):583–589, 2021. DOI: 10.1038/s41586-021-03819-2 · PMID: 34265844 · PMCID: PMC8371605.
- Metadata verified 2026-10-13 via the Europe PMC REST API (`https://www.ebi.ac.uk/europepmc/webservices/rest/search?query=DOI:"10.1038/s41586-021-03819-2"&format=json`), which returned the record above. Status: ✅ Metadata verified (full-text not inspected). Author list shown as first seven and last six entries; the full co-author list is longer.

### [18] pysam — documentation
- URL: https://pysam.readthedocs.io/en/latest/
- Accessed: 2026-10-13. Status: ✅ Directly inspected.
- Supports: "Pysam is a python module for reading, manipulating and writing genomic data sets"; "a wrapper of the htslib C-API"; SAM/BAM/VCF/BCF/BED/GFF/GTF/FASTA/FASTQ support; "access to the command line functionality of the samtools and bcftools packages"; compression and indexed random access; bundled htslib/samtools/bcftools versions (1.24 at access).

### [19] Biotite — documentation site
- URL: https://www.biotite-python.org/
- Accessed: 2026-10-13. Status: ✅ Directly inspected.
- Supports: Biotite "bundles popular tasks in computational molecular biology into a uniform and fast Python library"; sequence data (including 3D structural alphabets), structure handling "in an intuitive NumPy-like way" (PDB, CIF/BinaryCIF, MOL/SDF, trajectories), database access (NCBI Entrez, UniProt, PDB, PubChem), external-software interfaces. Project-listed publications (metadata as listed by the site, not independently verified beyond the listing): Kunzmann & Hamacher, *BMC Bioinformatics* 19:346 (2018), DOI 10.1186/s12859-018-2367-z; Kunzmann et al., *BMC Bioinformatics* 24 (2023), DOI 10.1186/s12859-023-05345-6.

### [20] scikit-bio — website
- URL: https://scikit.bio/
- Accessed: 2026-10-13. Status: ✅ Directly inspected.
- Supports: "A community-driven Python library for bioinformatics"; feature areas (biological sequences, phylogenetic trees, community diversity metrics such as UniFrac and PD, ordination, multivariate statistics, compositional data); 3-Clause BSD license.

### [21] NCBI Bookshelf — E-utilities documentation page
- URL: https://www.ncbi.nlm.nih.gov/books/NBK25497/
- Attempted: 2026-10-13. Status: ❌ **Not verified** — the fetch was blocked by a bot-protection interstitial, and retry attempts (including during the final audit) were blocked in the same way; the page content could not be inspected. Consequence: this repository describes Entrez's interface requirements using Biopython's own documentation ([5]) rather than citing NCBI policy directly.

## C. Term-usage survey: "AI4Bio" — recorded limitation

No authoritative formal definition of "AI4Bio" was located during this project's source verification. Search-level findings (2026-10-13) suggested the term is used informally with varying scope, but the directly attempted full-text sources (an ACM-BCB invitation letter PDF and an ai4b.io symposium program PDF) could not be retrieved in readable form, and neither could be verified. **No citable usage source is included.** Accordingly, document 05 defines "AI4Bio" as this repository's own definitional choice rather than citing an external standard.

## D. Verification methods and limitations

- All sources were fetched and inspected on 2026-10-13. Web pages were processed via automated fetch-and-summarize; quoted fragments and figures used in the documents were checked against the fetched content at writing time. A full re-verification of live URLs and quoted text was completed on 2026-10-13 during the final quality audit, with further source checks performed for the subsequent corrections review; the results reflect the sources as of that date — external pages can change over time, and one source could not be accessed (see [21]).
- Version-sensitive facts (release numbers, dates, Python requirements, dependency lists) are pinned to the access date and should be re-checked against the sources before being relied upon later.
- Distinction of claims: statements in the documents marked as "repository assessment" or "repository interpretation" are this project's own analysis, not sourced facts. All other substantive technical claims cite a verified source from this register.
