- flatMap
- reduce
- filter()
- map() - new stream


```java
Stream<String> namesStream = Stream.of("John", "Marry", "George", "Paul", "Alice", "Ann");
 namesStream
 .filter(e -> e.startsWith("A"))
 .map(String::toUpperCase)
 .sorted()
 .forEach(System.out::println);
 
 

List<String> namesList = Arrays.asList("John", "Marry", "George", "Paul", "Alice", "Ann");
 namesList
 .stream()
 .filter(e -> e.startsWith("A"))
 .map(String::toUpperCase)
 .sorted()
 .forEach(System.out::println);
 
 
 
List<String> namesList = Arrays.asList("John", "Marry", "George", "Paul", "Alice", "Ann");
 namesList
 .stream()
 .filter(e -> {
 System.out.println("filter: " + e);
 return true;
 })
 .forEach(e -> System.out.println("forEach: " + e));
 ```
 
 