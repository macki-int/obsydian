Format for Display Value Only
```java
public static void applyNumericFormat(Workbook outWorkbook, Row row, Cell cell, Double value, String styleFormat) {
	CellStyle style = outWorkbook.createCellStyle();
	DataFormat format = outWorkbook.createDataFormat();
	style.setDataFormat(format.getFormat(styleFormat));
	cell.setCellValue(value); cell.setCellStyle(style);
}
```

Validate
```java
File file = new File("number_test.xlsx"); 
try (Workbook outWorkbook = new XSSFWorkbook()) { 
	Sheet sheet = outWorkbook.createSheet("Numeric Sheet"); 
	Row row = sheet.createRow(0); 
	Cell cell = row.createCell(0); 
	ExcelNumericFormat.applyNumericFormat(outWorkbook, row, cell, 10.251, "0.00");
	FileOutputStream fileOut = new FileOutputStream(file);
	outWorkbook.write(fileOut); fileOut.close(); 
}
```
![[ApachePOIValidate.png]]

Test
```java
try (Workbook inWorkbook = new XSSFWorkbook("number_test.xlsx")) { 
	Sheet sheet = inWorkbook.cloneSheet(0); 
	Row row = sheet.getRow(0); 
	Assertions.assertEquals(10.251, row.getCell(0).getNumericCellValue()); 
}
```

Format for Both Actual and Display Value
```java
File file = new File("number_test.xlsx");
try (Workbook outWorkbook = new HSSFWorkbook()) {
    Sheet sheet = outWorkbook.createSheet("Numeric Sheet");
    Row row = sheet.createRow(0);
    Cell cell = row.createCell(0);
    DecimalFormat df = new DecimalFormat("#,###.##");
    ExcelNumericFormat.applyNumericFormat(outWorkbook, row, cell, Double.valueOf(df.format(10.251)), "#,###.##");
    FileOutputStream fileOut = new FileOutputStream(file);
    outWorkbook.write(fileOut);
    fileOut.close();
}
```
![[ApachePOIFormatActualAndDisplay.png]]

Test
```java
try (Workbook inWorkbook = new XSSFWorkbook("number_test.xlsx")) { 
	Sheet sheet = inWorkbook.cloneSheet(0); 
	Row row = sheet.getRow(0); 
	Assertions.assertEquals(10.25, row.getCell(0).getNumericCellValue()); 
}