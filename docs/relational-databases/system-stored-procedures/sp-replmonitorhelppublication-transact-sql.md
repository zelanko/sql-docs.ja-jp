---
title: "sp_replmonitorhelppublication (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_replmonitorhelppublication_TSQL
- sp_replmonitorhelppublication
helpviewer_keywords:
- sp_replmonitorhelppublication
ms.assetid: 7928c50c-617f-41c5-9e0f-4e42e8be55dc
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 581bfbad00edf6797f2bc21b15a17421d8217d73
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spreplmonitorhelppublication-transact-sql"></a>sp_replmonitorhelppublication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  パブリッシャー側の 1 つ以上のパブリケーションに関する現在の状態情報を返します。 このストアド プロシージャはレプリケーションの監視に使用し、ディストリビューター側でディストリビューション データベースについて実行されます。  
  
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
 [  **@publisher**  =] **'***パブリッシャー***'**  
 状態を監視しているパブリッシャーの名前を指定します。 *パブリッシャー*は**sysname**既定値は NULL です。 場合**null**、すべてのパブリッシャーのディストリビューターを使用する情報が返されます。  
  
 [  **@publisher_db**  =] **'***publisher_db***'**  
 パブリッシャー データベースの名前を指定します。 *publisher_db*は**sysname**既定値は NULL です。 NULL の場合、パブリッシャー側のパブリッシュされたすべてのデータベースに関する情報が返されます。  
  
 [  **@publication**  =] **'***パブリケーション***'**  
 監視されているパブリケーションの名前を指定します。 *パブリケーション*は**sysname**既定値は NULL です。  
  
 [  **@publication_type**  =] *publication_type*  
 パブリケーションの種類を指定します。 *publication_type*は**int**、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**0**|トランザクション パブリケーションです。|  
|**1**|スナップショット パブリケーションです。|  
|**2**|マージ パブリケーションです。|  
|NULL (既定値)|レプリケーションは、パブリケーションの種類を決定しようと試みます。|  
  
 [  **@refreshpolicy=** ] *refreshpolicy*  
 内部使用のみです。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**publisher_db**|**sysname**|パブリッシャーの名前です。|  
|**パブリケーション**|**sysname**|パブリケーションの名前です。|  
|**publication_type**|**int**|パブリケーションで、これらの値のいずれかの型です。<br /><br /> **0** = トランザクション パブリケーション<br /><br /> **1** = スナップショット パブリケーション<br /><br /> **2** = マージ パブリケーション|  
|**ステータス**|**int**|パブリケーションに関連付けられているすべてのレプリケーション エージェントの状態の最大値です。次のいずれかの値をとります。<br /><br /> **1** = 開始<br /><br /> **2** = に成功しました<br /><br /> **3** = 実行中<br /><br /> **4** = アイドル状態<br /><br /> **5** = 再試行<br /><br /> **6** = に失敗しました|  
|**警告**|**int**|パブリケーションに属しているサブスクリプションによって生成されるしきい値警告の最大値です。次の 1 つ以上の値の論理和になります。<br /><br /> **1** = expiration: トランザクション パブリケーションに対するサブスクリプションが、保有期間のしきい値内で同期されていません。<br /><br /> **2** = 待機時間、トランザクション パブリッシャーからサブスクライバーにデータをレプリケートにかかった時間 (秒) がしきい値を超えています。<br /><br /> **4** = mergeexpiration 保有期間のしきい値内で、マージ パブリケーションに対するサブスクリプションが同期されていません。<br /><br /> **8** = mergefastrunduration - マージ サブスクリプションの同期の完了にかかった時間のしきい値を超過、秒単位で高速ネットワーク接続します。<br /><br /> **16** = mergeslowrunduration - マージ サブスクリプションの同期の完了にかかった時間低速またはダイヤルアップ ネットワーク接続経由で (秒単位) がしきい値を超えています。<br /><br /> **32** = mergefastrunspeed 配信率、マージ サブスクリプションの同期中の行は、高速ネットワーク接続経由でのしきい値の割合を 1 秒あたりの行を維持するために失敗しました。<br /><br /> **64** = mergeslowrunspeed 配信率、マージ サブスクリプションの同期中の行が低速またはダイヤルアップ ネットワーク接続経由でのしきい値の割合を 1 秒あたりの行を維持するために失敗しました。|  
|**worst_latency**|**int**|データ変更が、トランザクション パブリケーションのログ リーダー エージェントとディストリビューション エージェントで伝達されるまでの最大待機時間 (秒単位) です。|  
|**best_latency**|**int**|トランザクション パブリケーションのログ リーダー エージェントまたはディストリビューション エージェントによって反映されるデータ変更の最小待機時間 (秒) です。|  
|**average_latency**|**int**|トランザクション パブリケーションのログ リーダー エージェントまたはディストリビューション エージェントによって反映されるデータ変更の平均待機時間 (秒) です。|  
|**last_distsync**|**datetime**|ディストリビューション エージェントが最後に実行された日時です。|  
|**保有期間**|**int**|パブリケーションの保有期間は。|  
|**latencythreshold**|**int**|トランザクション パブリケーションに設定されている待機時間のしきい値です。|  
|**expirationthreshold**|**int**|パブリケーション (マージ パブリケーションの場合) に設定されている有効期限のしきい値です。|  
|**agentnotrunningthreshold**|**int**|エージェントが実行されない最長時間に対して設定されるしきい値です。|  
|**subscriptioncount**|**int**|パブリケーションに対するサブスクリプションの数です。|  
|**runningdistagentcount**|**int**|ディストリビューション エージェントの数がパブリケーションに対して実行しています。|  
|**snapshot_agentname**|**sysname**|パブリケーションのスナップショット エージェント ジョブの名前です。|  
|**logreader_agentname**|**sysname**|トランザクション パブリケーションのログ リーダー エージェント ジョブの名前です。|  
|**qreader_agentname**|**sysname**|キュー更新をサポートするトランザクション パブリケーションのキュー リーダー エージェント ジョブの名前です。|  
|**worst_runspeedPerf**|**int**|マージ パブリケーションの最長同期時間です。|  
|**best_runspeedPerf**|**int**|マージ パブリケーションの最短同期時間です。|  
|**average_runspeedPerf**|**int**|マージ パブリケーションの平均同期時間です。|  
|**retention_period_unit**|**int**|Express を使用する単位は、*保有*です。|  
|**パブリッシャー**|**sysname**|パブリケーションをパブリッシュする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの名前です。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_replmonitorhelppublication**はあらゆる種類のレプリケーションで使用します。  
  
## <a name="permissions"></a>Permissions  
 メンバーにのみ、 **db_owner**または**replmonitor**ディストリビューション データベースの固定データベース ロールが実行できる**sp_replmonitorhelppublication**です。  
  
## <a name="see-also"></a>参照  
 [Programmatically Monitor Replication (プログラムによるレプリケーションの監視)](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
