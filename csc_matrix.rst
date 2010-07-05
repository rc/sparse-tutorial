Compressed Sparse Column Format (CSC)
=====================================

* column oriented

  * three NumPy arrays: `indices`, `indptr`, `data`

    * `indices` is array of row indices
    * `data` is array of corresponding nonzero values
    * `indptr` points to column starts in `indices` and `data`
    * length is `n_col + 1`, last item = number of values = length of both
      `indices` and `data`
    * nonzero values of the `i`-th column are `data[indptr[i]:indptr[i+1]]`
      with row indices `indices[indptr[i]:indptr[i+1]]`
    * item `(i, j)` can be accessed as `data[indptr[j]+k]`, where `k` is
      position of `i` in `indices[indptr[j]:indptr[j+1]]`

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

* efficient column slicing, column-oriented operations
* slow row slicing, expensive changes to the sparsity structure
* use:

  * actual computations (most linear solvers support this format)

* examples::
