---
description: Create メソッドの例 (VB)
title: Create メソッドの例 (VB) |Microsoft Docs
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
- Create method [ADOX], Visual Basic example
ms.assetid: d7ea0244-596a-404e-8f30-71cadab8d8fc
author: rothja
ms.author: jroth
ms.openlocfilehash: 40a50d983365285ccf0001f46450613bdf78bd87
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88440204"
---
# <a name="create-method-example-vb"></a>Create メソッドの例 (VB)
次のコードは、 [create](../../../ado/reference/adox-api/create-method-adox.md) メソッドを使用して新しい Microsoft Jet データベースを作成する方法を示しています。  
  
```  
Attribute VB_Name = "Create"  
Option Explicit  
  
' BeginCreateDatabaseVB  
Sub CreateDatabase()  
    On Error GoTo CreateDatabaseError  
  
    Dim cat As New ADOX.Catalog  
    cat.Create "Provider='Microsoft.Jet.OLEDB.4.0';Data Source='new.mdb'"  
  
    'Clean up  
    Set cat = Nothing  
    Exit Sub  
  
CreateDatabaseError:  
    Set cat = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndCreateDatabaseVB  
```  
  
## <a name="see-also"></a>参照  
 [Catalog オブジェクト (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Create メソッド (ADOX)](../../../ado/reference/adox-api/create-method-adox.md)
