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
def count_greater_than_100(sequence):
    count = 0
    for x in sequence:
        if x > 100:
            count = count + 1
    return count
```

2. Functional approach using filter

```clojure
(defn count-greather-than-100
  [sequence]
  (count (filter #(> % 100) sequence)))
```

3. 
  1. composition of pure functions does not require handling mutable variable.  
  2. if count mutable variable was in a shared context it's not safe for concurrent access.
  3. functional version can be written so as to be re-usable with any predicate, not just x > 100 such as:

```clojure
(defn count-where
  [pred seq]
  (count (filter pred seq)))
```



