---
title: sp_replmonitorhelpsubscription (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replmonitorhelpsubscription_TSQL
- sp_replmonitorhelpsubscription
helpviewer_keywords:
- sp_replmonitorhelpsubscription
ms.assetid: a681b2db-c82d-4624-a10c-396afb0ac42f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 92cd44dcc30a0843409c908cb3cc3a76276519aa
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58528204"
---
# <a name="spreplmonitorhelpsubscription-transact-sql"></a>sp_replmonitorhelpsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  パブリッシャー側の 1 つ以上のパブリケーションに属するサブスクリプションの現在の状態情報を返します。サブスクリプションごとに 1 行のデータが返されます。 レプリケーションの監視に使用される、このストアド プロシージャはディストリビューターのディストリビューション データベースで実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_replmonitorhelpsubscription [ @publisher = ] 'publisher'  
    [ , [ @publisher_db = ] 'publisher_db' ]  
    [ , [ @publication = ] 'publication' ]  
    [ , [ @publication_type = ] publication_type ]   
    [ , [ @mode = ] mode ]  
    [ , [ @topnum = ] topnum ]   
    [ , [ @exclude_anonymous = ] exclude_anonymous ]   
    [ , [ @refreshpolicy = ] refreshpolicy ]  
```  
  
## <a name="arguments"></a>引数  
`[ @publisher = ] 'publisher'` 状態が監視されているパブリッシャーの名前です。 *パブリッシャー*は**sysname**既定値は NULL です。 場合**null**ディストリビューターを使用するすべてのパブリッシャーの情報が返されます。  
  
`[ @publisher_db = ] 'publisher_db'` パブリッシュされたデータベースの名前です。 *publisher_db*は**sysname**既定値は NULL です。 NULL の場合は、パブリッシャー側でパブリッシュされたデータベースのすべての情報が返されます。  
  
`[ @publication = ] 'publication'` 監視されているパブリケーションの名前。 *パブリケーション*は**sysname**既定値は NULL です。  
  
`[ @publication_type = ] publication_type` 場合、パブリケーションの種類。 *publication_type*は**int**、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**0**|トランザクション パブリケーション。|  
|**1**|スナップショット パブリケーション。|  
|**2**|マージ パブリケーションです。|  
|NULL (既定値)|レプリケーションは、パブリケーションの種類を決定しようとします。|  
  
`[ @mode = ] mode` 情報を監視するサブスクリプションを返すときに使用するフィルターのモード。 *モード*は**int**、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**0** (既定値)|すべてのサブスクリプションを返します。|  
|**1**|エラーがあるサブスクリプションだけを返します。|  
|**2**|しきい値超過の警告を生成したサブスクリプションだけを返します。|  
|**3**|エラーがあるか、しきい値超過の警告を生成したサブスクリプションだけを返します。|  
|**4**|最上位 25 のパフォーマンスの低いサブスクリプションを返します。|  
|**5**|最上位 50 の低いサブスクリプションを返します。|  
|**6**|現在同期されているサブスクリプションのみを返します。|  
|**7**|現在同期していないサブスクリプションだけを返します。|  
  
`[ @topnum = ] topnum` 指定された数の返されたデータの上部にあるサブスクリプションのみに結果セットを制限します。 *topnum*は**int**、既定値はありません。  
  
`[ @exclude_anonymous = ] exclude_anonymous` 匿名プル サブスクリプションを結果セットから除外するかどうかです。 *exclude_anonymous*は**ビット**、既定値は**0**です値の**1**匿名サブスクリプションを除外することを意味し、値**0。** 含まれていることを意味します。  
  
`[ @refreshpolicy = ] refreshpolicy` 内部でのみ使用します。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**status**|**int**|パブリケーションに関連付けられているすべてのレプリケーション エージェントの状態を検査し、次の順序で見つかった最も高いステータスを返します。<br /><br /> **6** = に失敗しました<br /><br /> **5** = 再試行<br /><br /> **2** = 停止<br /><br /> **4** = アイドル状態<br /><br /> **3** = 実行中<br /><br /> **1** = 開始|  
|**警告**|**int**|パブリケーションに属しているサブスクリプションによって生成されるしきい値警告の最大値です。次の 1 つ以上の値の論理和になります。<br /><br /> **1** = 有効期限の保有期間のしきい値内で、トランザクション パブリケーションに対するサブスクリプションが同期されていません。<br /><br /> **2** = 待機時間、トランザクション パブリッシャーからサブスクライバーへのデータのレプリケートにかかった時間 (秒)、しきい値を超えています。<br /><br /> **4** = mergeexpiration 保有期間のしきい値内でマージ パブリケーションに対するサブスクリプションが同期されていません。<br /><br /> **8** = mergefastrunduration - マージ サブスクリプションの同期の完了にかかった時間、高速ネットワーク接続経由で秒単位で、しきい値を超えています。<br /><br /> **16** = mergeslowrunduration - マージ サブスクリプションの同期の完了にかかった時間、低速またはダイヤルアップ ネットワーク接続経由で秒単位で、しきい値を超えています。<br /><br /> **32** = mergefastrunspeed - 配信率マージ サブスクリプションの同期中の行が高速ネットワーク接続経由でのしきい値の割合で、1 秒あたりの行を維持するために失敗しました。<br /><br /> **64** mergeslowrunspeed - 配信率 = マージ サブスクリプションの同期中の行が低速またはダイヤルアップ ネットワーク接続経由でのしきい値の割合で、1 秒あたりの行を維持するために失敗しました。|  
|**サブスクライバー**|**sysname**|サブスクライバーの名前です。|  
|**subscriber_db**|**sysname**|サブスクリプションで使用されるデータベースの名前です。|  
|**publisher_db**|**sysname**|パブリケーション データベースの名前です。|  
|**パブリケーション**|**sysname**|パブリケーションの名前です。|  
|**publication_type**|**int**|パブリケーションで、これらの値のいずれかの種類を示します。<br /><br /> **0** = トランザクション パブリケーション<br /><br /> **1** = スナップショット パブリケーション<br /><br /> **2** = マージ パブリケーション|  
|**サブタイプ**|**int**|サブスクリプションの種類です。次のいずれかの値をとります。<br /><br /> **0**プッシュを =<br /><br /> **1** = プル<br /><br /> **2** = 匿名|  
|**latency**|**int**|トランザクション パブリケーションのログ リーダーまたはディストリビューション エージェントによって反映されるデータの変更を秒単位で最大待ち時間。|  
|**latencythreshold**|**int**|これを超える警告が発生したトランザクション パブリケーションの最大待機時間です。|  
|**agentnotrunning**|**int**|エージェントが実行されませんが、時間単位の長さです。|  
|**agentnotrunningthreshold**|**int**|時間単位の時間の長さは、エージェントが、警告が発生するまで実行されません。|  
|**timetoexpiration**|**int**|同期されていない場合は、サブスクリプションにより有効期限が切れるまでの時間の時間の長さです。|  
|**expirationthreshold**|**int**|サブスクリプションでは、警告が発生する有効期限が切れるまでの時間、時間です。|  
|**last_distsync**|**datetime**|ディストリビューション エージェントが最後に実行された日時。|  
|**distribution_agentname**|**sysname**|トランザクション パブリケーションに対するサブスクリプションのディストリビューション エージェント ジョブの名前です。|  
|**mergeagentname**|**sysname**|マージ パブリケーションに対するサブスクリプションのマージ エージェント ジョブの名前です。|  
|**mergesubscriptionfriendlyname**|**sysname**|サブスクリプションに付けられた表示名です。|  
|**mergeagentlocation**|**sysname**|マージ エージェントが実行されるサーバーの名前です。|  
|**mergeconnectiontype**|**int**|マージ パブリケーションに対するサブスクリプションの同期時に使用される接続です。次のいずれかの値をとります。<br /><br /> **1** = ローカル エリア ネットワーク (LAN)<br /><br /> **2** = ダイヤルアップ ネットワーク接続<br /><br /> **3** = web 同期します。|  
|**mergePerformance**|**int**|サブスクリプションに対するすべての同期と比較した前回の同期のパフォーマンスです。前回の同期の配信速度を前回までのすべての配信速度の平均で割った値に基づいて算出されます。|  
|**mergerunspeed**|**float**|サブスクリプションの最後の同期の配信率です。|  
|**mergerunduration**|**int**|サブスクリプションの最後の同期の完了に時間の長さです。|  
|**monitorranking**|**int**|サブスクリプション、結果の並べ替えに使用される順位値が設定されている、これらの値のいずれかを指定できます。<br /><br /> トランザクション パブリケーションの場合 :<br /><br /> **60** = エラー<br /><br /> **56** = 警告: パフォーマンス クリティカル<br /><br /> **52** = 警告: まもなく期限切れまたは期限切れ<br /><br /> **50** = 警告: 初期化されていないサブスクリプション<br /><br /> **40** = コマンドの再試行に失敗しました<br /><br /> **30** = (成功) を実行していません。<br /><br /> **20** = 実行中 (開始、実行中、またはアイドル状態)<br /><br /> マージ パブリケーションの場合。<br /><br /> **60** = エラー<br /><br /> **56** = 警告: パフォーマンス クリティカル<br /><br /> **54** = 警告: 長期マージ<br /><br /> **52** = 警告: 間もなく期限切れになりません。<br /><br /> **50** = 警告: 初期化されていないサブスクリプション<br /><br /> **40** = コマンドの再試行に失敗しました<br /><br /> **30** = 実行中 (開始、実行中、またはアイドル状態)<br /><br /> **20** = (成功) を実行していません。|  
|**distributionagentjobid**|**binary(16)**|トランザクション パブリケーションに対するサブスクリプションのディストリビューション エージェント ジョブの ID。|  
|**mergeagentjobid**|**binary(16)**|マージ パブリケーションに対するサブスクリプションのマージ エージェント ジョブの ID。|  
|**distributionagentid**|**int**|サブスクリプションのディストリビューション エージェント ジョブの ID。|  
|**distributionagentprofileid**|**int**|ディストリビューション エージェントによって使用されるエージェント プロファイルの ID。|  
|**mergeagentid**|**int**|サブスクリプションのマージ エージェント ジョブの ID。|  
|**mergeagentprofileid**|**int**|マージ エージェントで使用されるエージェント プロファイルの ID。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_replmonitorhelpsubscription**はあらゆる種類のレプリケーションで使用します。  
  
 **sp_replmonitorhelpsubscription**の値によって決定されると、サブスクリプションの状態の重大度に基づく結果セットを並べ替えます*monitorranking*します。 たとえば、エラー状態のすべてのサブスクリプションの列は、警告状態のサブスクリプションの列よりも上に並べられます。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **db_owner**または**replmonitor** 、ディストリビューション データベースの固定データベース ロールが実行できる**sp_replmonitorhelpsubscription**します。  
  
## <a name="see-also"></a>参照  
 [Programmatically Monitor Replication (プログラムによるレプリケーションの監視)](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
