# Computational-Genomics-Sequence-Alignment

A hands-on computational biology (dry lab) notebook exploring core **Biopython** workflows — sequence handling, alignment, translation, BLAST searching, and phylogenetics — applied to real public bioinformatics datasets.

## Overview

This project walks through the foundational toolkit a bioinformatician uses when working with DNA/protein sequence data in Python, using **Biopython** as the primary library. Rather than synthetic examples, each concept is demonstrated on real GenBank/FASTA records, a Pfam seed alignment, the SARS-CoV-2 reference genome, and an antimicrobial-resistance genomics dataset.

## Contents

1. **Sequence fundamentals** — `Seq` and `SeqRecord` objects, nucleotide/amino acid alphabets, reverse complements, transcription
2. **Sequence annotation** — `SeqFeature` objects, feature locations, extracting sub-sequences, reading/writing FASTA vs. GenBank formats
3. **Reading real sequence files** — parsing single and multi-record FASTA files, and detailed GenBank records (annotations, features, gene/CDS qualifiers)
4. **Translation** — codon tables, DNA/RNA → protein translation, identifying ORFs/protein chains from a full genome
5. **Pairwise alignment** — global and local alignment of DNA and protein sequences, including BLOSUM62-scored protein alignment
6. **Multiple sequence alignment & phylogenetics** — building an MSA, computing a distance matrix, constructing Neighbor-Joining and Parsimony trees, and visualizing/manipulating phylogenetic trees (Newick, PhyloXML)
7. **BLAST** — querying NCBI BLASTN/BLASTP programmatically and parsing results to identify unknown sequences
8. **Applied genomics example** — aligning antimicrobial-resistance-associated genomic unitigs (*Neisseria gonorrhoeae*) to a query sequence

## Datasets used

| Dataset | Description |
|---|---|
| `NC_005816` | *Yersinia pestis* biovar Microtus str. 91001 plasmid pPCP1 (GenBank + FASTA) |
| `MN908947` | SARS-CoV-2 reference genome (FASTA) |
| `PF05371_seed` | Pfam seed alignment (Clustal format) of phage coat protein homologs |
| *N. gonorrhoeae* unitig set | Genomic unitigs labeled for azithromycin (`azm_sr`) and cefixime (`cfx_sr`) resistance |

## Key results

- Parsed the *Y. pestis* plasmid GenBank record (9,609 bp; 13 annotations; 41 features; 10 genes/10 CDS) and confirmed programmatically that stored CDS translations matched independently computed translations.
- Translated the SARS-CoV-2 genome and identified the longest resulting protein chain (2,701 aa).
- Ran global and local pairwise alignments (including BLOSUM62-scored protein alignment) and compared scoring schemes.
- Built a 7-sequence, 52-column multiple sequence alignment of phage coat proteins and constructed both Neighbor-Joining and Parsimony phylogenetic trees from it.
- Queried NCBI BLASTN with the *Y. pestis* plasmid sequence, returning matching plasmid records at E-value = 0.0.
- Queried NCBI BLASTP with the translated SARS-CoV-2 protein chain against the PDB database, correctly identifying it as the viral RNA-directed RNA polymerase (nsp12).
- Ranked antimicrobial-resistance-associated unitigs by alignment score against a query sequence.

## Tools / Libraries

- [Biopython](https://biopython.org) — `Bio.Seq`, `Bio.SeqRecord`, `Bio.SeqIO`, `Bio.SeqFeature`, `Bio.pairwise2`, `Bio.Align`, `Bio.AlignIO`, `Bio.Blast`, `Bio.Phylo`
- `pandas`, `numpy`
- `matplotlib`, `seaborn`
- `panel`, `bokeh` (interactive alignment visualization)

## Notebook

The full walkthrough with code and outputs is in [`biopython-bioinformatics-basics.ipynb`](./biopython-bioinformatics-basics.ipynb).

## Skills demonstrated

Sequence I/O and parsing (FASTA/GenBank), sequence feature annotation, transcription/translation, pairwise and multiple sequence alignment, substitution matrix (BLOSUM62) scoring, phylogenetic tree construction (NJ, Parsimony) and visualization, BLAST querying and result parsing, applied genomic sequence analysis.
