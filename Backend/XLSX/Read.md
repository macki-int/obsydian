```xml
<dependency> 
	<groupId>org.apache.poi</groupId> 
	<artifactId>poi-ooxml</artifactId> 
	<version>5.17</version> 
</dependency>
```

```java
FileInputStream file = new FileInputStream(new File(fileLocation));
Workbook workbook = new XSSFWorkbook(file);

Sheet sheet = workbook.getSheetAt(0);

Map<Integer, List<String>> data = new HashMap<>();
int i = 0;
for (Row row : sheet) {
    data.put(i, new ArrayList<String>());
    for (Cell cell : row) {
        switch (cell.getCellType()) {
            case STRING:
				data.get(i).add(cell.getStringCellValue());
				break;
            case NUMERIC: 
				if (DateUtil.isCellDateFormatted(cell)) {
					data.get(i).add(cell.getDateCellValue() + ""); } 
				else { 
					data.get(i).add(cell.getNumericCellValue() + ""); 
				}
				break;
            case BOOLEAN: 
				data.get(i).add(cell.getBooleanCellValue() + "");
				break;
            case FORMULA: 
				data.get(i).add(cell.getCellFormula() + "");
				break;
            default: 
				data.get(new Integer(i)).add(" ");
        }
    }
    i++;
}
```