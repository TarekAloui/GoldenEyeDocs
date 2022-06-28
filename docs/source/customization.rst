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