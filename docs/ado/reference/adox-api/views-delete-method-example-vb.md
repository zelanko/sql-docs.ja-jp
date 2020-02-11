---
title: Views Delete メソッドの例 (VB) |Microsoft Docs
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
- Delete method [ADOX]
ms.assetid: 17df2a83-4166-4df8-8c17-0a33aaac8582
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8077e22b2bdbd9fe55cca1ea7306443ee9d61ce7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67964743"
---
# <a name="views-delete-method-example-vb"></a>Views Delete メソッドの例 (VB)
次のコードは、 [delete](../../../ado/reference/adox-api/delete-method-adox-collections.md)メソッドを使用して、カタログからビューを削除する方法を示しています。  
  
```  
' BeginDeleteViewVB  
Sub Main()  
    On Error GoTo DeleteViewError  
  
    Dim cat As New ADOX.Catalog  
  
    ' Open the catalog  
    cat.ActiveConnection = "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source='Northwind.mdb';"  
  
    'Delete the View  
    cat.Views.Delete "AllCustomers"  
  
    'Clean up  
    Set cat.ActiveConnection = Nothing  
    Set cat = Nothing  
    Exit Sub  
  
DeleteViewError:  
    Set cat = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndDeleteViewVB  
```  
  
## <a name="see-also"></a>参照  
 [Delete メソッド (ADOX Collections)](../../../ado/reference/adox-api/delete-method-adox-collections.md)   
 [Views コレクション (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)
