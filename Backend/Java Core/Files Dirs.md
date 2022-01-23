
```java
Path path = Paths.get("does-not-exist.txt");
assertFalse(Files.exists(path));


Path tempFile = Files.createTempFile("baeldung", "text"); 
assertTrue(Files.exists(tempFile));

assertFalse(Files.notExists(tempDirectory));

assertTrue(Files.isDirectory(tempDirectory)); 
assertFalse(Files.isDirectory(tempFile)); 
assertTrue(Files.isRegularFile(tempFile));

Files.deleteIfExists(target);

```
or

```java

Path currentDir = Paths.get("."); // currentDir = "."
Path fullPath = currentDir.toAbsolutePath(); // fullPath = "/Users/guest/workspace"
Path one = currentDir.resolve("file.txt"); // one = "./file.txt"
Path fileName = one.getFileName(); // fileName = "file.txt"



//if file exist
Path currentDir = Paths.get("").toAbsolutePath(); 
Path path = currentDir.resolve("file.txt");
path.normalize();
Files.exist(path) 

```

Dir
```java

Path currentWorkingDir = Paths.get("").toAbsolutePath();

//working diretory from properties
String currentWorkingDir = System.getProperty("user.dir");

//normalize!
currentWorkingDir.normalize().toString();
```