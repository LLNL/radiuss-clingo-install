.. ## Copyright (c) 2019-2021, Lawrence Livermore National Security, LLC and
.. ## other RADIUSS Project Developers. See the top-level COPYRIGHT file for details.
.. ##
.. ## SPDX-License-Identifier: (MIT)

Welcome to Radiuss Clingo Install!
=================================

RADIUSS Clingo Install is a sub-project from the RADIUSS initiative providing a
testing infrastructure to test that clingo installs correctly on any LC machine
of interest. It does so automatically in GitLab while tracking changes in
Spack.

LLNL's RADIUSS project (Rapid Application Development via an Institutional
Universal Software Stack) aims to broaden usage across LLNL and the open source
community of a set of libraries and tools used for HPC scientific application
development.


What exactly is this repo about?
================================

In this repo, we configured Gitlab CI to generate CI pipelines that build any
spack and clingo in various configurations on various machines.

The intended use is to setup schedules to build clingo for spack on a regular
basis and check that this is not broken.

This can also be used to populate and update a Spack bootstrap store for a
frozen spack version (for reproducibility / reliability).


Table of Contents
=================

.. toctree::
   :maxdepth: 2

Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`
