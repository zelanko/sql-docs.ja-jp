---
title: MSsubscription_agents (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
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
- MSsubscription_agents
- MSsubscription_agents_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSsubscription_agents system table
ms.assetid: 86ad5891-0bef-4963-9381-7d5b45245a0c
caps.latest.revision: 25
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: fda3a53eae90bd9c21c25124cef2254451cb1ab1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "33010989"
---
# <a name="mssubscriptionagents-transact-sql"></a>MSsubscription_agents (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSsubscription_agents**サブスクリプションのプロパティを追跡するためにディストリビューション エージェントおよび更新可能なサブスクリプションのトリガーでテーブルを使用します。 次の表は、サブスクリプション データベースに格納されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**id**|**int**|行の ID です。|  
|**パブリッシャー**|**sysname**|パブリッシャーの名前。|  
|**publisher_db**|**sysname**|パブリケーション データベースの名前です。|  
|**パブリケーション**|**sysname**|パブリケーションの名前を指定します。|  
|**subscription_type**|**int**|サブスクリプションのタイプです。<br /><br /> 0 = プッシュ<br /><br /> 1 = プル<br /><br /> 2 = プル匿名|  
|**queue_id**|**sysname**|ID、[!INCLUDE[msCoName](../../includes/msconame-md.md)]パブリッシャー側でキューのメッセージします。 *queue_id*に設定されている**SQL**の SQL ベースのキューを更新します。|  
|**update_mode**|**tinyint**|更新のタイプです。<br /><br /> **0** = 読み取り専用です。<br /><br /> **1** = 即時更新します。<br /><br /> **2**メッセージ キューを使用するキュー更新を = です。<br /><br /> **3**イミディ エイト = メッセージ キューを使用してフェールオーバーとしてキューに置かれた更新プログラムで更新します。<br /><br /> **4** SQL Server キューを使用するキュー更新を = です。<br /><br /> **5** = キュー更新フェールオーバーでは、SQL Server キューを使用する即時更新します。|  
|**failover_mode**|**bit**|更新のフェールオーバー タイプが選択された場合、そのタイプは次のいずれかです。<br /><br /> **0** = 即時更新が使用されています。 フェールオーバーは有効ではありません。<br /><br /> **1** = キュー更新が使用されています。 フェールオーバーは有効です。 フェールオーバーに使用されているキューがで指定された、 *update_mode*値。|  
|**spid**|**int**|現在稼働している、または稼動した直後のディストリビューション エージェントが使用する接続のシステム プロセス ID です。|  
|**login_time**|**datetime**|現在稼働している、または稼動した直後のディストリビューション エージェント接続の日時です。|  
|**allow_subscription_copy**|**bit**|サブスクリプション データベースをコピーできるかどうかを指定します。|  
|**attach_state**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**attach_version**|**binary(16)**|アタッチされたサブスクリプションのバージョンに相当する一意識別子です。|  
|**last_sync_status**|**int**|現在稼働している、または稼動した直後のディストリビューション エージェントの、最新の実行ステータスです。 ステータスの値が示す内容は次のとおりです。<br /><br /> **1** = 開始します。<br /><br /> **2** = に成功しました。<br /><br /> **3** = 実行中です。<br /><br /> **4** = アイドル状態です。<br /><br /> **5** = 再試行します。<br /><br /> **6** = 失敗します。|  
|**last_sync_summary**|**sysname**|現在稼働している、または稼動した直後のディストリビューション エージェントの、最新のメッセージです。 ステータスの値が示す内容は次のとおりです。<br /><br /> **開始しました。**<br /><br /> **成功しました。**<br /><br /> **進行中です。**<br /><br /> **アイドル状態です。**<br /><br /> **再試行してください。**<br /><br /> **失敗します。**|  
|**last_sync_time**|**datetime**|日付と時刻、 *last_sync_summary*と*last_sync_status*列が更新されました。 SqlServer エージェント サービス ジョブとして稼動しているプルまたは匿名ディストリビューション エージェントは、これらの列を更新しません。 この場合、履歴情報がジョブ履歴テーブルに代わりに記録されます。|  
|**queue_server**|**sysname**|内部使用のみです。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_helppullsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql.md)  
  
  
