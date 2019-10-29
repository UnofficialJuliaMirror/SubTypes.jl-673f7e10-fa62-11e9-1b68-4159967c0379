<div align="center">

# SubTypes.jl

[![Stable Docs](https://img.shields.io/badge/docs-stable-blue.svg)](https://bhgomes.github.io/SubTypes.jl/stable)
[![Latest Docs](https://img.shields.io/badge/docs-latest-blue.svg)](https://bhgomes.github.io/SubTypes.jl/latest)
[![Travis Build Status](https://travis-ci.com/bhgomes/SubTypes.jl.svg?branch=master)](https://travis-ci.com/bhgomes/SubTypes.jl)

_Custom Subtyping in Julia_

</div>

## Custom Subtype

To create a custom subtype define the following data

```julia
SubType{T, P, Flag}
#=
        ^  ^  ^
        1  2  3
1 => Underlying Type
2 => Predicate Data
3 => Type Flag
=#
```

and a predicate processing function

```julia
check_predicate(P, Val(Flag), x::T)
```

which checks if `x::T` should be of type `SubType{T, P, Flag}`. The flag is a way to mark the subtypes for overloading.

## Predefined Custom Subtypes

The custom subtypes `Constrained` and `ConstrainedSymbol` are predefined in the module and they emulate set inclusion subtyping, i.e.

```julia
x::Constrained{T, S}  <=>  x.value::T in S
```

and `ConstrainedSymbol` is set inclusion for `Symbol` types. Inspiration for this type comes from [this post](https://discourse.julialang.org/t/creating-custom-type-of-enumerations-of-symbols/18635/7) by Mohamed Tarek [@mohamed82008](https://github.com/mohamed82008).

## Helper Functions

This module also comes with these helper functions defined for terms and types:

```julia
eltype(::SubType{T}) = T
predicate(::SubType{T, P}) = P
flag(::SubType{T, P, Flag}) = Flag
support(::Constrained{T, S}) = S
```

## Installation

To install, run the following in a Julia session:

```julia
]add SubTypes
```

---
<div align="center">

#### [(UN)LICENSE](UNLICENSE)
Knowledge is Freedom.
</div>
