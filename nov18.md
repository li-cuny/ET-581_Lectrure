# Stream API

##  Loops

- Traditional loops (`for`, `while`) are **imperative** → tell the computer *how* to do something.
- Streams are **declarative** → tell the computer *what* you want.
- Streams allow **pipeline processing**, lazy evaluation, and more readable code.

**Example:**

```java
// Imperative
List<String> names = Arrays.asList("Alice", "Bob", "Charlie");
List<String> shortNames = new ArrayList<>();
for(String name : names){
    if(name.length() <= 3){
        shortNames.add(name);
    }
}

// Declarative using Streams
List<String> shortNames2 = names.stream()
                                .filter(n -> n.length() <= 3)
                                .collect(Collectors.toList());
```

---

## Stream Basics

- **Stream sources:** collections (List, Set), arrays, I/O channels, generator functions.  
- **Intermediate operations:** transform/filter data → return Stream  
  - Examples: `filter()`, `map()`, `sorted()`, `distinct()`  
- **Terminal operations:** produce a result → end pipeline  
  - Examples: `collect()`, `forEach()`, `count()`, `reduce()`  
- Streams **cannot be reused** after a terminal operation.

---

## Simple Pipeline Example

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);

int sumOfEvenSquares = numbers.stream()
                              .filter(n -> n % 2 == 0)
                              .map(n -> n * n)
                              .reduce(0, Integer::sum);

System.out.println(sumOfEvenSquares); // Output: 20
```

---

## Collectors

- Collect results from streams:

```java
List<String> names = Arrays.asList("Alice", "Bob", "Charlie");

List<String> filteredNames = names.stream()
                                  .filter(n -> n.startsWith("A"))
                                  .collect(Collectors.toList());

System.out.println(filteredNames); // [Alice]
```

- Common collectors: `toSet()`, `toMap()`, `joining()`, `groupingBy()`, `partitioningBy()`.

---

## Parallel Streams

- For parallel processing:

```java
int sum = numbers.parallelStream()
                 .mapToInt(Integer::intValue)
                 .sum();
```

- Use only for CPU-intensive operations or large datasets.

---

## 💡Intermediate operations Tips 

- **Intermediate operations** return a new stream and are **lazy**; nothing happens until a terminal operation is invoked.  
- You can chain multiple intermediate operations to create a **pipeline**.  
- Use `peek()` for debugging to inspect elements without modifying them.  

---

## 💡 Terminal Operation Tips

- Terminal operations **end the stream pipeline**; the stream cannot be reused.  
- Use **forEach()** for side effects, **collect()** or **reduce()** for results.  
- Combine with intermediate operations (`filter`, `map`) to manipulate data before terminal operations.  
- `Optional` results from `findFirst()` / `findAny()` help avoid `NullPointerException`.  

---

# Java Stream API – Intermediate Operations

## Intermediate Operations Table (Quick Reference)

| Intermediate Operation | Purpose / Description | Example |
|------------------------|--------------------|---------|
| **filter()** | Filters elements based on a predicate. | `names.stream().filter(n -> n.length() <= 3)` |
| **map()** | Transforms each element into another object/value. | `names.stream().map(String::length)` |
| **flatMap()** | Flattens a stream of collections/arrays into a single stream. | `listOfLists.stream().flatMap(List::stream)` |
| **distinct()** | Removes duplicate elements. | `numbers.stream().distinct()` |
| **sorted()** | Sorts elements. | `names.stream().sorted()` |
| **peek()** | Performs an action on each element (for debugging). | `names.stream().peek(System.out::println)` |
| **limit()** | Limits the stream to first N elements. | `names.stream().limit(2)` |
| **skip()** | Skips first N elements. | `names.stream().skip(1)` |


---

# Java Stream API – Terminal Operations

## Terminal Operations Table (Quick Reference)

| Terminal Operation | Purpose / Description | Example |
|-------------------|--------------------|---------|
| **forEach()** | Performs an action on each element. Side-effect operation, returns void. | `names.stream().forEach(System.out::println)` |
| **collect()** | Converts the stream into a collection or other structure. Produces a result. | `names.stream().filter(n -> n.startsWith("A")).collect(Collectors.toList())` |
| **count()** | Counts the number of elements in the stream. | `names.stream().filter(n -> n.length() > 3).count()` |
| **reduce()** | Combines elements into a single value using an accumulator function. | `nums.stream().reduce(0, Integer::sum)` |
| **findFirst()** | Returns an `Optional` containing the first element matching criteria. | `names.stream().filter(n -> n.length() > 3).findFirst()` |
| **findAny()** | Returns an `Optional` containing any element matching criteria. | `names.parallelStream().filter(n -> n.length() > 3).findAny()` |
| **anyMatch()** | Returns `true` if any element matches the condition. | `names.stream().anyMatch(n -> n.length() > 5)` |
| **allMatch()** | Returns `true` if all elements match the condition. | `names.stream().allMatch(n -> n.startsWith("A"))` |
| **noneMatch()** | Returns `true` if no elements match the condition. | `names.stream().noneMatch(String::isEmpty)` |
| **joining()** | Concatenates all string elements in the stream (optional delimiter/prefix/suffix). | `names.stream().collect(Collectors.joining(", "))` |

---
