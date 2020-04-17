---
title: トランザクションの使用 |マイクロソフトドキュメント
description: 名前空間は、ADO.NETおよび SQL Server CLR 統合と完全に統合されたトランザクション フレームワークを提供します。
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
ms.openlocfilehash: 7fa98e9e13062d358a6a1810485d45c8d9d3e911
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488499"
---
# <a name="using-systemtransactions"></a>System.Transactions の使用
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  **System.Transactions**名前空間は、ADO.NETおよび[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]共通言語ランタイム (CLR) の統合と完全に統合されたトランザクション フレームワークを提供します。 クラス**は**、分散トランザクションに接続を暗黙的に参加させることによって、コード ブロック トランザクションを作成します。 **TransactionScope**でマークされたコード ブロックの末尾で**Complete**メソッドを呼び出す必要があります。 プログラムの実行がコード ブロックから離れると **、Dispose**メソッドが呼び出され **、Complete**メソッドが呼び出されない場合はトランザクションが中止されます。 コードがスコープから離れるような例外がスローされると、このトランザクションは中止されたと見なされます。  
  
 **using**ブロックが終了したときに **、Dispose**メソッドが**TransactionScope**オブジェクトで呼び出されるように **、using ブロックを使用**することをお勧めします。 トランザクションのコミットまたはロールバックに失敗すると **、TransactionScope**の既定のタイムアウトが 1 分であるため、パフォーマンスが著しい低下する可能性があります。 **using**ステートメントを使用しない場合は **、Try**ブロックですべての処理を実行し **、Finally**ブロックで**Dispose**メソッドを明示的に呼び出す必要があります。  
  
 **TransactionScope**内で例外が発生した場合、トランザクションは不整合としてマークされ、破棄されます。 **トランザクション スコープ**が破棄されると、ロールバックされます。 例外が発生しなければ、参加しているトランザクションがコミットされます。  
  
 **TransactionScope**は、ローカルおよびリモートのデータ ソースまたは外部リソース マネージャーがアクセスされている場合にのみ使用してください。 これは、トランザクションがコンテキスト接続内でのみ使用されている場合でも **、TransactionScope**によって常にトランザクションが昇格されるためです。  
  
> [!NOTE]  
>  クラス**は**、既定で**シリアル化可能**な**トランザクション**を作成します。 アプリケーションによっては、分離レベルを低くして、アプリケーション内の競合を回避することを検討する必要があります。  
  
> [!NOTE]  
>  リモート サーバーに対する分散トランザクション内では、大量のデータベース リソースが消費されるため、更新、挿入、および削除だけを実行することをお勧めします。 操作がローカル サーバーで実行される場合は、分散トランザクションは必要なく、ローカル トランザクションで十分です。 SELECT ステートメントは、不必要にデータベース リソースをロックすることがあります。また、選択に多くのトランザクションを要する場合もあります。 データベース以外の作業は、トランザクション処理を行う他のリソース マネージャーを必要とする場合を除き、トランザクションのスコープ外で行う必要があります。 トランザクションのスコープ内の例外によってトランザクションのコミットが妨げられますが **、TransactionScope**クラスには、トランザクション自体のスコープ外でコードが行った変更をロールバックする規定がありません。 トランザクションがロールバックされたときに何らかのアクションを実行する必要がある場合は **、System.Transactions.IEnlistmentNotification**インターフェイスの独自の実装を記述し、トランザクションに明示的に参加する必要があります。  
  
## <a name="example"></a>例  
 を使用するには **、System.Transactions.dll**ファイルへの参照が必要です。  
  
 次のコードでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の 2 つの異なるインスタンスに対して昇格可能なトランザクションを作成する方法を説明します。 これらのインスタンスは、**トランザクション スコープ**ブロックにラップされる 2 つの異なる**System.Data.SqlClient.SqlConnection**オブジェクトによって表されます。 このコードは using ステートメントを**使用**して**TransactionScope**ブロックを作成し、最初の接続を開き、その接続を自動的に**TransactionScope**に参加させます。 最初、トランザクションは完全な分散トランザクションではなく、軽量トランザクションとして参加します。 このコードでは、条件ロジックが存在することを前提としています (説明を簡単にするために、このロジックは省略しています)。 2 番目の接続は、必要な場合にのみ開き、それを**TransactionScope**に参加させます。 2 番目の接続が開かれると、トランザクションは完全な分散トランザクションに自動的に昇格します。 その後、トランザクションをコミットする**TransactionScope.Complete**を呼び出します。 このコードは、接続の**using**ステートメントを終了するときに、2 つの接続を破棄します。 **トランザクション スコープ**のメソッドは、**トランザクション スコープ**の**using**ブロックの終了時に自動的に呼び**TransactionScope**出されます。 例外が**TransactionScope**ブロック内の任意のポイントでスローされた場合 **、Complete**は呼び出されず、**トランザクション スコープ**が破棄されるときに分散トランザクションがロールバックされます。  
  
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
  
  
