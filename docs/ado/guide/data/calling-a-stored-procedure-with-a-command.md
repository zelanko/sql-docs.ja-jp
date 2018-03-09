---
title: "コマンドでストアド プロシージャを呼び出す |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- calling stored procedures [ADO]
- stored procedures [ADO]
- commands [ADO]
ms.assetid: 685f7652-2271-4ede-b552-2eeb8c756b4c
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 613c9d2e018360798eb71748473750712dec461e
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="calling-a-stored-procedure-with-a-command"></a>コマンドでストアド プロシージャを呼び出す
コマンドを使用して、ストアド プロシージャを呼び出すことができます。 このトピックの最後に、コード サンプルは、次のように定義されている CustOrdersOrders と呼ばれる、Northwind サンプル データベース内のストアド プロシージャを参照します。  
  
```  
CREATE PROCEDURE CustOrdersOrders @CustomerID nchar(5) AS  
SELECT OrderID, OrderDate, RequiredDate, ShippedDate  
FROM Orders  
WHERE CustomerID = @CustomerID  
ORDER BY OrderID  
```  
  
 ストアド プロシージャの呼び出しおよび定義する方法に関する詳細について、SQL Server のマニュアルを参照してください。  
  
 このストアド プロシージャで使用されるコマンドのような[Command オブジェクトのパラメーター](../../../ado/guide/data/command-object-parameters.md)です。 顧客の ID パラメーターを受け取りし、その顧客の注文に関する情報を返します。 次のコード サンプルは、ADO のソースとしてこのストアド プロシージャを使用**Recordset**です。  
  
 ADO の別の機能にアクセスするストアド プロシージャを使用することができます。**パラメーター**コレクション**更新**メソッドです。 このメソッドを使用すると、実行時に、コマンドに必要なパラメーターに関するすべての情報で ADO 自動的に入力します。 は、パフォーマンスの低下、この方法で ADO は、パラメーターについては、データ ソースをクエリする必要があります。  
  
 次のコード サンプルと内のコードの間で他の重要な相違点が存在[Command オブジェクトのパラメーター](../../../ado/guide/data/command-object-parameters.md)パラメーターを手動で入力した場所、します。 まず、このコードは設定されません、 **Prepared**プロパティを**True**のため、SQL Server のストアド プロシージャの定義でプリコンパイル済みです。 2 番目、 **CommandType**のプロパティ、**コマンド**にオブジェクトが変更された**adCmdStoredProc** ADO コマンドがストアド プロシージャをしたことを通知するために 2 番目の例です。  
  
 最後に、2 番目の例では、パラメーター参照する必要にインデックスを使用して、値を設定するときにデザイン時に、パラメーターの名前がわからないためです。 新しい設定することができる場合は、パラメーターの名前が分かって[NamedParameters](../../../ado/reference/ado-api/namedparameters-property-ado.md)のプロパティ、**コマンド**を True にオブジェクトおよびプロパティの名前を参照してください。 ストアド プロシージャで最初のパラメーターの位置が示されている理由をでしょうか (@CustomerID) は、0 ではなく 1 (`objCmd(1) = "ALFKI"`)。 これは、パラメーター 0 には、SQL Server のストアド プロシージャからの戻り値が含まれているためです。  
  
```  
'BeginAutoParamCmd  
    On Error GoTo ErrHandler:  
  
    Dim objConn As New ADODB.Connection  
    Dim objCmd As New ADODB.Command  
    Dim objParm1 As New ADODB.Parameter  
    Dim objRs As New ADODB.Recordset  
  
    ' Set CommandText equal to the stored procedure name.  
    objCmd.CommandText = "CustOrdersOrders"  
    objCmd.CommandType = adCmdStoredProc  
  
    ' Connect to the data source.  
    Set objConn = GetNewConnection  
    objCmd.ActiveConnection = objConn  
  
    ' Automatically fill in parameter info from stored procedure.  
    objCmd.Parameters.Refresh  
  
    ' Set the param value.  
    objCmd(1) = "ALFKI"  
  
    ' Execute once and display...  
    Set objRs = objCmd.Execute  
  
    Debug.Print objParm1.Value  
    Do While Not objRs.EOF  
        Debug.Print vbTab & objRs(0) & vbTab & objRs(1) & vbTab & _  
                    objRs(2) & vbTab & objRs(3)  
        objRs.MoveNext  
    Loop  
  
    ' ...then set new param value, re-execute command, and display.  
    objCmd(1) = "CACTU"  
    Set objRs = objCmd.Execute  
  
    Debug.Print objParm1.Value  
    Do While Not objRs.EOF  
        Debug.Print vbTab & objRs(0) & vbTab & objRs(1) & vbTab & _  
                    objRs(2) & vbTab & objRs(3)  
        objRs.MoveNext  
    Loop  
  
    'clean up  
    objRs.Close  
    objConn.Close  
    Set objRs = Nothing  
    Set objConn = Nothing  
    Set objCmd = Nothing  
    Set objParm1 = Nothing  
    Exit Sub  
  
ErrHandler:  
    'clean up  
    If objRs.State = adStateOpen Then  
        objRs.Close  
    End If  
  
    If objConn.State = adStateOpen Then  
        objConn.Close  
    End If  
  
    Set objRs = Nothing  
    Set objConn = Nothing  
    Set objCmd = Nothing  
    Set objParm1 = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
'EndAutoParamCmd  
  
'BeginNewConnection  
Private Function GetNewConnection() As ADODB.Connection  
    Dim oCn As New ADODB.Connection  
    Dim sCnStr As String  
  
    sCnStr = "Provider='SQLOLEDB';Data Source='MySqlServer';" & _  
             "Integrated Security='SSPI';Initial Catalog='Northwind';"  
    oCn.Open sCnStr  
  
    If oCn.State = adStateOpen Then  
        Set GetNewConnection = oCn  
    End If  
  
End Function  
'EndNewConnection  
```  
  
## <a name="see-also"></a>参照  
 [サポート技術情報の記事 117500](http://go.microsoft.com/fwlink/?LinkId=117500)
