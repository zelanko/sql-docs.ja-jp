---
description: SortOrder プロパティの例 (VB)
title: 順序のプロパティの例 (VB) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- SortOrder property [ADOX]
ms.assetid: d9502254-d89b-4bcb-94f1-6418f89e7f30
author: rothja
ms.author: jroth
ms.openlocfilehash: 089c4e7f402e374ab4af43c683270ad488c0f8bb
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2020
ms.locfileid: "88769361"
---
# <a name="sortorder-property-example-vb"></a>SortOrder プロパティの例 (VB)
この例では、インデックスの[Columns](./columns-collection-adox.md)コレクションに追加された[列](./column-object-adox.md)の[順序](./sortorder-property-adox.md)[付け](./index-object-adox.md)プロパティを示します。 このコードでは、 **Employees** テーブルの Country 列に昇順のインデックスが追加され、レコードが表示されます。 次に、このコードにより、 **Employees** テーブルの Country 列に降順のインデックスが追加され、レコードが再び表示されます。 昇順と降順のインデックスの違いを示します。  
  
```  
' BeginSortOrderVB  
Sub Main()  
    On Error GoTo SortOrderXError  
  
    Dim cnn As New ADODB.Connection  
    Dim catNorthwind As New ADOX.Catalog  
    Dim idxAscending As New ADOX.Index  
    Dim idxDescending As New ADOX.Index  
    Dim rstEmployees As New ADODB.Recordset  
  
    ' Connect to the catalog.  
    cnn.Open "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source='Northwind.mdb';"  
    Set catNorthwind.ActiveConnection = cnn  
  
    ' Append Country column to new index.  
    idxAscending.Columns.Append "Country"  
    idxAscending.Columns("Country").SortOrder = adSortAscending  
    idxAscending.Name = "Ascending"  
    idxAscending.IndexNulls = adIndexNullsAllow  
  
    'Append new index to Employees table.  
    catNorthwind.Tables("Employees").Indexes.Append idxAscending  
  
    rstEmployees.Index = idxAscending.Name  
    rstEmployees.Open "Employees", cnn, adOpenKeyset, _  
        adLockOptimistic, adCmdTableDirect  
  
    With rstEmployees  
        .MoveFirst  
        Debug.Print "Index = " & .Index  
        Debug.Print "  Country - Name"  
  
        ' Enumerate the Recordset. The value of the  
        ' IndexNulls property will determine if the newly  
        ' added record appears in the output.  
        Do While Not .EOF  
            Debug.Print "    " & !Country & " - " & _  
                !FirstName & " " & !LastName  
            .MoveNext  
        Loop  
  
        .Close  
    End With  
  
    ' Append Country column to new index.  
    idxDescending.Columns.Append "Country"  
    idxDescending.Columns("Country").SortOrder = adSortDescending  
    idxDescending.Name = "Descending"  
    idxDescending.IndexNulls = adIndexNullsAllow  
  
    'Append descending index to Employees table.  
    catNorthwind.Tables("Employees").Indexes.Append idxDescending  
  
    rstEmployees.Index = idxDescending.Name  
    rstEmployees.Open "Employees", cnn, adOpenKeyset, _  
        adLockOptimistic, adCmdTableDirect  
  
    With rstEmployees  
        .MoveFirst  
        Debug.Print "Index = " & .Index  
        Debug.Print "  Country - Name"  
  
        ' Enumerate the Recordset. The value of the  
        ' IndexNulls property will determine if the newly  
        ' added record appears in the output.  
        Do While Not .EOF  
            Debug.Print "    " & !Country & " - " & _  
                !FirstName & " " & !LastName  
            .MoveNext  
        Loop  
  
        .Close  
    End With  
  
    ' Delete new indexes because this is a demonstration.  
    catNorthwind.Tables("Employees").Indexes.Delete idxAscending.Name  
    catNorthwind.Tables("Employees").Indexes.Delete idxDescending.Name  
  
    'Clean up  
    cnn.Close  
    Set catNorthwind = Nothing  
    Set idxAscending = Nothing  
    Set idxDescending = Nothing  
    Set rstEmployees = Nothing  
    Set cnn = Nothing  
    Exit Sub  
  
SortOrderXError:  
  
    Set catNorthwind = Nothing  
    Set idxAscending = Nothing  
    Set idxDescending = Nothing  
  
    If Not rstEmployees Is Nothing Then  
        If rstEmployees.State = adStateOpen Then rstEmployees.Close  
    End If  
    Set rstEmployees = Nothing  
  
    If Not cnn Is Nothing Then  
        If cnn.State = adStateOpen Then cnn.Close  
    End If  
    Set cnn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndSortOrderVB  
```  
  
## <a name="see-also"></a>参照  
 [Column オブジェクト (ADOX)](./column-object-adox.md)   
 [Columns コレクション (ADOX)](./columns-collection-adox.md)   
 [Index オブジェクト (ADOX)](./index-object-adox.md)   
 [SortOrder プロパティ (ADOX)](./sortorder-property-adox.md)