https://www.jsonschema2pojo.org/
http://jsonschema2pojo.org.testednet.com/


https://howtodoinjava.com/gson/gson-parse-json-array/

```java
String userJson = "[{'name': 'Alex','id': 1}, "
        + "{'name': 'Brian','id':2}, "
        + "{'name': 'Charles','id': 3}]";
     
Gson gson = new Gson(); 
 
User[] userArray = gson.fromJson(userJson, User[].class);  
 
for(User user : userArray) {
  System.out.println(user);
}

```

```java
String userJson = "[{'name': 'Alex','id': 1}, "
        + "{'name': 'Brian','id':2}, "
        + "{'name': 'Charles','id': 3}]";
     
Gson gson = new Gson(); 
 
Type userListType = new TypeToken<ArrayList<User>>(){}.getType();
 
ArrayList<User> userArray = gson.fromJson(userJson, userListType);  
 
for(User user : userArray) {
  System.out.println(user);
}

/**
User [id=1, name=Alex]
User [id=2, name=Brian]
User [id=3, name=Charles]
*/

```

```java
String departmentJson = "{'id' : 1, "
    + "'name': 'HR',"
    + "'users' : ["
      + "{'name': 'Alex','id': 1}, "
      + "{'name': 'Brian','id':2}, "
      + "{'name': 'Charles','id': 3}]}";
 
Gson gson = new Gson(); 
 
Department department = gson.fromJson(departmentJson, Department.class);  
 
System.out.println(department);

/**
Department [id=1, name=HR,
	users=[User [id=1, name=Alex],
	User [id=2, name=Brian],
	User [id=3, name=Charles]]]
*/
```
