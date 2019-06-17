---
title: MSdistribution_history (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSdistribution_history
- MSdistribution_history_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSdistribution_history system table
ms.assetid: 55665bd2-9e1d-4efc-8f60-c63a24f66b28
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 305223fca45bb1916598f02c16cc4e38981e861d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62903698"
---
# <a name="msdistributionhistory-transact-sql"></a>MSdistribution_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSdistribution_history**テーブルは、ローカル ディストリビューターに関連付けられているディストリビューション エージェントの履歴行を保持します。 このテーブルは、ディストリビューション データベースに格納されます。  
  
## <a name="definition"></a>定義  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**agent_id**|**int**|ディストリビューション エージェントの ID。|  
|**runstatus**|**int**|実行中の状態:<br /><br /> **1** = 開始します。<br /><br /> **2** = 成功します。<br /><br /> **3** = 実行中です。<br /><br /> **4** = アイドル状態です。<br /><br /> **5** = 再試行します。<br /><br /> **6** = 失敗します。|  
|**start_time**|**datetime**|ジョブの実行開始時刻です。|  
|**time**|**datetime**|メッセージが記録された時刻。|  
|**duration**|**int**|メッセージ セッションの実行時間 (秒) です。|  
|**comments**|**nvarchar (4000)**|メッセージ テキストです。|  
|**xact_seqno**|**varbinary(16)**|最後に処理されたトランザクション シーケンス番号です。|  
|**current_delivery_rate**|**float**|最後の履歴エントリ以降 1 秒あたりに配信される平均コマンド数。|  
|**current_delivery_latency**|**int**|コマンドがディストリビューション データベースから最後の履歴エントリ以降のサブスクライバーに適用されるまでの待機時間。 単位はミリ秒。|  
|**delivered_transactions**|**int**|セッションに配信されたトランザクション数の合計。|  
|**delivered_commands**|**int**|セッションに配信されたコマンド数の合計。|  
|**average_commands**|**int**|セッションで配信される平均コマンド数。|  
|**delivery_rate**|**float**|配信されたコマンドを 1 秒あたりの平均です。|  
|**delivery_latency**|**int**|コマンドがディストリビューション データベースに登録されてからサブスクライバーに適用されるまでの待機時間です。 単位はミリ秒。|  
|**total_delivered_commands**|**bigint**|サブスクリプションの作成後に配信されたコマンド数の合計。|  
|**error_id**|**int**|内のエラーの ID、 **MSrepl_error**システム テーブル。|  
|**updateable_row**|**bit**|設定**1**履歴行を上書きできる場合。|  
|**timestamp**|**timestamp**|このテーブルのタイムスタンプ列です。|  
  
## <a name="see-also"></a>関連項目  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
