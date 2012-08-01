# Example Problems for Teaching Functional Programming and Clojure

Beginner:
---------

Count a sequence
----------------
Questions:
1. Design and write an imperative function which counts the number of elements in a sequence that are numerically less than 100.
2. How can this function can be written in Clojure as the composition of pure functions?
3. What are the advantages of this approach?
4. What are its disadvantages?

Answer Guide:

1. Imperative Style (Python) (*Note: This is only an example, not idiomatic Python which would be functional)

```python
def count_greater_100(sequence):
    count = 0
    for x in sequence:
        if x > 100:
            count = count + 1
    return count
```




