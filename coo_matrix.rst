Coordinate Format (COO)
=======================

* also known as the 'ijv' or 'triplet' format
    * three NumPy arrays: `row`, `col`, `data`
    * `data[i]` is value at `(row[i], col[i])` position
    * permits duplicate entries
    * subclass of :class:`_data_matrix` (sparse matrix classes with
      `.data` attribute)
* fast format for constructing sparse matrices
* constructor accepts:
    * dense matrix (array)
    * sparse matrix
    * shape tuple (create empty matrix)
    * `(data, ij)` tuple
* very fast conversion to and from CSR/CSC formats
* fast matrix * vector (sparsetools)
* fast and easy item-wise operations
    * manipulate data array directly (fast NumPy machinery)
* no slicing, no arithmetics (directly)
* use:
    * facilitates fast conversion among sparse formats
    * when converting to CSR or CSC format, duplicate entries are summed
      together
        * facilitates efficient construction of finite element matrices
* examples::
