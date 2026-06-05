# OrderedSet

A lightweight and efficient implementation of an **Ordered Set** for Python.

`OrderedSet` combines the uniqueness guarantees of a `set` with the insertion-order preservation of a `list`.

## Why OrderedSet?

Python provides:

* `set` → unique elements, no guaranteed ordering semantics
* `list` → ordered elements, allows duplicates
* `dict` → preserves insertion order, but is designed for key-value mappings

Many applications need a collection that:

* Preserves insertion order
* Prevents duplicates
* Provides O(1) membership checks
* Supports efficient insertion and deletion

`OrderedSet` fills this gap.

## Features

* Preserve insertion order
* Enforce element uniqueness
* O(1) average-case lookup
* O(1) average-case insertion
* O(1) average-case deletion
* Iterable
* Pythonic API
* Lightweight implementation

## Installation

```bash
pip install orderedset
```

## Quick Start

```python
from orderedset import OrderedSet

s = OrderedSet()

s.add("A")
s.add("B")
s.add("A")

print(s)
```

Output:

```python
OrderedSet(['A', 'B'])
```

## Creating an OrderedSet

```python
s = OrderedSet(["A", "B", "C"])
```

Duplicate values are automatically ignored:

```python
s = OrderedSet(["A", "B", "A", "C"])

print(s)
```

Output:

```python
OrderedSet(['A', 'B', 'C'])
```

## Membership Testing

```python
"A" in s
```

Returns:

```python
True
```

## Iteration

```python
for item in s:
    print(item)
```

Output:

```python
A
B
C
```

## Length

```python
len(s)
```

Returns:

```python
3
```

## Remove Elements

```python
s.remove("A")
```

Raises `KeyError` if the element does not exist.

## Discard Elements

```python
s.discard("A")
```

Does nothing if the element does not exist.

## Pop Operations

Remove and return the first inserted element:

```python
s.pop_first()
```

Remove and return the most recently inserted element:

```python
s.pop_last()
```

## Set Operations

### Union

```python
s1 | s2
```

### Intersection

```python
s1 & s2
```

### Difference

```python
s1 - s2
```

## Example

```python
s1 = OrderedSet(["A", "B"])
s2 = OrderedSet(["B", "C"])

print(s1 | s2)
```

Output:

```python
OrderedSet(['A', 'B', 'C'])
```

## Complexity

| Operation | Complexity |
| --------- | ---------- |
| add       | O(1)       |
| remove    | O(1)       |
| discard   | O(1)       |
| contains  | O(1)       |
| iteration | O(n)       |
| len       | O(1)       |

## Implementation

The current implementation is built on top of Python's insertion-ordered dictionary, allowing the data structure to provide both ordering guarantees and efficient lookups.

Internally:

```python
{
    "A": None,
    "B": None,
    "C": None
}
```

The dictionary keys represent the set elements while the values are ignored.

## Motivation

Developers frequently write code such as:

```python
unique_items = list(dict.fromkeys(items))
```

or

```python
seen = set()
result = []

for item in items:
    if item not in seen:
        seen.add(item)
        result.append(item)
```

These patterns indicate a need for an ordered set abstraction.

This project aims to provide a clean, explicit, and Pythonic solution.

## Roadmap

* [ ] Core OrderedSet implementation
* [ ] Full test coverage
* [ ] Type hints
* [ ] Set algebra operators
* [ ] Benchmark suite
* [ ] Custom hash-table implementation
* [ ] PyPI release
* [ ] Documentation website

## Contributing

Contributions, feature requests, and bug reports are welcome.

Please open an issue or submit a pull request.

## License

MIT License
