**Optional.isPresent**
```java
public String getPersonName() {
  Optional<String> name = getName();
  if (name.isPresent()) {
    return name.get();
  }
  return "DefaultName";
}
```

lepiej:
**Optional.orElse**
```java
public String getPersonName() {
  Optional<String> name = getName();
  return name.orElse("DefautName");
}
```

Jeśli obliczenie wartości domyślnej jest kosztowne, to może to spowodować problemy z wydajnością. 
```java
public Optional<Table> retrieveTable() {
  return Optional.ofNullable(constructTableFromCache())
                 .orElse(fetchTableFromRemote());
}
```

lepiej:
**Optional.orElseGet**
```java
public Optional<Table> retrieveTable() {
  return Optional.ofNullable(constructTableFromCache())
                 .orElseGet(this::fetchTableFromRemote);
}
```

**Optional.empty**
```java
public Optional<String> getPersonName() {
  Person person = getPerson();
  if (ALLOWED_NAMES.contains(person.getName())) {
    return Optional.ofNullable(person.getName());
  }
  return Optional.empty();
}
```

lepiej:
**Optional.ofNullable**
```java
public Optional<String> getPersonName() {
  Person person = getPerson();
  return Optional.ofNullable(person.getName())
                 .filter(ALLOWED_NAMES::contains);
}
```

**Nie twórz Optional z kolekcji** 
```java
public Optional<List<String>> getNames() {
  if (isDevMode()) {
    return Optional.of(getPredefinedNames());
  }
  try {
    List<String> names = getNamesFromRemote();
    return Optional.of(names);
  }
  catch (Exception e) {
    log.error("Cannot retrieve names from the remote server", e);
    return Optional.empty();
  }
}
```

lepiej:
```java
public List<String> getNames() {
  if (isDevMode()) {
    return getPredefinedNames();
  }
  try {
    return getNamesFromRemote();
  }
  catch (Exception e) {
    log.error("Cannot retrieve names from the remote server", e);
    return emptyList();
  }
}
```

**Nie przekazuj Optional jako parametru**
```java
public void doAction() {
  OptionalInt age = getAge();
  Optional<Role> role = getRole();
  applySettings(name, age, role);
}
```

lepiej:
```java
public void doAction() {
  OptionalInt age = getAge();
  Optional<Role> role = getRole();
  applySettings(name, age.orElse(defaultAge), role.orElse(defaultRole));
}
```
Jeśli `age` i `role` będzie można pominąć, to takie podejście nie zadziała.
Pozostaje deklaracja oddzielnych metod dla różnych potrzeb użytkowników. (wygląda rozwlekle, ale użytkownik ma możliwość robienia dokładnie tego, co chce zrobić)
```java
void applySettings(String name) { ... }
void applySettings(String name, int age) { ... }
void applySettings(String name, Role role) { ... }
void applySettings(String name, int age, Role role) { ... }
```

Nie używaj Optional jako pól klas
- nie implementuje interfejsu Serializable
- Hibernate nie może mapować wartości z bazy danych na Optional
- Problem w dużych aplikacjach z dużą ilością beanów 


Niektóre frameworki dobrze zintegrowały się z Optional. 
**Jackson**
Prosty DTO oraz EndPoint
```java
public class PersonDTO {
  private long id;
  private String firstName;
  private String lastName;
  // getters, constructors, and etc.
}
```
```java
@GetMapping("/person/{id}")
public PersonDTO getPersonDTO(@PathVariable long id) {
    return personRepository.findById(id)
            .map(person -> new PersonDTO(
                    person.getId(),
                    person.getFirstName(),
                    person.getLastName())
            )
            .orElseThrow();
}
```

Wynik `GET /person/1`
```java
{
  "id": 1,
  "firstName": "John",
  "lastName": "Brown"
}
```

Zastąpienie `String` przy pomocy `Optional<String>`. 
```java
public class PersonDTO {
  private long id;
  private Optional<String> firstName;
  private Optional<String> lastName;
  // getters, constructors, and etc.
}
```
```java
@GetMapping("/person/{id}")
public PersonDTO getPersonDTO(@PathVariable long id) {
    return personRepository.findById(id)
            .map(person -> new PersonDTO(
                    person.getId(),
                    Optional.ofNullable(person.getFirstName()),
                    Optional.empty()
            ))
            .orElseThrow();
}
```

Wynik `GET /person/1`
```java
{
  "id": 1,
  "firstName": "John",
  "lastName": null}
``` 


**Optional tylko dla getterów**
```java
public class PersonDTO {
    private long id;
    private String firstName;
    private String lastName;
    
    public PersonDTO(long id, String firstName, String lastName) {
        this.id = id;
        this.firstName = firstName;
        this.lastName = lastName;
    }
    
    public long getId() {
        return id;
    }
    
    public Optional<String> getFirstName() {
        return Optional.ofNullable(firstName);
    }
    
    public Optional<String> getLastName() {
        return Optional.ofNullable(lastName);
    }
}
```

Klasy tej można spokojnie użyć jako encji DTO albo **Hibernate**.Optional nie ma żadnego wpływu na dane - opakowuje wartości null, aby obsłużyły nieobecne dane.