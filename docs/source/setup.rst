Setup
=====

.. _installation:

Installation
############
Ubuntu with sudo privileges
***************************
1. Download ninja-build which is needed for qtorch.

    ::

        sudo apt install ninja-build

2. Download the other project dependencies. Please make sure you are inside the goldeneye folder when applying this command.

    ::

        pip install -r requirements.txt

3. Setup environment variable (replace with the directory where the imagenet dataset is downloaded).

    ::

        ML_DATASETS=/dir/to/imagenet/

Docker
******

Code Overview
#############

Scripts Folder (scripts)
************************
The **scripts** folder includes wrappers around the goldeneye framework to simplify its use.

Source Folder (src)
*******************
The **src** folder contains all of the goldeneye core logic such as number system implementation and error injection routines.

Validation Folder (val)
***********************
The **val** folder is used for unit-testing the code. You can run it using pytest to check that the installation process was successful.
