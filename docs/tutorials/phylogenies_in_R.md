# Phylogenies in R

Chances are that at some point you'll need to manipulate phylogenies, for which R can be a convenient go-to language. 

## Phylogenies as objects of class 'phylo'

Popular packages such as ape() store trees as a 'phylo'-class. This class is a list that holds the necessay information of a phylogeny in different components: 

- edge a two-column matrix where each row represents a branch (or edge) of the tree. The nodes and tips are represented by integers; the n tips are numbered from 1 to n, and the m (internal) nodes from n+1 to n+m (the root being n + 1). For each row, the first column gives the ancestor.
- edge.length (optional) a numeric vector giving the lengths of the branches given by edge.
- tip.label a vector of mode character giving the labels of the tips; the order of these labels corresponds to the integers 1 to n in edge.
- Nnode an integer value giving the number of nodes in the tree (m). 
- node.label (optional) a vector of mode character giving the labels of the nodes (ordered in the same way than tip.label).
- root.edge (optional) a numeric value giving the length of the branch at the
root if it exists.


## Phylogenies with metadata

> to add: ggtree() //  treeio().

link to <https://yulab-smu.top/treedata-book/index.html>

