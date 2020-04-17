---
title: オブジェクト |マイクロソフトドキュメント
description: SQL Server で実行されている CLR データベース オブジェクトの場合は、SqlPipe オブジェクトの Send メソッドを使用して、接続されたパイプに結果を送信できます。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- custom result sets [CLR integration]
- SqlPipe object
- tabular results
ms.assetid: 3e090faf-085f-4c01-a565-79e3f1c36e3b
author: rothja
ms.author: jroth
ms.openlocfilehash: 7b95788d37fa8f8c2e57c2b20aa222938c65dc6c
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487535"
---
# <a name="sqlpipe-object"></a>SqlPipe オブジェクト
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、結果や出力パラメーターを呼び出し側のクライアントに送信するストアド プロシージャ (または拡張ストアド プロシージャ) を作成することがごく一般的でした。  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)]ストアド プロシージャでは、0 個以上の行を返す**SELECT**ステートメントは、接続された呼び出し元の "パイプ" に結果を送信します。  
  
 で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]実行されている共通言語ランタイム (CLR) データベース オブジェクトの場合は **、SqlPipe**オブジェクトの**Send**メソッドを使用して、接続されたパイプに結果を送信できます。 オブジェクトの**パイプ**プロパティに**SqlContext**アクセスして **、SqlPipe**オブジェクトを取得します。 **SqlPipe**クラスは概念的には、ASP.NETで見つかった**応答**クラスに似ています。 詳細については、.NET Framework Software Development Kit の SqlPipe クラスのリファレンス ドキュメントを参照してください。  
  
## <a name="returning-tabular-results-and-messages"></a>表形式の結果とメッセージを返す  
 **SqlPipe には****、3**つのオーバーロードを持つ Send メソッドがあります。 これらは次のとおりです。  
  
-   `void Send(string message)`  
  
-   `void Send(SqlDataReader reader)`  
  
-   `void Send(SqlDataRecord record)`  
  
 **Send**メソッドは、クライアントまたは呼び出し元にデータを直接送信します。 通常は **、 SqlPipe**からの出力を使用するクライアントですが、入れ子になった CLR ストアド プロシージャの場合、出力コンシューマはストアド プロシージャにすることもできます。 たとえば、Procedure1 がコマンド テキスト "EXEC Procedure2" の SqlCommand.ExecuteReader() を呼び出すとします。 Procedure2 もマネージド ストアド プロシージャです。 ここで Procedure2 が SqlPipe.Send( SqlDataRecord ) を呼び出すと、行はクライアントではなく、Procedure1 のリーダーに送信されます。  
  
 **Send**メソッドは、クライアント上に情報メッセージとして表示される文字列メッセージを送信[!INCLUDE[tsql](../../includes/tsql-md.md)]します。 **また、SqlDataRecord**を使用して単一行の結果セットを送信することも **、SqlDataReader**を使用して複数行の結果セットを送信することもできます。  
  
 オブジェクト**には**、**メソッドもあります**。 このメソッドを使用すると、**コマンド (SqlCommand**オブジェクトとして渡されます) を実行し、結果を直接呼び出し元に返すことができます。 送信されたコマンドにエラーがある場合、パイプに例外が送信されますが、呼び出し元のマネージド コードにもコピーが送信されます。 呼び出し元コードが例外をキャッチしない場合は、履歴を伝わり [!INCLUDE[tsql](../../includes/tsql-md.md)] コードに反映され、2 度出力に表示されます。 呼び出し元コードが例外をキャッチした場合、パイプ コンシューマーにはまだエラーが表示されますが、重複するエラーはありません。  
  
 コンテキスト接続に関連付けられている**SqlCommand**のみを受け取ることができます。非コンテキスト接続に関連付けられたコマンドを受け取ることはできません。  
  
## <a name="returning-custom-result-sets"></a>カスタム結果セットを返す  
 マネージ ストアド プロシージャは **、 SqlDataReader**から取得されていない結果セットを送信できます。 **メソッド**と共に **、ストアド**プロシージャがカスタム結果セット**SendResultsEnd**をクライアントに送信できるようにします。  
  
 **結果の開始**は、入力として**SqlData レコード**を取ります。 さらに、結果セットの先頭にマークを付け、レコード メタデータを使用して、結果セットを説明するメタデータを生成します。 レコードの値は**送信**されません。 **SendResultsRow**を使用して送信されるすべての後続の行は、そのメタデータ定義と一致する必要があります。  
  
> [!NOTE]  
>  **メソッドを**呼び出した後は **、結果行**と**結果終了**のみを呼び出すことができます。 同じ**SqlPipe**のインスタンス内の他のメソッドを呼び出すと、**無効な操作例外が**発生します。 **SendResultsEnd**は **、SqlPipe**を他のメソッドを呼び出すことができる初期状態に戻します。  
  
### <a name="example"></a>例  
 **uspGetProductLine**ストアド プロシージャは、指定された製品ライン内のすべての製品の名前、製品番号、色、および定価を返します。 このストアド プロシージャは*prodLine*に完全に一致します。  
  
 C#  
  
```  
using System;  
using System.Data;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
  
public partial class StoredProcedures  
{  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void uspGetProductLine(SqlString prodLine)  
{  
    // Connect through the context connection.  
    using (SqlConnection connection = new SqlConnection("context connection=true"))  
    {  
        connection.Open();  
  
        SqlCommand command = new SqlCommand(  
            "SELECT Name, ProductNumber, Color, ListPrice " +  
            "FROM Production.Product " +   
            "WHERE ProductLine = @prodLine;", connection);  
  
        command.Parameters.AddWithValue("@prodLine", prodLine);  
  
        try  
        {  
            // Execute the command and send the results to the caller.  
            SqlContext.Pipe.ExecuteAndSend(command);  
        }  
        catch (System.Data.SqlClient.SqlException ex)  
        {  
            // An error occurred executing the SQL command.  
        }  
     }  
}  
};  
```  
  
 Visual Basic  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
  
Partial Public Class StoredProcedures  
<Microsoft.SqlServer.Server.SqlProcedure()> _  
Public Shared Sub uspGetProductLine(ByVal prodLine As SqlString)  
    Dim command As SqlCommand  
  
    ' Connect through the context connection.  
    Using connection As New SqlConnection("context connection=true")  
        connection.Open()  
  
        command = New SqlCommand( _  
        "SELECT Name, ProductNumber, Color, ListPrice " & _  
        "FROM Production.Product " & _  
        "WHERE ProductLine = @prodLine;", connection)  
        command.Parameters.AddWithValue("@prodLine", prodLine)  
  
        Try  
            ' Execute the command and send the results   
            ' directly to the caller.  
            SqlContext.Pipe.ExecuteAndSend(command)  
        Catch ex As System.Data.SqlClient.SqlException  
            ' An error occurred executing the SQL command.  
        End Try  
    End Using  
End Sub  
End Class  
```  
  
 次[!INCLUDE[tsql](../../includes/tsql-md.md)]のステートメントは、ツーリング 自転車製品の一覧を返す**uspGetProduct**プロシージャを実行します。  
  
```  
EXEC uspGetProductLineVB 'T';  
```  
  
## <a name="see-also"></a>参照  
 [オブジェクト](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqldatarecord-object.md)   
 [CLR ストアド プロシージャ](https://msdn.microsoft.com/library/bbdd51b2-a9b4-4916-ba6f-7957ac6c3f33)   
 [ADO.NET に対する SQL Server インプロセス固有の拡張機能](../../relational-databases/clr-integration-data-access-in-process-ado-net/sql-server-in-process-specific-extensions-to-ado-net.md)  
  
  
