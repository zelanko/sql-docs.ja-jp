---
title: "接続オブジェクトを使用して |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connections [ADO]
ms.assetid: 4b34f971-5699-43e7-9b15-137d334fa66e
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: da71dc67a1fd6a17f75c5aceaf7a88dce7d328ab
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="using-a-connection-object"></a>接続オブジェクトを使用します。
開始する前に、**接続**オブジェクト、データ ソースと接続の種類に関する特定の情報を定義する必要があります。 この情報の大部分が保持している、 *ConnectionString*のパラメーター、 [Open メソッド](../../../ado/reference/ado-api/open-method-ado-connection.md)上、**接続**オブジェクト、または、 [ConnectionStringプロパティ](../../../ado/reference/ado-api/connectionstring-property-ado.md)上、**接続**オブジェクト。 接続文字列は、セミコロンで区切って、単一引用符で囲まれた値を使用する引数と値のペアの一覧で構成されます。 例:  
  
```  
Dim sConn As String  
sConn = "Provider='SQLOLEDB';Data Source='MySqlServer';" & _  
             "Initial Catalog='Northwind';Integrated Security='SSPI';"  
```  
  
> [!NOTE]
>  接続文字列でも、ODBC データ ソース名 (DSN) またはデータ リンク (UDL) ファイルを指定することができます。 Dsn の詳細については、次を参照してください。[データ ソースを管理する](../../../odbc/admin/managing-data-sources.md)ODBC プログラマ リファレンスにします。 Udl の詳細については、次を参照してください。[データ リンク API の概要](http://msdn.microsoft.com/en-us/95c180ea-bd4f-4dca-b95a-576afd135bbc)OLE DB プログラマーズ リファレンスです。  
  
 通常、呼び出すことによって接続を確立する、 **Connection.Open**を適切なメソッド、*接続文字列*パラメーターとして。 Visual Basic コード スニペットを次に例を示します。  
  
```  
Dim oConn As ADODB.Connection  
Dim oRs As ADODB.Recordset  
Dim sConn As String  
Dim sSQL as String  
  
' Open a connection.  
Set oConn = New ADODB.Connection  
.Open   
  
' Make a query over the connection.  
sSQL = "SELECT ProductID, ProductName, CategoryID, UnitPrice " & _  
             "FROM Products"  
Set oRs = New ADODB.Recordset  
oRs.Open sSQL, , adOpenStatic, adLockBatchOptimistic, adCmdText  
  
MsgBox oRs.RecordCount  
  
' Close the connection.  
oConn.Close  
Set oConn = Nothing  
  
```  
  
 ここで**oRs.Open**受け取り、**接続**オブジェクト (*oConn*) 変数の値としてその*ActiveConnection*パラメーター。 また、 **Connection.CursorLocation**プロパティの既定値が想定**adUseServer**です。 これに対し、 [HelloData](../../../ado/guide/data/hellodata-a-simple-ado-application.md)前のセクションの例です。 次の命令は、実行時エラーになります。  
  
```  
oRs.MarshalOptions = adMarshalModifiedOnly  
' Disconnect the Recordset.  
Set oRs.ActiveConnection = Nothing  
```
