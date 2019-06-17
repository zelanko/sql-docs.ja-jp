---
title: '[クエリ オプション] ([詳細] ページ) の実行 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.query.advanced.f1
ms.assetid: 661595ce-99b9-4316-ad80-ed04002d04d5
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: f08758af9c75e36dbf8c8d4d62ae17352972b79d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66089093"
---
# <a name="query-options-execution-advanced-page"></a>[クエリ オプション] の [実行] ([詳細設定] ページ)
  **SET** ステートメントを使用する際には、さまざまなオプションを指定できます。 このページを使用して **set** オプションを指定し、Microsoft SQL Server クエリを実行します。 各オプションの詳細については、SQL Server オンライン ブックを参照してください。  
  
 **SET NOCOUNT**  
 結果セットのメッセージとして、行数を返しません。 既定では、このオプションはオフになっています。  
  
 **SET NOEXEC**  
 クエリを実行しません。 既定では、このオプションはオフになっています。  
  
 **SET PARSEONLY**  
 各クエリの構文をチェックするだけで、クエリを実行しません。 既定では、このオプションはオフになっています。  
  
 **SET CONCAT_NULL_YIELDS_NULL**  
 このチェック ボックスがオンの場合、既存の値と `NULL` を連結するクエリは、結果として常に `NULL` を返します。 このチェック ボックスがオフの場合、既存の値と `NULL` を連結するクエリは、既存の値を返します。 既定では、このオプションはオンになっています。  
  
 **SET ARITHABORT**  
 このチェック ボックスがオンの場合、式の評価中に `INSERT`、`DELETE`、または `UPDATE` ステートメントで算術エラー (オーバーフロー、0 による除算、またはドメイン エラー) が発生すると、クエリまたはバッチは終了します。 このチェック ボックスがオフの場合、可能であればその値に対して  `NULL` が与えられ、クエリが続行されます。さらに、結果にメッセージが含められます。 この動作の詳細については、オンライン ブックを参照してください。 既定では、このオプションはオンになっています。  
  
 **SET SHOWPLAN_TEXT**  
 このチェック ボックスがオンの場合、各クエリに対してクエリ プランがテキスト形式で返されます。 既定では、このオプションはオフになっています。  
  
 **SET STATISTICS TIME**  
 このチェック ボックスがオンの場合、各クエリに対して時間統計情報が返されます。 既定では、このオプションはオフになっています。  
  
 **SET STATISTICS IO**  
 このチェック ボックスがオンの場合、各クエリに対して入出力 (I/O) に関する統計情報が返されます。 既定では、このオプションはオフになっています。  
  
 **SET TRANSACTION ISOLATION LEVEL**  
 既定では READ COMMITTED トランザクション分離レベルが設定されます。 詳細については、「[SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql)」を参照してください。 SNAPSHOT トランザクション分離レベルは使用できません。 SNAPSHOT 分離を使用するには、次の [!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントを追加します。  
  
```  
SET TRANSACTION ISOLATION LEVEL SNAPSHOT;  
GO  
```  
  
 **デッドロックの優先度を設定**  
 既定値の **[Normal]** の場合、デッドロックが発生したときに各クエリに同じ優先度が与えられます。 このクエリがデッドロックの競合で常に敗北し、終了されるクエリとして選択されるようにするには、ドロップダウン リストで優先度 [Low] を選択してください。  
  
 **SET LOCK TIMEOUT**  
 既定値の -1 は、トランザクションが完了するまでロックが保持されることを示します。 値が 0 の場合は、待ち時間はありません。ロックがかかるとすぐにメッセージが返されます。 トランザクションを終了するまでのロックを 0 ミリ秒よりも長く保持する必要がある場合は、0 より大きい値を指定します。  
  
 **SET QUERY_GOVERNOR_COST_LIMIT**  
 **query governor cost limit** オプションは、クエリを実行できる時間の上限を指定する場合に使用します。 クエリ コストとは、特定のハードウェア構成でクエリを完了するために必要とされる予測所要時間を秒単位で表したものです。 既定値の 0 は、クエリの実行に関して時間的制限がないことを示します。  
  
 **プロバイダー メッセージ ヘッダーを抑制します。**  
 このチェック ボックスがオンの場合、プロバイダー (OLE DB プロバイダーなど) からの状態メッセージが表示されません。 既定では、このチェック ボックスはオンになっています。 プロバイダー レベルで失敗するクエリのトラブルシューティングを行うときにプロバイダー メッセージを表示するには、このチェック ボックスをオフにします。  
  
 **クエリの実行後に切断します。**  
 このチェック ボックスがオンの場合、クエリが完了した後に SQL Server への接続が終了します。 既定では、このオプションはオフになっています。  
  
 **既定値にリセット**  
 このページ上のすべての値を元の既定値にリセットします。  
  
  
