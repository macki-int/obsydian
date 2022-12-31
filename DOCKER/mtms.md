`clean`
`build`
`package`  (maven-surefire-plugin or mvn package -DskipTests)
```ocaml
mvn clean install -Dskip.unit-tests=true -Dskip.integration-tests=true -Dskip.end-to-end-tests=true
```
-------------------------------------------------------------------------------
copi *.jar*  file to server (/home/user/target - parent directory must have Dockerfile)
`scp d:\temp\mtmj.jar user@0.0.0.0:/home/user/mtmj.jar` copy from local to server
`cp /home/user/mtms.jar /home/user/target/mtms.jar` on server copy from-directory-to-directory

`docker build . -t ts/mtms:0.0.0` building image

`docker run -d --rm -it --network host ts/mtms:0.1.0 --restart unless-stopped`

docker ps  (what [container_id])

docker logs -follow [container_id]



