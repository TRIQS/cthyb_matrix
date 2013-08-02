
.. index::  DMFT Loops

.. _dmftloop:

Building DMFT calculations
================================

TRIQS includes all basic ingredients to write DMFT computations: impurity
solvers, Green's functions.  The self-consistency condition is assembled from
these ingredients, using the basic operations on Green's function (arithmetic
operations, slicing, ...).

This illustrates the idea of the introduction.  There is no `general` DMFT
computation class that would handle all cases, just the bricks to build them
easily. Here's an example:


Plain-vanilla DMFT: the Bethe lattice 
------------------------------------------

Here is a complete computation of a single-site DMFT on a Bethe lattice
:download:`[file] <single_site_bethe.py>`:

.. literalinclude:: single_site_bethe.py

The solvers are discussed in :ref:`solvers`, so let us just emphasize
that the DMFT loop itself is `polymorphic`: it would run as well with
any other solver, we only use the `G0` and `G` functions present in any solver
(see :ref:`solver_concept`). Even if here the self-consistency condition is very simple,
this property would still be true in more complex cases.

This run generates a file :file:`single_site_bethe.h5` containing the Green's function
at every iteration. You can plot them to see the convergence on the solver:

.. plot:: dmft/plot.py
  :include-source:
  :scale: 70
