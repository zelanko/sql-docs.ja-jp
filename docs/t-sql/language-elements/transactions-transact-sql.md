---
title: "トランザクション (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Transactions
- Transactions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- transactions [SQL Server]
- transactions [SQL Server], about transactions
- UOW [SQL Server]
- unit of work [SQL Server]
ms.assetid: 1485c375-921a-42af-a871-bb333cc08d3e
caps.latest.revision: 24
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 8660d0ac8d6205a94fdab24f41e41bac40a8671e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="transactions-transact-sql"></a>トランザクション (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  トランザクションは、1 つの作業を表す単位です。 トランザクションが成功すると、トランザクションの実行中に行われたすべてのデータ変更がコミットされ、データベースの変更が確定します。 エラーが発生したため、トランザクションを取り消すか、またはロールバックする必要がある場合、すべてのデータ変更は消去されます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]次のトランザクション モードで動作します。  
  
 自動コミット トランザクション  
 各ステートメントは 1 つのトランザクションです。  
  
 明示的なトランザクション  
 各トランザクションは、BEGIN TRANSACTION ステートメントで明示的に開始し、COMMIT または ROLLBACK ステートメントで明示的に終了します。  
  
 暗黙のトランザクション  
 新しいトランザクションは、前のトランザクションが終了すると暗黙的に開始しますが、各トランザクションは COMMIT または ROLLBACK ステートメントで明示的に終了します。  
  
 バッチ スコープのトランザクション  
 複数のアクティブな結果セット (MARS) にのみ適用可能な[!INCLUDE[tsql](../../includes/tsql-md.md)]MARS セッションで開始された明示的または暗黙的なトランザクションがバッチ スコープのトランザクションになります。 バッチの完了時にコミットまたはロールバックされていないバッチスコープのトランザクションは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] により自動的にロールバックされます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] には、次のトランザクション ステートメントが用意されています。  
  
|||  
|-|-|  
|[分散トランザクションの開始](../../t-sql/language-elements/begin-distributed-transaction-transact-sql.md)|[ROLLBACK TRANSACTION](../../t-sql/language-elements/rollback-transaction-transact-sql.md)|  
|[トランザクションを開始します。](../../t-sql/language-elements/begin-transaction-transact-sql.md)|[ROLLBACK WORK](../../t-sql/language-elements/rollback-work-transact-sql.md)|  
|[トランザクションをコミットします。](../../t-sql/language-elements/commit-transaction-transact-sql.md)|[トランザクションを保存します](../../t-sql/language-elements/save-transaction-transact-sql.md)|  
|[作業をコミットします。](../../t-sql/language-elements/commit-work-transact-sql.md)||  
  
## <a name="see-also"></a>参照  
 [[SET implicit_transactions] & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-implicit-transactions-transact-sql.md)   
 [@@TRANCOUNT &#40;Transact-SQL&#41;](../../t-sql/functions/trancount-transact-sql.md)  
  
  
