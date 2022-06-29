Customization
=============
.. contents::

Adding custom number systems in Python
######################################

Adding custom number systems in Goldeneye is straightforward. You have to implement a sub-class for your number system with 4 necessary methods and one optional method (real_to_format_tensor_meta).

1. Open "src/num_sys_class.py".
2. Implement a class that inherits from "_number_sys" with its __init__ method.
3. Implement the "real_to_format" method which turns a real number into a bitstring denoting the representation of that number in your custom number system.
4. Implement the real_to_format_tensor method accepts a real tensor and returns a an equivalent tensor in the simulated custom number format.
5. Implement "format_to_real" which accepts a bitstring in the custom number system and returns a real number
6. \[OPTIONAL\] Implement the real_to_format_tensor_meta method which accepts a real tensor and returns an equivalent tensor in the simulated custom number system. This method is specific to converting from real to the number system's metadata. This can only be useful in number systems where there is some metadata that is stored separate from the individual numbers (e.g. common exponent in block floating point).


Please refer to the pre-implemented number systems under "src/num_sys_class.py" as guiding examples (e.g. block_fp and adaptive_float).

Adding custom number systems in C++
###################################
The class framework for building a number system in C++ is identical to that in Python. We will make use of PyTorch's library to allow us to run our C++ code inside a Python function. At the top of our .cpp file, we can simply type ``#include <torch/extension.h>``, which will give us all the necessary libraries we need to create our functions.

1. Similar to the Python implementation, initialize a sub-class with the 4 necessary methods.

2. Write the corresponding functions in C++ in "src/num_sys.cpp". You should also add the function prototypes to the header file, "src/num_sys.h", in case you would like to do some testing in a separate file in C++.

3. At the end of the .cpp file, you will need to add a pybind module, similar to the one below. This will allow you to call your C++ functions inside the Python code. Here you can replace "func_name_py" with the name you would like to call your function by in Python, "func_name_cpp" with  the name of the C++ function in "src/num_sys.cpp", and "Description" with a short description of your function in plaintext.

   ::

      PYBIND11_MODULE(TORCH_EXTENSION_NAME, m) {
          m.def("func_name_py", &func_name_cpp, "Description");
      }
   

4. Finally, you will need to import these functions into your .py file. We will use just-in-time compilation, since it avoids the use of a "setup.py" file. In order to do so, we need to include ``from torch.utils.cpp_extension import load`` in our "src/num_sys_class.py" file. We then include the following where where "module_name" can be replaced with the module name you want to use and "directory_to_cpp_file" is the path from "src/" to your .cpp file.

   ::

      current_path = os.path.dirname(os.path.realpath(__file__))
      module_name = load(
          name="module_name",
          sources=[
              os.path.join(current_path, "directory_to_cpp_file"),
          ]
      )

Adaptive Float and Block Float were both implemented using C++ under "src/num_sys.cpp", so you can refer to those functions as needed.
