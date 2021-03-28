# Mixins

---

A technique for object composition is _Mixins_.

## The Concept

Deconstruct reusable functionality into a series of classes that cannot be
instantiated on their own. These clases can then be "mixed into" a class
that needs to include that functionality.

```python
class Walker:
  def walk(self):
    print("Walking")

class BrainEater:
  def eat(self, brains):
    print("yum...")

class WhiteWalker(Walker, BrainEater):
  pass

zombie = WhiteWalker()
zombie.walk()
zombie.eat("tasty brains")
```

## Handling Name Collision
Order mixins by highest importance to lowest from left to right.
```python
class Fast:
  def move(self):
    print("Running. Gonna getcha...")

class Slow:
  def move(self):
    print("Walking. Please slow down.")

class FastZombie(Fast, Slow):
  pass

class SlowZombie(Slow, Fast):
  pass

romero = SlowZombie()
romero.move()
# Prints "Walking. Please slow down."

boyle = FastZombie()
boyle.move()
# Prints "Running. Gonna getcha..."
```