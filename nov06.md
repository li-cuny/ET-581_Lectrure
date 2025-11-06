### Wrapper class
- A wrapper class “wraps” a primitive data type into an object, so we can use it in places where an object is required.
- collections in Java only store objects — not primitive types.

| Primitive Type | Wrapper Class |
| -------------- | ------------- |
| byte           | Byte          |
| short          | Short         |
| int            | Integer       |
| long           | Long          |
| float          | Float         |
| double         | Double        |
| char           | Character     |
| boolean        | Boolean       |

### Boxing and Unboxing
#### Boxing

➡️ Converting a primitive type into its wrapper class object.
```java
int a = 5;
Integer obj = Integer.valueOf(a);  // boxing
```
Unboxing

➡️ Converting a wrapper class object back into its primitive type.
```java
Integer obj = 10;
int a = obj.intValue();  // unboxing
```
### Auto-boxing and Auto-unboxing
```
Integer x = 5;  // int → Integer (auto-boxing)
int y = x;      // Integer → int (auto-unboxing)
```
| Primitive | Wrapper Class | Boxing (Primitive → Object)  | Unboxing (Object → Primitive) | Auto-boxing / Auto-unboxing           |
| --------- | ------------- | ---------------------------- | ----------------------------- | ------------------------------------- |
| `int`     | `Integer`     | `Integer.valueOf(int i)`     | `intValue()`                  | `Integer i = 20; int z = i;`          |
| `long`    | `Long`        | `Long.valueOf(long l)`       | `longValue()`                 | `Long l = 100L; long m = l;`          |
| `double`  | `Double`      | `Double.valueOf(double d)`   | `doubleValue()`               | `Double d = 2.5; double e = d;`       |
| `char`    | `Character`   | `Character.valueOf(char c)`  | `charValue()`                 | `Character c = 'A'; char ch = c;`     |
| `boolean` | `Boolean`     | `Boolean.valueOf(boolean b)` | `booleanValue()`              | `Boolean b = true; boolean flag = b;` |





