# Snake Equality

Here your goal is for this to be true:

```python
# From server.py
...

if n is ord(c) and n+1 is not ord(c) + 1:

...
```

### About the `is` operator

It compares two variable and returns true only if they allocate the same memory address.

However, if you try the following:
```python
1 is 1
```
It will still return true, even though they are initialized separately.

This is because [Python caches small numbers](https://stackoverflow.com/a/133024/12826774), which is the key to solving this challenge.

### Solving it

If we choose `n` to be [the largest number that Python will still cache](https://stackoverflow.com/a/15172182/12826774), while `n is ord(c)` will still be true, `n+1` and `ord(c) + 1` will not have the same address.

### Demonstration

```python
n = 256
c = "Ā" # U+0100, 0100 being 256 in hexadecimal

if  n    is    ord(c)    and    n+1    is not    ord(c) + 1:
# ⇒256      ⇒ord("Ā")       ⇒256+1          ⇒ord("Ā") + 1
#    ⋮        ⇒256            ⇒257            ⇒256 + 1
#    ⋮           ⋮                 ⋮             ⇒257
# ⇒≤256     ⇒≤256           ⇒>256           ⇒>256
# ⇒Cached   ⇒Cached         ⇒Not cached     ⇒Not cached
```
