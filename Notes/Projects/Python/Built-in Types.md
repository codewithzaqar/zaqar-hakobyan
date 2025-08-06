### Lists

Lists are mutable sequences, typically used to store collections of homogeneous items (where the precise degree of similarity will vary by application).

#### *class* `list([iterable])`
Lists may be constructed in several ways:

- Using a pair of square brackets to denote the empty list: `[]` 
- Using square brackets, separating items with commas: `[a]`, `[a, b, c]`
- Using a list comprehension: `[x for x in iterable]`
- Using the type constructor: `list()` or `list(iterable)`

The constructor builds a list whose items are the same and in the same order as *iterable*'s items. *iterable* may be either a sequence, a container that supports iteration, or an iterator object. If *iterable* is already a list, a copy is made and returned, similar to `iterable[:]`. For example, `list('abc')` returns `['a', 'b', 'c']` and `list( (1, 2, 3) )` returns `[1, 2, 3]`. If no argument is given, the constructor creates a new empty list, `[]`.

May other operations also produce lists, including the [[Built-in Functions#`sorted(iterable, /, *, key=None, reverse=False)`|sorted( )]] built-in.

List implement all of the [[common]] and [[mutable]] sequence operations. Lists also provide the following additional method: