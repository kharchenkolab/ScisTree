# ScisTree
Cell tree inference and genotype calling from noisy single cell data. 

ScisTree is a computer program for inferring cell tree and calling genotypes from uncertain single cell genotype data. If you use ScisTree, please cite: 

Accurate and Efficient Cell Tree Inference and Genotype Calling from Noisy Single Cell Data: the Maximum Likelihood Perfect Phylogeny Approach, Yufeng Wu, manuscript, 2018.

The key feature of ScisTree is that it works with uncertain genotypes with individualized probability. That is, you can specify for each genotype (at a row/cell or column/site) different probabilities of being a particular genotype state. ScisTree allows both binary or ternary genotypes. Here is an example for binary genotypes. Note: don't include blank rows in the input genotype file.

# This is an example for binary genotypes.
HAPLOID 5 4

0.8 0.02 0.8 0.8

0.02 0.02 0.02 0.8

0.8 0.02 0.02 0.8

0.02 0.8 0.8 0.8

0.8 0.02 0.8 0.02

The first line specifies the type of genotypes (HAPLOID or TERNARY), number of sites and number of cells. Lines started with # are ignored by ScisTree. You should have one line for each site. For each line, specify the probability of being genotype 0 (for binary genotypes) or being 0 and 1 (consecutively for ternary genotypes) for each cells. For example, in the above example, the first 0.8 on the first row means this genotype is equal to 0 with probability 0.8. Here is an example for ternary genotypes.

# This is an example for ternary genotypes.
TERNARY 5 4

0.8 0.05 0.02 0.1 0.8 0.05 0.8 0.01

0.02 0.1 0.02 0.15 0.02 0.05 0.8 0.1

0.8 0.1 0.02 0.1 0.02 0.15 0.8 0.1

0.02 0.1 0.8 0.05 0.8 0.15 0.8 0.1

0.8 0.1 0.02 0.1 0.8 0.15 0.02 0.1

Here, the first 0.8 and 0.05 on the first row mean the genotype of the first cell has probability 0.8 of being 0, and probability 0.05 of being 1 (and thus probability of 0.15 being genotype 2).

Once you have the executable for ScisTree, simple type to run:

./scistree example.dat

This would infer a cell tree based on maximum likelihood. If you want to impute the genotypes, type:

./scistree -v example.dat

Refer to the user manual for more details on how to use ScisTree.
