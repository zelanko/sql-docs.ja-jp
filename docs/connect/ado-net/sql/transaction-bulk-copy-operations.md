---
title: トランザクションと一括コピー操作
description: トランザクション内で一括コピー操作を実行する方法、およびトランザクションをコミットまたはロールバックする方法について説明します。
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: f6f0cbc9-f7bf-4d6e-875f-ad1ba0b4aa62
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: 685bb349366ad955248a05e23ec030788dcbc63d
ms.sourcegitcommit: 6b3569977b034554883a94d73d1c4df6e2f74fe2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2020
ms.locfileid: "85106908"
---
# <a name="transaction-and-bulk-copy-operations"></a>トランザクションと一括コピー操作

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

一括コピー操作は、単独の操作として、または、複数の手順からなるトランザクションの一部として実行されます。 複数の手順からなるトランザクションの一部として実行する場合、挿入、更新、削除など、他のデータベース操作に加えて、同じトランザクション内で一括コピー操作を複数回実行でき、トランザクション全体をコミットまたはロールバックすることもできます。  
  
既定では、一括コピー操作は単独の操作として行われます。 この一括コピー操作は非トランザクション方式で処理され、ロールバックできません。 エラーが発生したときに一括コピーのすべてまたは一部をロールバックする必要がある場合は、次のことが行えます。

 - <xref:Microsoft.Data.SqlClient.SqlBulkCopy> マネージド トランザクションを使用する

 - 既存のトランザクション内で一括コピー操作を実行する

 - **System.Transactions** <xref:System.Transactions.Transaction> に登録する  
  
## <a name="performing-a-non-transacted-bulk-copy-operation"></a>非トランザクション処理の一括コピー操作の実行  
次のコンソール アプリケーションでは、非トランザクション処理のバルク コピー操作で処理中にエラーが検出されたときに、そのエラーの内容を表示します。  
  
例では、コピー元のテーブルとコピー先のテーブルにはそれぞれ、**ProductID** という名前の `Identity` 列があります。 このコードでは、最初にコピー先のテーブルの行をすべて削除してコピー先を用意し、コピー元のテーブルに存在する **ProductID** 行を 1 行挿入しています。 既定では、`Identity` 列の新しい値は追加した各行のコピー先のテーブル内で生成されます。 この例では、代わりに、コピー元のテーブルからの `Identity` 値を使用するバルク ロード処理を強制的に行う接続が開かれている場合、オプションが設定されます。  
  
このバルク コピー操作は、<xref:Microsoft.Data.SqlClient.SqlBulkCopy.BatchSize%2A> プロパティを 10 に設定して実行されます。 操作中に無効な行が検出されると、例外がスローされます。 次に示す最初の例の一括コピー操作はトランザクション処理ではありません。 エラーの時点までにコピーされたすべてのバッチがコミットされます。 重複するキーを含むバッチがロールバックされ、残りのバッチを処理する前に一括コピー操作が停止されます。  
  
> [!NOTE]
>  このサンプルは、「[一括コピーのセットアップ例](bulk-copy-example-setup.md)」で説明しているように作業テーブルを作成して取得してからでないと動作しません。 このコードでは、**SqlBulkCopy** だけを使用した構文について説明します。 コピー元およびコピー先のテーブルが同一の SQL Server インスタンス内に存在する場合、Transact-SQL`INSERT … SELECT` ステートメントを使用すれば簡単かつ高速にデータをコピーすることができます。  
  
[!code-csharp[DataWorks SqlBulkCopyOptions_Default#1](~/../sqlclient/doc/samples/SqlBulkCopyOptions_Default.cs#1)]
  
## <a name="performing-a-dedicated-bulk-copy-operation-in-a-transaction"></a>トランザクションでの専用の一括コピー操作の実行  
既定では、一括コピー操作は専用のトランザクションで実行されます。 専用の一括コピー操作を実行する場合は、接続文字列を使用して <xref:Microsoft.Data.SqlClient.SqlBulkCopy> のインスタンスを作成するか、アクティブなトランザクションがない既存の <xref:Microsoft.Data.SqlClient.SqlConnection> オブジェクトを使用します。 一括コピー操作によって、各シナリオでトランザクションが作成され、その後、トランザクションがコミットまたはロールバックされます。  
  
<xref:Microsoft.Data.SqlClient.SqlBulkCopy> クラス コンストラクターで <xref:Microsoft.Data.SqlClient.SqlBulkCopyOptions.UseInternalTransaction> オプションを明示的に指定して、独自のトランザクションで一括コピー操作を実行することができます。 操作の各バッチは、個別のトランザクション内で実行されます。  
  
> [!NOTE]
>  異なるバッチは別々のトランザクション内で実行されます。このため、バルク コピー操作中にエラーが発生した場合、現在処理中のバッチの行はすべてロールバックされますが、エラーの発生前にバッチでコピーされた行はデータベースに残ります。  
  
次のコンソール アプリケーションは前の例と似ていますが、1 つ違う点があります。この例では、一括コピー操作が専用のトランザクションを管理しています。 エラーの時点までにコピーされたすべてのバッチがコミットされます。 重複するキーを含むバッチがロールバックされ、残りのバッチを処理する前に一括コピー操作が停止されます。 
  
> [!IMPORTANT]
>  このサンプルは、「[一括コピーのセットアップ例](bulk-copy-example-setup.md)」で説明しているように作業テーブルを作成して取得してからでないと動作しません。 このコードでは、**SqlBulkCopy** だけを使用した構文について説明します。 コピー元およびコピー先のテーブルが同一の SQL Server インスタンス内に存在する場合、Transact-SQL`INSERT … SELECT` ステートメントを使用すれば簡単かつ高速にデータをコピーすることができます。  
  
[!code-csharp[DataWorks SqlBulkCopyOptions_UseInternalTransaction#1](~/../sqlclient/doc/samples/SqlBulkCopyOptions_UseInternalTransaction.cs#1)]
  
## <a name="using-existing-transactions"></a>既存のトランザクションの使用  
既存の <xref:Microsoft.Data.SqlClient.SqlTransaction> オブジェクトを、<xref:Microsoft.Data.SqlClient.SqlBulkCopy> コンストラクターのパラメーターとして指定できます。 この場合、一括コピー操作は既存のトランザクションで行われます。トランザクションの状態は変更されず、コミットも中止もされません。 これにより、アプリケーションで他のデータベース操作とのトランザクションに一括コピー操作を含めることができるようになります。 ただし、<xref:Microsoft.Data.SqlClient.SqlTransaction> オブジェクトを指定せずに null 参照を渡した場合、接続にアクティブなトランザクションが含まれていると、例外がスローされます。   
  
エラーが発生したため一括コピー操作全体をロールバックする必要がある場合、またはロールバック可能な大きな処理の一部として一括コピー処理を実行する場合は、<xref:Microsoft.Data.SqlClient.SqlTransaction> オブジェクトを <xref:Microsoft.Data.SqlClient.SqlBulkCopy> コンストラクターに指定できます。  
  
次のコンソール アプリケーションは最初の (トランザクションのない) 例とほぼ同じですが、バルク コピー操作がより大きな外部トランザクションに含まれている点が異なります。 主キーの違反エラーが発生した場合、トランザクションはすべてロールバックされ、コピー先のテーブルに行は追加されません。  
  
> [!IMPORTANT]
>  このサンプルは、「[一括コピーのセットアップ例](bulk-copy-example-setup.md)」で説明しているように作業テーブルを作成して取得してからでないと動作しません。 このコードでは、**SqlBulkCopy** だけを使用した構文について説明します。 コピー元およびコピー先のテーブルが同一の SQL Server インスタンス内に存在する場合、Transact-SQL`INSERT … SELECT` ステートメントを使用すれば簡単かつ高速にデータをコピーすることができます。  
  
[!code-csharp[DataWorks SqlBulkCopy_ExternalTransaction#1](~/../sqlclient/doc/samples/SqlBulkCopy_ExternalTransaction.cs#1)]
  
## <a name="next-steps"></a>次のステップ
- [SQL Server での一括コピー操作](bulk-copy-operations-sql-server.md)
