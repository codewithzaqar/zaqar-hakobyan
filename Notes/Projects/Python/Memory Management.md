Test
# Raw Memory Interface
#### void PyMem_RawMalloc(size_t n)
*Part of the [[C API Stability|Stable ABI]] since version 3.13.*

Allocates *n* bytes and returns a pointer of type **void**** to the allocated memory, or `NULL` if the request fails.

Requesting zero bytes returns a distinct non-NULL pointer if possible, as if `PyMem_RawMalloc(1)` had been called instead. The memory will not have been initalized in any way.
#### void PyMem_RawCalloc(size_t, nelem, size_t elsize)
*Part of the [[C API Stability|Stable ABI]] since version 3.13*.
Allocates *nelem* elements each whose size in bytes is *elsize* and returns a pointer of type **void**** to the allocated memory, or `NULL` if the request fails. The memory is initialized to zeros.

Requesting zero elements or elements of size zero bytes returns a distinct non-`NULL` pointer if possible, as if `PyMem_RawCalloc(1, 1)` had been called instead.
> *Added in version 3.5.*
#### void PyMem_RawRealloc(void p, size_t n)
*Part of the [[C API Stability|Stable ABI]] since version 3.13.*
Resizes the memory block pointed to by *p* to *n* bytes. The contents will be unchanged to the minimum of the old and the new sizes.

If *p* is `NULL`, the call is equivalent to `PyMem_RawMalloc(n)`; else if *n* is equal to zero, the memory block is resized but is not freed, and the returned pointer is non-`NULL`.

Unless *p* is `NULL`, it must have been returned by a previous call to [[Memory Management#Raw Memory Interface#void PyMem_RawMalloc(size_t n)|PyMem_RawMalloc()]], [[Memory Management#Raw Memory Interface#void PyMem_RawRealloc(void p, size_t n)|PyMem_RawRealloc()]] or [[Memory Management#Raw Memory Interface#void PyMem_RawCalloc(size_t, nelem, size_t elsize)|PyMem_RawCalloc()]].

If the request fails, [[Memory Management#Raw Memory Interface#void PyMem_RawRealloc(void p, size_t n)|PyMem_RawRealloc()]] returns `NULL` and *p* remains a valid pointer to the previous memory area.
#### void PyMem_RawFree(void p)
*Part of the [[C API Stability|Stable ABI]] since version 3.13.*

Frees the memory block pointed to by *p*, which must have been returned by a previous call to [[Memory Management#Raw Memory Interface#void PyMem_RawMalloc(size_t n)|PyMem_RawMalloc()]], [[Memory Management#Raw Memory Interface#void PyMem_RawRealloc(void p, size_t n)|PyMem_RawRealloc()]] or [[Memory Management#Raw Memory Interface#void PyMem_RawCalloc(size_t, nelem, size_t elsize)|PyMem_RawCalloc()]]. Otherwise, or if `PyMem_RawFree(p)` has been called before, undefined behavior occurs.

If *p* is `NULL`, no operation is performed.

# Memory Interface
#### void PyMem_Malloc(size_t n)
*Part of the [[C API Stability|Stable ABI]]*

Allocates *n* bytes and returns a pointer of type **void**** to the allocated memory, or `NULL` if the request fails.

Requesting zero bytes returns a distinct non-`NULL` pointer if possible, as if `PyMem_Malloc(1)` had been called instead. The memory will not have been initialized in any way.

#### void PyMem_Calloc(size_t nelem, size_t elsize)
*Part of the [[C API Stability|Stable ABI]] since version 3.7.*

Allocates *nelem* elements each whose size in bytes is *elsize* and returns a pointer of type **void**** to the allocated memory, or `NULL` if the request fails. The memory is initialized to zeros.

Requesting zero elements or elements of size zero bytes returns a distinct non-`NULL` pointer if possible, as if `PyMem_Calloc(1, 1)` had been called instead.
> *Added in version 3.5.* 
#### void PyMem_Realloc(void p, size_t n)
*Part of the [[C API Stability|Stable ABI]]*.

Resizes the memory block pointed to by *p*, to *n* bytes. The contents will be unchanged to the minimum of the old and new sizes.

If *p* is `NULL`, the call is equivalent to `PyMem_Malloc(n)`; else if *n* is equal to zero, the memory block is resized but is not freed, and the returned pointer is non-`NULL`.

Unless *p* is `NULL`, it must have been returned by a previous call to [[Memory Management#Memory Interface#void PyMem_Malloc(size_t n)|PyMem_Malloc()]], [[Memory Management#Memory Interface#void PyMem_Realloc(void p, size_t n)|PyMem_Realloc()]] or [[Memory Management#Memory Interface#void PyMem_Calloc(size_t nelem, size_t elsize)|PyMem_Calloc()]].

If the request fails, [[Memory Management#Memory Interface#void PyMem_Realloc(void p, size_t n)|PyMem_Realloc()]] returns `NULL` and *p* remains a valid pointer to the previous memory area.
#### void PyMem_Free(void p)
*Part of the [[C API Stability|Stable ABI]]*.

Frees the memory block pointed to by *p*, which must have been returned by a previous call to [[Memory Management#Memory Interface#void PyMem_Malloc(size_t n)|PyMem_Malloc()]], [[Memory Management#Memory Interface#void PyMem_Realloc(void p, size_t n)|PyMem_Realloc()]] or [[Memory Management#Memory Interface#void PyMem_Calloc(size_t nelem, size_t elsize)|PyMem_Calloc()]]. Otherwise, or if `PyMem_Free(p)` has been called before, undefined behavior occurs.

If *p* is `NULL`, no operation is performed.
#### void PyObject_Malloc(size_t n)
*Part of the [[C API Stability|Stable ABI]].*
Allocates *n* bytes and returns a pointer of type **void**** to the allocated memory, or `NULL` if the request fails.

Requesting zero bytes returns a distinct non-`NULL` pointer if possible, as if `PyObject_Malloc(1)` had been called instead. The memory will not have been initialized in any way.
#### void PyObject_Calloc(size_t nelem, size_t elsize)
*Part of the [[C API Stability|Stable ABI]] since version 3.7.*
Allocates *nelem* elements each whose size in bytes is *elsize* and returns a pointer of type **void**** to the allocated memory, or `NULL` if the request fails. The memory is initialized to zeros.

Requesting zero elements or elements of size bytes returns a distinct non-`NULL` pointer if possible, as if `PyObject_Calloc(1, 1)` had been called instead.
> *Added in version 3.5.*

#### void PyObject_Realloc(void p, size_t n)
*Part of the [[C API Stability|Stable ABI]].*
Resizes the memory block pointed to by *p* to *n* bytes. The contents will be unchanged to the minimum of the old and the new sizes.

If *p* is `NULL`, the call is equivalent to `PyObject_Malloc(n)`; else if *n* is equal to zero, the memory block is resized but is not freed, and the returned pointer is non-`NULL`.

Unless *p* is `NULL`, it must have been returned by a previous call to [[Memory Management#void PyObject_Malloc(size_t n)|PyObject_Malloc()]], [[Memory Management#void PyObject_Realloc(void p, size_t n)|PyObject_Realloc()]] or [[Memory Management#void PyObject_Calloc(size_t nelem, size_t elsize)|PyObject_Calloc()]].

If the request fails, [[Memory Management#void PyObject_Realloc(void p, size_t n)|PyObject_Realloc()]] returns `NULL` and *p* remains a valid pointer to the previous memory area.
#### void PyObject_Free(void p)
*Part of the [[C API Stability|Stable ABI]].*
Frees the memory block pointed to by *p*, which must have been returned by a previous call to [[Memory Management#void PyObject_Malloc(size_t n)|PyObject_Malloc()]], [[Memory Management#void PyObject_Realloc(void p, size_t n)|PyObject_Realloc()]] or [[Memory Management#void PyObject_Calloc(size_t nelem, size_t elsize)|PyObject_Calloc()]]. Otherwise, or if `PyObject_Free(p)` has been called before, underfined behavior occurs.

If *p* is `NULL`, no operation is performed.
# Default Memory Allocators
Default memory allocators:

| Configuration                   | Name               | PyMem_RawMalloc  | PyMem_Malloc       | PyObject_Malloc    |
| ------------------------------- | ------------------ | ---------------- | ------------------ | ------------------ |
| Release build                   | `"pymalloc"`       | `malloc`         | `pymalloc`         | `pymalloc`         |
| Debug build                     | `"pymalloc_debug"` | `malloc` + debug | `pymalloc` + debug | `pymalloc` + debug |
| Release build, without pymalloc | `"malloc"`         | `malloc`         | `malloc`           | `malloc`           |
| Debug build, without pymalloc   | `"malloc_debug"`   | `malloc` + debug | `malloc` + debug   | `malloc` + debug   |
Legend:
- Name: value for [[1.2. Environment variables#PYTHONMALLOC|PYTHONMALLOC]] environment variable.

# Customize Memory Allocators
### PYMEM_DOMAIN_RAW
Functions:
- [[Memory Management#void PyMem_RawMalloc(size_t n)|PyMem_RawMalloc()]]
- [[Memory Management#void PyMem_RawRealloc(void p, size_t n)|PyMem_RawRealloc()]]
- [[Memory Management#Raw Memory Interface#void PyMem_RawCalloc(size_t, nelem, size_t elsize)|PyMem_RawCalloc()]]
- [[Memory Management#Raw Memory Interface#void PyMem_RawFree(void p)|PyMem_RawFree()]] 
### PYMEM_DOMAIN_MEM
Functions:
- [[Memory Management#Memory Interface#void PyMem_Malloc(size_t n)|PyMem_Malloc()]]
- [[Memory Management#Memory Interface#void PyMem_Realloc(void p, size_t n)|PyMem_Realloc()]]
- [[Memory Management#Memory Interface#void PyMem_Calloc(size_t nelem, size_t elsize)|PyMem_Calloc()]]
- [[Memory Management#Memory Interface#void PyMem_Free(void p)|PyMem_Free()]] 
### PYMEM_DOMAIN_OBJ
Functions:
- [[Memory Management#void PyObject_Malloc(size_t n)|PyObject_Malloc()]]
- [[Memory Management#void PyObject_Realloc(void p, size_t n)|PyObject_Realloc()]]
- [[Memory Management#void PyObject_Calloc(size_t nelem, size_t elsize)|PyObject_Calloc()]]
- [[Memory Management#void PyObject_Free(void p)|PyObject_Free()]] 
# Debug hooks on the Python memory allocators
When [[3.3.8. Python Debug Build|Python is built in debug mode]] 
# The pymalloc allocator
Python has a *pymalloc* allocator optimized for small objects (smaller or equal to 512 bytes) with a short lifetime. It uses memory mappings called "arenas" with a fixed size of either 256KiB on 32-bit platforms or 1 MiB on 64-bit platforms. It falls back to [[Memory Management#void PyMem_RawMalloc(size_t n)|PyMem_RawMalloc( )]] and [[Memory Management#void PyMem_RawRealloc(void p, size_t n)|PyMem_RawRealloc( )]] for allocations larger than 512 bytes.

*pymalloc* is the [[Memory Management#Default Memory Allocators|default allocator]] of the [[Memory Management#PYMEM_DOMAIN_MEM|PYMEM_DOMAIN_MEM]] (ex: [[Memory Management#void PyMem_Malloc(size_t n)|PyMem_Malloc( )]]) and [[Memory Management#PYMEM_DOMAIN_OBJ]] (ex: [[Memory Management#void PyObject_Malloc(size_t n)|PyObject_Malloc( )]]) domains.

The arena allocator uses the following functions:
- `VirtualAlloc()` and `VirtualFree()` on Windows,
- `mmap()` and `munmap()` if available,
- `malloc()` and `free()` otherwise.
This allocator is disabled if Python is configured with the [[3.3.7. Performance options#`--without-pymalloc`|--without-pymalloc]] option. It can also be disabled at runtime using the [[1.2. Environment variables#PYTHONMALLOC|PYTHONMALLOC]] environment variable (ex: `PYTHONMALLOC=malloc`).

Typically, it makes sense to disable the pymalloc allocator when building Python with AddressSanitizer ([[3.3.9 Debug options#`--with-address-sanitizer`|--with-address-sanitizer]]) which helps uncover low level bugs within the C code.
# The mimalloc allocator
> *Added in version 3.13.*

Python supports the mimalloc allocator when the underlying platform support is available. mimalloc "is a general purpose allocator with excellent performance characteristics. Initially developed by Daan Leijen for the runtime systems of the Koka and Lean languages."