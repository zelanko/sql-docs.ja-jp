---
title: "プロパティの例 (VB) を最適化 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: VB
helpviewer_keywords: Optimize property [ADO], Visual Basic example
ms.assetid: 652194af-cfa4-4aa0-a6d6-fa409bbc3f98
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a9c42c39a9d91b78bb57fc9ae1731c3d61513088
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="optimize-property-example-vb"></a>プロパティの例 (VB) の最適化します。
この例で、[フィールド](../../../ado/reference/ado-api/field-object.md)オブジェクトの動的**最適化**プロパティです。 ***Zip***のフィールド、***作成者***テーブルに、 ***Pubs***データベースのインデックスが付いていません。 設定、[最適化](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md)プロパティを**True**上、 ***zip***フィールド承認のパフォーマンスを向上させるインデックスを作成する ADO、 [を見つける](../../../ado/reference/ado-api/find-method-ado.md)メソッドです。  
  
```  
'BeginOptimizeVB  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
    'To integrate this code  
    'replace the data source and initial catalog values  
    'in the connection string.  
  
    ' Declare the recordset and connection variables.  
    Dim Cnxn As ADODB.Connection  
    Dim rstAuthors As ADODB.Recordset  
    Dim strCnxn As String  
    Dim strSQLAuthors As String  
  
     ' Open connection.  
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" & _  
        "Initial Catalog='Pubs';Integrated Security='SSPI';"  
    Set Cnxn = New ADODB.Connection  
    Cnxn.Open strCnxn  
  
     ' open recordset client-side to enable index creation.  
    Set rstAuthors = New ADODB.Recordset  
    rstAuthors.CursorLocation = adUseClient  
    strSQLAuthors = "SELECT * FROM Authors"  
    rstAuthors.Open strSQLAuthors, Cnxn, adOpenStatic, adLockReadOnly, adCmdText  
     ' Create the index.  
    rstAuthors!zip.Properties("Optimize") = True  
     ' Find Akiko Yokomoto  
    rstAuthors.Find "zip = '94595'"  
  
     ' Show results.  
    Debug.Print rstAuthors!au_fname & " " & rstAuthors!au_lname & " " & _  
             rstAuthors!address & " " & rstAuthors!city & " " & rstAuthors!State  
    rstAuthors!zip.Properties("Optimize") = False  'Delete the index.  
  
    ' Clean up.  
    rstAuthors.Close  
    Cnxn.Close  
    Set rstAuthors = Nothing  
    Set Cnxn = Nothing  
    Exit Sub  
  
ErrorHandler:  
    ' clean up  
    If Not rstAuthors Is Nothing Then  
        If rstAuthors.State = adStateOpen Then rstAuthors.Close  
    End If  
    Set rstAuthors = Nothing  
  
    If Not Cnxn Is Nothing Then  
        If Cnxn.State = adStateOpen Then Cnxn.Close  
    End If  
    Set Cnxn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
'EndOptimizeVB  
```  
  
## <a name="see-also"></a>参照  
 [Field オブジェクト](../../../ado/reference/ado-api/field-object.md)   
 [Optimize プロパティ - 動的 (ADO)](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md)
