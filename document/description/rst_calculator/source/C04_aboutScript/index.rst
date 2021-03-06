.. -----------------------------------------------------------------------------
   ..
   ..  Filename       : index.rst
   ..  Author         : Huang Leilei
   ..  Status         : draft
   ..  Created        : 2022-03-28
   ..  Description    : about script
   ..
.. -----------------------------------------------------------------------------

About Script
============

   Directory *script* contains **three** different kinds of scripts

*  :get: generation or calculation tools
*  :analysis: analysis tools or environments
*  :run: regression or automation environments


Get
---

   Directory *get* contains generation tools, which may contain tools like

*  generation tools to produce test vectors
*  calculation tools to get SNR, PSNR results


Analysis
--------

   Directory *analysis* contains analysis tools or environments, which may contain tools or environments like

*  analysis tools to process the output of C models
*  analysis environments to process the intermediate data of C models
*  analysis environments to do pre-researches


Run
---

   Directory *run* contains regression or automation environments, which may contain environments like

*  automation environments to do updates or checks
*  regression environments to run C models


Existing Environments
---------------------

   Information on several existing environments is listed below.


getTvCalculator
```````````````

*  Function

   #. |  generate test vectors according to the information specified by parameter *CSTR_INFO_ITEM_ALL*
      |  and save them to directory *CSTR_DIRECTORY*

*  Pre-Request

      .. table::
         :align: left
         :widths: auto

         ========= ============
          item      my version
         ========= ============
          python3   3.8.10
         ========= ============

*  Content

      .. table::
         :align: left
         :widths: auto

         ===================================== ================================= ============
          item                                  description                       postscript
         ===================================== ================================= ============
          getTvCalculator.sh                    generating script (top)
          getTvCalculator.py                    generating script (kernel)
          /mnt/e/DOWNLOAD/SEQUENCE/CALCULATOR   directory for generated vectors   generated by command *getTvCalculator.sh*
         ===================================== ================================= ============

*  Usage

      |  In the WSL environment, change the directory to *script/get/getTvCalculator*,
      |  then you can

   #. complete the above functions with

      ::

         ./getTvCalculator.sh

      then you will get

      .. +++++++++++++++++ uncommented to help the decision of width

      .. image:: scriptGetTvCalculator_usage1.png
         :width: 390

      \

      .. +++++++++++++++++ uncommented to help the decision of width

      .. image:: scriptGetTvCalculator_usage2.png
         :width: 520


runListUpdate
`````````````

*  Function

   #. update auto-generated codes like *cfg_\*.cpp*
   #. convert files from DOS format to UNIX format
   #. delete trailing blanks
   #. collect markers like *TODO*, *NOTE*, *???* or *!!!*
   #. collect file status (draft, phase ??? or something alike)
   #. remove empty directory

*  Pre-Request

      none

*  Content

      .. table::
         :align: left
         :widths: auto

         ================== ====================================== ============
          item               description                            postscript
         ================== ====================================== ============
          runListUpdate.sh   3.8.10
          dump               directory for collected informations   generated by command *./runListUpdate.sh*
         ================== ====================================== ============

*  Usage

      |  In the WSL environment, change the directory to *script/run/runListUpdate*,
      |  then you can

   *  complete the above functions with

      ::

         ./runListUpdate.sh

      then you will get

      .. ++++++++++++++++ uncommented to help the decision of width

      .. image:: scriptRunListUpdate_usage1.png
         :width: 350

      \

      .. ++++++++++++++++ uncommented to help the decision of width

      .. image:: scriptRunListUpdate_usage2.png
         :width: 495


runCalculator
`````````````

*  Function

   #. generate executable file *calculator*
   #. create a directory named with session\ *CSTR_TAG* (session tag, default value is Test)
   #. copy run script *runCalculator.sh*, executable file *calculator*, configuration file *calculator.cfg* to directory session\ *CSTR_TAG*
   #. change the directory to session\ *CSTR_TAG* and automatically run *calculator* to process specified with parameter *CSTR_DIR_VECT* (vector directory) and *CSTR_INFO_VECT_ALL* (vector information)
   #. calculate and note down md5sum of output files
   #. do correctness check (does not exist in this environment)
   #. extract/calculate and notedown SNR, PSNR or other performance related information (does not exist in this environment)
   #. change the directory back

*  Pre-Request

      .. table::
         :align: left
         :widths: auto

         ========= ============
          item      my version
         ========= ============
          gcc, g++  9.3.0
          Make      4.2.1
          cmake     3.16.3
          md5sum    8.30
         ========= ============

*  Content

      .. table::
         :align: left
         :widths: auto

         ================== ==================== ============
          File Name          Descriptions         postscript
         ================== ==================== ============
          makefile           makefile
          runCalculator.sh   regression script
          calculator.cfg     configuration file
          sessionTest        regression session   generated by command *make run*
         ================== ==================== ============

*  Usage

      |  In the WSL environment, change the directory to *script/run/runCalculator*,
      |  then you can

   #. view help with

      ::

         make

      then you will get

      .. +++++++++++++++ uncommented to help the decision of width

      .. image:: scriptRunCalculator_make.png
         :width: 630

   #. complete the above functions with

      ::

         make run

      then you will get

      .. +++++++++++++++ uncommented to help the decision of width

      .. image:: scriptRunCalculator_make_run_0.png
         :width: 705

      \.\.\.

      .. +++++++++++++++ uncommented to help the decision of width

      .. image:: scriptRunCalculator_make_run_1.png
         :width: 1075

      \.\.\.

      .. +++++++++++++++ uncommented to help the decision of width

      .. image:: scriptRunCalculator_make_run_2.png
         :width: 620

      \.\.\.

      .. +++++++++++++++ uncommented to help the decision of width

      .. image:: scriptRunCalculator_make_run_3.png
         :width: 940

   #. clean files with

      ::

         make clean

      or

      ::

         make clean_all

      then you will get

      .. +++++++++++++++ uncommented to help the decision of width

      .. image:: scriptRunCalculator_make_clean.png
         :width: 950
