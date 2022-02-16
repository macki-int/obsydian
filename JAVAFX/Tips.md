ashed line: Style: `-fx-stroke-dash-array` and value `10`


```java
Line line1 = new Line(20, 40, 270, 40);
line1.getStrokeDashArray().addAll(25d, 20d, 5d, 20d);

Line line2 = new Line(20, 60, 270, 60);
line2.getStrokeDashArray().addAll(50d, 40d);

Line line3 = new Line(20, 80, 270, 80);
line3.getStrokeDashArray().addAll(25d, 10d);

Line line4 = new Line(20, 100, 270, 100);
line4.getStrokeDashArray().addAll(2d);

Line line5 = new Line(20, 120, 270, 120);
line5.getStrokeDashArray().addAll(2d, 21d);

pane.getChildren().addAll(line1, line2, line3, line4, line5);
```




http://www.java2s.com/Tutorials/Java/JavaFX/0040__JavaFX_Line.htm