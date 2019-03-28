---
title: sp_replmonitorhelppublication (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replmonitorhelppublication_TSQL
- sp_replmonitorhelppublication
helpviewer_keywords:
- sp_replmonitorhelppublication
ms.assetid: 7928c50c-617f-41c5-9e0f-4e42e8be55dc
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 812ddd803d2a41695429902d6d8fc470ccef9576
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58529219"
---
# <a name="spreplmonitorhelppublication-transact-sql"></a>sp_replmonitorhelppublication (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  パブリッシャー側の 1 つ以上のパブリケーションに関する現在の状態情報を返します。 レプリケーションの監視に使用される、このストアド プロシージャはディストリビューターのディストリビューション データベースで実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_replmonitorhelppublication [ @publisher = ] 'publisher'  
    [ , [ @publisher_db = ] 'publisher_db'   
    [ , [ @publication = ] 'publication'   
    [ , [ @publication_type = ] publication_type ]   
    [ , [ @refreshpolicy = ] refreshpolicy ]  
```  
  
## <a name="arguments"></a>引数  
`[ @publisher = ] 'publisher'` 状態が監視されているパブリッシャーの名前です。 *パブリッシャー*は**sysname**既定値は NULL です。 場合**null**ディストリビューターを使用するすべてのパブリッシャーに関する情報が返されます。  
  
`[ @publisher_db = ] 'publisher_db'` パブリッシュされたデータベースの名前です。 *publisher_db*は**sysname**既定値は NULL です。 NULL の場合は、パブリッシャー側でパブリッシュされたデータベースのすべての情報が返されます。  
  
`[ @publication = ] 'publication'` 監視されているパブリケーションの名前。 *パブリケーション*は**sysname**既定値は NULL です。  
  
`[ @publication_type = ] publication_type` 場合、パブリケーションの種類。 *publication_type*は**int**、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**0**|トランザクション パブリケーション。|  
|**1**|スナップショット パブリケーション。|  
|**2**|マージ パブリケーションです。|  
|NULL (既定値)|レプリケーションは、パブリケーションの種類を決定しようとします。|  
  
`[ @refreshpolicy = ] refreshpolicy` 内部でのみ使用します。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**publisher_db**|**sysname**|パブリッシャーの名前です。|  
|**パブリケーション**|**sysname**|パブリケーションの名前です。|  
|**publication_type**|**int**|パブリケーションで、これらの値のいずれかの型です。<br /><br /> **0** = トランザクション パブリケーション<br /><br /> **1** = スナップショット パブリケーション<br /><br /> **2** = マージ パブリケーション|  
|**status**|**int**|パブリケーションに関連付けられているすべてのレプリケーション エージェントの状態の最大値です。次のいずれかの値をとります。<br /><br /> **1** = 開始<br /><br /> **2** = に成功しました<br /><br /> **3** = 実行中<br /><br /> **4** = アイドル状態<br /><br /> **5** = 再試行<br /><br /> **6** = に失敗しました|  
|**警告**|**int**|パブリケーションに属しているサブスクリプションによって生成されるしきい値警告の最大値です。次の 1 つ以上の値の論理和になります。<br /><br /> **1** = 有効期限の保有期間のしきい値内で、トランザクション パブリケーションに対するサブスクリプションが同期されていません。<br /><br /> **2** = 待機時間、トランザクション パブリッシャーからサブスクライバーへのデータのレプリケートにかかった時間 (秒)、しきい値を超えています。<br /><br /> **4** = mergeexpiration 保有期間のしきい値内でマージ パブリケーションに対するサブスクリプションが同期されていません。<br /><br /> **8** = mergefastrunduration - マージ サブスクリプションの同期の完了にかかった時間、高速ネットワーク接続経由で秒単位で、しきい値を超えています。<br /><br /> **16** = mergeslowrunduration - マージ サブスクリプションの同期の完了にかかった時間、低速またはダイヤルアップ ネットワーク接続経由で秒単位で、しきい値を超えています。<br /><br /> **32** = mergefastrunspeed - 配信率マージ サブスクリプションの同期中の行が高速ネットワーク接続経由でのしきい値の割合で、1 秒あたりの行を維持するために失敗しました。<br /><br /> **64** mergeslowrunspeed - 配信率 = マージ サブスクリプションの同期中の行が低速またはダイヤルアップ ネットワーク接続経由でのしきい値の割合で、1 秒あたりの行を維持するために失敗しました。|  
|**worst_latency**|**int**|トランザクション パブリケーションのログ リーダーまたはディストリビューション エージェントによって反映されるデータの変更を秒単位で最大待ち時間。|  
|**best_latency**|**int**|秒単位のトランザクション パブリケーションのログ リーダーまたはディストリビューション エージェントによって反映されるデータ変更で最も短い。|  
|**average_latency**|**int**|平均待機時間、トランザクション パブリケーションのログ リーダーまたはディストリビューション エージェントによって反映されるデータの変更 (秒)。|  
|**last_distsync**|**datetime**|ディストリビューション エージェントが最後に実行された日時です。|  
|**保有期間**|**int**|パブリケーションの保有期間です。|  
|**latencythreshold**|**int**|トランザクション パブリケーションの待機時間のしきい値が設定されています。|  
|**expirationthreshold**|**int**|マージ パブリケーションの場合は、パブリケーションの設定の有効期限のしきい値です。|  
|**agentnotrunningthreshold**|**int**|しきい値は、長い間、エージェントが実行されないように設定されています。|  
|**subscriptioncount**|**int**|パブリケーションに対するサブスクリプションの数です。|  
|**runningdistagentcount**|**int**|ディストリビューション エージェントの数が、パブリケーションに対して実行しています。|  
|**snapshot_agentname**|**sysname**|パブリケーションのスナップショット エージェント ジョブの名前。|  
|**logreader_agentname**|**sysname**|トランザクション パブリケーションのログ リーダー エージェント ジョブの名前。|  
|**qreader_agentname**|**sysname**|サポートするトランザクション パブリケーションに対するキュー リーダー エージェント ジョブの名前はキュー更新。|  
|**worst_runspeedPerf**|**int**|マージ パブリケーションの最長同期時間です。|  
|**best_runspeedPerf**|**int**|マージ パブリケーションの最短同期時間です。|  
|**average_runspeedPerf**|**int**|マージ パブリケーションの平均同期時間です。|  
|**retention_period_unit**|**int**|Express を使用する単位は、*保有*します。|  
|**パブリッシャー**|**sysname**|パブリケーションをパブリッシュする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの名前です。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_replmonitorhelppublication**はあらゆる種類のレプリケーションで使用します。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **db_owner**または**replmonitor** 、ディストリビューション データベースの固定データベース ロールが実行できる**sp_replmonitorhelppublication**します。  
  
## <a name="see-also"></a>参照  
 [Programmatically Monitor Replication (プログラムによるレプリケーションの監視)](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
