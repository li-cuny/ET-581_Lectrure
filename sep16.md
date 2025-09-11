# Java Random Number

## Math.random()
- **Type:** Static method
- **Returns:** double (0.0 ≤ x < 1.0)
- **Simple, no object needed**

### Examples
```java
// Random double between 0.0 and 1.0
double r = Math.random();

// Random int between 0 and 9
int n = (int)(Math.random() * 10);

```
### Random class (java.util.Random)

Type: Class, need to create instance

Can generate: int, double, boolean, float, long

Optional seed for reproducible sequences
### Examples
```java
import java.util.Random;
Random rand = new Random(); // or new Random(seed)

// Random double 0.0 <= x < 1.0
double rDouble = rand.nextDouble();

// Random int between 0 and 9
int rInt = rand.nextInt(10);

// Random boolean
boolean rBool = rand.nextBoolean();

```