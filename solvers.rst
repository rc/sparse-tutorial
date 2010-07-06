Linear System Solvers
=====================

* sparse matrix/eigenvalue problem solvers live in :mod:`scipy.sparse.linalg`
* the submodules:
    * :mod:`dsolve`: direct factorization methods for solving linear systems
    * :mod:`isolve`: iterative methods for solving linear systems
    * :mod:`eigen`: sparse eigenvalue problem solvers

Sparse Direct Solvers
---------------------

* default solver: SuperLU 4.0
    * included in SciPy
* optional: umfpack
    * recommended for performance
    * wrappers now live in :mod:`scikits.umfpack`
    * check-out the new :mod:`scikits.suitesparse` by Nathaniel Smith
* example:

.. literalinclude:: examples/direct_solve.py

Iterative Solvers
-----------------

* the :mod:`isolve` module contains the following solvers:
    * ``bicg`` (BIConjugate Gradient)
    * ``bicgstab`` (BIConjugate Gradient STABilized)
    * ``cg`` (Conjugate Gradient) - symmetric positive definite matrices
      only
    * ``cgs`` (Conjugate Gradient Squared)
    * ``gmres`` (Generalized Minimal RESidual)
    * ``minres`` (MINimum RESidual)
    * ``qmr`` (Quasi-Minimal Residual)

LinearOperator Class
^^^^^^^^^^^^^^^^^^^^

.. code-block:: python

    from scipy.sparse.linalg.interface import LinearOperator


* common interface for performing matrix vector products
* useful abstraction that enables using dense and sparse matrices within
  the solvers, as well as *matrix-free* solutions
* has `shape` and `matvec()` (+ some optional parameters)
* example:

.. code-block:: python

    >>> import numpy as np
    >>> from scipy.sparse.linalg import LinearOperator
    >>> def mv(v):
    ...     return np.array([2*v[0], 3*v[1]])
    ...
    >>> A = LinearOperator((2, 2), matvec=mv)
    >>> A
    <2x2 LinearOperator with unspecified dtype>
    >>> A.matvec(np.ones(2))
    array([ 2.,  3.])
    >>> A * np.ones(2)
    array([ 2.,  3.])


Common Parameters
^^^^^^^^^^^^^^^^^

* mandatory:

  A : {sparse matrix, dense matrix, LinearOperator}
      The N-by-N matrix of the linear system.
  b : {array, matrix}
      Right hand side of the linear system. Has shape (N,) or (N,1).

* optional:

  x0  : {array, matrix}
      Starting guess for the solution.
  tol : float
      Relative tolerance to achieve before terminating.
  maxiter : integer
      Maximum number of iterations.  Iteration will stop after maxiter
      steps even if the specified tolerance has not been achieved.
  M : {sparse matrix, dense matrix, LinearOperator}
      Preconditioner for A.  The preconditioner should approximate the
      inverse of A.  Effective preconditioning dramatically improves the
      rate of convergence, which implies that fewer iterations are needed
      to reach a given error tolerance.
  callback : function
      User-supplied function to call after each iteration.  It is called
      as callback(xk), where xk is the current solution vector.


Eigenvalue Problem Solvers
--------------------------

* the :mod:`eigen` module contains:
    * ``arpack``
        * a collection of Fortran77 subroutines designed to
          solve large scale eigenvalue problems
    * ``lobpcg`` (Locally Optimal Block Preconditioned Conjugate
      Gradient Method)
        * works very well in combination with `PyAMG <>`_

* example by Nils Wagner:

    * :download:`examples/lobpcg_sakurai.py`

* output::

    $ python examples/lobpcg_sakurai.py 
    Results by LOBPCG for n=2500

    [ 0.06250083  0.06250028  0.06250007]

    Exact eigenvalues

    [ 0.06250005  0.0625002   0.06250044]

    Elapsed time 7.01

.. image:: figures/lobpcg_eigenvalues.png
