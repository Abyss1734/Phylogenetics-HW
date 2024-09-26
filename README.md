# How humans populated the Earth 
## 1. Construct an evolutionary tree based on human mtDNA data
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

![Описание изображения](Images/tree_with_bootstrap.png)

From the tree, it's clear that the longest branch is FJ713601.1, a human code from haplogroup L1c1d, Central African (to decrypt the codes, see the appendix).
We conclude that Eve originated from Africa (Yes, this is a discovery!).

## 2. Use the multiple alignment you constructed and estimate how old Mitochondrial Eve is. How old is the most recent ancestor of all non-Africans?

We will determine the approximate age of Eve using the script Eve_age.ipynb (located in the Code folder), which calculates the number of mutations between haplogroup L1c1d and the other haplogroups, selects the highest value from the results, and multiplies it by the average rate of mitochondrial mutations (and divides it into two).
Determining the average rate of mitochondrial mutations is not easy, even with sources — the data varies depending on the method and source — ranging from 1,000 to 15,000 years per mutation. Moreover, the method for calculating Eve's age should be more complex than just multiplying two numbers — mutations in mitochondria occur at different rates depending on the location in the genome (coding/non-coding regions, etc.). However, I decided not to complicate it and took the average from all sources — 4,000 years per mutation. The obtained data is close to reality:

| Metric                              | Value          |
|-------------------------------------|----------------|
| Maximum number of mutations          | 96             |
| Estimated age of Mitochondrial Eve  | 192,000 years  |


## 3. Add five Neanderthal samples and three Denisovan samples to the set of Homo sapiens samples and construct the resulting evolutionary tree. What is the age of the most recent Neanderthal-modern human ancestor?

By adding new fasta files to the Human folder, we will repeat all the actions from point 1 and obtain the following tree:

![Описание изображения](Images/3.png)

From the tree, it can be seen that the most recent Neanderthal in the dataset is KX198087.1 (GoyetQ305-4 Neanderthal).
Repeating the actions from point 2, but with the script Neanderthal_age.ipynb (located in the Code folder) for KX198087.1, we obtain the following data, which is also close to reality:

| Metric                              | Value          |
|-------------------------------------|----------------|
| Maximum number of mutations          | 213            |
| Estimated age of the most recent Neanderthal | 426,000 years  |

## 4. Place the particular human sample on the obtained tree.

Taking mitochondrial genome data from a random person from GeneBank (HM156694.1), we will repeat the actions from point 1 and obtain the following tree:

![Описание изображения](Images/4.png)

![Описание изображения](Images/2.png)

From it, it is clear that the person belongs to the same haplogroup as KY686209.1 (M60), KP172432.1 (D1) and JN084079.1 (D4e1a1). Presumably, this person belongs to the D-haplogroup.

## Human Population Expansion

Based on the phylogenetic analyses and genetic data, it is evident that human populations have undergone significant migrations and expansions over the millennia. The age estimates of Mitochondrial Eve, ranging from 100,000 to 200,000 years, suggest that our common maternal ancestor lived during a period when modern humans were beginning to migrate out of Africa.

Fossil evidence, such as the Omo remains in Kenya, supports the timeline of early human existence in Africa. As humans spread out, they encountered and interacted with other hominin species like Neanderthals and Denisovans. Genetic data indicate that interbreeding events occurred, contributing to the genetic diversity seen in modern non-African populations today.

Geographically, early humans likely followed water sources and utilized land bridges, such as those that existed during glacial periods, to migrate to new territories. The evidence of distinct haplogroups and genetic markers in various regions illustrates the complex pathways of human migration, influenced by environmental factors, resource availability, and social interactions.

In summary, the journey of humans populating the Earth is marked by a series of migrations, interactions with other species, and adaptations to diverse environments, which have shaped our genetic legacy and cultural diversity.

## Appendix

| Sequence ID  | Haplogroup | Population        |
|--------------|------------|-------------------|
| JQ247408.1   | A2f1a      | Native American   |
| KX459697.1   | A4-A200G   | Chinese           |
| KP172434.1   | B2         | Argentinian       |
| JF499899.1   | B4d1       | Chinese           |
| KP017255.1   | C1d3       | Uruguayan         |
| JF811749.1   | C4a1       | Turkish           |
| KP172432.1   | D1         | Argentinian       |
| JN084079.1   | D4e1a1     | Chinese           |
| HQ259121.1   | F1a3       | Filipino          |
| KU521454.1   | F3b1       | Taiwanese         |
| KY934476.1   | H1h1       | Finnish           |
| KY077676.1   | H7j1       | Ashkenazi         |
| KP340170.1   | HV4a1      | Iranian           |
| KY348642.1   | I1a1a3     | Scottish          |
| GU590993.1   | I3         | Irish             |
| KY369152.2   | I4a        | Irish             |
| HQ914447.1   | J1b        | Armenian          |
| KX440262.1   | J2a2d1     | Tunisian          |
| KX440275.1   | J2b1       | Russian           |
| KT698008.1   | K1a4a1     | Serbian           |
| HQ189135.1   | K2a3       | Dutch             |
| FJ713601.1   | L1c1d      | Central African   |
| KR135883.1   | L2a1a      | Mozambican        |
| KR135861.1   | L2e1       | Sudanese          |
| KT819263.1   | L3e5a1     | Morocco           |
| KM986608.1   | L4b2a1     | Yemeni            |
| KM986625.1   | M23        | Yemeni            |
| KY686209.1   | M60        | Indonesian        |
| KM986616.1   | N1a1a3     | Yemeni            |
| JN084084.1   | N9a10      | Chinese           |
| KY303770.1   | R2c        | Saudi Arabian     |
| KY686210.1   | R6         | Thai              |
| JF837819.1   | T1a1       | Finnish           |
| KX440315.1   | T2a1a      | Turkish           |
| JN419195.1   | T2b16      | French            |
| KT698006.1   | U2e2a4     | Serbian           |
| HM804485.1   | U6a7a1     | English           |
| KY496869.1   | V          | Finnish           |
| JF343123.1   | V3b1       | English           |
| KU508374.1   | W1c        | Swedish           |
| KY934478.1   | W6         | Bulgarian         |
| HM453712.1   | X2B        | American          |
| HM448049.1   | X2d        | Polish            |
| KU521494.1   | Y2a1       | Indonesian        |
| KU521491.1   | Y2a1       | Malaysian         |
