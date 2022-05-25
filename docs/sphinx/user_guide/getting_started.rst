.. ##
.. ## Copyright (c) 2022, Lawrence Livermore National Security, LLC and
.. ## other RADIUSS Project Developers. See the top-level COPYRIGHT file for details.
.. ##
.. ## SPDX-License-Identifier: (MIT)
.. ##

.. _getting_started-label:

*******************************************
Getting started with Radiuss Clingo Install
*******************************************

Radiuss Clingo Install is a CI only repo. It consists in using GitLab CI
capabilities to automate complex actions while allowing easy customization and
user-friendly visual rendering in the UI.

Radiuss Clingo Install is meant to run on LC GitLab instance. The main repo,
hosted on GitHub for accessibility and visibility, is mirrored on LC GitLab for
testing and/or running specific configs on demand.

No build is required. Instead, one may either clone the project in their own LC
Gitlab space, or create a specific branch in the original GitHub repo. There is
no preferred solution at this stage.

==============================
Cloning Radiuss Clingo Install
==============================

Radiuss Clingo Install is meant to run on LC Gitlab. Projects may choose to
maintain their own clone. A simple pull and push clone from your local machine
should suffice:

  $ git clone git@github.com:LLNL/radiuss-clingo-install.git
  $ git remote add gitlab ssh://git@czgitlab.llnl.gov:7999/<group>/radiuss-clingo-install.git
  $ git push gitlab
