- flatMap
- reduce
- filter()
- sorted()
- map() - new stream
- collect()
- max()
- min()
- average()
- sum()
- range()


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
 
 
 
 List<String> strings = Arrays.asList("a1", "a2", "b3", "b4", "c5", "c6");
 strings
 .stream()
 .map(string -> string.substring(1))
 .mapToInt(Integer::parseInt)
 .average()
 .ifPresent(System.out::println); // 3.5
 ```
 
 