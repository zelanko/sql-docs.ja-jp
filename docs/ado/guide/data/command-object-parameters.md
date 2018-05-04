---
title: オブジェクトのパラメーターをコマンド |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Command object [ADO], parameters
ms.assetid: 10e7ef4a-78bf-4e91-931e-cbc6c065dd4c
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fa60d076d6c4a3d4eea2092db92c3006d4fd0905
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="command-object-parameters"></a>コマンド オブジェクトのパラメーター
前に説明したトピック[作成し、簡単なコマンドを実行する](../../../ado/guide/data/creating-and-executing-a-simple-command.md)です。 使用して、興味深い、[コマンド](../../../ado/reference/ado-api/command-object-ado.md)オブジェクトが SQL コマンドのパラメーター化する、次の例で示すようにします。 この変更により、パラメーターのたびに、別の値を渡して、コマンドを再利用することです。 [プロパティの準備ができている](../../../ado/reference/ado-api/prepared-property-ado.md)プロパティを**コマンド**にオブジェクトが設定されている**true**、ADO で指定されたコマンドのコンパイルにプロバイダーが必要になります[CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md)を初めて実行する前にします。 メモリ内でコンパイル済みのコマンドも保持されます。 少しがパフォーマンスの向上、コマンドがその後呼び出されるたびに結果を準備するためのオーバーヘッドが原因で実行される最初の時間のコマンドの実行はこの低下します。 そのため、1 つ以上の時間を使用する場合にのみ、コマンドを準備する必要があります。  
  
```  
'BeginManualParamCmd  
    On Error GoTo ErrHandler:  
  
    Dim objConn As New ADODB.Connection  
    Dim objCmd As New ADODB.Command  
    Dim objParm1 As New ADODB.Parameter  
    Dim objRs As New ADODB.Recordset  
  
    ' Set the CommandText as a parameterized SQL query.  
    objCmd.CommandText = "SELECT OrderID, OrderDate, " & _  
                         "RequiredDate, ShippedDate " & _  
                         "FROM Orders " & _  
                         "WHERE CustomerID = ? " & _  
                         "ORDER BY OrderID"  
    objCmd.CommandType = adCmdText  
  
    ' Prepare command because we will be executing it more than once.  
    objCmd.Prepared = True  
  
    ' Create new parameter for CustomerID. Initial value is ALFKI.  
    Set objParm1 = objCmd.CreateParameter("CustId", adChar, _  
                    adParamInput, 5, "ALFKI")  
    objCmd.Parameters.Append objParm1  
  
    ' Connect to the data source.  
    Set objConn = GetNewConnection  
    objCmd.ActiveConnection = objConn  
  
    ' Execute once and display.  
    Set objRs = objCmd.Execute  
  
    Debug.Print objParm1.Value  
    Do While Not objRs.EOF  
        Debug.Print vbTab & objRs(0) & vbTab & objRs(1) & vbTab & _  
                    objRs(2) & vbTab & objRs(3)  
        objRs.MoveNext  
    Loop  
  
    ' .Set new param value, re-execute command, and display.  
    objCmd("CustId") = "CACTU"  
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
'EndManualParamCmd  
  
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
  
 すべてのプロバイダーは、準備されたコマンドをサポートします。 このプロパティに設定するとすぐに、エラーを返す場合がありますが、プロバイダーがコマンドの準備をサポートしていない場合**True**です。 エラーが返されない場合、要求をコマンド ウィンドウとセットを準備するのには無視されます、 **Prepared**プロパティを**false**です。
