Goldeneye
=========

Overview
########
**Goldeneye** is a functional simulator of different number systems with fault injection capabilities. 
It is built on top of the Pytorch deep learning framework and the PytorchFi fault injection library. 
Goldeneye can be used either for conducting fault injection campaigns or the general study of the 
reliability and accuracy of various number systems. This documentation gives an overview of the different 
use-cases of Goldeneye and how to customize it to your own number systems and models.

Getting Started
###############
This documentation provides an overview of the features of Goldeneye including its usage and how to customize 
it to your specific use-cases.

Contents
########

.. toctree::
   :maxdepth: 2

   Overview <index>
   Setup <setup>
   Usage <usage>
   Customization <customization>

About the project
#################

This project was developed by the Harvard Architecture, Circuits and Compilers research group.

`Goldeneye <https://github.com/ma3mool/goldeneye/>`_ is an open-source functional simulator of different number systems with fault injection capabilities. It is built around the pytorch ecosystem and the `Pytorchfi <https://www.pytorchfi.dev/>`_ fault injection library.

Contributors
************
- `Abdulrahman Mahmoud <https://www.linkedin.com/in/abdulrahman-mahmoud-a9206b57/>`_
- `Thierry Tambe <https://www.linkedin.com/in/thierry-tambe-6221a515/>`_
- `Tarek Aloui <https://www.linkedin.com/in/tarek-aloui/>`_
- `David Brooks <http://www.eecs.harvard.edu/~dbrooks/>`_
- `Gu-Yeon Wei <https://www.linkedin.com/in/gu-yeon-wei-7071371/>`_
- `Josh Park <https://www.linkedin.com/in/jhpark25//>`_

Citation
########

If you use or reference Goldeneye, please cite:

::

   @INPROCEEDINGS{GoldeneyeMahmoudTambeDSN2022,
   author={A. {Mahmoud} and T. {Tambe} and T. {Aloui} and D. {Brooks} and G. {Wei}},
   booktitle={2022 52nd Annual IEEE/IFIP International Conference on Dependable Systems and Networks (DSN)},
   title={GoldenEye:  A Platform for Evaluating Emerging Data Formats in DNN Accelerators},
   year={2022},
   }

License
#######

MIT License. Copyright (c) 2022 Harvard VLSI-Arch Research Group.