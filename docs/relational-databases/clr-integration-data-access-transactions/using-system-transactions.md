---
title: Using system.string |Microsoft Docs
description: ADO.NET 名前空間には、SQL Server と CLR 統合に完全に統合されたトランザクションフレームワークが用意されています。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TransactionScope class
- Dispose method
- System.Transactions namespace
ms.assetid: 79656ce5-ce46-4c5e-9540-cf9869bd774b
author: rothja
ms.author: jroth
ms.openlocfilehash: 1fed4e8106fc5348c94a3c7afda0ec903f570eff
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85765363"
---
# <a name="using-systemtransactions"></a>System.Transactions の使用
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  System.string**名前空間は、** ADO.NET および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 共通言語ランタイム (CLR) 統合と完全に統合されたトランザクションフレームワークを提供します。 System.object**クラスは**、接続を分散トランザクションに暗黙的に参加させることによって、コードブロックをトランザクションにします。 **TransactionScope**によってマークされたコードブロックの最後に**Complete**メソッドを呼び出す必要があります。 **Dispose**メソッドは、プログラムの実行がコードブロックから出たときに呼び出され、 **Complete**メソッドが呼び出されなかった場合にトランザクションは中止されます。 コードがスコープから離れるような例外がスローされると、このトランザクションは中止されたと見なされます。  
  
 Using**ブロックを**使用して、 **using**ブロックが終了したときに、 **TransactionScope**オブジェクトで**Dispose**メソッドが呼び出されるようにすることをお勧めします。 保留中のトランザクションのコミットまたはロールバックに失敗すると、 **TransactionScope**の既定のタイムアウトが1分であるため、パフォーマンスが大幅に低下する可能性があります。 **Using**ステートメントを使用しない場合は、 **Try**ブロックですべての作業を実行し、 **Finally**ブロックで**Dispose**メソッドを明示的に呼び出す必要があります。  
  
 **TransactionScope**内で例外が発生した場合、トランザクションは不整合としてマークされ、破棄されます。 このメソッドは、 **TransactionScope**が破棄されるとロールバックされます。 例外が発生しない場合は、参加しているトランザクションがコミットされます。  
  
 **TransactionScope**は、ローカルおよびリモートのデータソースまたは外部リソースマネージャーがアクセスされている場合にのみ使用してください。 これは、 **TransactionScope**がコンテキスト接続内でのみ使用されている場合でも、常にトランザクションが昇格するためです。  
  
> [!NOTE]  
>  **TransactionScope**クラスは、既定で**Serializable**の**IsolationLevel**を使用してトランザクションを作成します。 使用しているアプリケーションによっては、アプリケーション内での競合を回避するために、分離レベルを低下させる必要がある場合があります。  
  
> [!NOTE]  
>  リモート サーバーに対する分散トランザクション内では、大量のデータベース リソースが消費されるため、更新、挿入、および削除だけを実行することをお勧めします。 操作がローカル サーバーで実行される場合は、分散トランザクションは必要なく、ローカル トランザクションで十分です。 SELECT ステートメントは、不必要にデータベース リソースをロックすることがあります。また、選択に多くのトランザクションを要する場合もあります。 データベース以外の作業は、トランザクション処理を行う他のリソース マネージャーを必要とする場合を除き、トランザクションのスコープ外で行う必要があります。 トランザクションのスコープ内で例外が発生しても、トランザクションはコミットされませんが、 **TransactionScope**クラスは、コードがトランザクション自体のスコープ外で行った変更をロールバックするための準備を行いません。 トランザクションがロールバックされるときに何らかのアクションを実行する必要がある場合は、 **IEnlistmentNotification**インターフェイスの独自の実装を記述し、トランザクションに明示的に参加する必要があります。  
  
## <a name="example"></a>例  
 **システムトランザクション**を操作するには、System.Transactions.dll ファイルへの参照が必要です。  
  
 次のコードでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の 2 つの異なるインスタンスに対して昇格可能なトランザクションを作成する方法を説明します。 これらのインスタンスは、 **TransactionScope**ブロックにラップされている2つ**の異なる system.string**オブジェクトで表されます。 このコードは、 **using**ステートメントを使用して**transactionscope**ブロックを作成し、最初の接続を開きます。これにより、 **transactionscope**に自動的に参加します。 このトランザクションは、完全な分散トランザクションとしてではなく、最初に軽量のトランザクションとして参加します。 このコードでは、条件ロジックが存在することを前提としています (説明を簡単にするために、このロジックは省略しています)。 必要な場合にのみ2番目の接続を開き、 **TransactionScope**に参加します。 2 番目の接続が開かれると、トランザクションは完全な分散トランザクションに自動的に昇格します。 次に、コードは**TransactionScope**を呼び出します。これによりトランザクションがコミットされます。 このコードは、接続に対し**て using ステートメントを**終了するときに、2つの接続を破棄します。 Transactionscope**の transactionscope**メソッドは、 **transactionscope**の**using**ブロックの終了時に自動的に呼び出されます。 **TransactionScope** **Transactionscope**ブロック内の任意のポイントで例外がスローされた場合、 **Complete**は呼び出されず、 **transactionscope**が破棄されると、分散トランザクションがロールバックされます。  
  
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
  
## <a name="see-also"></a>関連項目  
 [CLR 統合とトランザクション](../../relational-databases/clr-integration-data-access-transactions/clr-integration-and-transactions.md)  
  
  
