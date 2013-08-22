:orphan:

.. highlight:: bash

Installation
============

The continuous-time hybridization-expansion matrix solver is based on the TRIQS library. Therefore
the TRIQS library must be installed on your system (see `<http://ipht.cea.fr/triqs>`_ for details about
TRIQS and on its installation). In the following, we will suppose that TRIQS is installed in
the ``path_to_triqs`` directory.


Installation steps
------------------

If you obtained the continuous-time hybridization-expansion matrix solver
through a TRIQS bundle (`<http://ipht.cea.fr/triqs/bundles>`_) then you can
skip steps 1 to 4 and directly go into the
``triqs_bundle/applications/1_cthyb_matrix/build`` directory. Note that
obtaining applications through the bundle ensures that the version of the TRIQS
library is compatible with the version of the applicaton.

#. Download the sources of the matrix solver from github::

     $ git clone git@github.com:TRIQS/cthyb_matrix.git src

#. This has created a directory ``src`` with all code sources. Go into the
   ``src`` directory and look at all available version of the matrix solver::

     $ cd src && git tag

#. Checkout a version of the code compatible with the TRIQS library. Any two versions
   that have the same first two digits are compatible, e.g. the TRIQS library 1.0.x is
   complatible with any matrix solver 1.0.y::

     $ git co 1.0.0

#. Go back up one directory and create an empty build directory where you will compile the code::

     $ cd .. && mkdir build && cd build

#. In the build directory call cmake specifying where the TRIQS library is installed::

     $ cmake -DTRIQS_PATH=path_to_triqs ../src

#. Compile the code::

     $ make

#. Test that everything went fine::

     $ make test

#. Install the code::

     $ make install

