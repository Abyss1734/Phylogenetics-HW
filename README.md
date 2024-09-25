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

# 2. Use the multiple alignment you constructed and estimate how old Mitochondrial Eve is. How old is the most recent ancestor of all non-Africans?

We will determine the approximate age of Eve using the script Eve_age.ipynb (located in the Code folder), which calculates the number of mutations between haplogroup L1c1d and the other haplogroups, selects the highest value from the results, and multiplies it by the average rate of mitochondrial mutations.
Determining the average rate of mitochondrial mutations is not easy, even with sources—the data varies depending on the method and source—ranging from 1,000 to 15,000 years per mutation. Moreover, the method for calculating Eve's age should be more complex than just multiplying two numbers—mutations in mitochondria occur at different rates depending on the location in the genome (coding/non-coding regions, etc.). However, I decided not to complicate it and took the average from all sources — 3,000 years per mutation. The obtained data is close to reality:

3. Add five Neanderthal samples and three Denisovan samples to the set of Homo sapiens samples and construct the resulting evolutionary tree. What is the age of the most recent Neanderthal-modern human ancestor?

By adding new fasta files to the Human folder, we will repeat all the actions from point 1 and obtain the following tree:

From the tree, it can be seen that the most recent Neanderthal in the dataset is KX198087.1 (GoyetQ305-4 Neanderthal).
Repeating the actions from point 2, but with the script Neanderthal_age.ipynb (located in the Code folder) for KX198087.1, we obtain the following data, which is also close to reality:

4. Place the particular human sample on the obtained tree.

Taking mitochondrial genome data from a random person from GeneBank, we will repeat the actions from point 1 and obtain the following tree:

From it, it is clear that the person belongs to the same haplogroup as...
