Dictionary of Keys Format (DOK)
===============================

* subclass of Python dict

  * keys are `(row, column)` index tuples (no duplicate entries allowed)
  * values are corresponding non-zero values

* efficient for constructing sparse matrices incrementally
* constructor accepts:

  * dense matrix (array)
  * sparse matrix
  * shape tuple (create empty matrix)

* efficient O(1) access to individual elements
* flexible slicing, changing sparsity structure is efficient, can resize
* can be efficiently converted to a coo_matrix once constructed
* slow arithmetics (`for` loops with `dict.iteritems()`)
* use:

  * when sparsity pattern is not known apriori or changes

* examples::
