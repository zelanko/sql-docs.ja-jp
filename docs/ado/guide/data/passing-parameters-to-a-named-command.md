---
title: 名前付きコマンドにパラメーターを渡す |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- named commands [ADO]
- commands [ADO], passing parameters to a named command
ms.assetid: 36e0cdbe-7f50-40f5-af0d-700f5d8dc75a
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: db51630bf9629920ce91af22fc731f3a5c919fd0
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="passing-parameters-to-a-named-command"></a>名前付きコマンドにパラメーターを渡す
コマンドの結果として渡される出力と同様、*アウト*名前付きのコマンドでは、パラメーターの変数パラメーター化コマンドへのされてとして渡された*で*変数名前付きのコマンドをします。  
  
 次のコード例のすべての注文の取得を行うとにより配置された顧客の**CustomerID** "ALKFI"は、Northwind データベースからです。 値**CustomerID**は名前付きのコマンドが呼び出されるときに指定します。  
  
```  
Const DS = "MySqlServer"  
Const DB = "Northwind"  
Const DP = "SQLOLEDB"  
  
Dim objConn As New ADODB.Connection  
Dim objRs As New ADODB.Recordset  
Dim objComm As New ADODB.Command  
  
CommandText = "SELECT OrderID, OrderDate, " & _  
                     "RequiredDate, ShippedDate " & _  
                     "FROM Orders " & _  
                     "WHERE CustomerID = ? " & _  
                     "ORDER BY OrderID"  
  
ConnectionString = "Provider=" & DP & _  
                   ";Data Source=" & DS & _  
                   ";Initial Catalog=" & DB & _  
                   ";Integrated Security=SSPI;"  
  
' Connect to the data source.  
objConn.Open ConnectionString  
  
' Set a named command.  
objComm.CommandText = CommandText  
objComm.CommandType = adCmdText  
objComm.Name = "GetOrdersOf"  
Set objComm.ActiveConnection = objConn  
  
' Call the named command, passing a CustomerID value  
' as the input parameter.   
'    "ALFKI" is the required input parameter,  
'    objRs is the resultant output variable.  
objConn.GetOrdersOf "ALKFI", objRs  
  
' Display the result.  
Debug.Print "All orders by ALFKI:"  
Do While Not objRs.EOF  
    Debug.Print vbTab & objRs(0) & vbTab & objRs(1) & vbTab & _  
                objRs(2) & vbTab & objRs(3)  
    objRs.MoveNext  
Loop  
  
' Clean up.  
objRs.Close  
objConn.Close  
Set objRs = Nothing  
Set objConn = Nothing  
Set objComm = Nothing  
```  
  
 すべての入力パラメーターは、任意の出力変数を付ける必要があります、パラメーターのデータ型と一致する必要がありますまたは対応するフィールドのものに変換できることを確認します。 次のステートメント-  
  
```  
objConn.GetOrdersOf 12345, objRs  
```  
  
 — の必須の入力パラメーターであるため、一致しないデータ型のエラーが発生、**文字列**の種類のではありません、**整数**型です。  
  
 次の呼び出し。  
  
```  
objConn.GetOrdersOf "12345", objRs  
```  
  
 — 有効ですが、データベースにこのようなレコードが存在しないために、設定、空の結果を得られます。  
  
## <a name="see-also"></a>参照  
 [Connection オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)
