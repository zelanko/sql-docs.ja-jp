---
title: 接続オブジェクトのメソッドとしてストアド プロシージャの呼び出し |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- calling stored procedures [ADO]
- stored procedures [ADO]
- commands [ADO]
ms.assetid: 35ffdb79-a931-4271-a3bb-0cd804cf173e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3202b607f3971dd1fcad2c3ae5e0ed83a667e923
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62472803"
---
# <a name="calling-a-stored-procedure-as-a-method-on-a-connection-object"></a>Connection オブジェクトに対するメソッドとしてストアド プロシージャを呼び出す
関連するオープンでネイティブ メソッドの場合と同様に、ストアド プロシージャを呼び出すことができます**接続**オブジェクト。 名前付きコマンドを呼び出すことに似ています、**接続**オブジェクト。  
  
 次の Visual Basic のコード例では、CustOrdersOrders、便宜上、ここでもう一度表示と呼ばれる、Northwind サンプル データベースでストアド プロシージャを呼び出します。  
  
```  
CREATE PROCEDURE CustOrdersOrders @CustomerID nchar(5) AS  
SELECT OrderID, OrderDate, RequiredDate, ShippedDate  
FROM Orders  
WHERE CustomerID = @CustomerID  
ORDER BY OrderID  
```  
  
 次のコード例は、関連するオープンでネイティブ メソッドの場合と同様に、ストアド プロシージャを呼び出す方法を示します**接続**オブジェクト。  
  
```  
Const DS = "MySQLServer"  
Const DB = "Northwind"  
Const DP = "SQLOLEDB"  
  
Dim objConn As New ADODB.Connection  
Dim objRs As New ADODB.Recordset  
Dim objComm As New ADODB.Command  
  
ConnectionString = "Provider=" & DP & _  
                   ";Data Source=" & DS & _  
                   ";Initial Catalog=" & DB & _  
                   ";Integrated Security=SSPI;"  
  
' Connect to the data source.  
objConn.Open ConnectionString  
  
' Set a stored procedure  
  
Set objComm.ActiveConnection = objConn  
  
' Execute the stored procedure on  
' the active connection object...  
'    "ALFKI" is the required input parameter,  
'    objRs is the resultant output variable.  
  
' Display the result.  
Debug.Print "Results returned from sp_CustOrdersOrders for ALFKI: "  
Do While Not objRs.EOF  
    Debug.Print vbTab & objRs(0) & vbTab & objRs(1) & vbTab & _  
                objRs(2) & vbTab & objRs(3)  
    objRs.MoveNext  
 Loop  
  
'Clean up.  
objRs.Close  
objConn.Close  
Set objRs = Nothing  
Set objConn = Nothing  
Set objComm = Nothing  
```  
  
## <a name="see-also"></a>参照  
 [Connection オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)
