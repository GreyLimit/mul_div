# mul_div
A software implementation of an unsigned combined Multiply then Divide routine.

This template code enables systems with restricted abilities to perform fast(ish[^1]) multiplication followed by division operations *without the intermediate values overflowing the base value type*.

This does **not** mean that overflows **cannot** happen, only that the multiplication component does not overflow.  If the divisor is small (relative to the intermediate product) then the final result can *still* overflow the base value type.

Usage:  It is a template function, so include the header file, then 'call' the function providing the unsigned type you want it to operate in as the template argument, thus:

```
x = mul_div<unsigned int>( a, b, c );
```
  
This will calculate `x = a * b / c` where all values are of 'unsigned int'.

All unsigned datatypes can be used in the template class from 'unsigned char' to 'unsigned long long int'.  Use as appropiate.

[^1]: This is, obviously, a relative term.  Having done some comparitive tests the code is suprisingly not hugely slower than simply asking the compiler to cast values to a larger type while doing the calculation.  The algorithum has O(N) performance where N is essentially the number of bits in the base value type. However, this code continues to work even using the compilers largest data type, and was originally written to support calculations within small 8 bit MCUs which typically do not have built in support for these calculations.
