---
title: "現在のトランザクションにアクセスする |Microsoft ドキュメント"
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
- current transaction access
- Current property
- Transaction class
ms.assetid: 1a4e2ce5-f627-4c81-8960-6a9968cefda2
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: abcc68d96e7516b31a231efeb4c5c851b10dee45
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="accessing-the-current-transaction"></a>現在のトランザクションへのアクセス
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
トランザクションの時点で実行されている共通言語ランタイム (CLR) コードでアクティブな場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が入力すると、トランザクションはによって公開される、 **System.Transactions.Transaction**クラスです。 **Transaction.Current**プロパティは、現在のトランザクションにアクセスするために使用します。 ほとんどの場合、トランザクションに明示的にアクセスする必要はありません。 ADO.NET データベース接続に対してチェック**Transaction.Current**時に自動的に、 **Connection.Open**メソッドが呼び出され、そのトランザクションに、接続を透過的に登録 (しない限り、**Enlist**キーワードが接続文字列で false に設定されている)。  
  
 使用することができます、**トランザクション**次のシナリオで直接オブジェクト。  
  
-   自動参加が行われないリソースや、何かの理由で初期化中に参加しなかったリソースを参加させる場合。  
  
-   リソースを明示的にトランザクションに参加させる場合。  
  
-   ストアド プロシージャまたは関数内から外部トランザクションを終了させる場合。 この場合は、<xref:System.Transactions.TransactionScope> を使用します。 たとえば、次のコードでは、現在のトランザクションがロールバックされます。  
  
    ```  
    using(TransactionScope transactionScope = new TransactionScope(TransactionScopeOptions.Required)) { }  
    ```  
  
 以下に、外部トランザクションを取り消す別の方法を説明します。  
  
## <a name="canceling-an-external-transaction"></a>外部トランザクションのキャンセル  
 外部トランザクションは、次の方法でマネージ プロシージャまたは関数からキャンセルできます。  
  
-   マネージ プロシージャまたは関数は、出力パラメーターを使用して値を返すことができます。 呼び出し元[!INCLUDE[tsql](../../includes/tsql-md.md)]プロシージャ返される値を確認して、必要に応じて、実行できる**ROLLBACK TRANSACTION**です。  
  
-   マネージ プロシージャまたは関数は、カスタムの例外をスローできます。 呼び出し元[!INCLUDE[tsql](../../includes/tsql-md.md)]プロシージャが、マネージ プロシージャまたは関数 try ブロックと catch ブロックでスローされる例外をキャッチして実行できる**ROLLBACK TRANSACTION**です。  
  
-   マネージ プロシージャまたは関数を呼び出して、現在のトランザクションを取り消すことができます、 **Transaction.Rollback**メソッドの特定の条件が満たされた場合。  
  
 マネージ プロシージャまたは関数内で呼び出された場合、 **Transaction.Rollback**メソッドは、あいまいなエラー メッセージで例外をスローし、try/catch ブロックでラップすることができます。 表示されるエラー メッセージは、たとえば次のようになります。  
  
```  
Msg 3994, Level 16, State 1, Procedure uspRollbackFromProc, Line 0  
Transaction is not allowed to roll back inside a user defined routine, trigger or aggregate because the transaction is not started in that CLR level. Change application logic to enforce strict transaction nesting.  
```  
  
 この例外は想定されるものであり、コードの実行を継続するには try/catch ブロックが必要です。 try/catch ブロックがない場合、例外はすぐに呼び出し元の [!INCLUDE[tsql](../../includes/tsql-md.md)] プロシージャにスローされ、マネージ コードの実行は終了します。 マネージ コードが実行を終了すると、別の例外が発生します。  
  
```  
Msg 3991, Level 16, State 1, Procedure uspRollbackFromProc, Line 1   
The context transaction which was active before entering user defined routine, trigger or aggregate " uspRollbackFromProc " has been ended inside of it, which is not allowed. Change application logic to enforce strict transaction nesting. The statement has been terminated.  
```  
  
 この例外も想定されるもので、実行を継続するには、トリガーを起動するアクションを実行する [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントでの try/catch ブロックが必要です。 この 2 つの例外がスローされますが、トランザクションはロールバックされ、変更はコミットされません。  
  
### <a name="example"></a>例  
 次の例に示しますを使用してマネージ プロシージャから、ロールバック対象のトランザクション、 **Transaction.Rollback**メソッドです。 前後の try/catch ブロックに注意してください、 **Transaction.Rollback**マネージ コード内のメソッドです。 [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトは、アセンブリおよびマネージ ストアド プロシージャを作成します。 注意している、 **EXEC uspRollbackFromProc**をマネージ プロシージャ実行の完了時にスローされる例外をキャッチするため、ステートメントが try ブロックと catch ブロックでラップされます。  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
using System.Transactions;  
  
public partial class StoredProcedures  
{  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void uspRollbackFromProc()  
{  
   using (SqlConnection connection = new SqlConnection(@"context connection=true"))  
   {  
      // Open the connection.  
      connection.Open();  
  
      bool successCondition = true;  
  
      // Success condition is met.  
      if (successCondition)  
      {  
         SqlContext.Pipe.Send("Success condition met in procedure.");   
         // Perform other actions here.  
      }  
  
      //  Success condition is not met, the transaction will be rolled back.  
      else  
      {  
         SqlContext.Pipe.Send("Success condition not met in managed procedure. Transaction rolling back...");  
         try  
         {  
               // Get the current transaction and roll it back.  
               Transaction trans = Transaction.Current;  
               trans.Rollback();  
         }  
         catch (SqlException ex)  
         {  
            // Catch the expected exception.   
            // This allows the connection to close correctly.                      
         }    
      }  
  
      // Close the connection.  
      connection.Close();  
   }  
}  
};  
```  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Transactions  
  
Partial Public Class StoredProcedures  
<Microsoft.SqlServer.Server.SqlProcedure()> _  
Public Shared Sub  uspRollbackFromProc ()  
   Using connection As New SqlConnection("context connection=true")  
  
   ' Open the connection.  
   connection.Open()  
  
   Dim successCondition As Boolean  
   successCondition = False  
  
   ' Success condition is met.  
   If successCondition Then  
  
      SqlContext.Pipe.Send("Success condition met in procedure.")  
  
      ' Success condition is not met, the transaction will be rolled back.  
  
   Else  
      SqlContext.Pipe.Send("Success condition not met in managed procedure. Transaction rolling back...")  
      Try  
         ' Get the current transaction and roll it back.  
         Dim trans As Transaction  
         trans = Transaction.Current  
         trans.Rollback()  
  
      Catch ex As SqlException  
         ' Catch the exception instead of throwing it.    
         ' This allows the connection to close correctly.                      
      End Try  
  
   End If  
  
   ' Close the connection.  
   connection.Close()  
  
End Using  
End Sub  
End Class  
```  
  
 **Transact-SQL**  
  
```  
--Register assembly.  
CREATE ASSEMBLY TestProcs FROM 'C:\Programming\TestProcs.dll'   
Go  
CREATE PROCEDURE uspRollbackFromProc AS EXTERNAL NAME TestProcs.StoredProcedures.uspRollbackFromProc  
Go  
  
-- Execute procedure.  
BEGIN TRY  
BEGIN TRANSACTION   
-- Perform other actions.  
Exec uspRollbackFromProc  
-- Perform other actions.  
PRINT N'Commiting transaction...'  
COMMIT TRANSACTION  
END TRY  
  
BEGIN CATCH  
SELECT ERROR_NUMBER() AS ErrorNum, ERROR_MESSAGE() AS ErrorMessage  
PRINT N'Exception thrown, rolling back transaction.'  
ROLLBACK TRANSACTION  
PRINT N'Transaction rolled back.'   
END CATCH  
Go  
  
-- Clean up.  
DROP Procedure uspRollbackFromProc;  
Go  
DROP ASSEMBLY TestProcs;  
Go  
```  
  
## <a name="see-also"></a>参照  
 [CLR 統合とトランザクション](../../relational-databases/clr-integration-data-access-transactions/clr-integration-and-transactions.md)  
  
  
