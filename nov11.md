# Java Collections: Set Interface


## 1️⃣ What is a Set?

- `Set` is a **Collection that contains no duplicate elements**.  
- It **extends the Collection interface**, so it has all the Collection methods.
- **Key difference from List/ArrayList:**
  - No duplicates allowed
  - No index-based access
  - Ordering depends on implementation

---

## 2️⃣ Common Set Implementations

| Class | Order | Notes |
|-------|-------|------|
| `HashSet` | Unordered | Fast, allows one `null` |
| `LinkedHashSet` | Insertion order | Preserves order of insertion |
| `TreeSet` | Sorted | Natural ordering or via Comparator, **no null allowed** |

---

## 3️⃣ Key Methods (Inherited from Collection)

| Method | Behavior in Set |
|--------|----------------|
| `add(E e)` | Adds element **only if not already present** |
| `remove(Object o)` | Removes element |
| `contains(Object o)` | Checks if element exists |
| `iterator()` | Returns iterator, order depends on Set type |
| `addAll(Collection<? extends E> c)` | Adds **only unique** elements from another collection |
| `clear()` | Removes all elements |
| `size()` | Number of elements |

---

## 4️⃣ Example: Set vs List

```java
import java.util.*;

public class SetExample {
    public static void main(String[] args) {
        List<String> list = new ArrayList<>();
        list.add("Apple");
        list.add("Apple"); // duplicate allowed

        Set<String> set = new HashSet<>();
        set.add("Apple");
        set.add("Apple"); // duplicate ignored

        System.out.println("List: " + list); // [Apple, Apple]
        System.out.println("Set: " + set);   // [Apple]
    }
}


# Collection :  Queue

A **Queue** is a collection designed for **holding elements before
processing**.\
It follows the **FIFO (First In, First Out)** principle --- the first
element added is the first removed.

### 💡 Real-life Analogy

Think of a line at a ticket counter --- the person who comes first gets
served first.

------------------------------------------------------------------------

##  Queue Interface Declaration

``` java
public interface Queue<E> extends Collection<E>
```

This means: - A `Queue` is a **subinterface of Collection**\
- It adds **extra methods** for queue-style insertion, removal, and
inspection

------------------------------------------------------------------------

## Common Implementations

  -----------------------------------------------------------------------
  Class                     Description
  ------------------------- ---------------------------------------------
  `LinkedList`              Doubly-linked structure, allows `null`
                            elements

  `PriorityQueue`           Orders elements by priority (natural order or
                            comparator)

  `ArrayDeque`              Array-based, faster than LinkedList, does
                            **not** allow `null`
  -----------------------------------------------------------------------

------------------------------------------------------------------------

## 🧠 4️⃣ Core Queue Methods

  --------------------------------------------------------------------------
  Method         Description         Behavior When Empty / Full
  -------------- ------------------- ---------------------------------------
  `offer(E e)`   Adds element to the Returns `false` if fails
                 queue               

  `add(E e)`     Adds element to the Throws exception if fails
                 queue               

  `poll()`       Removes and returns Returns `null` if empty
                 head                

  `remove()`     Removes and returns Throws `NoSuchElementException`
                 head                

  `peek()`       Retrieves head      Returns `null` if empty
                 (without removing)  

  `element()`    Retrieves head      Throws `NoSuchElementException`
                 (without removing)  
  --------------------------------------------------------------------------

🧩 **Tip:**\
Use `offer`, `poll`, and `peek` for **safe, non-exception** operations.

------------------------------------------------------------------------

## 💻 5️⃣ Example --- Using Queue with LinkedList

``` java
import java.util.*;

public class QueueExample {
    public static void main(String[] args) {
        Queue<String> queue = new LinkedList<>();

        queue.offer("A");
        queue.offer("B");
        queue.offer("C");

        System.out.println("Queue: " + queue);
        System.out.println("Head: " + queue.peek());  // A

        System.out.println("Removed: " + queue.poll()); // removes A
        System.out.println("After removal: " + queue);  // [B, C]
    }
}
```

**Output:**

    Queue: [A, B, C]
    Head: A
    Removed: A
    After removal: [B, C]

------------------------------------------------------------------------

## 🔄 6️⃣ Queue vs List

  ## 🔄 6️⃣ Queue vs List

| Feature | `List` | `Queue` |
|----------|---------|----------|
| **Access Type** | Indexed | FIFO |
| **Add Element** | `add(index, e)` | `offer(e)` |
| **Remove Element** | `remove(index)` | `poll()` |
| **Peek Element** | `get(index)` | `peek()` |
| **Typical Use** | Store and access by index | Process elements in order |

---

```
          java.lang.Iterable
                 │
           java.util.Collection<E>
                 │
 ┌───────────────┼───────────────┐
 │               │               │
List<E>          Set<E>         Queue<E>
 │               │               │
 │               │               │
 ├─ ArrayList     ├─ HashSet      ├─ LinkedList
 ├─ LinkedList    ├─ LinkedHashSet├─ PriorityQueue
 ├─ Vector        ├─ TreeSet      ├─ ArrayDeque
 └─ Stack        (SortedSet)      └─ (Deque<E> subinterface)

```