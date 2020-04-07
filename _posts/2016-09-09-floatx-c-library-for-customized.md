---
title: 'FloatX: A C++ Library for Customized Floating-Point Arithmetic'
date: 2020-01-08T02:17:00+01:00
draft: false
---

![](https://avatars2.githubusercontent.com/u/33952981?s=400&v=4 "GitHub - oprecomp/FloatX: Header-only C++ library for low precision floating point type emulation.")  

[](https://github.com/oprecomp/FloatX#floatx-float-extended)FloatX (Float eXtended)
===================================================================================

NOTE: This project is under active development, and is not yet ready for use!

FloatX is a header-only C++ library which extends floating point types beyond the native single and double (and on some hardware half) precision types. It provides template types which allow the user to select the number of bits used for the exponent and significand parts of the floating point number. The idea of FloatX is based on the FlexFloat library, but, instead of implementing the functionality in C and providing C++ wrappers, FloatX is written completely in C++, which makes it more natural to the end user. In addition, FloatX provides a superset of FlexFloat's functionalities, and achieves higher performance.

[](https://github.com/oprecomp/FloatX#features)Features
-------------------------------------------------------

This section lists the functionalities provided by FloatX. Functionalities that are also provided by FlexFloat have (_flexfloat_) appended to the description. In addition, functionalities that are planned, but are not yet implemented are also listed and have (**TODO**) appended.

*   header-only library, without a compiled component, and heavy inlineing, resulting in relatively high performance
*   `floatx` class template, which allows emulation of non-native types with `exp_bits` exponent bits and `sig_bits` significand bits using a natively supported `backend_float` type to perform arithmetic operations (_flexfloat_ - provides a similar functionality in the C++ wrapper, but the memory consumption of the flexfloat C++ class is suboptimal. Additionally, the only supported backend native types are double and softfloat float64)
*   `floatxr` class template, which provides the same functionality as `floatx`, but allows to change the precision of the type at runtime. This class is easier to experiment with, but is not as efficient as `floatx` in both the performance, as well as the memory consumption. (It's performance and memory consumption can be compared to that of the types provided by flexfloat) (_flexfloat_ - provides this in the C library, but not in the C++ wrapper)
*   conversions between builtin types and `floatx` (_flexfloat_ - has a bug where NaN can be cast to Inf during conversion)
*   assignments on `floatx` and `floatxr` types (_flexfloat_)
*   relational operations on `floatx` and `floatxr` types (_flexfloat_ - does not handle NaN properly)
*   relational operations between different types
*   arithmetic operations on `floatx` and `floatxr` types (_flexfloat_)
*   arithmetic operations between different types with implicit type promotion
*   `std::ostream& operator <<(std::ostream&, floatx[r])` (_flexfloat_)
*   `std::istream& operator >>(std::istream&, floatx[r])`
*   conversion to `std::bitset` (_flexfloat_ - can only print a bitwise representation)
*   conversion to `std::string`
*   optional operation counters (requires a compiled runtime library) (**TODO**)
*   automatic deduction of the smallest native type which can fit the requested number of exponent and significand bits (**TODO**)
*   optimized performance in case the requested type matches a natively supported type (_flexfloat_ - only enabled for single, inconsistently with the rest of the librry - e.g. flexfloat's equivalent of half uses 4x more memory than the equivalent of float) (**TODO**)
*   compressed storage which allows to reduce memory footprint (**TODO**)
*   rounding modes other than "round to zero" (**TODO**)
*   CUDA support (**TODO** - should already work, but not tested)

[](https://github.com/oprecomp/FloatX#what-floatx-is-not)What FloatX is NOT
---------------------------------------------------------------------------

FloatX does not implement arbitrary floating point types. The only supported types are "subtypes" of those natively supported by the hardware. In case you need implementations of larger types, consider using the SoftFloat library. (With some effort, you should also be able to use SoftFloat types as backend for FloatX)

FloatX **emulates** the types of custom precision, and, while trying to achieve as high performance as possible, it is **not** capable of magically delivering better performance than natively supported types. Thus, do not expect `floatx<3, 3>` to consume less memory, or be faster than e.g. float. (`floatx<8, 23>` should deliver similar performance as float though).

That being said, it is not likely that FloatX will be useful in production codes. On the other hand, it can be handy in research projects which aim to study the effects of using different precisions.

[](https://github.com/oprecomp/FloatX#installation)Installation
---------------------------------------------------------------

To use the library, just make sure that `floatex.hpp` (from the `src/` folder) is in your include path.

Alternatively, if you are using CMake, a `CMakeLists.txt` file is provided. You can download the repository into your project and use the following code to depend on the floatx target:

```
add_subdirectory(floatx) target_add_library(my_target PRIVATE floatx) 
```

### [](https://github.com/oprecomp/FloatX#building-the-examples--unit-tests)Building the examples / unit tests

A standard CMake command line sequence should do:

```
mkdir build && cd build && cmake .. && make 
```

To run all the tests:

```
make test 
```

This will (hopefully) output a summary of the form:

```
test_............ Passed 
```

To run only one of the tests (and see more detail output):

```
./test/ 
```

[](https://github.com/oprecomp/FloatX#examples)Examples
-------------------------------------------------------

TODO

[](https://github.com/oprecomp/FloatX#acknowledgments)Acknowledgments
---------------------------------------------------------------------

TODO

  
  
from Hacker News https://github.com/oprecomp/FloatX