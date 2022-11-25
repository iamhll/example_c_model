.. -----------------------------------------------------------------------------
   ..
   ..  Filename       : index.rst
   ..  Author         : Huang Leilei
   ..  Status         : draft
   ..  Created        : 2022-11-18
   ..  Description    : introduction
   ..
.. -----------------------------------------------------------------------------

Introduction
============

Project Tree
------------

   As the name suggested, *git_example_c_model* is an example for C models, which has the following project tree.

   ::

      ├── build                              all kinds of build environments
      │     ├── linux                          Linux environments
      │     │     └── *                          a Linux environment for *
      │     ├── windows                        Windows environments
      │     └     └── *                          a Windows environment for *
      ├── document                           all kinds of documents
      │     ├── doxygen                        source-file-related documents
      │     ├── description                    module-related documents
      │     ├── brief                          branch-related documents
      │     ├── conclusion                     phase-related documents
      │     └── performance                    evaluation-related documents
      ├── script                             all kinds of scripts
      │     ├── get                            generation or calculation tools
      │     ├── analysis                       analysis tools or environments
      │     └── run                            regression or automation environments
      ├── source                             all kinds of source codes
      │     ├── *                              codes for *
      │     │     ├── top                        top-level codes
      │     │     ├── kernel                     kernel-level codes
      │     │     ├── unit                       unit-level codes
      └     └     └── common                     common-level codes

   I will introduce those directories in the following pages.
