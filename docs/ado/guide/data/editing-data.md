---
title: "データの編集 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ADO, editing data
- AdUseClient [ADO]
- editing data [ADO]
ms.assetid: ef514f85-c446-4f05-824e-c9313b2ffae1
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 76a5921185f6643f328559e3bc73dfac46bfee0c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="editing-data"></a>データの編集
について説明してきました ADO を使用してデータ ソースへの接続、コマンドの実行で、結果を得る方法、**レコード セット**オブジェクト内を移動したり、 **Recordset**です。 ここで、次の基本的な ADO 操作について説明します。 データを編集します。  
  
 このセクションでは、サンプルを使用して引き続き**レコード セット**で導入された[データを調べる](../../../ado/guide/data/examining-data.md)、1 つの重要な変更とします。 開くには、次のコードが使用される、 **Recordset**:  
  
```  
'BeginEditIntro  
    Dim strSQL As String  
    Dim objRs1 As ADODB.Recordset  
  
    strSQL = "SELECT * FROM Shippers"  
  
    Set objRs1 = New ADODB.Recordset  
  
    objRs1.Open strSQL, GetNewConnection, adOpenStatic, _  
                adLockBatchOptimistic, adCmdText  
  
    ' Disconnect the Recordset from the Connection object.  
    Set objRs1.ActiveConnection = Nothing  
'EndEditIntro  
```  
  
 コードに重要な変更は、設定、 **CursorLocation**のプロパティ、**接続**オブジェクトと等しい**adUseClient**で、 *GetNewConnection* (次の例に示すように) 関数で、クライアント カーソルの使用を示します。 クライアント側およびサーバー側のカーソルの違いの詳細については、次を参照してください。[カーソルとロック](../../../ado/guide/data/understanding-cursors-and-locks.md)です。  
  
 **CursorLocation**プロパティの**adUseClient**設定、データ ソース (この場合は SQL Server) からクライアント コード (デスクトップ ワークステーション) の場所にカーソルの位置を移動します。 この設定は、作成し、カーソルを管理するためにクライアントで OLE DB 用のクライアント カーソル エンジンを起動する ADO を強制します。  
  
 お気付きを**LockType**のパラメーター、**開く**方法に変更**adLockBatchOptimistic**です。 これにより、カーソルがバッチ モードで開きます。 (プロバイダーが複数の変更をキャッシュし、呼び出した場合にのみ、基になるデータ ソースに書き込みます、 **UpdateBatch**メソッドです)。加えられた変更、 **Recordset**までデータベースには更新されません、 **UpdateBatch**メソッドが呼び出されます。  
  
 最後に、このセクションのコードは、GetNewConnection 関数の変更バージョンを使用します。 このバージョンの関数は、クライアント側カーソルを返すようになりました。 関数は、次のようになります。  
  
```  
'BeginNewConnection  
Public Function GetNewConnection() As ADODB.Connection  
    On Error GoTo ErrHandler:  
  
    Dim objConn As New ADODB.Connection  
    Dim strConnStr As String  
  
    strConnStr = "Provider='SQLOLEDB';Initial Catalog='Northwind';" & _  
                 "Data Source='MySqlServer';Integrated Security='SSPI';"  
  
    objConn.ConnectionString = strConnStr  
    objConn.CursorLocation = adUseClient  
    objConn.Open  
  
    Set GetNewConnection = objConn  
  
    Exit Function  
  
ErrHandler:  
    Set objConn = Nothing  
    Set GetNewConnection = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Function  
'EndNewConnection  
```  
  
 このセクションでは、次のトピックを扱います。  
  
-   [既存のレコードの編集](../../../ado/guide/data/editing-existing-records.md)  
  
-   [レコードを追加します。](../../../ado/guide/data/adding-records.md)  
  
-   [サポートされている機能を決定します。](../../../ado/guide/data/determining-what-is-supported.md)  
  
-   [Delete メソッドを使用してレコードを削除します。](../../../ado/guide/data/deleting-records-using-the-delete-method.md)  
  
-   [他の方法: SQL ステートメントの使用](../../../ado/guide/data/alternatives-using-sql-statements.md)

