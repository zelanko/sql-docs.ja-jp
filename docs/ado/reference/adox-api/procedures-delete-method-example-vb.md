---
title: "プロシージャの削除の方法の例 (VB) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Delete method [ADOX], Visual Basic example
ms.assetid: 94f1ac93-e778-4a40-a85e-94bce5316ac7
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 83322007d526d1efa8fa72c5a982882dba52ef12
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="procedures-delete-method-example-vb"></a>プロシージャの削除の方法の例 (VB)
次のコードを使用してプロシージャを削除する方法の例、[削除](../../../ado/reference/adox-api/delete-method-adox-collections.md)のメソッド、[プロシージャ](../../../ado/reference/adox-api/procedures-collection-adox.md)コレクション。  
  
```  
' BeginDeleteProcedureVB  
Sub Main()  
    On Error GoTo DeleteProcedureError  
  
    Dim cat As New ADOX.Catalog  
  
    ' Open the catalog.  
    cat.ActiveConnection = _  
        "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source='Northwind.mdb';"  
  
    ' Delete the procedure.  
    cat.Procedures.Delete "CustomerById"  
  
    'Clean up.  
    Set cat.ActiveConnection = Nothing  
    Set cat = Nothing  
    Exit Sub  
  
DeleteProcedureError:  
    Set cat = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndDeleteProcedureVB  
```  
  
## <a name="see-also"></a>参照  
 [ActiveConnection プロパティ (ADOX)](../../../ado/reference/adox-api/activeconnection-property-adox.md)   
 [カタログ オブジェクト (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Delete メソッド (ADOX コレクション)](../../../ado/reference/adox-api/delete-method-adox-collections.md)   
 [プロシージャのオブジェクト (ADOX)](../../../ado/reference/adox-api/procedure-object-adox.md)   
 [プロシージャのコレクション (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)

