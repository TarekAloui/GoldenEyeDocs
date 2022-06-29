Usage
=====

.. contents::

How to Use
##########
To add custom models and/or pretrained weights:
1. add your model to `src/othermodels/`
2. add pt files to `src/othermodels/state_dicts`
3. modify `getNetwork()` in `src/util.py` to correspond to the dataset and model name. 
4. also add the appropriate `import` in `/src/util.py`

Your model.py file in `src/othermodels/` should have a few general attributes:
1. A codeblock similar to easily find your model versions 

   ::
   
      __all__ = [
          "baseline",
          "v1",
          "v2",
      ]

2. A separate function for each name in Step 1, which instantiates your model and extracts the correct model parameters from ``/src/othermodels/state_dicts/``. As an example, check out: https://github.com/huyvnphan/PyTorch_CIFAR10/blob/master/cifar10_models/resnet.py


Model accuracy
##############

In order to evaluate the accuracy of your model, you can directly use the `accuracy_profile <https://github.com/ma3mool/goldeneye/blob/main/scripts/accuracy_profile.sh/>`_ script, which will run the preprocess, profile, and split_data python scripts from src/

::

    ./scripts/accuracy_profile.sh NETWORK BATCH FORMAT BITWIDTH RADIX

Model Resiliency
################

In order to evaluate the resiliency of your model, you should run the `end_to_end script <https://github.com/ma3mool/goldeneye/blob/main/scripts/end_to_end.sh/>`_, which will run all the python scripts from src/ in order (preprocess, profile, split_data, injections and postprocess)

::

    ./scripts/end_to_end.sh NETWORK DATASET BATCH FORMAT BITWIDTH RADIX INJECTIONS_LOC

Domain Space Exploration
########################

In order to conduct Domain Space Exploration, you should run the script `sweep.sh <https://github.com/ma3mool/goldeneye/blob/main/scripts/sweep.sh/>`_ which will run the python file sweep_num_formats.py

::
    
    ./scripts/sweep.sh


