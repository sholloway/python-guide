# Functions, Generators, and List Comprehensions

---

## Functions

## Generators

Generators are special objects.

### Generator Functions

#### Communicating with the Yield Expression

Generator functions look and behave just like traditional Python functions except
that they use the _yield_ keyword insted of retun.
Unlike _return_, a generator does not exit the function when _yield_ is called.
Rather, _yield_ is used to send data back to the function caller. When this happens
the state of the function is tracked. When next() is called on the generator object
the generator continues.

```python
def my_gen():
  yield "Yielded Once"
  yield "Yielded Twice"
  yield "Yielded Three Times"

gen = my_gen()
try:
  print(next(gen)) #Yielded Once
  print(next(gen)) #Yielded Twice
  print(next(gen)) #Yielded Three Times
  print(next(gen)) #Thows StopIteration
catch StopIteration:
  print("All Done")
```

#### Communicating with Generator.send()

The calling function can send data to the generator with the _send_ method.

```python

def ping():
  while True:
    pong = (yield "ping")
    print(f"In ping(): {pong}")
    if pong == "stop":
      break;

p = ping()
count = 0
for msg in p: # calling next()
  # print(f"In For Loop: {msg}")
  msg = "more" if count < 10 else "stop"
  count = count + 1
  p.send(msg) # Send also progresses the generator like calling next()
```

#### Stopping a Generator

A generator can be explicitly stopped by either having it throw an exception
or closing it.

```python
#Stopping a generator by throwing an exception.
p = ping()
for msg in p:
  p.throw(Exception())
```

```python
# Closing a generator
p = ping()
for msg in p:
  p.close() # Raises StopIteration
```

### Generator Expressions

Generator expressions are similar to list comprehensions. They enable defining a
generator objects with a single expression. The expression is assumed to invoke _yield_
at the end of every line.

```python
# Create a generator that returns the current value of x in the range of 0 to 10.
a_generator = (x for x in range(10))
next(a_generator) # returns 0
next(a_generator) # returns 1
next(a_generator) # returns 2
```

### Generator Typing

According to the [docs](https://docs.python.org/3/library/typing.html?highlight=generator#typing.Generator)
Generators have the type typing.Generator. The type has the pattern Generator[YieldType, SendType, ReturnType].

## List Comprehensions
