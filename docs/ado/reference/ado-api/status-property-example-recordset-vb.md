---
title: "ステータスのプロパティの例 (レコード セット) (VB) |Microsoft ドキュメント"
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
- Status property [ADO Recordset], Visual Basic example
ms.assetid: e37b4d46-380d-4615-b4bb-e1a7b0851771
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 47093e6eca66a135034a63bc2f05041555a1481b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="status-property-example-recordset-vb"></a>ステータスのプロパティの例 (レコード セット) (VB)
この例では、[ステータス](../../../ado/reference/ado-api/status-property-ado-recordset.md)バッチ更新の前に、バッチ操作で変更されたレコードを表示するプロパティです。  
  
```  
'BeginStatusRecordsetVB  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
    'To integrate this code  
    'replace the data source and initial catalog values  
    'in the connection string  
  
    ' connection and recordset variables  
    Dim rstTitles As ADODB.Recordset  
    Dim Cnxn As ADODB.Connection  
    Dim strCnxn As String  
    Dim strSQLTitles As String  
  
     ' open connection  
    Set Cnxn = New ADODB.Connection  
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" & _  
        "Initial Catalog='Pubs';Integrated Security='SSPI';"  
    Cnxn.Open strCnxn  
  
     ' open recordset for batch update  
    Set rstTitles = New ADODB.Recordset  
    strSQLTitles = "Titles"  
    rstTitles.Open strSQLTitles, Cnxn, adOpenKeyset, adLockBatchOptimistic, adCmdTable  
  
    ' change the type of psychology titles  
    Do Until rstTitles.EOF  
        If Trim(rstTitles!Type) = "psychology" Then rstTitles!Type = "self_help"  
        rstTitles.MoveNext  
    Loop  
  
    ' display Title ID and status  
    rstTitles.MoveFirst  
    Do Until rstTitles.EOF  
        If rstTitles.Status = adRecModified Then  
            Debug.Print rstTitles!title_id & " - Modified"  
        Else  
            Debug.Print rstTitles!title_id  
        End If  
    rstTitles.MoveNext  
    Loop  
  
    ' clean up  
    rstTitles.Close  
    Cnxn.Close  
    Set rstTitles = Nothing  
    Set Cnxn = Nothing  
    Exit Sub  
  
ErrorHandler:  
    ' clean up  
    If Not rstTitles Is Nothing Then  
        If rstTitles.State = adStateOpen Then  
            ' Cancel the update because this is a demonstration  
            rstTitles.CancelBatch  
            rstTitles.Close  
        End If  
    End If  
    Set rstTitles = Nothing  
  
    If Not Cnxn Is Nothing Then  
        If Cnxn.State = adStateOpen Then Cnxn.Close  
    End If  
    Set Cnxn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
'EndStatusRecordsetVB  
```  
  
## <a name="see-also"></a>参照  
 [Status プロパティ (ADO レコード セット)](../../../ado/reference/ado-api/status-property-ado-recordset.md)
