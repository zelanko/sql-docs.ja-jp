---
title: "System.Transactions の使用 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TransactionScope class
- Dispose method
- System.Transactions namespace
ms.assetid: 79656ce5-ce46-4c5e-9540-cf9869bd774b
caps.latest.revision: "16"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 40c3ac24cc6be800fea8da1fab407569e4cdab87
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="using-systemtransactions"></a>System.Transactions の使用
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]**System.Transactions**名前空間は ADO.NET と完全に統合される新しいトランザクション フレームワークを提供し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]共通言語ランタイム (CLR) 統合します。 **System.Transactions.TransactionScope**クラスは、暗黙的に接続を分散トランザクションに参加させることで、コード ブロックをトランザクションです。 呼び出す必要があります、**完了**でマークされたメソッドのコード ブロックの最後に、 **TransactionScope**です。 **Dispose**プログラムの実行が中止された場合、トランザクションの原因と、コード ブロックを離れるときに、メソッドが呼び出され、**完了**メソッドは呼び出されません。 コードがスコープから離れるような例外がスローされると、このトランザクションは中止されたと見なされます。  
  
 使用されていることをお勧め、**を使用して**いることを確認するブロック、 **Dispose**メソッドが、 **TransactionScope**オブジェクトと、 **を使用して**ブロックを終了します。 コミットまたは保留中のトランザクションをロールバックに失敗することができます重大なパフォーマンスが低下するための既定のタイムアウト、 **TransactionScope**は 1 分です。 使用しない場合、**を使用して**ステートメントでは、すべての処理を実行する必要があります、**再試行**をブロックし、明示的に呼び出す、 **Dispose**メソッドで、**最後に**ブロックします。  
  
 内で例外が発生した場合、 **TransactionScope**トランザクションが不整合としてマークされているし、破棄されます。 ロールバックされるときに、 **TransactionScope**が破棄されています。 例外が発生しなければ、参加しているトランザクションがコミットされます。  
  
 **TransactionScope**ローカルおよびリモート データ ソースまたは外部のリソース マネージャーにアクセスしている場合にのみに使用する必要があります。 これは、ため**TransactionScope**コンテキスト接続内でのみ使用されている場合でもを昇格させると、トランザクションを常に発生します。  
  
> [!NOTE]  
>  **TransactionScope**クラスを作成して、トランザクション、 **System.Transactions.Transaction.IsolationLevel**の**Serializable**既定です。 アプリケーションによっては、分離レベルを低くして、アプリケーション内の競合を回避することを検討する必要があります。  
  
> [!NOTE]  
>  リモート サーバーに対する分散トランザクション内では、大量のデータベース リソースが消費されるため、更新、挿入、および削除だけを実行することをお勧めします。 操作がローカル サーバーで実行される場合は、分散トランザクションは必要なく、ローカル トランザクションで十分です。 SELECT ステートメントは、不必要にデータベース リソースをロックすることがあります。また、選択に多くのトランザクションを要する場合もあります。 データベース以外の作業は、トランザクション処理を行う他のリソース マネージャーを必要とする場合を除き、トランザクションのスコープ外で行う必要があります。 トランザクションのスコープ内で例外には、トランザクションのコミットが防止されますが、 **TransactionScope**クラスには用意されていない変更をロールバックして、コードによってトランザクションのスコープの外で行われました。できません。 トランザクションがロールバックされたときに何らかのアクションを実行する必要がある場合は、独自の実装を記述する必要があります、 **System.Transactions.IEnlistmentNotification**インターフェイス、およびトランザクションに明示的に参加します。  
  
## <a name="example"></a>例  
 使用する**System.Transactions**、System.Transactions.dll ファイルへの参照をする必要があります。  
  
 次のコードでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の 2 つの異なるインスタンスに対して昇格可能なトランザクションを作成する方法を説明します。 これらのインスタンスが 2 つの異なるによって表される**System.Data.SqlClient.SqlConnection**でラップされているオブジェクト、 **TransactionScope**ブロックします。 コードを作成、 **TransactionScope**ブロックを**を使用して**ステートメントでは、自動的に参加させることで、最初の接続を開くと、 **TransactionScope**です。 最初、トランザクションは完全な分散トランザクションではなく、軽量トランザクションとして参加します。 このコードでは、条件ロジックが存在することを前提としています (説明を簡単にするために、このロジックは省略しています)。 2 番目の接続が開きますが、必要な場合にのみに参加させます、 **TransactionScope**です。 2 番目の接続が開かれると、トランザクションは完全な分散トランザクションに自動的に昇格します。 次に、コードを呼び出して**TransactionScope.Complete**トランザクションがコミットされます。 コードを終了するときに 2 つの接続の破棄、**を使用して**接続に対してステートメントです。 **TransactionScope.Dispose**のメソッド、 **TransactionScope**の終了時に自動的に呼び出されますが、**を使用して**のブロック、 **TransactionScope**です。 任意の場所で例外がスローされるかどうか、 **TransactionScope**ブロック、**完了**が呼び出されません、および、分散トランザクションはロールバックときに、 **TransactionScope**が破棄されています。  
  
 Visual Basic  
  
```  
Using transScope As New TransactionScope()  
    Using connection1 As New SqlConnection(connectString1)  
        ' Opening connection1 automatically enlists it in the   
        ' TransactionScope as a lightweight transaction.  
        connection1.Open()  
  
        ' Do work in the first connection.  
  
        ' Assumes conditional logic in place where the second  
        ' connection will only be opened as needed.  
        Using connection2 As New SqlConnection(connectString2)  
            ' Open the second connection, which enlists the   
            ' second connection and promotes the transaction to  
            ' a full distributed transaction.  
            connection2.Open()  
  
            ' Do work in the second connection.  
  
        End Using  
    End Using  
  
    ' Commit the transaction.  
    transScope.Complete()  
End Using  
```  
  
 C#  
  
```  
using (TransactionScope transScope = new TransactionScope())  
{  
    using (SqlConnection connection1 = new   
       SqlConnection(connectString1))  
    {  
        // Opening connection1 automatically enlists it in the   
        // TransactionScope as a lightweight transaction.  
        connection1.Open();  
  
        // Do work in the first connection.  
  
        // Assumes conditional logic in place where the second  
        // connection will only be opened as needed.  
        using (SqlConnection connection2 = new   
            SqlConnection(connectString2))  
        {  
            // Open the second connection, which enlists the   
            // second connection and promotes the transaction to  
            // a full distributed transaction.   
            connection2.Open();  
  
            // Do work in the second connection.  
        }  
    }  
    //  The Complete method commits the transaction.  
    transScope.Complete();  
}  
```  
  
## <a name="see-also"></a>参照  
 [CLR 統合とトランザクション](../../relational-databases/clr-integration-data-access-transactions/clr-integration-and-transactions.md)  
  
  
