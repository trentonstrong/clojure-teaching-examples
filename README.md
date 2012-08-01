# Example Problems for Teaching Functional Programming and Clojure

Beginner:
---------

Count a sequence
----------------
Questions:
* Design and write an imperative function which counts the number of elements in a sequence that are numerically less than 100.
* How can this function can be written in Clojure as the composition of pure functions?
* What are the advantages of this approach?
* What are its disadvantages?

Answer Guide:

* Imperative Style (Python) (*Note: This is only an example, not idiomatic Python which would be functional)

```python
def count_greater_than_100(sequence):
    count = 0
    for x in sequence:
        if x > 100:
            count = count + 1
    return count
```

* Functional approach using filter

```clojure
(defn count-greather-than-100
  [sequence]
  (count (filter #(> % 100) sequence)))
```

* Advantages:
  * composition of pure functions does not require handling mutable variable.  
  * if count mutable variable was in a shared context it's not safe for concurrent access.
  * functional version can be written so as to be re-usable with any predicate, not just x > 100 such as:

```clojure
(defn count-where
  [pred seq]
  (count (filter pred seq)))
```

* Disadvantages:
imperative version does not have any memory requirements other than the negligible accumulator and iterator index,
while the functional version creates a filtered copy of the sequence in order to perform the count.
this disadvantage is not actually reflected in reality however, since Clojure (like most other functional languages) optimizes
data structures to share memory in contexts like these.  A new array is not created by filter, only a new "view" onto that array,
made simpler because we can guarantee the sequence is immutable.



