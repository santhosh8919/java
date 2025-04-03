# java

### **What is a String in Java?**
In Java, a **String** is an object that represents a sequence of characters. The `String` class is part of the `java.lang` package and is widely used to handle text-based data.

Strings in Java are **immutable**, meaning once a `String` object is created, its value cannot be changed.

### **Why Use Strings in Java?**
1. **Text Processing:** Strings are used to store and manipulate textual data.
2. **Immutability for Security:** Since strings cannot be changed, they are safe for multi-threaded applications.
3. **Efficient Memory Management:** Java uses a **String Pool** to optimize memory usage by storing string literals.
4. **Built-in Methods:** Java provides many useful methods like `length()`, `charAt()`, `substring()`, `toUpperCase()`, and `toLowerCase()` to manipulate strings.

### **Main Purpose of Strings in Java**
- **Data Representation:** Store names, messages, or any textual content.
- **Communication:** Strings are used in networking, APIs, and user interactions.
- **Parsing & Formatting:** Strings help in reading and processing user input, files, and database records.

# Why is String Not a Primitive Type?
Objects, Not Variables: A String is an instance of the java.lang.String class, meaning it is an object, not a primitive like int, char, or boolean

In Java, there are multiple ways to initialize a `String`. Here are the different types of `String` initialization with examples:

---

### **1. Using String Literal (Recommended)**
```java
String str1 = "Hello, Java!";
```
✅ **Stored in the String Pool (Heap memory).**  
✅ **Memory-efficient** (avoids creating duplicate objects).

---

### **2. Using `new` Keyword (Heap Memory)**
```java
String str2 = new String("Hello, Java!");
```
⚠️ **Not recommended** unless necessary, as it creates a new object even if the same value exists in the string pool.

---

### **3. Using Character Array**
```java
char[] charArray = {'H', 'e', 'l', 'l', 'o'};
String str3 = new String(charArray);
```
✅ Useful when converting character data to a String.

---

### **4. Using `StringBuilder` or `StringBuffer`**
```java
StringBuilder sb = new StringBuilder("Hello");
String str4 = sb.toString();
```
✅ **Mutable** (Can modify content without creating new objects).  
✅ Recommended when frequent modifications are needed.

---

### **5. Using `String.valueOf()` (Convert Other Types to String)**
```java
int num = 100;
String str5 = String.valueOf(num);
```
✅ Converts **any primitive** to a String.

---

### **6. Using `concat()` Method**
```java
String str6 = "Hello".concat(" World!");
```
✅ Joins two strings efficiently.

---

### **7. Using `format()` Method**
```java
String str7 = String.format("My age is %d", 25);
```
✅ Useful for **formatted output**.

---

### **8. Using `join()` Method (Since Java 8)**
```java
String str8 = String.join(", ", "Java", "Python", "C++");
```
✅ Used to join multiple strings with a delimiter.

---

### **9. Using `substring()` (Extract Part of a String)**
```java
String str9 = "Hello, Java!".substring(0, 5);
```
✅ Extracts `"Hello"` from `"Hello, Java!"`.

---

### **What is a String Literal in Java?**  
A **String literal** is a sequence of characters enclosed in double quotes (`""`). It is the simplest and most memory-efficient way to create a `String` in Java.

### **Example of String Literal**
```java
String str1 = "Hello, Java!";
String str2 = "Hello, Java!";
```
📌 **Stored in the String Pool** (part of the heap memory).  
📌 **Memory-efficient**: If `"Hello, Java!"` already exists in the pool, Java **does not create a new object**. Instead, `str2` refers to the existing object.

---

### **How String Literals Work (String Pool Concept)**
- Java maintains a **String Pool** where it stores string literals.
- If a new literal is created and it already exists in the pool, Java **reuses** the reference instead of creating a new object.

```java
//String Pool (memory type)
String s1 = "Java";  
String s2 = "Java";  // 😎s2 refers to the same object as s1  
System.out.println(s1 == s2);  //😎 true (same memory location)
```

**But when using `new String()`, a new object is always created:**
```java
//Heap Memory (Object Memory) (memory type)
String s3 = new String("Java");
System.out.println(s1 == s3);  //📝⚠️ false (different memory locations)
```

Let's break down the code and explain each output in detail.  

---

### **Code Explanation**
```java
class Solution {
    public static void main(String[] args) {
        System.out.println(new Solution());
```
#### **What happens here?**
- `new Solution()` creates an instance of the `Solution` class.
- By default, `System.out.println(new Solution());` calls the **`toString()` method** from the `Object` class.
- Since `toString()` is **not overridden**, it prints:
  ```
  Solution@<hashcode>
  ```
  Example output: `Solution@1b6d3586` (hashcode will be different every time).

---

### **String Comparison**
```java
String s1 = "hello";
String s2 = "hello";
String s3 = new String("hello");
String s4 = new String("hello");
```
#### **Memory Allocation**
| Variable | Creation Type | Storage Location | Reuse |
|----------|--------------|------------------|-------|
| `s1` | String Literal | String Pool | ✅ Reused |
| `s2` | String Literal | String Pool | ✅ Reused |
| `s3` | `new String("hello")` | Heap (New Object) | ❌ New object created |
| `s4` | `new String("hello")` | Heap (New Object) | ❌ New object created |

---

### **Comparison using `==` (Reference Comparison)**
#### **1. `System.out.println(s1 == s2); // true`**
- `s1` and `s2` refer to the **same object** in the **String Pool**.
- Since literals are stored in the String Pool and reused, both point to the same memory location.
- **Output:** `true`

#### **2. `System.out.print(s1 == s3); // false`**
- `s1` is in the **String Pool**, while `s3` is in the **Heap** (because of `new String("hello")`).
- They have the **same value** but are stored in different locations.
- **Output:** `false`

#### **3. `System.out.println(s3 == s4); // false`**
- `s3` and `s4` are created using `new`, so each time a **new object** is created in the **Heap**.
- They are two different objects with the **same value** but **different memory locations**.
- **Output:** `false`

---

### **Comparison using `equals()` (Content Comparison)**
#### **4. `System.out.println(s1.equals(s2)); // true`**
- `.equals()` checks the **actual content** of the strings.
- Both `s1` and `s2` store `"hello"`, so they are **equal**.
- **Output:** `true`

#### **5. `System.out.println(s1.equals(s3)); // true`**
- `s1` (`String Pool`) and `s3` (`Heap`) store the **same value** `"hello"`.
- `.equals()` compares content, not memory locations.
- **Output:** `true`

#### **6. `System.out.println(s3.equals(s4)); // true`**
- `s3` and `s4` are **different objects**, but both contain `"hello"`.
- `.equals()` checks content, so they are **equal**.
- **Output:** `true`

---

### **Final Output**
```
Solution@<hashcode>  // Object memory reference
true                 // s1 == s2 (same pool reference)
false                // s1 != s3 (pool vs. heap)
false                // s3 != s4 (different heap objects)
true                 // s1.equals(s2) (same content)
true                 // s1.equals(s3) (same content)
true                 // s3.equals(s4) (same content)
```

---

### **Summary**
| Comparison | Type | Checks | Result |
|------------|------|--------|--------|
| `==` | Reference | Memory address | Different for new objects |
| `.equals()` | Content | Actual string value | Always `true` if values match |

Would you like to explore `intern()` to force `s3` and `s4` into the String Pool? 🚀

---

### **Advantages of String Literals**
✅ **Memory-efficient** (Avoids duplicate objects).  
✅ **Faster performance** (Reuses existing objects).  
Java provides a rich set of methods in the `String` class to manipulate and work with strings. Since there are many methods, I’ll explain them in a concise yet comprehensive way, grouped by their functionality. The `String` class is immutable, meaning these methods don’t modify the original string but often return a new one.

# 👻 breakdown of all the key `String` methods in Java:

---

### 1. **Creation and Basic Info**
- **`length()`**: Returns the length (number of characters) of the string.
  ```java
  String str = "Hello";
  System.out.println(str.length());  // Output: 5
  ```
- **`isEmpty()`**: Checks if the string is empty (`""`).
  ```java
  System.out.println("".isEmpty());  // Output: true
  ```
- **`isBlank()`**: Checks if the string is empty or contains only whitespace (Java 11+).
  ```java
  System.out.println("  ".isBlank());  // Output: true
  ```

---

### 2. **Character Access**
- **`charAt(int index)`**: Returns the character at the specified index (0-based).
  ```java
  String str = "Hello";
  System.out.println(str.charAt(1));  // Output: e
  ```
- **`toCharArray()`**: Converts the string to a character array.
  ```java
  char[] chars = "Hello".toCharArray();  // ['H', 'e', 'l', 'l', 'o']
  ```

---

### 3. **Comparison**
- **`equals(Object obj)`**: Checks if two strings are equal (case-sensitive).
  ```java
  String str1 = "Hello";
  String str2 = "hello";
  System.out.println(str1.equals(str2));  // Output: false
  ```
- **`equalsIgnoreCase(String str)`**: Compares strings ignoring case.
  ```java
  System.out.println("Hello".equalsIgnoreCase("hello"));  // Output: true
  ```
- **`compareTo(String str)`**: Compares two strings lexicographically (returns 0 if equal, negative if less, positive if greater).
  ```java
  System.out.println("apple".compareTo("banana"));  // Output: negative
  ```
- **`compareToIgnoreCase(String str)`**: Same as `compareTo`, but ignores case.

---

### 4. **Searching**
- **`contains(CharSequence s)`**: Checks if the string contains a substring.
  ```java
  System.out.println("Hello World".contains("World"));  // Output: true
  ```
- **`indexOf(int ch)`** or **`indexOf(String str)`**: Returns the first occurrence of a character or substring (-1 if not found).
  ```java
  String str = "Hello";
  System.out.println(str.indexOf("l"));  // Output: 2
  ```
- **`lastIndexOf(int ch)`** or **`lastIndexOf(String str)`**: Returns the last occurrence.
  ```java
  System.out.println("Hello".lastIndexOf("l"));  // Output: 3
  ```
- **`startsWith(String prefix)`**: Checks if the string starts with the specified prefix.
  ```java
  System.out.println("Hello".startsWith("He"));  // Output: true
  ```
- **`endsWith(String suffix)`**: Checks if the string ends with the specified suffix.
  ```java
  System.out.println("Hello".endsWith("lo"));  // Output: true
  ```

---

### 5. **Manipulation**
- **`substring(int beginIndex)`** or **`substring(int beginIndex, int endIndex)`**: Extracts a substring.
  ```java
  String str = "Hello World";
  System.out.println(str.substring(6));      // Output: World
  System.out.println(str.substring(0, 5));   // Output: Hello
  ```
- **`concat(String str)`**: Concatenates another string to the end.
  ```java
  System.out.println("Hello".concat(" World"));  // Output: Hello World
  ```
- **`replace(char oldChar, char newChar)`** or **`replace(CharSequence target, CharSequence replacement)`**: Replaces characters or substrings.
  ```java
  System.out.println("Hello".replace('l', 'p'));  // Output: Heppo
  System.out.println("Hello".replace("ll", "y")); // Output: Heyo
  ```
- **`replaceAll(String regex, String replacement)`**: Replaces all matches of a regex pattern.
  ```java
  System.out.println("Hello123".replaceAll("[0-9]", ""));  // Output: Hello
  ```
- **`replaceFirst(String regex, String replacement)`**: Replaces the first match of a regex.
  ```java
  System.out.println("Hello123Hello".replaceFirst("[0-9]", "X"));  // Output: HelloX23Hello
  ```
- **`trim()`**: Removes leading and trailing whitespace.
  ```java
  System.out.println("  Hello  ".trim());  // Output: Hello
  ```
- **`strip()`**: Removes leading and trailing whitespace (more robust, Java 11+).
  ```java
  System.out.println("  Hello  ".strip());  // Output: Hello
  ```
- **`stripLeading()`**: Removes only leading whitespace (Java 11+).
- **`stripTrailing()`**: Removes only trailing whitespace (Java 11+).
- **`toLowerCase()`**: Converts the string to lowercase.
  ```java
  System.out.println("HELLO".toLowerCase());  // Output: hello
  ```
- **`toUpperCase()`**: Converts the string to uppercase.
  ```java
  System.out.println("hello".toUpperCase());  // Output: HELLO
  ```

---

### 6. **Splitting and Joining**
- **`split(String regex)`**: Splits the string into an array based on a regex.
  ```java
  String[] words = "Hello World".split(" ");
  // Output: ["Hello", "World"]
  ```
- **`join(CharSequence delimiter, CharSequence... elements)`**: Joins strings with a delimiter (Java 8+).
  ```java
  String result = String.join("-", "Hello", "World");
  System.out.println(result);  // Output: Hello-World
  ```

---

### 7. **Formatting**
- **`format(String format, Object... args)`**: Creates a formatted string (static method).
  ```java
  String str = String.format("Name: %s, Age: %d", "Alice", 25);
  System.out.println(str);  // Output: Name: Alice, Age: 25
  ```
- **`valueOf(type value)`**: Converts a value (int, double, etc.) to a string (static method).
  ```java
  String num = String.valueOf(123);  // Output: "123"
  ```

---

### 8. **Miscellaneous**
- **`matches(String regex)`**: Checks if the string matches a regex pattern.
  ```java
  System.out.println("abc123".matches("[a-z]+[0-9]+"));  // Output: true
  ```
- **`getBytes()`**: Converts the string to a byte array.
  ```java
  byte[] bytes = "Hello".getBytes();
  ```
- **`codePointAt(int index)`**: Returns the Unicode code point at the specified index.
  ```java
  System.out.println("Hello".codePointAt(0));  // Output: 72 (Unicode for 'H')
  ```
- **`intern()`**: Returns a canonical representation of the string (useful for string pooling).
  ```java
  String str = new String("Hello").intern();
  ```

---

### Example Program Using Some Methods
```java
public class StringMethodsExample {
    public static void main(String[] args) {
        String str = "  Hello World  ";
        
        System.out.println("Length: " + str.length());
        System.out.println("Trimmed: " + str.trim());
        System.out.println("Uppercase: " + str.toUpperCase());
        System.out.println("Contains 'World': " + str.contains("World"));
        System.out.println("Substring: " + str.substring(2, 7));
        System.out.println("Replaced: " + str.replace("World", "Java"));
    }
}
```

**Output:**
```
Length: 14
Trimmed: Hello World
Uppercase:   HELLO WORLD  
Contains 'World': true
Substring: Hello
Replaced:   Hello Java  
```

---

### Notes
- Most methods return a new `String` because strings are immutable.
- Some methods (like `split`, `replaceAll`) use regular expressions (regex).
- Methods like `isBlank`, `strip`, and `join` were added in Java 11 or 8, so check your Java version if they don’t work.


