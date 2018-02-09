---
title: "SqlPipe オブジェクト |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- custom result sets [CLR integration]
- SqlPipe object
- tabular results
ms.assetid: 3e090faf-085f-4c01-a565-79e3f1c36e3b
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5db45b3c67fcf865214ad422662acfb80bab293e
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="sqlpipe-object"></a>SqlPipe オブジェクト
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、結果や出力パラメーターを呼び出し側のクライアントに送信するストアド プロシージャ (または拡張ストアド プロシージャ) を作成することがごく一般的でした。  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)]任意のストアド プロシージャ、**選択**0 個以上の行を返すステートメントが接続されている呼び出し元の「パイプ」に、その結果を送信  
  
 共通言語ランタイム (CLR) データベースで実行されているオブジェクト[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を使用して接続しているパイプに結果を送信することができます、**送信**のメソッド、 **SqlPipe**オブジェクト。 アクセス、**パイプ**のプロパティ、 **SqlContext**を取得するオブジェクト、 **SqlPipe**オブジェクト。 **SqlPipe**クラスは、概念的に似ています、**応答**クラスは、ASP.NET で見つかりました。 詳細については、.NET Framework Software Development Kit の SqlPipe クラスのリファレンス ドキュメントを参照してください。  
  
## <a name="returning-tabular-results-and-messages"></a>表形式の結果とメッセージを返す  
 **SqlPipe**が、**送信**メソッドで、次の 3 つのオーバー ロードがあります。 これらは次のとおりです。  
  
-   `void Send(string message)`  
  
-   `void Send(SqlDataReader reader)`  
  
-   `void Send(SqlDataRecord record)`  
  
 **送信**メソッドは、クライアントまたは呼び出し元に直接データを送信します。 出力を使用するクライアントでは通常、 **SqlPipe**、入れ子になった CLR ストアド プロシージャの場合、出力のコンシューマーこともできます、ストアド プロシージャです。 たとえば、Procedure1 がコマンド テキスト "EXEC Procedure2" の SqlCommand.ExecuteReader() を呼び出すとします。 Procedure2 もマネージ ストアド プロシージャです。 ここで Procedure2 が SqlPipe.Send( SqlDataRecord ) を呼び出すと、行はクライアントではなく、Procedure1 のリーダーに送信されます。  
  
 **送信**メソッドの PRINT と同等の情報メッセージとしてクライアントに表示される文字列メッセージを送信[!INCLUDE[tsql](../../includes/tsql-md.md)]です。 単一行の結果セットを使用しても送信できる**SqlDataRecord**、または複数行の結果セットを使用して、 **SqlDataReader**です。  
  
 **SqlPipe**オブジェクトもあります、 **ExecuteAndSend**メソッドです。 このメソッドは、コマンドを実行するために使用できます (として渡される、 **SqlCommand**オブジェクト) と、呼び出し元に直接の結果を送信します。 送信されたコマンドにエラーがある場合、パイプに例外が送信されますが、呼び出し元のマネージ コードにもコピーが送信されます。 呼び出し元コードが例外をキャッチしない場合は、履歴を伝わり [!INCLUDE[tsql](../../includes/tsql-md.md)] コードに反映され、2 度出力に表示されます。 呼び出し元コードが例外をキャッチした場合、パイプ コンシューマーにはまだエラーが表示されますが、重複するエラーはありません。  
  
 だけを受け取ります、 **SqlCommand**コンテキスト接続に関連付けられている以外の場合は、コンテキスト接続以外に関連付けられているコマンドを実行できません。  
  
## <a name="returning-custom-result-sets"></a>カスタム結果セットを返す  
 マネージ ストアド プロシージャから付属していない結果セットを送信できる、 **SqlDataReader**です。 **SendResultsStart**メソッドと共に**SendResultsRow**と**SendResultsEnd**、ストアド プロシージャをクライアントにカスタム結果セットを送信します。  
  
 **SendResultsStart**受け取り、 **SqlDataRecord**の入力として。 さらに、結果セットの先頭にマークを付け、レコード メタデータを使用して、結果セットを説明するメタデータを生成します。 レコードの値を送信しません**SendResultsStart**です。 それ以降、すべての行を使用して送信**SendResultsRow**、そのメタデータ定義に一致する必要があります。  
  
> [!NOTE]  
>  呼び出した後、 **SendResultsStart**メソッドのみ**SendResultsRow**と**SendResultsEnd**呼び出すことができます。 同じインスタンスで他のメソッドを呼び出して**SqlPipe**により、 **InvalidOperationException**です。 **SendResultsEnd**設定**SqlPipe**他のメソッドを呼び出すことができます、初期状態にします。  
  
### <a name="example"></a>例  
 **UspGetProductLine**ストアド プロシージャ名、製品番号、色、および指定した製品ライン内のすべての製品の表示価格を返します。 このストアド プロシージャでは、完全に一致する*prodLine*です。  
  
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
  
 次[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントの実行、 **uspGetProduct**プロシージャで、ツーリング自転車製品の一覧を返します。  
  
```  
EXEC uspGetProductLineVB 'T';  
```  
  
## <a name="see-also"></a>参照  
 [SqlDataRecord オブジェクト](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqldatarecord-object.md)   
 [CLR ストアド プロシージャ](http://msdn.microsoft.com/library/bbdd51b2-a9b4-4916-ba6f-7957ac6c3f33)   
 [ADO.NET に対する SQL Server インプロセス固有の拡張機能](../../relational-databases/clr-integration-data-access-in-process-ado-net/sql-server-in-process-specific-extensions-to-ado-net.md)  
  
  
