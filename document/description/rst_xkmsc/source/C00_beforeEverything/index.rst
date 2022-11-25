.. -----------------------------------------------------------------------------
   ..
   ..  Filename       : index.rst
   ..  Author         : Huang Leilei
   ..  Status         : draft
   ..  Created        : 2022-11-18
   ..  Description    : before everything
   ..
.. -----------------------------------------------------------------------------

Before Everything
=================

   Please get the following items ready before you start.


WSL
---

   #. enable the developer mode

      .. image:: WSL_step1.png
         :width: 800

   #. install Ubuntu

      .. image:: WSL_step2.png
         :width: 800

   #. enable the WSL function

      .. image:: WSL_step3.png
         :width: 800

   #. open Ubuntu (For the first time, it will install itself and ask you to create a default UNIX user account)

      .. image:: WSL_step4.png
         :width: 800

   #. change apt source

      *  open file */etc/apt/sources.list* with root privilege
      *  replace the original contents with

         ::

            deb http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse
            deb http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse
            deb http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse
            deb http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse
            deb http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse
            deb-src http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse
            deb-src http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse
            deb-src http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse
            deb-src http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse
            deb-src http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse

         |  **please replace the codename (bionic) with that of your system,**
         |  which could be queried with

         ::

            lsb_release -c

   #. change pip source

      *  create file *~/.pip/pip.conf*
      *  fill it with

         ::

            [global]
            index-url = https://mirrors.aliyun.com/pypi/simple

            [install]
            trusted-host=mirrors.aliyun.com

   #. install basic tools

      ::

         sudo apt-get update
         sudo apt-get -f install
         sudo apt-get upgrade
         sudo apt-get install cmake ffmpeg g++ gcc gitk make python3 python3-pip tree --fix-missing
         sudo pip3 install numpy sphinx

   #. change some settings

      *  open file *~/.bashrc* with root privilege
      *  replace

         ::

            PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

         with

         ::

            PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u\[\033[00m\]@\[\033[01;34m\]\W\[\033[00m\]\$ '


Git
---

   #. install Git and TortoiseGit

      .. image:: Git_step1a.png
         :width: 500

      (https://git-scm.com/downloads)

      .. image:: Git_step1b.png
         :width: 500

      (https://tortoisegit.org/download/)


Xming
-----

   #. install Xming

      .. image:: Xming_step1.png
         :width: 500

      (http://www.straightrunning.com/XmingNotes/)

   #. set global variable *DISPLAY*

      *  open *~/.bashrc* with root privilege
      *  add

         ::

            export DISPLAY=:0.0


VS Code
-------

   #. install VS Code

      .. image:: VSCode_step1.png
         :width: 500

      (https://code.visualstudio.com/Download)

   #. install some extensions

      *  Better Comments
      *  Binary
      *  C/C++
      *  Chinese (Simplified) Language Pack for Visual Studio code
      *  Excel Viewer
      *  Git History
      *  Jupyter
      *  Matlab
      *  Octave
      *  Python
      *  Remote - WSL
      *  Tcl
      *  Verilog-HDL/SystemVerilog/Bluespec SystemVerilog
      *  vscode-pdf
      *  ...

      \

      .. image:: VSCode_step2.png
         :width: 800

   #. change some settings

      *  enable *Indent Using Spaces* (press key *ctrl*\ +\ *shift*\ +\ *p* and search it)
      *  disable *C_Cpp: Code Folding* of *C/C++* extension (open *C/C++*\ 's settings and search it)
      *  ...

   #. open folders and reopen them in WSL

      .. image:: VSCode_step4.png
         :width: 800

   #. Now you can start to work!
