---
title: MSsnapshot_history (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSsnapshot_history
- MSsnapshot_history_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSsnapshot_history system table
ms.assetid: 56bf4128-1689-4963-9343-432dd0898d31
author: stevestein
ms.author: sstein
ms.openlocfilehash: a84b8c8caae460975a871a22d7cdac6d741d4d93
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67997281"
---
# <a name="mssnapshot_history-transact-sql"></a>MSsnapshot_history (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSsnapshot_history**テーブルには、ローカルディストリビューターに関連付けられているスナップショットエージェントの履歴行が含まれています。 このテーブルは、ディストリビューションデータベースに格納されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**agent_id**|**int**|スナップショットエージェントの ID。|  
|**runstatus**|**int**|実行ステータスです。<br /><br /> **1** = 開始します。<br /><br /> **2** = 成功します。<br /><br /> **3** = 実行中です。<br /><br /> **4** = アイドル状態。<br /><br /> **5** = 再試行します。<br /><br /> **6** = 失敗。|  
|**start_time**|**datetime**|ジョブの実行開始時刻です。|  
|**time**|**datetime**|メッセージがログに記録される時刻。|  
|**duration**|**int**|メッセージ セッションの実行時間 (秒) です。|  
|**コメント**|**nvarchar(255)**|メッセージ テキストです。|  
|**delivered_transactions**|**int**|セッションで配信されたトランザクションの合計数。|  
|**delivered_commands**|**int**|1秒間に配信されたコマンドの数。|  
|**delivery_rate**|**float (53)**|1秒間に配信された平均コマンド。|  
|**error_id**|**int**|[MSrepl_errors](../../relational-databases/system-tables/msrepl-errors-transact-sql.md)システムテーブル内のエラーの ID。|  
|**timestamp**|**timestamp**|このテーブルのタイムスタンプ列です。|  
  
## <a name="see-also"></a>参照  
 [レプリケーションテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
