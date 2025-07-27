# Before Python Initialization

#### void Py_Initialize()
*Part of the [[C API Stability|Stable ABI]]*.

Initialize the Python Interpreter. In an application embedding Python, this should be called before using any other Python/C API functions; see [[#Before Python Initialization|Before Python Initialization]]