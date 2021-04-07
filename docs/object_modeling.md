# Object Modeling

---

**Techniques**

- [Mixins and Traits](./mixins.md)

## Classes

### Vanila Clases

```python
class Zombie:
  def __init__(self, speed: int) -> None:
    self._walking_speed = speed
```

### With Type Annotations

- [Python Property](https://docs.python.org/3/library/functions.html#property)
- [Stack Overflow Explaination](https://stackoverflow.com/questions/17330160/how-does-the-property-decorator-work-in-python)
- Note: In the REPL, see help(property)

```python
class Zombie:
  def __init__(self, speed: int):
    self._walking_speed = speed

  @property
  def walking_speed(self) -> int:
    """Getter for walking speed."""
    return self._walking_speed

  @walking_speed.setter
  def walking_speed(self, speed: int) -> None:
    """Setter for walking speed."""
    self._walking_speed = speed
```

### Data Classes

- Added in v3.7.
- Uses type annotations.
- @dataclass generates boiler plate class code on the fly.
- Default is mutable objects. Can make immutable with @dataclass(frozen=True)
- @dataclass(order=True) will add comparison functions that enable sorting and use in data structures like dictionaries and sets.
- The dataclass.field function can be used to specify behaviors per field at run time. For example a field can be specified to not be used in the hash method implementation.
- [The Docs](https://docs.python.org/3/library/dataclasses.html)
- [Deep Dive Talk](https://www.youtube.com/watch?v=T-TwcmT6Rcw)

```python
from dataclasses import dataclass

@dataclass
class Zombie:
  speed: int
  food: str = "brains" # Default Value

z = Zombie(5)
y = Zombie(10, "pasta")
print(z.speed) # Prints: 5
z.speed = 6
print(z.speed) # Prints: 6

@dataclass(frozen=True)
class FrozenZombie:
  speed: int
  food: str

f = FrozenZombie(5, 'brains')
print(f.speed) #prints 5
f.speed = 6 #Throws dataclasses.FrozenInstanceError: cannot assign to field 'speed'
```

## Tuples

### Basic Tuples

- Immutable
- Native Data Type
- Access attributes via position index.
- Syntax is similar to lists.
- [Tuple Tutorial](https://realpython.com/python-lists-tuples/#python-tuples)

```python
from enum import Enum

class ZombieProps(Enum):
  SPEED = 0
  FOOD = 1

zombie = (5, 'brains')
# Fetch individual tuple values with positional index.
speed = zombie[ZombieProps.SPEED.value]
food = zombie[ZombieProps.FOOD.value]

# Can unpack a tuple into variables in a single line.
(s, f) = zombie
```

### Named Tuples

- Immutable
- Access properties with named attributes
- Syntax is similar to classes.

```python
from typing import NamedTuple
class Zombie(NamedTuple):
  speed: int
  food: str

z = Zombie(5,'brains')
s = z.speed
```

## Dictionaries

- Larger memory overhead than tuples because of attribute name storage.
- Mutable.

```python
zombie = {
  "speed": 5, "food": "brains"
}
s = zombie.get("speed")
```
