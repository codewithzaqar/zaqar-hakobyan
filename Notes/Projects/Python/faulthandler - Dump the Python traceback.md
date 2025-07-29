> *Added in version 3.3.*

This module contains functions to dump Python tracebacks explicitly, on a fault, after a timeout, or on a user signal. Call [[faulthandler - Dump the Python traceback#`faulthandler.enable(file=sys.stderr, all_threads=True)|faulthandler.enable( )]]  
# Fault handler state
#### `faulthandler.enable(file=sys.stderr, all_threads=True)`
Enable the fault handler: install handlers for the  [[signal - Set handlers for asynchronous events#`signal.SIGSEGV`|SIGSEGV]], 