.. -----------------------------------------------------------------------------
   ..
   ..  Filename       : index.rst
   ..  Author         : Huang Leilei
   ..  Status         : draft
   ..  Created        : 2022-03-28
   ..  Description    : about build
   ..
.. -----------------------------------------------------------------------------

About Build
===========

   Directory *build* contains **two** different kinds of environments.

*  :linux: Linux-based build environments
*  :windows: Windows-based build environments


Existing Environments
---------------------

   Information on several existing environments is listed below.

linux/calculator
````````````````

*  Function

   #. generate and run executable file *calculator* under Linux OS

*  Pre-Request

      .. table::
         :align: left
         :widths: auto

         ========== ============
          item       my version
         ========== ============
          gcc, g++   9.3.0
          Make       4.2.1
          cmake      3.16.3
         ========== ============

*  Content

      .. table::
         :align: left
         :widths: auto

         ========== =============
          item       description
         ========== =============
          build.sh   build script
          run.sh     (single-)run script
         ========== =============

*  Usage

      |  In the WSL environment, change the directory to *build/linux/calculator*,
      |  then you can

   #. create a building environment with

      ::

         ./build.sh

      then you will get

      .. \+++++++++++++ uncommented to help the decision of width

      .. image:: buildCalculatorLinux_Usage1.png
         :width: 700

   #. generate executable file *calculator* with

      ::

         make

      then you will get

      .. \+++++++++++++ uncommented to help the decision of width

      .. image:: buildCalculatorLinux_Usage2.png
         :width: 1115

   #. run executable file *calculator* (with a given configuration setting) with

      ::

         ./calculator -c ../../../script/run/runCalculator/calculator.cfg

      then you will get

      .. \+++++++++++++ uncommented to help the decision of width

      .. image:: buildCalculatorLinux_Usage3.png
         :width: 675

   #. |  Sure, to run with a different configuration setting,
      |  you can either change the contents of configuration file *calculator.cfg* or overwrite them through the CLI (command-line interface).
      |  For example,

      ::

         ./calculator -c ../../../script/run/runCalculator/calculator.cfg --numFrame 3

      .. \+++++++++++++ uncommented to help the decision of width

      .. image:: buildCalculatorLinux_Usage4a.png
         :width: 775

      |  Besides, I have created a (single-)run script *run.sh* which would execute the above steps one by one.
      |  Build parameters can be passed through -B "...";
      |  Run parameters can be passed through -R "...".
      |  For example,

      ::

         ./run.sh -R "--numFrame 5"

      .. \+++++++++++++ uncommented to help the decision of width

      .. image:: buildCalculatorLinux_Usage4b.png
         :width: 705


windows/calculator
``````````````````

*  Function

   #. generate and run executable file *calculator* under Windows OS

*  Pre-Request

      .. table::
         :align: left
         :widths: auto

         =============== ============
          item            my version
         =============== ============
          CMake           3.21.0
          Visual Studio   2017-15.9.37
         =============== ============

*  Content

      .. table::
         :align: left
         :widths: auto

         =============== =============
          item            description
         =============== =============
          build_2017.dat  VS_2017 build script
          build_2019.dat  VS_2019 build script
         =============== =============

*  Usage

      |  In Windows Explorer, change the directory to *build/windows/calculator*,
      |  then you can

   #. |  double click the corresponding build.bat to create a building environment
      |  (choose build_2017.bat if Visual Studio 2017 is installed)
      |  (choose build_2019.bat if Visual Studio 2019 is installed)

      .. image:: buildCalculatorWindows_Usage1.png
         :width: 1000

   #. open solution file *calculator.sln*

      .. image:: buildCalculatorWindows_Usage2.png
         :width: 800

   #. right click on solution *calculator* and set it as the startup item

      .. image:: buildCalculatorWindows_Usage3.png
         :width: 800

   #. right click on solution *calculator* and click *properties*, then add

      ::

         -c ../../../script/run/runCalculator/calculator.cfg

      |  to the command-line parameter
      |  (both slash and backslash can be recognized)

      .. image:: buildCalculatorWindows_Usage4a.png
         :width: 800

      .. image:: buildCalculatorWindows_Usage4b.png
         :width: 800

   #. click button *Start* or press key *F5* to generate executable file *calculator* and run it with the given configuration setting

      .. image:: buildCalculatorWindows_Usage5.png
         :width: 900
