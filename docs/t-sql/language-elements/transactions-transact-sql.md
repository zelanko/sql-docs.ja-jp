---
title: "トランザクション (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/25/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Transactions
- Transactions_TSQL
dev_langs: TSQL
helpviewer_keywords:
- transactions [SQL Server]
- transactions [SQL Server], about transactions
- UOW [SQL Server]
- unit of work [SQL Server]
ms.assetid: 1485c375-921a-42af-a871-bb333cc08d3e
caps.latest.revision: "24"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: afd593c02535ec51932bb2c036e34c3406d8a87d
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="transactions-transact-sql"></a>トランザクション (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  トランザクションは、1 つの作業を表す単位です。 トランザクションが成功すると、トランザクションの実行中に行われたすべてのデータ変更がコミットされ、データベースの変更が確定します。 エラーが発生したため、トランザクションを取り消すか、またはロールバックする必要がある場合、すべてのデータ変更は消去されます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]次のトランザクション モードでは動作します。  
  
 自動コミット トランザクション  
 各ステートメントは 1 つのトランザクションです。  
  
 明示的なトランザクション  
 各トランザクションは、BEGIN TRANSACTION ステートメントで明示的に開始し、COMMIT または ROLLBACK ステートメントで明示的に終了します。  
  
 暗黙のトランザクション  
 新しいトランザクションは、前のトランザクションが終了すると暗黙的に開始しますが、各トランザクションは COMMIT または ROLLBACK ステートメントで明示的に終了します。  
  
 バッチ スコープのトランザクション  
 複数のアクティブな結果セット (MARS) にのみ適用可能な[!INCLUDE[tsql](../../includes/tsql-md.md)]MARS セッションで開始された明示的または暗黙的なトランザクションがバッチ スコープのトランザクションになります。 バッチの完了時にコミットまたはロールバックされていないバッチスコープのトランザクションは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] により自動的にロールバックされます。  

> [!NOTE] 
> データ ウェアハウスの製品に関連する特別な考慮事項を参照してください。[トランザクション (SQL データ ウェアハウス)](transactions-sql-data-warehouse.md)です。   

## <a name="in-this-section"></a>このセクションの内容  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]次のトランザクション ステートメントを提供します。  
  
|||  
|-|-|  
|[BEGIN DISTRIBUTED TRANSACTION](../../t-sql/language-elements/begin-distributed-transaction-transact-sql.md)|[ROLLBACK TRANSACTION](../../t-sql/language-elements/rollback-transaction-transact-sql.md)|  
|[BEGIN TRANSACTION](../../t-sql/language-elements/begin-transaction-transact-sql.md)|[ROLLBACK WORK](../../t-sql/language-elements/rollback-work-transact-sql.md)|  
|[COMMIT TRANSACTION](../../t-sql/language-elements/commit-transaction-transact-sql.md)|[SAVE TRANSACTION](../../t-sql/language-elements/save-transaction-transact-sql.md)|  
|[COMMIT WORK](../../t-sql/language-elements/commit-work-transact-sql.md)||  
  
## <a name="see-also"></a>参照  
 [[SET implicit_transactions] &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-implicit-transactions-transact-sql.md)   
 [@@TRANCOUNT &#40;Transact-SQL&#41;](../../t-sql/functions/trancount-transact-sql.md)  
  
  
