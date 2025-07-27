Unless documented otherwise, Python's C API is covered by the Backwards Compatibility Policy, [PEP 387](https://peps.python.org/pep-0387). Most changes to it are source-compatible (typically by only adding new API). Changing existing API or removing API is only done after a depreciation period or to fix serious issues.

CPython's Application Binary Interface (ABI) is forward-and backwards-compatible across a minor release (if these are compiled the same way; see [[#Platform Considerations|Platform Considerations]] below).

## Limited C API
Python 3.2 introduced the *Limited API*, a subset of Python's C API. Extensions that only use the API can be compiled once and be loaded on multiple versions of Python. Contents of the Limited API are [[#Contents of Limited API|listed below]].
## Stable ABI
To enable this, Python provides a *Stable ABI*: a set of symbols that will remain ABI-compatible across Python 3.x versions.
> **Note**: The Stable ABI prevents ABI issues, like linker errors due to missing symbols or data corruption due to changes in structure layouts or function signatures. However, other changes in Python can change the *behavior* of extensions. See Python's Backwards Compatibility Policy ([PEP 387](https://peps.python.org/pep-0387)) for details.

The Stable ABI contains symbols exposed in the [[#Limited C API|Limited API]], but also other ones - for example, functions necessary to support older versions of the Limited API.

On Windows, extensions that use the Stable ABI should be linked against `python3.dll` rather than a version-specific library such as `python39.dll`.

On some platforms, Python will look for and load shared library files named with the `abi3` tag (e.g. `mymodule.abi3.so`) it does not check if such extensions conform to a Stable ABI. The user (or their packaging tools) need to ensure that, for example, extensions built with the 3.10+ Limited API are not installed for lower versions of Python.

All functions in the Stable ABI are present as functions in Python's shared library, not solely as macros. This makes them usable from languages that don't use the C preprocessor.
# Platform Considerations
ABI stability depends not only on Python, but also on the compiler used, lower-level libraries and compiler options. For the purposes of the [[#Stable ABI|Stable ABI]],
# Contents of Limited API
Currently, the [[#Limited C API|Limited API]] includes the following items: