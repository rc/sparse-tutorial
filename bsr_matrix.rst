Block Compressed Row Format (BSR)
=================================

* basically a CSR with dense sub-matrices of fixed shape instead of scalar
  items
    * block size `(R, C)` must evenly divide the shape of the matrix `(M, N)`
    * three NumPy arrays: `indices`, `indptr`, `data`
        * `indices` is array of column indices for each block
        * `data` is array of corresponding nonzero values of shape `(nnz, R, C)`
    	* ...
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
* many arithmetic operations considerably more efficient than CSR for
  sparse matrices with dense sub-matrices
* use:
    * like CSR
    * vector-valued finite element discretizations
* examples::

