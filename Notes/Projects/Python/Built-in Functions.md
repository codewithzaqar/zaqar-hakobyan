#### `max(iterable, *, key=None)`
#### `min(iterable, *, key=None)`
#### `sorted(iterable, /, *, key=None, reverse=False)`
Return a new sorted list from the items in *iterable*.

Has two optional arguments which must be specified as keyword arguments.

*key* specifies a function of one argument that is used to extract a comparison key from each element in *iterable* (for example, `key=str.lower`). The default value is `None` (compare the elements directly).

*reverse* is a boolean value. If set to `True`, then the list elements are sorted as if each comparison were reversed.

Use [[functools.cmp_to_key( )]] to convert an old-style *cmp* function to a *key* function.

The built-in [[#`sorted(iterable, /, *, key=None, reverse=False)`|sorted( )]] function is guaranteed to be stable. A sort is stable if it guarantees not to change the relative order of elements that compare equal  - this is helpful for sorting in multiple passes (for example, sort by department, than by salary grade).

The sort algorithm uses only `<` comparisons between items. While defining an [[3.3.1. Basic customization|__it__( )]] method will suffice for sorting, [PEP 8](https://peps.python.org/pep-0008) recommends that all six [[6.10. Comparisons|rich comparisons]] 