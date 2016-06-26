# LookupTables.jl
[![Build Status](https://travis-ci.org/bernizt/LookupTables.jl.svg?branch=master)](https://travis-ci.org/bernizt/LookupTables.jl)

LookupTables is a small [Julia](http://julialang.org/) package that implements a 2d lookup table.

## Example usage:

Start by loading LookupTables:

```Julia
using LookupTables
```

If this is our lookup table:

|    | 1 | 3 | 7 |
|----|---|---|---|
| 2  | 1 | 1 | 5 |
| 10 | 3 | 3 | 2 |

```Julia
const rowsvector = [2,10]
const columnsvector = [1,3,7]
const output = = [1 1 5; 3 3 2]
```

Then create a LookupTable2d object:

```Julia
const mylookuptable= LookupTable2d(rowsvector,columnsvector,output)
```

You can now check its values by executing:

```Julia
lookup(10,7,mylookuptable)
  2.0
lookup(2,3,mylookuptable)
  1.0
lookup(2,5,mylookuptable)
  3.0
```

Finally, you can pass a 4th argument to the _lookup_ function to select the interpolation method:

* 0 - Interpolation-Extrapolation _(default)_
* 1 - Interpolation-Use End Values
* 2 - Use Input Nearest
* 3 - Use Input Below
* 4 - Use Input Above
