# 🗺️ `Map` interface


## 🧱 1. What Is a `Map`?

A **`Map`** stores **key–value pairs**.  
Each **key** is unique and maps to **exactly one value**.

Think of it like a dictionary:
- **Key** → Word  
- **Value** → Definition  

Or a student database:
- **Key** → Student ID  
- **Value** → Student Name  

```java
Map<Integer, String> students = new HashMap<>();
students.put(101, "Alice");
students.put(102, "Bob");
```
| Method                        | Description                       | Example                                  |
| ----------------------------- | --------------------------------- | ---------------------------------------- |
| `put(K key, V value)`         | Adds or replaces a key–value pair | `map.put(1, "A")`                        |
| `get(Object key)`             | Retrieves value by key            | `map.get(1)`                             |
| `remove(Object key)`          | Removes entry                     | `map.remove(2)`                          |
| `containsKey(Object key)`     | Checks if key exists              | `map.containsKey(1)`                     |
| `containsValue(Object value)` | Checks if value exists            | `map.containsValue("A")`                 |
| `keySet()`                    | Returns all keys                  | `for(Integer k : map.keySet())`          |
| `values()`                    | Returns all values                | `for(String v : map.values())`           |
| `entrySet()`                  | Returns key–value pairs           | `for(Map.Entry<K,V> e : map.entrySet())` |



## 🧱 Main Implementations Overview

| Implementation | Ordered? | Sorted? | Allows nulls? | Typical Use |
|----------------|-----------|----------|----------------|--------------|
| **HashMap** | ❌ No | ❌ No | ✅ Yes | Fast lookups and general-purpose mapping |
| **LinkedHashMap** | ✅ Insertion order | ❌ No | ✅ Yes | Maintain insertion order (predictable iteration) |
| **TreeMap** | ✅ Yes | ✅ By key | ❌ No | Keep keys sorted (natural or custom order) |


## 🔹 1️⃣ HashMap

- The most commonly used `Map` implementation.
- Constant-time performance on most operations - fast.
- Does **not** guarantee any order of keys or values.

## 🔹 2️⃣ LinkedHashMap

- Extends HashMap but maintains a linked list of entries in insertion order.

- Iteration order = the order in which keys were inserted.

- Slightly slower than HashMap, but predictable.

## 🔹 3️⃣ TreeMap

- Stores entries in a sorted order based on keys.

- Uses a Red–Black tree internally.

- Does not allow null keys (throws NullPointerException).

# Internal Structure of HashMap

- Uses an **array of buckets**
- Each bucket can hold **one or more entries** (linked list or tree)

```
Array (buckets):
Index 0 → empty
Index 1 → [Key1=Value1] → [Key5=Value5]  (linked list for collisions)
Index 2 → [Key2=Value2]
Index 3 → empty
```

- `hashCode()` → determines **bucket index**
- `equals()` → determines the **correct key** in the bucket

---

## Why Two Methods?

### Step 1: Locate bucket → `hashCode()`
- Quickly narrows down candidate location
- Avoids scanning all entries

### Step 2: Verify equality → `equals()`
- Handles collisions in the bucket
- Confirms logical equality

**Analogy:**

- `hashCode()` = street number  
- `equals()` = person’s name  

---

## Example with Custom Key

```java
class Student {
    int id;
    String name;

    @Override
    public boolean equals(Object o) {
        if (!(o instanceof Student)) return false;
        return id == ((Student) o).id;
    }

    @Override
    public int hashCode() {
        return Integer.hashCode(id);
    }
}

Map<Student, String> map = new HashMap<>();
map.put(new Student(1, "Alice"), "A");

System.out.println(map.get(new Student(1, "Alice"))); // "A" ✅
```

- Without `hashCode()` → `get()` returns `null`  
- Without `equals()` → logical equality fails  

---

## Collisions and Linked Lists

- Multiple keys may hash to the **same bucket**
- Stored as **linked list** or **tree** (Java 8+ Treeify large buckets)
- Lookup in the bucket uses `equals()`  

```
Bucket 1 → [Key1=Value1] → [Key5=Value5] → [Key9=Value9]
```


---

## Array Growth (Resize)

- `HashMap` has **capacity** and **load factor** (default 0.75)
- Threshold = `capacity * load factor`
- When entries exceed threshold → array **doubles** → entries **rehash-distributed**

