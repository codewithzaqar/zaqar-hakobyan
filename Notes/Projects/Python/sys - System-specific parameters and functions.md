This module provides access to some variables used or maintained by the interpreter and to functions that interact strongly with the interpreter. It is always available. Unless explicitly noted otherwise, all variables are read-only.
#### `sys.abiflags`
On POSIX systems where Python was built with the standard `configure` script, this contains the ABI flags as specified by [PEP 3149](https://peps.python.org/pep-3149).
> *Added in version 3.2.* 

> *Changed in version 3.8:* Default flags became an empty string (`m` flag for pymalloc has been removed).

[[Introduction#Notes on availability|Availability]]: Unix.
