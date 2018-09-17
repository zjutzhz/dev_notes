# Java
## 1. java 基础
## InputStream from file or URL
If you want to obtain an InputStream to retrieve data from a URL, then using the URL.openStream method will return an InputStream, which can be used like any other InputStream.

```java
InputStream is;

// if we were getting data from a file, we might use:
is = new FileInputStream("/path/to/file");

// or, from a URL, then retrieve an InputStream from a URL
is = new URL("http://google.com/").openStream();
```
参考[Java fileinputstream using with url](https://stackoverflow.com/questions/5528388/java-fileinputstream-using-with-url)

## UML入门
```uml
@startuml
Class Stage
Class Timeout
Stage <|-- Timeout
@enduml
```

```uml
@startuml
testdot
@enduml
```
