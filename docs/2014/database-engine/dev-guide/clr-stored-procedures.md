---
title: CLR ストアドプロシージャ |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- database objects [CLR integration], stored procedures
- stored procedures [CLR integration]
- common language runtime [SQL Server], stored procedures
- building database objects [CLR integration], stored procedures
- output parameters [CLR integration]
- tabular results
ms.assetid: bbdd51b2-a9b4-4916-ba6f-7957ac6c3f33
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 4998058d55cd49c0eecfdecce2edc609a4d62c1f
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84933724"
---
# <a name="clr-stored-procedures"></a>CLR ストアド プロシージャ
  ストアド プロシージャは、スカラー式では使用できないルーチンです。 ストアド プロシージャはスカラー関数とは異なり、表形式の結果やメッセージをクライアントに返す操作、DDL (データ定義言語) ステートメントや DML (データ操作言語) ステートメントを呼び出す操作、出力パラメーターを返す操作が行えます。 CLR 統合の利点とマネージコードとの使い分けの詳細については [!INCLUDE[tsql](../../includes/tsql-md.md)] 、「 [clr 統合の概要](../../relational-databases/clr-integration/clr-integration-overview.md)」を参照してください。  
  
## <a name="requirements-for-clr-stored-procedures"></a>CLR ストアド プロシージャの要件  
 共通言語ランタイム (CLR) では、ストアドプロシージャは、アセンブリ内のクラスのパブリック静的メソッドとして実装され [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] ます。 この静的メソッドは、void として宣言することも、整数値を返すようにすることもできます。 整数値を返す場合は、その整数値はストアド プロシージャからのリターン コードとして扱われます。 次に例を示します。  
  
 `EXECUTE @return_status = procedure_name`  
  
 @return_status変数には、メソッドによって返される値が含まれます。 このメソッドを void として宣言した場合は、リターン コードは 0 になります。  
  
 パラメーターを受け取るメソッドの場合、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 実装のパラメーター数は、このストアド プロシージャの [!INCLUDE[tsql](../../includes/tsql-md.md)] 宣言で使用したパラメーター数と同じにする必要があります。  
  
 CLR ストアド プロシージャに渡すパラメーターには、マネージド コード内に同等のパラメーターを持つネイティブの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 型であればどの型でも使用できます。 プロシージャを作成する [!INCLUDE[tsql](../../includes/tsql-md.md)] 構文では、これらの型には最も適切なネイティブ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と同等の型を指定する必要があります。 型変換の詳細については、「 [CLR パラメーターデータのマッピング](../../relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md)」を参照してください。  
  
### <a name="table-valued-parameters"></a>テーブル値パラメーター  
 テーブル値パラメーター (TVP) とは、プロシージャや関数に渡されるユーザー定義のテーブル型です。TVP を使用すると、複数行のデータを効率的にサーバーに渡すことができます。 TVP の機能はパラメーター配列に似ていますが、より柔軟性が高く、[!INCLUDE[tsql](../../includes/tsql-md.md)] との統合も緊密です。 テーブル値パラメーターを使用するとパフォーマンスが向上する可能性もあります。 また、サーバーへのラウンド トリップを減らすのにも役立ちます。 スカラー パラメーターのリストを使用するなどしてサーバーに複数の要求を送信する代わりに、データを TVP としてサーバーに送信できます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のプロセスで実行されているマネージド ストアド プロシージャやマネージド関数にユーザー定義のテーブル型をテーブル値パラメーターとして渡したり、戻り値として受け取ったりすることはできません。 Tvp の詳細については、「[データベースエンジン&#41;&#40;テーブル値パラメーターの使用](../../relational-databases/tables/use-table-valued-parameters-database-engine.md)」を参照してください。  
  
## <a name="returning-results-from-clr-stored-procedures"></a>CLR ストアド プロシージャから結果を返す  
 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] ストアド プロシージャからの情報はいくつかの形式で返すことができます。 出力パラメーター、表形式の結果、およびメッセージの形式を使用できます。  
  
### <a name="output-parameters-and-clr-stored-procedures"></a>OUTPUT パラメーターと CLR ストアド プロシージャ  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャと同様に、OUTPUT パラメーターを使用して [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] ストアド プロシージャから情報を返すことができます。 [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャの作成に使用する [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] DML 構文は、[!INCLUDE[tsql](../../includes/tsql-md.md)] で記述されたストアド プロシージャの作成に使用する構文と同じです。 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] クラスの実装コードの対応するパラメーターは、引数として参照渡しのパラメーターを使用する必要があります。 Visual Basic では、C# と同じように出力パラメーターがサポートされないことに注意してください。 次に示すように、パラメーターを参照によって指定し、属性を適用し \<Out()> て出力パラメーターを表す必要があります。  
  
```vb
Imports System.Runtime.InteropServices  
...  
Public Shared Sub PriceSum ( <Out()> ByRef value As SqlInt32)  
```  
  
 OUTPUT パラメーターを使用して情報を返すストアド プロシージャを次に示します。  
  
```csharp  
using System;  
using System.Data.SqlTypes;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;   
  
public class StoredProcedures   
{  
   [Microsoft.SqlServer.Server.SqlProcedure]  
   public static void PriceSum(out SqlInt32 value)  
   {  
      using(SqlConnection connection = new SqlConnection("context connection=true"))   
      {  
         value = 0;  
         connection.Open();  
         SqlCommand command = new SqlCommand("SELECT Price FROM Products", connection);  
         SqlDataReader reader = command.ExecuteReader();  
  
         using (reader)  
         {  
            while( reader.Read() )  
            {  
               value += reader.GetSqlInt32(0);  
            }  
         }           
      }  
   }  
}  
```  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
Imports System.Runtime.InteropServices  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class StoredProcedures   
    ''' <summary>  
    ''' Executes a query and iterates over the results to perform a summation.  
    ''' </summary>  
    <Microsoft.SqlServer.Server.SqlProcedure> _  
    Public Shared Sub PriceSum( <Out()> ByRef value As SqlInt32)  
  
        Using connection As New SqlConnection("context connection=true")  
           value = 0  
           Connection.Open()  
           Dim command As New SqlCommand("SELECT Price FROM Products", connection)  
           Dim reader As SqlDataReader  
           reader = command.ExecuteReader()  
  
           Using reader  
              While reader.Read()  
                 value += reader.GetSqlInt32(0)  
              End While  
           End Using  
        End Using          
    End Sub  
End Class  
```  
  
 上記の CLR ストアドプロシージャを含むアセンブリがサーバー上に構築され、作成されたら、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ように使用してデータベースでプロシージャを作成し、 *SUM*を OUTPUT パラメーターとして指定します。  
  
```sql
CREATE PROCEDURE PriceSum (@sum int OUTPUT)  
AS EXTERNAL NAME TestStoredProc.StoredProcedures.PriceSum  
-- if StoredProcedures class was inside a namespace, called MyNS,  
-- you would use:  
-- AS EXTERNAL NAME TestStoredProc.[MyNS.StoredProcedures].PriceSum  
```  
  
 *Sum*が SQL Server データ型として宣言され、 `int` clr ストアドプロシージャで定義されている*値*パラメーターが clr データ型として指定されていることに注意して `SqlInt32` ください。 呼び出し元のプログラムが CLR ストアドプロシージャを実行すると、に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] よって自動的に `SqlInt32` clr データ型がデータ型に変換され `int` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  変換できる CLR データ型と変換できない CLR データ型の詳細については、「 [Clr パラメーターデータのマッピング](../../relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md)」を参照してください。  
  
### <a name="returning-tabular-results-and-messages"></a>表形式の結果とメッセージを返す  
 表形式の結果とメッセージは、`SqlPipe` クラスの `Pipe` プロパティを使用して取得した `SqlContext` オブジェクトを使用してクライアントに返されます。 `SqlPipe` オブジェクトには `Send` メソッドがあります。 `Send` メソッドを呼び出すことにより、パイプ経由で呼び出し側のアプリケーションにデータを送信できます。  
  
 次に示すのは、`SqlPipe.Send` を送信したり、単純にテキスト文字列を送信するために使用する、`SqlDataReader` メソッドのオーバーロードです。  
  
###### <a name="returning-messages"></a>メッセージを返す  
 `SqlPipe.Send(string)` はクライアント アプリケーションへのメッセージの送信に使用します。 メッセージのテキストの上限は 8,000 文字です。 メッセージが 8,000 文字を超えると、そのメッセージは切り詰められます。  
  
###### <a name="returning-tabular-results"></a>表形式の結果を返す  
 クエリの結果を直接クライアントに送信するには、`Execute` オブジェクトの `SqlPipe` メソッドのいずれかのオーバーロードを使用します。 マネージド メモリにコピーされることなくデータがネットワーク バッファーに転送されるので、これはクライアントに結果を返す最も効率的な方法です。 次に例を示します。  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlTypes;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;   
  
public class StoredProcedures   
{  
   /// <summary>  
   /// Execute a command and send the results to the client directly.  
   /// </summary>  
   [Microsoft.SqlServer.Server.SqlProcedure]  
   public static void ExecuteToClient()  
   {  
   using(SqlConnection connection = new SqlConnection("context connection=true"))   
   {  
      connection.Open();  
      SqlCommand command = new SqlCommand("select @@version", connection);  
      SqlContext.Pipe.ExecuteAndSend(command);  
      }  
   }  
}  
```  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class StoredProcedures   
    ''' <summary>  
    ''' Execute a command and send the results to the client directly.  
    ''' </summary>  
    <Microsoft.SqlServer.Server.SqlProcedure> _  
    Public Shared Sub ExecuteToClient()  
        Using connection As New SqlConnection("context connection=true")  
            connection.Open()  
            Dim command As New SqlCommand("SELECT @@VERSION", connection)  
            SqlContext.Pipe.ExecuteAndSend(command)  
        End Using  
    End Sub  
End Class  
```  
  
 インプロセス プロバイダーによりそれ以前に実行されたクエリの結果を送信するには (または `SqlDataReader` のカスタム実装を使用して事前処理するには)、`Send` メソッドの `SqlDataReader` を受け取るオーバーロードを使用します。 このメソッドは、前述の直接的なメソッドより少し動作が遅くなりますが、クライアントにデータを送信する前に、きわめて柔軟にデータを操作できます。  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlTypes;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;   
  
public class StoredProcedures   
{  
   /// <summary>  
   /// Execute a command and send the resulting reader to the client  
   /// </summary>  
   [Microsoft.SqlServer.Server.SqlProcedure]  
   public static void SendReaderToClient()  
   {  
      using(SqlConnection connection = new SqlConnection("context connection=true"))   
      {  
         connection.Open();  
         SqlCommand command = new SqlCommand("select @@version", connection);  
         SqlDataReader r = command.ExecuteReader();  
         SqlContext.Pipe.Send(r);  
      }  
   }  
}  
```  
 
```vb  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class StoredProcedures   
    ''' <summary>  
    ''' Execute a command and send the results to the client directly.  
    ''' </summary>  
    <Microsoft.SqlServer.Server.SqlProcedure> _  
    Public Shared Sub SendReaderToClient()  
        Using connection As New SqlConnection("context connection=true")  
            connection.Open()  
            Dim command As New SqlCommand("SELECT @@VERSION", connection)  
            Dim reader As SqlDataReader  
            reader = command.ExecuteReader()  
            SqlContext.Pipe.Send(reader)  
        End Using  
    End Sub  
End Class  
```  
  
 動的な結果セットを作成し、それにデータを設定してクライアントに送信するには、現在の接続からのレコードを作成し、`SqlPipe.Send` を使用してそれらを送信できます。  
  
```csharp  
using System.Data;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;   
using System.Data.SqlTypes;  
  
public class StoredProcedures   
{  
   /// <summary>  
   /// Create a result set on the fly and send it to the client.  
   /// </summary>  
   [Microsoft.SqlServer.Server.SqlProcedure]  
   public static void SendTransientResultSet()  
   {  
      // Create a record object that represents an individual row, including it's metadata.  
      SqlDataRecord record = new SqlDataRecord(new SqlMetaData("stringcol", SqlDbType.NVarChar, 128));  
  
      // Populate the record.  
      record.SetSqlString(0, "Hello World!");  
  
      // Send the record to the client.  
      SqlContext.Pipe.Send(record);  
   }  
}  
```  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class StoredProcedures   
    ''' <summary>  
    ''' Create a result set on the fly and send it to the client.  
    ''' </summary>  
    <Microsoft.SqlServer.Server.SqlProcedure> _  
    Public Shared Sub SendTransientResultSet()  
        ' Create a record object that represents an individual row, including it's metadata.  
        Dim record As New SqlDataRecord(New SqlMetaData("stringcol", SqlDbType.NVarChar, 128) )  
  
        ' Populate the record.  
        record.SetSqlString(0, "Hello World!")  
  
        ' Send the record to the client.  
        SqlContext.Pipe.Send(record)          
    End Sub  
End Class   
```  
  
 次に、表形式の結果とメッセージを `SqlPipe` を使用して送信する例を示します。  
  
```csharp  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;   
  
public class StoredProcedures   
{  
   [Microsoft.SqlServer.Server.SqlProcedure]  
   public static void HelloWorld()  
   {  
      SqlContext.Pipe.Send("Hello world! It's now " + System.DateTime.Now.ToString()+"\n");  
      using(SqlConnection connection = new SqlConnection("context connection=true"))   
      {  
         connection.Open();  
         SqlCommand command = new SqlCommand("SELECT ProductNumber FROM ProductMaster", connection);  
         SqlDataReader reader = command.ExecuteReader();  
         SqlContext.Pipe.Send(reader);  
      }  
   }  
}  
```  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class StoredProcedures   
    ''' <summary>  
    ''' Execute a command and send the results to the client directly.  
    ''' </summary>  
    <Microsoft.SqlServer.Server.SqlProcedure> _  
    Public Shared Sub HelloWorld()  
        SqlContext.Pipe.Send("Hello world! It's now " & System.DateTime.Now.ToString() & "\n")  
        Using connection As New SqlConnection("context connection=true")  
            connection.Open()  
            Dim command As New SqlCommand("SELECT ProductNumber FROM ProductMaster", connection)  
            Dim reader As SqlDataReader  
            reader = command.ExecuteReader()  
            SqlContext.Pipe.Send(reader)  
        End Using  
    End Sub  
End Class   
```  
  
 最初の `Send` はクライアントにメッセージを送信し、2 番目は `SqlDataReader` を使用して表形式の結果を送信しています。  
  
 これらの例は、説明のみの目的でここに記載しています。 計算を集中的に行うアプリケーションには、実際には単純な [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントよりも CLR 関数の方が適しています。 上の例とほぼ同等の [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャを次に示します。  
  
```sql
CREATE PROCEDURE HelloWorld() AS  
BEGIN  
PRINT('Hello world!')  
SELECT ProductNumber FROM ProductMaster  
END;  
```  
  
> [!NOTE]  
>  メッセージと結果セットはクライアント アプリケーションで個別に取得されます。 たとえば、結果 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] セットは [**結果**] ビューに表示され、メッセージは [**メッセージ**] ウィンドウに表示されます。  
  
 上の Visual C# コードをファイル MyFirstUdp.cs に保存した場合、次のようにコンパイルします。  
  
```console
csc /t:library /out:MyFirstUdp.dll MyFirstUdp.cs   
```  
  
 上の Visual Basic コードをファイル MyFirstUdp.vb に保存した場合、次のようにコンパイルします。  
  
```console
vbc /t:library /out:MyFirstUdp.dll MyFirstUdp.vb   
```  
  
> [!NOTE]  
>  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降では、`/clr:pure` を指定してコンパイルした Visual C++ のデータベース オブジェクト (ストアド プロシージャなど) は実行できません。  
  
 生成されるアセンブリは登録でき、次の DDL を使用してエントリ ポイントを呼び出すことができます。  
  
```sql
CREATE ASSEMBLY MyFirstUdp FROM 'C:\Programming\MyFirstUdp.dll';  
CREATE PROCEDURE HelloWorld  
AS EXTERNAL NAME MyFirstUdp.StoredProcedures.HelloWorld;  
EXEC HelloWorld;  
```  
  
## <a name="see-also"></a>参照  
 [CLR ユーザー定義関数](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md)   
 [CLR ユーザー定義型](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)   
 [CLR トリガー](../../../2014/database-engine/dev-guide/clr-triggers.md)  
  
  
