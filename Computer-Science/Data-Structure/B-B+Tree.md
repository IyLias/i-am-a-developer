## What is B Tree? 

It is a generalized version of Binary Search Tree, allowing nodes with more than two children. The B-Tree is well suited for storage systems that read and write relatively large blocks of data such as databases and file systems.






<br><br>

## What is B+ Tree?

B+ Tree is a self-balancing tree data structure that keeps data sorted and allows searches, sequential access, insertions, and deletions always in O(log n).

B+ Tree is an  M-Way search tree with the following properties. 

- It is perfectly balanced. (every leaf node is at the same depth in the tree)

- Every node other than the root is at least half-full M/2-1 <= # Keys <= M-1 

- Every inner node with k Keys has k+1 non-null children. 

It's also a generalized version of Binary Search Tree, allowing nodes with more than two children. 
The B+ Tree is well suited for storage systems that read and write relatively large blocks of data such as databases and file systems. 


<br> 

### B+ Tree : Node

Every B+ Tree Node is comprised of an array of key/value pairs. 

-> The Keys are derived from the attribute that the index is based on.

-> The Values will differ based on whether the node is classified as an Inner Node or a Leaf Node. 

Leaf Node Values can be divided in two ways.

* Record ID

  A pointer to the location of the tuple to which the index entry corresponds.

* Tuple Data
  
  Leaf Node stores the actual contents of the tuple. 


<br>

### B+ Tree : Insert 

First, find correct Leaf Node L. And then Insert data entry into L in sorted order. 

If L has enough space, it's done. 

Otherwise, split L Keys into L and a new node L2. 




<br>

### B+ Tree : Delete 

Start at root, find Leaf Node L where entry belongs. 

Remove the entry. 

If L is at least half-full, it's done. 

If L has only M/2-1 entries, 

Try to re-distribute,borrowing from sibling. 
If re-distribution fails, merge L and sibling. 




<br>

### B+ Tree : Selection 




<br> 

### B+ Tree : Duplicate Keys

There are two approaches. 

1. Append Record ID. 

  It adds the tuple's unique Record ID( = own address) as part of the key to ensure that all keys are unique. 

2. Overflow Leaf Nodes

  It allows Leaf Nodes to spill into overflow Nodes that contain the duplicate Keys.





<br><br>

## What's the difference between B Tree and B+ Tree? 

<ins> Every Node in B Tree can store its values but in B+ Tree, only Leaf Nodes store values. </ins> This means that Inner Nodes in B+ Tree store more Keys so that depth of the tree is not deeper. So B+ Tree is optimized for systems that read and write large blocks of data. Since data is stored in disk in database, it needs to access the disk as few times as possible. (access to disk is super slow..)


Also there are Pointers in Leaf Nodes in B+ Tree, called Sibling Pointers, which connect Leaf Nodes each other and help sequential access efficiently.  



