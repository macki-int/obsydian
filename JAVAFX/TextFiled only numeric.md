```java 
textField.textProperty().addListener(new ChangeListener<String>(){

	@Override 
	public void changed(ObservableValue<? extends String> observable, String oldValue, String newValue) { 
		if (!newValue.matches("\\d*")) { 
			textField.setText(newValue.replaceAll("[^\\d]", "")); 
		} 
	} 
});
```