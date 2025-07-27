> *Added in version 3.8*.

Python can be initialized with [[Initialization, Finalization, and Threads#Before Python Initialization#Py_InitializeFromConfig(const PyConfig config)|Py_InitializeFromConfig()]] and the [[Python Initialization Configuration#type PyConfig|PyConfig]] structure.

#### int allocator
Name of the Python memory allocators:
- `PYMEM_ALLOCATOR_NOT_SET`(0): don't change memory allocators (use defaults).
- `PYMEM_ALLOCATOR_DEFAULT` (1): [[Memory Management#Default Memory Allocators|default memory allocators]] 

# Preinitialize Python with PyPreConfig
The preinitialization of Python:
- Set the Python memory allocators ([[Python Initialization Configuration#int allocator|PyPreConfig.allocator]])
# Initialization with PyConfig
Initializing the interpreter from a populated configuration struct is handled by calling [[Initialization, Finalization, and Threads#Py_InitializeFromConfig(const PyConfig config)|Py_InitializeFromConfig()]].

#### type PyConfig
Structure containing most parameters to configure Python.

When done, the [[Python Initialization Configuration#void PyConfig_Clear(PyConfig config)|PyConfig_Clear()]] function must be used to release the configuration memory.

Structure methods:
#### void PyConfig_Clear(PyConfig config)
Release configuration memory.

Most `PyConfig` methods [[]]