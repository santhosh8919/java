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

---

### **Advantages of String Literals**
✅ **Memory-efficient** (Avoids duplicate objects).  
✅ **Faster performance** (Reuses existing objects).  
