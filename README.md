# How humans populated the Earth 
# 1. Construct an evolutionary tree based on human mtDNA data
I combined all the fasta files into one using the command:
```
cat *.fasta > combined_sequences.fasta
```
Next, I annotated it using MAFFT:
```
mafft combined_sequences.fasta > aligned_sequences.fasta
```
I built the tree using FastTree:
```
FastTree -gtr -nt -boot 1000 aligned_sequences.fasta > tree_with_bootstrap.nwk
```
Since things didn't work out with R, I visualized the tree in Python using Biopython and Matplotlib in the script tree_with_bootstrap_mtdna_draw.ipynb (located in the Code folder, along with all further, practically identical scripts for tree visualization).
The resulting tree:

From the tree, it's clear that the longest branch is FJ713601.1, a human code from haplogroup L1c1d, Central African.
We conclude that Eve originated from Africa (Yes, this is a discovery!)
