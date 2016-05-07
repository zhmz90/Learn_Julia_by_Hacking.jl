# Wrap C library in Julia

### shared library
How to make a shared library

	`clang toy.c -o libtoy.so -fpic -shared`

### ccall
`ccall((:function, "library"), return_type, (input_type1,input_type2), input1, input2)`

`ccall` is actualy not a function. Details at [StefanKarpinski's answer in StackOverflow](http://stackoverflow.com/questions/35831775/issue-with-julia-ccall-interface-and-symbols).

``` Julia
	julia> @code_llvm ccall((:getenv,"libc"),Cstring,(Cstring,),"SHELL")
	ERROR: expression is not a function call, or is too complex for @code_llvm to analyze; break it down to simpler parts if possible
	 in error at ./error.jl:21
	
```	

If you want more details, `julia/src/ccall.cpp` may be helpful for you.

	
### data structure in Julia and C: alignment, padding, endianness etc

### write a simple wrapper


### References
- [Calling C and Fortran Code](http://docs.julialang.org/en/latest/manual/calling-c-and-fortran-code)

	
