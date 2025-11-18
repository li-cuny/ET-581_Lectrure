# Java Stream API 
## 1. Why Streams? 

### 🔹 Imperative vs Declarative
- **Imperative (loops):** You tell *how* to do the work  
- **Declarative (streams):** You describe *what* you want  

```java
// Imperative
List<String> names = Arrays.asList("Alice", "Bob", "Charlie");
List<String> shortNames = new ArrayList<>();
for (String name : names) {
    if (name.length() <= 3) {
        shortNames.add(name);
    }
}
```

```java
// Declarative – Stream API
List<String> shortNames2 = names.stream()
                                .filter(n -> n.length() <= 3)
                                .collect(Collectors.toList());
```

---

## 2. What Streams Are 

- A **Stream** represents a sequence of data  
- Supports **pipeline processing**  
- **Intermediate operations** → transform data  
- **Terminal operations** → produce result  
- Streams are **lazy**  
- Streams **cannot be reused**

---

## 3. Creating Streams (Stream Sources)

Top 5 most used methods:

### 1. From a Collection
```java
list.stream();
```

### 2. From an Array
```java
Arrays.stream(array);         // Stream<T>
Arrays.stream(intArray);      // IntStream
```

### 3. From Values
```java
Stream.of("A", "B", "C");
Stream.of(1, 2, 3);
```

### 4. From File Lines
```java
Files.lines(Path.of("data.txt"));
```

### 5. Infinite Streams
```java
Stream.generate(Math::random);
Stream.iterate(0, n -> n + 1);
```

---

## 4. Building a Pipeline (Simple Example)

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);

int sumOfEvenSquares = numbers.stream()
                              .filter(n -> n % 2 == 0)
                              .map(n -> n * n)
                              .reduce(0, Integer::sum);

System.out.println(sumOfEvenSquares); // 20
```

---

## 5. Intermediate Operations (Transforming Data)

### 💡 Tips
- Intermediate operations are **lazy**
- They return a **new stream**
- Used in **chains**
- Use `peek()` for debugging

### Intermediate Operations Table

| Intermediate Operation | Purpose / Description | Example |
|------------------------|------------------------|---------|
| **filter()** | Filters elements based on predicate | `filter(n -> n.length() <= 3)` |
| **map()** | Transforms each element | `map(String::length)` |
| **flatMap()** | Flattens nested streams | `flatMap(List::stream)` |
| **distinct()** | Removes duplicates | `distinct()` |
| **sorted()** | Sorts elements | `sorted()` |
| **peek()** | Debugging | `peek(System.out::println)` |
| **limit()** | Take first N elements | `limit(2)` |
| **skip()** | Skip first N elements | `skip(1)` |

---

## 6. Terminal Operations (Producing Final Result)

### 💡 Tips
- Terminal operations **end** the stream  
- The stream **cannot be reused**  
- Use `collect()` or `reduce()` for real results  
- `findFirst()` / `findAny()` return `Optional`

### Terminal Operations Table

| Terminal Operation | Purpose / Description | Example |
|-------------------|------------------------|---------|
| **forEach()** | Performs an action | `forEach(System.out::println)` |
| **collect()** | Converts to list/set/map | `collect(Collectors.toList())` |
| **count()** | Counts elements | `count()` |
| **reduce()** | Combines values | `reduce(0, Integer::sum)` |
| **findFirst()** | First matching element | `findFirst()` |
| **findAny()** | Any matching element (parallel friendly) | `findAny()` |
| **anyMatch()** | Any element matches | `anyMatch(n -> n > 5)` |
| **allMatch()** | All match | `allMatch(n -> n.startsWith("A"))` |
| **noneMatch()** | None match | `noneMatch(String::isEmpty)` |
| **joining()** | Concatenate strings | `collect(Collectors.joining(", "))` |

---

## 7. Collectors (Working with Results)

```java
List<String> names = Arrays.asList("Alice", "Bob", "Charlie");

List<String> filteredNames = names.stream()
                                  .filter(n -> n.startsWith("A"))
                                  .collect(Collectors.toList());
```

Common collectors:
- `toList()` / `toSet()`
- `toMap()`
- `joining()`
- `groupingBy()`
- `partitioningBy()`

---

## 8. Parallel Streams (Advanced)

```java
int sum = numbers.parallelStream()
                 .mapToInt(Integer::intValue)
                 .sum();
```

Use parallel streams when:
- Dataset is **large**
- Operations are **CPU-intensive**
