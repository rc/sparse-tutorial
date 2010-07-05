Introduction
============

(dense) matrix is:
* mathematical object
* data structure for storing a 2D array of values

important features:
* memory allocated once for all items
  * usually a contiguous chunk, think NumPy ndarray
* *fast* access to individual items (*)

Sparse Matrices vs. Sparse Matrix Storage Schemes
-------------------------------------------------

* sparse matrix is a matrix, which is *almost empty*
* storing all the zeros is wasteful $\rightarrow$ store only nonzero items
* pros: huge memory savings
* cons: depends on actual storage scheme, (*) usually does not hold

Typical Applications
--------------------

* solution of partial differential equations (PDEs)
  * the *finite element method*
  * mechanical engineering, electrotechnics, physics, ...
* graph theory
  * nonzero at $(i, j)$ means that node $i$ is connected to node $j$
* ...
