---
description: カタログ ActiveConnection プロパティの例 (VB)
title: Catalog ActiveConnection プロパティの例 (VB) |Microsoft Docs
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
- ActiveConnection property [ADOX], Visual Basic example
ms.assetid: bb3274b1-764d-43a7-a49f-ef55680ecd26
author: rothja
ms.author: jroth
ms.openlocfilehash: 4895f1ec08a0f10c93335fc36954f3a9098ffce4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88440414"
---
# <a name="catalog-activeconnection-property-example-vb"></a>カタログ ActiveConnection プロパティの例 (VB)
[ActiveConnection](../../../ado/reference/adox-api/activeconnection-property-adox.md)プロパティを有効な開いている接続に設定すると、カタログが開きます。 開いているカタログから、そのカタログ内に含まれているスキーマオブジェクトにアクセスできます。  
  
```  
' BeginOpenConnectionVB  
Sub Main()  
    On Error GoTo OpenConnectionError  
  
    Dim cnn As New ADODB.Connection  
    Dim cat As New ADOX.Catalog  
  
    cnn.Open "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source= 'Northwind.mdb';"  
    Set cat.ActiveConnection = cnn  
    Debug.Print cat.Tables(0).Type  
  
    'Clean up  
    cnn.Close  
    Set cat = Nothing  
    Set cnn = Nothing  
    Exit Sub  
  
OpenConnectionError:  
  
    Set cat = Nothing  
  
    If Not cnn Is Nothing Then  
        If cnn.State = adStateOpen Then cnn.Close  
    End If  
    Set cnn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndOpenConnectionVB  
```  
  
 **ActiveConnection**プロパティを有効な接続文字列に設定すると、カタログも "開く" ことができます。  
  
```  
Attribute VB_Name = "Catalog"  
```  
  
## <a name="see-also"></a>参照  
 [ActiveConnection プロパティ (ADOX)](../../../ado/reference/adox-api/activeconnection-property-adox.md)   
 [Catalog オブジェクト (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Table オブジェクト (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)   
 [Tables コレクション (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)   
 [Type プロパティ (テーブル) (ADOX)](../../../ado/reference/adox-api/type-property-table-adox.md)
