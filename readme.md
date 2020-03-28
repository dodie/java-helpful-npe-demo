# Java 14 Helpful NullPointerExceptions Demo

This repository contains an example code that uses the DOM API to discover
an XML document.

A typical usage of this API:

```java
department.getElementsByTagName("name").item(0).getChildNodes().item(0).getNodeValue();
```

If any method is to return a null in this chain, it will blow up with a `NullPointerException`.
But can you tell which?

**In the old days of Java all we got is**:

```
Exception in thread "main" java.lang.NullPointerException
        at Main.processEmployee(Main.java:83)
```

Finding out the exact source of the problem is left as an exercise for the reader.

However, **with Java 14's (Helpful NullPointerExceptions)[https://openjdk.java.net/jeps/358] the message contains a more
precise reason**:

```
Exception in thread "main" java.lang.NullPointerException: Cannot invoke "org.w3c.dom.Node.getChildNodes()" because the return value of "org.w3c.dom.NodeList.item(int)" is null
        at Main.processEmployee(Main.java:83)
```

# Requirements

Install Java 14.


# Usage

```bash
# Compile
javac --enable-preview -source 14 Main.java

# Run with Helpful NullPointerExceptions enabled
java -cp . --enable-preview -XX:+ShowCodeDetailsInExceptionMessages Main

# Run without Helpful NullPointerExceptions
java -cp . --enable-preview Main
```

