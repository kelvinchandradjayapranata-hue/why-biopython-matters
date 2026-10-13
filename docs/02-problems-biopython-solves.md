# 2. Problems Biopython Solves

This document catalogs what Biopython provides for common bioinformatics tasks. Every capability is classified as one of:

- **(i) Implemented in Biopython** — provided by the library's own code.
- **(ii) Requires external software** — Biopython provides an interface, but the actual program (or a licensed resource) must be obtained separately.
- **(iii) Requires a network service** — the capability depends on communication with a remote server.

This classification is this repository's organizing framework *(repository assessment)*; the underlying capabilities are documented in the cited sources. Bracketed numbers refer to [7. References](07-references.md).

## Representing sequences and annotations — (i)

`Seq` is Biopython's core sequence representation — string-like, with biological additions. `SeqRecord` adds identifiers, descriptions, annotations, and a list of `SeqFeature` objects describing sub-features with their locations.[4] The practical point *(repository assessment)*: downstream code operates on a domain-true object instead of ad-hoc strings and dictionaries, at the cost of learning the object model.

## Reading and writing biological file formats — (i)

`Bio.SeqIO` is the standard sequence input/output interface.[5][11] Per the current tutorial:

- `parse()` — "the workhorse function" — reads sequence data as `SeqRecord` objects and returns an iterator.[5]
- `read()` — returns a single record; raises if the file does not contain exactly one.[5]
- `write()` — writes records and returns how many were written.[5]
- `to_dict()` — holds records in memory; described as the most flexible but most memory-demanding option.[5]
- `index()` — records where each record sits in a file and parses on demand; takes a filename, not a handle.[5]
- `index_db()` — stores record information in an on-disk SQLite database rather than in memory.[5]
- `convert()` — performs format-to-format conversion directly.[5]

Formats named in the current tutorial include FASTA, FASTQ, GenBank (`gb`/`gp`), EMBL, Swiss-Prot (which `SeqIO.write()` "does not (yet) support" for output), twoBit, and tab; alignment formats such as PHYLIP and Clustal can be handled as sequences but are not supported by `index()`.[5] The broader catalog covers many more formats, and the project's wiki lists more than thirty with read/write notes — while explicitly stating that the authoritative list lives in the code docstrings.[11]

Documented caveats matter as much as coverage: Biopython does not guess formats ("we don't try and guess the file format for you!"); GenBank/EMBL output "does not yet preserve every last bit of annotation"; FASTQ can be read and converted to FASTA but not written from FASTA, because quality data cannot be invented; and writing certain formats requires information other formats do not carry.[5]

## Aligning sequences — (i)

Pairwise and multiple sequence alignment are handled under `Bio.Align`, which gained its pairwise aligner in release 1.72 as an alternative to the older `Bio.pairwise2` module.[9] `pairwise2` "was deprecated in Release 1.80," and the tutorial's pairwise2 chapter directs new code to `Bio.Align.PairwiseAligner`; the module remains documented and usable, and no removal release has been announced.[5][8] `Bio.AlignIO` reads and writes alignment files, including files containing multiple alignments.[4][6]

## Searching sequence databases — (ii) and (iii)

Biopython can call NCBI's **online** BLAST server (iii) or a **locally installed** standalone BLAST (ii), and it includes a parser for BLAST XML output (i).[4] The current tutorial includes chapters on BLAST and other sequence search tools.[5] The library also wraps external command-line programs — ClustalW and EMBOSS among them — which must be installed separately (ii).[4][10]

## Retrieving records from biological databases — (iii)

`Bio.Entrez` provides programmatic access to NCBI's resources through the Entrez Programming Utilities (E-utilities): `einfo`, `esearch`, `epost`, `esummary`, `efetch`, `elink`, `egquery`, and `espell`.[5] Because it communicates with NCBI servers, it is a network capability (iii), and the tutorial documents the interface requirements: the email parameter "has been mandatory since June 1, 2010"; usage is limited to three queries per second (ten with an API key), "automatically enforced by Biopython"; readers are pointed to NCBI's Entrez User Requirements; and the chapter warns that abusive usage can result in blocked access.[5] Biopython also interfaces with ExPASy/Swiss-Prot and KEGG (iii).[4][5]

> NCBI's own usage-policy pages could not be directly re-verified during this build (bot protection); the requirements above are cited to Biopython's own documentation. See the limitation recorded in [7. References](07-references.md).

## Working with 3D structures — (i), with external add-ons (ii)

`Bio.PDB` "focuses on working with crystal structures of biological macromolecules": `PDBParser` produces `Structure` objects organized as Structure → Model → Chain → Residue → Atom, and `MMCIFParser`/`MMCIF2Dict` handle mmCIF/PDBx files — "the standard PDB archive format" since 2014. BinaryCIF, MMTF, PQR, and PDBML inputs are also documented, as is 3D-printing-oriented output.[5] Some analyses need external programs: secondary-structure assignment requires installing DSSP (with a license — free for academic use), and residue-depth analysis requires MSMS (ii).[5] Parsing caveats are documented too: "Sometimes a PDB file cannot be unambiguously interpreted."[5]

## Phylogenetics, motifs, population genetics, and other modules — mixed

- `Bio.Phylo` — phylogenetic trees, including a PAML interface for external analyses (ii).[4][5][6]
- `Bio.motifs` — sequence motif work (i).[5][6]
- `Bio.Cluster` — clustering (i).[5][6]
- `Bio.PopGen` — population-genetics workflows, wrapping tools such as GENEPOP and SIMCOAL2 (ii).[4][6]
- BioSQL — storing annotated sequences in SQL databases; requires a database system and adapters (ii).[4][10]
- GenomeDiagram — graphical output; `Bio.Graphics` uses ReportLab (ii).[5][10]

## Summary table

| Task | Where | Class | Notes |
|---|---|---|---|
| Sequence representation and annotation | `Seq`, `SeqRecord`, `SeqFeature` | (i) | Core object model[4] |
| Sequence file I/O | `Bio.SeqIO` | (i) | Many formats; per-format caveats[5][11] |
| Alignment files | `Bio.AlignIO` | (i) | Multiple alignments per file supported[4] |
| Pairwise alignment | `Bio.Align` (`PairwiseAligner`) | (i) | `pairwise2` deprecated in 1.80[5][8] |
| BLAST search | online server / local install | (iii) / (ii) | XML output parser included (i)[4][10] |
| Database retrieval | `Bio.Entrez` | (iii) | Email and rate requirements documented[5] |
| Structure parsing | `Bio.PDB` | (i) | DSSP/MSMS external for some analyses[5] |
| Phylogenetics | `Bio.Phylo` (+ PAML) | (i) / (ii) | [4][5][6] |
| External tool wrappers | ClustalW, EMBOSS | (ii) | Must be installed separately[4][10] |
| Sequence storage | BioSQL | (ii) | Needs a database system[4][10] |

## What this list is not

Not every feature suits every problem: suitability depends on the data type, scale, and workflow, and several specialized tasks are better served by other tools (documents 05 and 06). This inventory describes what the library provides — not a claim that it should be the default everywhere.

---

**Sources:** [4], [5], [6], [8], [9], [10], [11] — see the annotated register in [7. References](07-references.md).
