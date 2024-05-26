
in directory:  
**Java /JRE/bin** file **keytool.exe**

_.\keytool.exe -genkey -keyalg RSA -alias selfsigned -keystore keystore.jks -validity 365 -keysize 2048_

add into application.properties:

```java
server.port=443
server.ssl.key-password=password
server.ssl.key-store-password=password
server.ssl.key-store=src/main/resources/keystore.jks
```