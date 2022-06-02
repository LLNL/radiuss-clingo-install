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

No installation is required. Instead, one may either clone the project in their
own LC Gitlab space, or create a specific branch in the original GitHub repo.

.. note::
   We prefer that projects share their configuration by contributing to the
   GitHub repo, but this is not mandatory.

==============================
Cloning Radiuss Clingo Install
==============================

Repository setup
================

Radiuss Clingo Install is meant to run on LC Gitlab. Projects may choose to
maintain their own clone. A simple pull and push clone from your local machine
should suffice:

.. code-block:: bash

  $ git clone git@github.com:LLNL/radiuss-clingo-install.git
  $ git remote add gitlab ssh://git@czgitlab.llnl.gov:7999/<group>/radiuss-clingo-install.git
  $ git push gitlab

==================================
Create a branch in the GitHub repo
==================================

Requirements
============

We welcome LLNL projects, in particular RADIUSS supported projects, to
contribute their configuration directly to the GitHub repo. To do so, one
should:

* Request write access to the GitHub repo.
* Submit a PR with their configuration.
* Make sure the configuration is working (see usage section).

.. note::
   It is mandatory that `CI_CONFIG_FILE` default to "none" on the main branch.
   In GitLab UI, it is then possible to trigger or schedule pipelines and
   define `CI_CONFIG_FILE` to the path of the desired configuration.

.. note::
   Only PRs originating from the GitHub repo can be mirrored on LC GitLab, no
   PR from forks can be tested. Please request write access.

=====================
Project configuration
=====================

Configuration file
==================

All the parameters are gathered in `configs/<config-name>.yml`.

 ======================== ====================================================== ===========
  Parameter                Description                                           Default
 ======================== ====================================================== ===========
  ``LLNL_SERVICE_USER``    Service Account used in CI                             __none__
  ``CUSTOM_CI_BUILD_DIR``  Where to locate build directories (prevent overquota)  __none__
  ``CI_SPACK_PATH``        Where to clone Spack, used to share a unique instance  `./spack`
  ``CI_SPACK_REPO``        Repository to clone Spack from                         __none__
  ``CI_SPACK_REF``         Reference (branch, commit) to clone in Spack history   __none__

=====
Usage
=====

The goal of this project is to install clingo on demand. We don't want to
re-install clingo each time a commit is pushed to a branch.

We configured the CI so that by default GitLab will run a single job notifying
the user that no configuration file was provided.

Installing Clingo using your configuration
==========================================

In order to effectively trigger the Clingo installation, one needs to set
`CI_CONFIG_FILE` to point to the desired configuration. This can only be done
in Gitlab UI.

Triggering a pipeline manually
------------------------------

To simply perform a one-time install, go to `CI-CD/Pipelines` and hit `Run
pipeline`.  GitLab opens a page where you can pick the branch you would like to
use, and specify variables for the pipeline: this is where you can set
`CI_CONFIG_FILE` with your configuration. Hit `Run pipeline` and the pipeline
starts immediately, effectively installing Clingo with your configuration.

Schedule a recurring pipeline
-----------------------------

Another usage can be to test that Clingo still installs without errors with the
latest Spack.

First, we need a new configuration file with `CI_SPACK_REF` set to `develop`.
Then we go to `CI-CD/Schedules` and define a new schedule. Pick a branch, set
`CI_CONFIG_FILE` with the new configuration, and choose a recurrence using the
cron syntax. Hit `Save pipeline schedule` and your pipeline will start at the
next defined recurrence.
