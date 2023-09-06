## IEEE754
![[Pasted image 20230308104003.png]]
**CORRECTION: DOUBLE BIAS = 1023**

Why learn how floating point numbers are stored?
- we may work with smaller data types where **over-/under- flow** can occur

Why two kinds of IEEE754 (`float`/`double`)?
- There are **infinite** floating point numbers; we cannot guarantee accuracy no matter what
- `double` can reduce the error: range expands slightly but the fraction is larger

Bias number allows us to represent **negative** exponents
- a way to avoid 2's complement

## IBM Floating Point
Basically IEEE754, except:
- stored exponent is **always** 7 bits w/ bias = 64 (0x40)
	- 32-bit: 1s 7e 24f
	- 64-bit: 1s 7e 56f