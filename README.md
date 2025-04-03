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
