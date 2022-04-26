```VBA
Sub insertPointBefor3() 
	Dim cell As Range 
	
	For Each cell In Selection.Cells 
		If cell.HasFormula = False Then 
			cell.Value = cell.Value / 1000 
		End If 
	Next 
End Sub
```