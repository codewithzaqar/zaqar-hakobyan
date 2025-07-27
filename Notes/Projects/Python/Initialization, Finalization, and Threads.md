See [[Python Initialization Configuration]] for details on how to configure the interpreter prior to initialization.
# Before Python Initialization

#### void Py_Initialize()
*Part of the [[C API Stability|Stable ABI]]*.

Initialize the Python Interpreter. In an application embedding Python, this should be called before using any other Python/C API functions; see [[#Before Python Initialization|Before Python Initialization]]

#### Py_InitializeFromConfig(const PyConfig config)
Initialize Python from *config* configuration, as described in [[Python Initialization Configuration|Initialization with PyConfig]].

See the [[Python Initialization Configuration]] section for details on pre-initalizing the interpreter, populating the runtime configuration structure, and querying the returned status structure.