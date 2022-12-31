```java
@GetMapping("/{id}/edit")
public String edit(@PathVariable Long id, Model model) {
  model.addAttribute("categoryDto", categoryService.findOne(id));
  return "category/edit";
}
```
```java
public Category findOne(Long id) {
  return categoryRepository.findOne(id);
}
```
```java
T findOne(ID primaryKey);
```
```java
<S extends T> Optional<S> findOne(Example<S> example);
```
```java
Optional<T> findById(ID id); 
```

1.  Suppose that if the entity is found you want to get it otherwise you want to get a default value.
```java
Foo foo = repository.findById(id)
                    .orElse(new Foo());
```

or get a `null` default value if it makes sense (same behavior as before the API change) :

```java
Foo foo = repository.findById(id)
                    .orElse(null);
```

2.  Suppose that if the entity is found you want to return it, else you want to throw an exception.
```java
return repository.findById(id)
        .orElseThrow(() -> new EntityNotFoundException(id));
```

3.  Suppose you want to apply a different processing according to if the entity is found or not (without necessarily throwing an exception).
```java
Optional<Foo> fooOptional = fooRepository.findById(id);
if (fooOptional.isPresent()) {
    Foo foo = fooOptional.get();
    // processing with foo ...
} else {
    // alternative processing....
}
```

https://stackoverflow.com/questions/49316751/spring-data-jpa-findone-change-to-optional-how-to-use-this