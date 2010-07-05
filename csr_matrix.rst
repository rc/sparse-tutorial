Compressed Sparse Row Format (CSR)
==================================

* row oriented

  * three NumPy arrays: `indices`, `indptr`, `data`

    * `indices` is array of column indices
    * `data` is array of corresponding nonzero values
    * `indptr` points to row starts in `indices` and `data`
    * length is `n_row + 1`, last item = number of values = length of both
      `indices` and `data`
    * nonzero values of the `i`-th row are `data[indptr[i]:indptr[i+1]]`
      with column indices `indices[indptr[i]:indptr[i+1]]`
    * item `(i, j)` can be accessed as `data[indptr[i]+k]`, where `k` is
      position of `j` in `indices[indptr[i]:indptr[i+1]]`

  * subclass of :class:`_cs_matrix` (common CSR/CSC functionality)

    * subclass of :class:`_data_matrix` (sparse matrix classes with
      `.data` attribute)

* fast matrix vector products and other arithmetics (sparsetools)
* constructor accepts:

  * dense matrix (array)
  * sparse matrix
  * shape tuple (create empty matrix)
  * `(data, ij)` tuple
  * `(data, indices, indptr)` tuple

* efficient row slicing, row-oriented operations
* slow column slicing, expensive changes to the sparsity structure
* use:

  * actual computations (most linear solvers support this format)

* examples::
