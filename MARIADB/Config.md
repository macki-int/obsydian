//hostname = "localhost";
//username = "demo_user";
//password = "abcdef";
//db = "demo";

`mysql -u root -p` - Log in command line MySQL/MariaDB

`CREATE DATABASE demo;`
`USE demo;`

`CREATE TABLE user_demo (
  id MEDIUMINT NOT NULL AUTO_INCREMENT PRIMARY KEY,
  demo_name CHAR(100),
  star_rating TINYINT,
  details VARCHAR(4000)
  ); `

`GRANT ALL ON demo.* to demo_user@localhost IDENTIFIED BY 'abcdef';
`