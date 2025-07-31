> *Added in version 3.7.*

The Python Development Mode introduces additional runtime checks that are too expensive to be enabled by default. It should not be more verbose than the default if the code is correct; new warnings are only emitted when an issue is detected.

It can be enabled using  the [[1.1.3. Miscellaneous options#-X|-X dev]] command line option or by setting the [[1.2. Environment variables#PYTHONDEVMODE|PYTHONDEVMODE]] environment variable to `1`.

See also [[3.3.8. Python Debug Build|Python Debug Build]] 