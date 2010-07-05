Abstract
--------

The scipy.sparse package provides a number of sparse matrix storage schemes
like compressed sparse row/column, linked list or coordinate formats. Each of
those is suitable for some applications and unsuitable for other ones. I will
first introduce every format available and mention its strong points and
weaknesses. I will also discuss some common difficulties, originating from the
fact, that the sparse matrix objects are not subclasses of numpy.ndarray,
namely fancy indexing issues.

Then I will dive into the related scipy.sparse.linalg module, that contains
sparse eigenvalue, iterative and direct solvers, and show how to use those
solvers.

Rough outline of the tutorial session:

  - Sparse matrix formats in SciPy

     - Introduction of the formats

     - Common issues

  - Sparse matrix solvers in SciPy              

If you have an interesting sparse computing-related topic other then those
mentioned above, post a comment, please.
