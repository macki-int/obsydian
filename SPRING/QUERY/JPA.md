https://www.baeldung.com/spring-data-partial-update

```java
@Modifying
@Query
("update Customer u set u.phone = :phone where u.id = :id") 
void updatePhone(@Param(value = "id") long id, @Param(value = "phone") String phone);
```

```java
@Modifying
@Query("update User u set u.firstname = ?1, u.lastname = ?2 where u.id = ?3")
void setUserInfoById(String firstname, String lastname, Integer userId);
```