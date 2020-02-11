---
title: 名前付きコマンド |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- named commands [ADO]
- commands [ADO]
ms.assetid: 5a0ec8f9-5ba3-4f9f-b80d-2073aa049586
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 928ac3b1d3cd753ded0bcf4337f10a654c9a3dc0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67924823"
---
# <a name="named-commands"></a>名前付きコマンド
[単純なコマンドを作成して実行すると](../../../ado/guide/data/creating-and-executing-a-simple-command.md)、コマンドを実行する1つの方法が表示されます。 別の方法として、名前付きコマンドを作成し、この名前付きコマンドを**接続**オブジェクト ( **Command**オブジェクトの**ActiveConnection**プロパティに割り当てられている) で直接呼び出すことができます。 コマンドに名前を付けるということは、**コマンド**オブジェクトの**name**プロパティに名前を割り当てることを意味します。 たとえば、次のように入力します。  
  
```  
objCmd.Name = "GetCustomers"  
objCmd.ActiveConnection = objConn  
objConn.GetCustomers objRs  
```  
  
 名前付きコマンドは、**接続**オブジェクトの "カスタムメソッド" のように機能します。 コマンドの結果は、この "カスタムメソッド" の out パラメーターとして返されます。  
  
 この機能の例を次に示します。  
  
```  
'BeginNamedCmd  
    On Error GoTo ErrHandler:  
  
    Dim objConn As New ADODB.Connection  
    Dim objCmd As New ADODB.Command  
    Dim objRs As New ADODB.Recordset  
  
    ' Connect to the data source.  
    Set objConn = GetNewConnection  
  
    objCmd.CommandText = "SELECT CustomerID, CompanyName FROM Customers"  
    objCmd.CommandType = adCmdText  
  
    'Name the command.  
    objCmd.Name = "GetCustomers"  
  
    objCmd.ActiveConnection = objConn  
  
    ' Execute using Command.Name from the Connection.  
    objConn.GetCustomers objRs  
  
    ' Display.  
    Do While Not objRs.EOF  
        Debug.Print objRs(0) & vbTab & objRs(1)  
        objRs.MoveNext  
    Loop  
  
    'clean up  
    objRs.Close  
    objConn.Close  
    Set objRs = Nothing  
    Set objConn = Nothing  
    Set objCmd = Nothing  
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
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
'EndNamedCmd  
```  
  
## <a name="see-also"></a>参照  
 [Connection オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)
