---
title: トランザクションの制御 (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- transactions [ADO]
ms.assetid: 189240e8-3ffa-4024-81a9-c6cb5d17eee0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3a8a13ee7637c0cb16e33e626a218e28242dabf4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67925775"
---
# <a name="controlling-transactions-ado"></a>トランザクションの制御 (ADO)
ADO は、接続オブジェクトの**BeginTrans**、 **CommitTrans**、および**RollbackTrans**の各メソッドを使用して **、接続内**のトランザクション処理をサポートします。 ADO でトランザクション処理を実装する一般的な考え方を、次の単純なコードスニペットに示します。  
  
```  
Const DS = "MySqlServer"  
Const DB = "Northwind"  
Const DP = "SQLOLEDB"  
  
Dim oConn As ADODB.Connection  
Dim oRs As ADODB.Recordset  
Dim sConn As String  
  
sConn = "Provider=" & DP & _  
          ";Data Source=" & DS & _  
          ";Initial Catalog=" & DB & _  
          ";Integrated Security=SSPI;"  
  
sSQL = "SELECT ProductID, ProductName FROM Products"  
  
Set oConn = New ADODB.Connection  
oConn.Open sConn  
  
' Create and Open the Recordset object.  
Set oRs = New ADODB.Recordset  
oRs.Open sSQL, oConn, adOpenStatic, adLockOptimistic, adCmdText  
  
If oRs.RecordCount > 1 Then  
  
    oRs.MoveFirst  
    Id1 = oRs("ProductID")  
    Name1 = oRs("ProductName")  
    oRs.MoveNext  
    Id2 = oRs("ProductID")  
    Name2 = oRs("ProductName")  
  
    q = "Switch ID's of " & Name1 & " and " & Name2 & "?"  
    If MsgBox(q, vbYesNo) = vbYes Then  
        oRs.MoveFirst  
        oRs("ProductName") = Name2  
        oRs.Update  
  
        oRs.MoveNext  
        oRs("ProductName") = Name1  
        oRs.Update  
  
        If MsgBox("Save changes?", vbYesNo) = vbYes Then  
  
        Else  
  
        End If  
    End If  
  
End If  
  
oRs.Close  
oConn.Close  
```  
  
 ここでは、2つのレコードが1つの操作単位として更新され、2つの製品名が入れ替えられているか、まったく変更されていないことを確認するために、トランザクション処理が使用されています。  
  
 トランザクション処理の詳細については[、「データの更新と永続](../../../ado/guide/data/updating-and-persisting-data.md)化」を参照してください。
