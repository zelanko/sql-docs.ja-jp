---
title: CONTEXT_INFO (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CONTEXT_INFO_TSQL
- CONTEXT_INFO
dev_langs:
- TSQL
helpviewer_keywords:
- CONTEXT_INFO function
- Multiple Active Result Sets
- context information [SQL Server]
- MARS [SQL Server]
- session context information [SQL Server]
ms.assetid: 571320f5-7228-4b0e-9d01-ab732d2d1eab
caps.latest.revision: 19
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 98a275622a809b3856b66d825cd48e2698fea51b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="contextinfo--transact-sql"></a>CONTEXT_INFO (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

[SET CONTEXT_INFO](../../t-sql/statements/set-context-info-transact-sql.md) ステートメントを使用して現在のセッションまたはバッチに設定された **context_info** 値を返します。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
CONTEXT_INFO()  
```  
  
## <a name="return-value"></a>戻り値
**Context_info** 値。
  
**Context_info** は設定されませんでした: 場合
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は NULL を返します。  
-   * * -[!INCLUDE[ssSDS](../../includes/sssds-md.md)] で  、一意のセッション固有 GUID.* * を返します。  
  
## <a name="remarks"></a>Remarks  
複数のアクティブな結果セット (MARS) によって、アプリケーションは複数のバッチまたは要求を同じ接続上で同時に実行できます。 MARS 接続上の 1 つのバッチで SET CONTEXT_INFO を実行する場合、CONTEXT_INFO 関数を SET ステートメントと同時に実行すると、新しいコンテキスト値が返されます。 接続上のその他の 1 つ以上のバッチで CONTEXT_INFO 関数を実行するには、SET ステートメントの実行が完了した後のバッチで開始しないと、新しい値は返されません。
  
## <a name="permissions"></a>アクセス許可  
特に必要な権限はありません。 コンテキスト情報は、**sys.dm_exec_request**s、**sys.dm_exec_sessions**、および **sys.sysprocesses** システム ビュー内にも保存されますが、これらのビューを直接クエリする場合は SELECT および VIEW SERVER STATE 権限が必要です。
  
## <a name="examples"></a>使用例  
次の簡単な例では、**context_info** 値を `0x1256698456` に設定してから、`CONTEXT_INFO` 関数を使用して値を取得します。
  
```sql
SET CONTEXT_INFO 0x1256698456;  
GO  
SELECT CONTEXT_INFO();  
GO  
```  
  
## <a name="see-also"></a>参照
[SET CONTEXT_INFO &#40;Transact-SQL&#41;](../../t-sql/statements/set-context-info-transact-sql.md)
  
  
