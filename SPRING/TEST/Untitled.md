https://www.baeldung.com/junit-5


```java
@BeforeAll 
static void setup() { 
	log.info("@BeforeAll - executes once before all test methods in this class"); 
}

@BeforeEach 
void init() { 
	log.info("@BeforeEach - executes before each test method in this class"); 
}

@AfterEach 
void tearDown() { 
	log.info("@AfterEach - executed after each test method."); 
} 
@AfterAll
static void done() { 
	log.info("@AfterAll - executed after all test methods."); 
}
```

```java
@Test
void lambdaExpressions() { 
	List numbers = Arrays.asList(1, 2, 3); 
	assertTrue(numbers.stream() 
		   .mapToInt(i -> i) 
		   .sum() > 5, () -> "Sum should be greater than 5"); 
}
```

```java
@Test 
void groupAssertions() { 
	int[] numbers = {0, 1, 2, 3, 4}; 
	assertAll("numbers", 
		()) -> assertEquals(numbers[0], 1), 
		() -> assertEquals(numbers[3], 3), 
		() -> assertEquals(numbers[4], 1) );
}
```

```java
@Test 
void shouldThrowException() { 
	Throwable exception = assertThrows(UnsupportedOperationException.class, () -> {
	 throw new UnsupportedOperationException("Not supported"); 
	 }); 
	 assertEquals(exception.getMessage(), "Not supported"); 
}

```

```java
@Test 
void assertThrowsException() {
	String str = null; 
	assertThrows(IllegalArgumentException.class, () -> {
	 Integer.valueOf(str); 
	}); 
}
```

https://javastart.pl/baza-wiedzy/testowanie-jednostkowe/given-when-then-w-testach

```java
@Test
public void shouldNeverServeCoffeeIfNoRemaining() {
	// given
	Cafe cafe = new Cafe();
	cafe.setCoffeesRemaining(1);

	// when 
	cafe.serveCoffee();

	// then
	assertFalse(cafe.canServeCoffee());
}
```