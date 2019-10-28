.. _getting-started:

==================================
How to Install Donnie's Software
==================================

_`Operating System Requirement`
-----------------------------------------------------
- Currently this project requires Ubuntu 16.04 `Ubuntu 16.04 <http://releases.ubuntu.com/16.04/>`_ (Xenial Xerus) is the recommended OS distribution. For older computers or VMs, `Lubuntu 16.04 <http://cdimage.ubuntu.com/lubuntu/releases/16.04/release/>`_ or `Ubuntu Mate 16.04 <https://ubuntu-mate.org/trusty/>`_ are recommended.
- Git installed.

_`Compile and Install Donnie Software on a Desktop Computer`
-------------------------------------
Open a terminal, and execute the following commands:

.. code-block:: bash

	mkdir ~/donnie; cd ~/donnie
	git clone --recurse-submodules -b devel https://github.com/lsa-pucrs/donnie-assistive-robot-sw.git
	cd donnie-assistive-robot-sw
	chmod +x ./install.sh
	export DONNIE_PATH=/opt/donnie 
	./install.sh

After the execution of the last command above, if the installation finished successfully you are ready to go! note:The last command above, in general, requires lot of time to finish.

Initializing the environment
^^^^^^^^^^^^^^^^^^^^^^^
With Donnie's environment installed on your computer, open a new terminal (crtl + alt + t) and run the command:

.. code-block:: bash

	donnie_player

Wait a few seconds for the environment to boot, and then run GoDonnie. There are two modes of execution:
Terminal mode: The code must be entered at the GoDonnie terminal and is executed by pressing the ESC key.

.. code-block:: bash

	GoDonnie -t

File Mode: Allows you to play GoDonnie files (extension .gd or .txt)

.. code-block:: bash

	GoDonnie -f <filename>

Some examples of GoDonnie files are in the directory.

.. code-block:: bash

	/opt/donnie/test/GoDonnie/
	
Note: To execute a file that is in another directory, you must indicate the directory path where it is located. For example, the file test.gd is in the /opt/donnie/test/GoDonnie/directory, to run it use the GoDonnie command as follows:
	
	- GoDonnie -f /opt/donnie/test/GoDonnie/test.gd
	
	Or go to the directory the file is in, before executing:
	
	- cd /opt/donnie/test/GoDonnie/
	
	- GoDonnie -f test.gd

Configuring Donnie
^^^^^^^^^^^^^^^^^^^^^^^

The installation script composes a standard instalation that we believe is the most appropriate for the average user. 
However, advanced parameters can be set if the user has experience with the appropriate tools.

The build system is based on cmake, so experience with Linux, `make <https://www.gnu.org/software/make/>`_, and `cmake <https://cmake.org/>`_ is required. All the individual parts of Donnie's Software Stack are also based on CMake. These are the software parts that can be customized, each with its own set of parameters:

- raspicam driver
- `Player <https://github.com/playerproject/player>`_
- `Stage <https://github.com/rtv/Stage>`_
- Donnie Software

each of these packages have their one sets of parameters.

Developers interested in customization might want to read the following files:

- `install.sh <https://github.com/lsa-pucrs/donnie-assistive-robot-sw/blob/master/install.sh>`_: For desktop setup procedure;
- `setup.sh.in <https://github.com/lsa-pucrs/donnie-assistive-robot-sw/blob/master/install/setup.sh.in>`_
- `install-rpi.sh <https://github.com/lsa-pucrs/donnie-assistive-robot-sw/blob/master/install-rpi.sh>`_: For embedded computer (e.g. Raspberry Pi) setup procedure;
- `setup-rpi.sh.in <https://github.com/lsa-pucrs/donnie-assistive-robot-sw/blob/master/install/setup-rpi.sh.in>`_
- and all the *CMakeLists.txt* files

Parameters for Donnie's Software
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The following list explains Donnie's main compilation parameters:

.. code-block:: none

	BUILD_DOCS           OFF              Generate Donnie's documents.
	BUILD_DOXYGEN        ON               This is the default document in HTML, meant only for developers.
	BUILD_DOXYGEN_PDF    OFF              The same document before, but in PDF.
	BUILD_EXAMPLES       OFF              Build the examples for each part of Donnie.
	BUILD_MANUAL         OFF              Build the manuals: software manual, hardware manual, user manual.
	CMAKE_BUILD_TYPE     Release | Debug  Debug mode is for developers only !
	DOC_LANGUAGE         en | pt-br | es  The language used to build documents and the GoDonnie interpreter. Future work !
