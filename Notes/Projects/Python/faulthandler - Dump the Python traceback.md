> *Added in version 3.3.*

This module contains functions to dump Python tracebacks explicitly, on a fault, after a timeout, or on a user signal. Call [[faulthandler - Dump the Python traceback#`faulthandler.enable(file=sys.stderr, all_threads=True)|faulthandler.enable( )]] to install fault handlers for the [[signal - Set handlers for asynchronous events#`signal.SIGSEGV`|SIGSEGV]], [[signal - Set handlers for asynchronous events#`signal.SIGFPE`|SIGFPE]], [[signal - Set handlers for asynchronous events#`signal.SIGABRT`|SIGABRT]], [[signal - Set handlers for asynchronous events#`signal.SIGBUS`|SIGBUS]], and [[signal - Set handlers for asynchronous events#`signal.SIGILL`|SIGILL]] signals. You can also enable them at startup by setting the [[1.2. Environment variables#PYTHONFAULTHANDLER|PYTHONFAULTHANDLER]] environment variable or by using the [[1.1.3. Miscellaneous options#-X|-X]] `faulthandler` command line option.

The fault handler is compatible with system faults handlers like Apport or the Windows fault handler. The module uses an alternative stack for signal handlers if the `sigaltstack()` function is available. This allows it to dump the traceback even on a stack overflow.

The fault handler is called on catastrophic cases and therefore can only use signal-safe functions (e.g. it cannot allocate memory on the heap). Because of this limitation traceback dumping is minimal compared to normal Python tracebacks:
- Only ASCII is supported. The `backslashreplace` error handler is used on encoding.
- Each string is limited to 500 characters.
- Only the filename, the function name and the line number are displayed. (no source code)
- It is limited to 100 frames and 100 threads.
- The order is reversed: the most recent call is shown first.
By default, the Python traceback is written to [[sys.stderr]]. To see tracebacks, applications must be run in the terminal. A log file can alternatively be passed to [[#`faulthandler.enable(file=sys.stderr, all_threads=True)`|faulthandler.enable( )]].

The module is implemented in C, so tracebacks can be dumped on a crash or when Python is deadlocked.

The [[Python Development Mode]] calls [[#`faulthandler.enable(file=sys.stderr, all_threads=True)`|faulthandler.enable( )]] at Python startup.
## Fault handler state
#### `faulthandler.enable(file=sys.stderr, all_threads=True)`
Enable the fault handler: install handlers for the  [[signal - Set handlers for asynchronous events#`signal.SIGSEGV`|SIGSEGV]], [[signal - Set handlers for asynchronous events#`signal.SIGFPE`|SIGFPE]], [[signal - Set handlers for asynchronous events#`signal.SIGABRT`|SIGABRT]], [[signal - Set handlers for asynchronous events#`signal.SIGBUS`|SIGBUS]] and [[signal - Set handlers for asynchronous events#`signal.SIGILL`|SIGILL]] signals to dump the Python traceback. If *all_threads* is `True`, produce tracebacks for running thread. Otherwise, dump only the current thread.

The *file* must be kept open until the fault handler is disabled: see [[#Issue with file descriptors|issue with file descriptors]].
> *Changed in version 3.5*: Added support for passing file descriptor to this function.

> *Changed in version 3.6*: On Windows, a handler for Windows exception is also installed.

> *Changed in version 3.10*: The dump now mentions if a garbage collector collection is running if *all_threads* is true.

## Issue with file descriptors
[[#`faulthandler.enable(file=sys.stderr, all_threads=True)`|enable( )]],