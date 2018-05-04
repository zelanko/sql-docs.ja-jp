---
title: MSreplication_monitordata (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
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
- MSreplication_monitordata_TSQL
- MSreplication_monitordata
dev_langs:
- TSQL
helpviewer_keywords:
- MSreplication_monitordata system table
ms.assetid: 843d3ffd-a1ef-4fd5-a744-c2252199793e
caps.latest.revision: 16
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 12e873a83a654513e003a808aa74fa803fc25fa2
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="msreplicationmonitordata-transact-sql"></a>MSreplication_monitordata (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSreplication_monitordata**テーブルには、監視対象のサブスクリプションごとに 1 行のレプリケーション モニターで使用されるキャッシュ データが含まれています。 このテーブルは、ディストリビューション データベースに保存されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**lastrefresh**|**datetime**|モニター データが更新された日時です。|  
|**computetime**|**int**|モニター データの計算にかかる時間 (秒単位) です。|  
|**publication_id**|**int**|パブリケーションの ID です。|  
|**パブリッシャー**|**sysname**|パブリッシャーの名前。|  
|**publisher_srvid**|**int**|パブリッシャーのサーバー ID です。|  
|**publisher_db**|**sysname**|パブリケーション データベースの名前です。|  
|**パブリケーション**|**sysname**|パブリケーションの名前を指定します。|  
|**publication_type**|**int**|パブリケーションの種類です。次のいずれかの値をとります。<br /><br /> **0** = トランザクション パブリケーション<br /><br /> **1** = スナップショット パブリケーション<br /><br /> **2** = マージ パブリケーション|  
|**agent_type**|**int**|レプリケーション エージェントの種類です。次のいずれかの値をとります。<br /><br /> **1**スナップショット エージェントを =<br /><br /> **2**ログ リーダー エージェントを =<br /><br /> **3** = ディストリビューション エージェント<br /><br /> **4** = マージ エージェント<br /><br /> **9**キュー リーダー エージェントを =|  
|**agent_id**|**int**|レプリケーション エージェントの ID です。|  
|**agent_name**|**sysname**|レプリケーション エージェント ジョブの名前です。|  
|**job_id**|**uniqueidentifier**|レプリケーション エージェント ジョブの GUID です。|  
|**ステータス**|**int**|レプリケーション エージェントの状態です。次のいずれかの値をとります。<br /><br /> **1** = 開始<br /><br /> **2** = に成功しました<br /><br /> **3** = 実行中<br /><br /> **4** = アイドル状態<br /><br /> **5** = 再試行<br /><br /> **6** = に失敗しました|  
|**isagentrunningnow**|**bit**|かどうか、エージェント ジョブが現在実行中の値を示すフラグ**1**ジョブが実行されていることを意味します。|  
|**警告**|**int**|サブスクリプションによって生成されるしきい値警告です。次の 1 つ以上の値の論理和演算をとります。<br /><br /> **1** = expiration: トランザクション パブリケーションに対するサブスクリプションが、保有期間のしきい値を超えるによって、保有期間のパーセンテージを超えました。<br /><br /> **2** = 待機時間、トランザクション パブリッシャーからサブスクライバーにデータをレプリケートにかかった時間 (秒) がしきい値を超えています。<br /><br /> **4** mergeexpiration = マージ パブリケーションに対するサブスクリプションが、保有期間ので、許容されるしきい値を超える保有期間のパーセンテージを超えました。 8 = mergefastrunduration : 高速ネットワーク接続を使用して、マージ サブスクリプションの同期を完了するのにかかった時間が、秒単位のしきい値を超えています。<br /><br /> **16** = mergeslowrunduration - マージ サブスクリプションの同期の完了にかかった時間低速またはダイヤルアップ ネットワーク接続経由で (秒単位) がしきい値を超えています。<br /><br /> **32** = mergefastrunspeed 配信率、マージ サブスクリプションの同期中の行は、高速ネットワーク接続経由でのしきい値の割合を 1 秒あたりの行を維持するために失敗しました。<br /><br /> **64** = mergeslowrunspeed 配信率、マージ サブスクリプションの同期中の行が低速またはダイヤルアップ ネットワーク接続経由でのしきい値の割合を 1 秒あたりの行を維持するために失敗しました。|  
|**last_distsync**|**datetime**|最後の日付と、ディストリビューション エージェントを実行した時刻。|  
|**agentstoptime**|**datetime**|エージェントが停止された日時です。|  
|**distdb**|**sysname**|サブスクリプション用のディストリビューション データベースの名前です。|  
|**保有期間**|**int**|パブリケーションの保有期間です。|  
|**time_stamp**|**datetime**|内部使用のみ。|  
|**worst_latency**|**int**|データ変更が、トランザクション パブリケーションのログ リーダー エージェントとディストリビューション エージェントで伝達されるまでの最大待機時間 (秒単位) です。|  
|**best_latency**|**int**|トランザクション パブリケーションのログ リーダー エージェントまたはディストリビューション エージェントによって反映されるデータ変更の最小待機時間 (秒) です。|  
|**avg_latency**|**int**|トランザクション パブリケーションのログ リーダー エージェントまたはディストリビューション エージェントによって反映されるデータ変更の平均待機時間 (秒) です。|  
|**cur_latency**|**int**|現在の実行処理中に、ログ リーダー エージェントまたはディストリビューション エージェントによって反映されるデータ変更の待機時間 (秒) です。|  
|**worst_runspeedPerf**|**int**|マージ パブリケーションの最長同期時間です。|  
|**best_runspeedPerf**|**int**|マージ パブリケーションの最短同期時間です。|  
|**average_runspeedPerf**|**int**|マージ パブリケーションの平均同期時刻|  
|**mergePerformance**|**int**|サブスクリプションに対するすべての同期と比較した前回の同期のパフォーマンスです。前回の同期の配信速度を前回までのすべての配信速度の平均で割った値に基づいて算出されます。|  
|**mergelatestsessionrunduration**|**int**|マージ エージェントが最後に実行された際の実行時間です。|  
|**mergelatestsessionrunspeed**|**float(53)**|マージ エージェントが最後に実行された際の配信率です。|  
|**mergelatestsessionconnectiontype**|**int**|最後のマージ エージェント セッションで使用した接続です。次のいずれかの値をとります。<br /><br /> **1** = ローカル エリア ネットワーク (LAN)<br /><br /> **2** = ダイヤルアップ ネットワーク接続|  
|**retention_period_unit**|**tinyint**|保有期間を定義するときに使用する単位を指定します。次のいずれかの値をとります。<br /><br /> **1** = 週<br /><br /> **2** = 月<br /><br /> **3** = 年|  
  
## <a name="see-also"></a>参照  
 [プログラムでレプリケーションを監視します。](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)   
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_replmonitorhelpsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replmonitorhelpsubscription-transact-sql.md)   
 [sp_replmonitorhelppublication &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replmonitorhelppublication-transact-sql.md)   
 [sp_replmonitorhelppublisher &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replmonitorhelppublisher-transact-sql.md)   
 [sp_replmonitorhelpmergesession &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replmonitorhelpmergesession-transact-sql.md)   
 [sp_replmonitorhelppublicationthresholds &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replmonitorhelppublicationthresholds-transact-sql.md)   
 [sp_replmonitorhelpmergesessiondetail &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replmonitorhelpmergesessiondetail-transact-sql.md)  
  
  
