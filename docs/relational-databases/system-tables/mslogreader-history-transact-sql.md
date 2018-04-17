---
title: MSlogreader_history (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSlogreader_history_TSQL
- MSlogreader_history
dev_langs:
- TSQL
helpviewer_keywords:
- MSlogreader_history system table
ms.assetid: 2e399fa1-3591-4c1c-96b7-7964fe82c7c4
caps.latest.revision: 29
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c1b119040efebb1724b026cdb213cfdb9389a0d8
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="mslogreaderhistory-transact-sql"></a>MSlogreader_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSlogreader_history**ローカル ディストリビューターに関連付けられているログ リーダー エージェントの履歴行を保持します。 このテーブルは、ディストリビューション データベースに保存されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**agent_id**|**int**|ログ リーダー エージェントの ID です。|  
|**runstatus**|**int**|実行ステータスです。<br /><br /> 1 = 開始<br /><br /> 2 = 成功します。<br /><br /> 3 = 実行中<br /><br /> 4 = アイドル状態です。<br /><br /> 5 = 再試行<br /><br /> 6 = 失敗|  
|**start_time**|**datetime**|ジョブの実行開始時刻です。|  
|**time**|**datetime**|メッセージが記録された時刻です。|  
|**duration**|**int**|メッセージ セッションの実行時間 (秒) です。|  
|**comments**|**nvarchar (255)**|メッセージ テキストです。|  
|**xact_seqno**|**varbinary(16)**|最後に処理されたトランザクション シーケンス番号です。|  
|**delivery_time**|**int**|最初のトランザクションが配信された時刻です。|  
|**delivered_transactions**|**int**|セッション中に配信されたトランザクションの総数です。|  
|**delivered_commands**|**int**|セッションに配信されたコマンド数の合計。|  
|**average_commands**|**int**|セッション中に配信された平均コマンド数です。|  
|**delivery_rate**|**float**|1 秒あたりの平均配信コマンド数です。|  
|**delivery_latency**|**int**|コマンドがパブリッシュされたデータベースに登録されてからディストリビューション データベースに登録されるまでの待機時間です。 単位はミリ秒。|  
|**error_id**|**int**|内のエラーの ID、 **MSrepl_error**システム テーブル。|  
|**timestamp**|**timestamp**|このテーブルのタイムスタンプ列です。|  
|**updateable_row**|**bit**|設定**1**履歴行を上書きできる場合です。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
