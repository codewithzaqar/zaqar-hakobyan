**Source code**: [Lib/warnings.py](https://github.com/python/cpython/blob/3.13/Lib/warnings.py)
___
Warning messages are typically issued in situations where it is useful to alert the user of some condition in a program, where that condition (normally) doesn't warrant raising an exception and terminating the program. For example, one might want to issue a warning when a program uses an obsolete module.

Python programmers issue warnings by calling the [[warnings - Warning control#warnings.warn(*message*, *category=None*, *stacklevel=1*, *source=None*, skip_file_prefixes=())|warn( )]]
# Warning Categories
There are a number of built-in exceptions that represent warning categories. This categorization is useful to be able to filter out groups of warnings.

While these are technically [[Build-in Exceptions|built-in exceptions]], they are documented here, because conceptually they belong to the warnings mechanism.

User code can define additional warning categories by subclassing one of the standard warning categories. A warning category must always be a subclass of the [[Build-in Exceptions#*exception* `Warning`|Warning]] class.

The following warnings category classes are currently defined:

# Available Functions
#### warnings.warn(*message*, *category=None*, *stacklevel=1*, *source=None*, skip_file_prefixes=())
Issue a warning, or maybe ignore it or raise an exception. The *category* argument, if given, must be a [[warnings - Warning control#Warning Categories|Warning Categories]]
