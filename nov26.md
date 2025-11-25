# Java File Handling

- Create files
- Read data from files
- Write data to files
- Delete files

---

## A. File Management (File system operations)
Use **`File` class**:  
- `exists()`  
- `createNewFile()`  
- `delete()`  
- `length()`  
- `getName()`  
- `getAbsolutePath()`  
- `list()`  

**Important:**  
The `File` class does **not** read or write file contents.

---

## B. Character/Text Files (Human-readable)
Use for `.txt`, `.csv`, `.json`.

Classes:
- `FileWriter`
- `BufferedWriter`
- `FileReader`
- `BufferedReader`
- `Scanner`

---

## C. Binary Files (Images, audio, video)
Use for non-text data like `.png`, `.mp3`, `.mp4`.

Classes:
- `FileInputStream`
- `FileOutputStream`
- `BufferedInputStream`
- `BufferedOutputStream`

---

---

# Java File Read and Write

## 1. Introduction

Java provides multiple APIs to read and write files. The most common and
modern approach is using the `java.nio.file` package, but older
approaches like `FileReader`, `BufferedReader`, and `FileWriter` are
still widely used.

------------------------------------------------------------------------

## 2. Reading Files

### **2.1 Using Files.readAllLines() (Simple & Modern)**

``` java
import java.nio.file.*;
import java.io.*;
import java.util.*;

public class ReadExample {
    public static void main(String[] args) throws Exception {
        List<String> lines = Files.readAllLines(Path.of("data.txt"));
        for (String line : lines) {
            System.out.println(line);
        }
    }
}
```

------------------------------------------------------------------------

### **2.2 Using BufferedReader (Traditional & Efficient)**

``` java
import java.io.*;

public class BufferedReaderExample {
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new FileReader("data.txt"));
        String line;
        while ((line = br.readLine()) != null) {
            System.out.println(line);
        }
        br.close();
    }
}
```

------------------------------------------------------------------------

## 3. Writing Files

### **3.1 Using Files.writeString()**

``` java
import java.nio.file.*;

public class WriteExample {
    public static void main(String[] args) throws Exception {
        Files.writeString(Path.of("output.txt"), "Hello World!");
    }
}
```

------------------------------------------------------------------------

### **3.2 Using BufferedWriter**

``` java
import java.io.*;

public class BufferedWriterExample {
    public static void main(String[] args) throws Exception {
        BufferedWriter bw = new BufferedWriter(new FileWriter("output.txt"));
        bw.write("Hello World!");
        bw.newLine();
        bw.write("Second line");
        bw.close();
    }
}
```

------------------------------------------------------------------------

## 4. Reading CSV Files (Basic)

``` java
import java.io.*;

public class CSVExample {
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new FileReader("data.csv"));
        String line;
        while ((line = br.readLine()) != null) {
            String[] parts = line.split(",");
            System.out.println("Name: " + parts[0] + ", Age: " + parts[1]);
        }
        br.close();
    }
}
```

------------------------------------------------------------------------

## 5. Writing CSV Files

``` java
import java.io.*;

public class WriteCSV {
    public static void main(String[] args) throws Exception {
        BufferedWriter bw = new BufferedWriter(new FileWriter("data.csv"));
        bw.write("John,25");
        bw.newLine();
        bw.write("Mary,30");
        bw.close();
    }
}
```

------------------------------------------------------------------------

## 6. Best Practices

-   Always close readers/writers (or use try-with-resources)
-   Prefer `java.nio.file` for modern applications
-   Use `BufferedReader`/`BufferedWriter` for large files
-   Validate CSV fields before parsing


### Text (Character) I/O 

| Reader (Input)                  | Writer (Output)                   | Notes / Use Case                                                                        |
| ------------------------------- | --------------------------------- | --------------------------------------------------------------------------------------- |
| `FileReader`                    | `FileWriter`                      | Low-level character reading/writing. Usually wrapped in buffered versions.              |
| `BufferedReader`                | `BufferedWriter`                  | Most common pattern. Efficient line-by-line text I/O.                                   |
| `Scanner`                       | `PrintWriter`                     | Reads tokens/lines; prints formatted text. Good for parsing and formatted output.       |
| `Files.newBufferedReader(Path)` | `Files.newBufferedWriter(Path)`   | Modern, buffered, supports charset. Preferred for new code.                             |
| `Files.readAllLines(Path)`      | `Files.writeString(Path, String)` | Convenience methods for small files. Reads all lines into memory / writes whole string. |
| `Files.lines(Path)`             | `Files.write(Path, List<String>)` | Stream-based modern API. Lazy reading / writing multiple lines.                         |


### Binary (Byte) I/O 

| InputStream (Input)          | OutputStream (Output)         | Notes / Use Case                                                                        |
| ---------------------------- | ----------------------------- | --------------------------------------------------------------------------------------- |
| `FileInputStream`            | `FileOutputStream`            | Low-level byte streams. Direct read/write of binary files.                              |
| `BufferedInputStream`        | `BufferedOutputStream`        | Wrap low-level streams for efficiency. Common for large files or frequent reads/writes. |
| `Files.newInputStream(Path)` | `Files.newOutputStream(Path)` | Modern, low-level streams. Can wrap in buffered streams for efficiency.                 |
| N/A                          | `Files.write(Path, byte[])`   | Modern convenience method to write byte arrays.                                         |

