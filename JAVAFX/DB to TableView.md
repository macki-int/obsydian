```java
public void seleccionaregistros() {
	ObservableList <Persona> data =FXCollections.observableArrayList();
		Connection conn=null;{
			try {
                 conn = DriverManager.getConnection("jdbc:sqlserver://DESKTOP-4JA6SFR:1433;databaseName=prueba", "sa", "123");
                  Statement mostrar=conn.createStatement();
                  ResultSet rs;
                  rs= mostrar.executeQuery("select * from cliente");
 
                  while (rs.next()){
                     data.add(new Persona(
                             rs.getString("nombre"),
                             rs.getString("apellido"),
                             rs.getInt("id"),
                             rs.getDate(4).toLocalDate())
                             );
                     tablacliente.setItems(data);
                  }
			} catch (SQLException e) {
                  e.printStackTrace();
			}
		}
}
```

https://coderanch.com/t/700830/java/display-date-data-tableview