List of Lists Format (LIL)
==========================

* row-based linked list
  * each row is a Python list (sorted) of column indices of non-zero elements
  * rows stored in a NumPy array (dtype=np.object)
  * non-zero values data stored analogously
* efficient for constructing sparse matrices incrementally
* constructor accepts:
  * dense matrix (array)
  * sparse matrix
  * shape tuple (create empty matrix)
* flexible slicing, changing sparsity structure is efficient
* slow arithmetics, slow column slicing due to being row-based
* use:
  * when sparsity pattern is not known apriori or changes
  * example: reading a sparse matrix from a text file

examples::

>>> mtx = sps.lil_matrix((4, 3))
>>> mtx
<4x3 sparse matrix of type '<type 'numpy.float64'>'
        with 0 stored elements in LInked List format>
>>> mtx[3,1] = 2
>>> mtx
<4x3 sparse matrix of type '<type 'numpy.float64'>'
        with 1 stored elements in LInked List format>
>>> print mtx
  (3, 1)        2.0
>>> mtx.todense()
matrix([[ 0.,  0.,  0.],
        [ 0.,  0.,  0.],
        [ 0.,  0.,  0.],
        [ 0.,  2.,  0.]])
>>> mtx[:,1]
<4x1 sparse matrix of type '<type 'numpy.float64'>'
        with 1 stored elements in LInked List format>
>>> mtx[1,:]
<1x3 sparse matrix of type '<type 'numpy.int32'>'
        with 0 stored elements in LInked List format>
