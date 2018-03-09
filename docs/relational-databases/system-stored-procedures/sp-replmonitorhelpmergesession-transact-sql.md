---
title: "sp_replmonitorhelpmergesession (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
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
- sp_replmonitorhelpmergesession_TSQL
- sp_replmonitorhelpmergesession
helpviewer_keywords:
- sp_replmonitorhelpmergesession
ms.assetid: a0400ba8-9609-4901-917e-925e119103a1
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 111c25448a3c9699451b22e1513e217988b475f6
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spreplmonitorhelpmergesession-transact-sql"></a>sp_replmonitorhelpmergesession (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  特定のレプリケーション マージ エージェントの過去のセッションに関する情報を返します。フィルター選択基準に一致するセッションごとに 1 行が返されます。 このストアド プロシージャは、マージ レプリケーションの監視に使用し、ディストリビューター側でディストリビューション データベースについて実行されるか、サブスクライバー側でサブスクリプション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_replmonitorhelpmergesession [ [ @agent_name = ] 'agent_name' ]  
    [ , [ @hours = ] hours ]  
    [ , [ @session_type = ] session_type ]  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @publisher_db = ] 'publisher_db' ]  
    [ , [ @publication = ] 'publication' ]   
```  
  
## <a name="arguments"></a>引数  
 [  **@agent_name**  =] **'***agent_name***'**  
 エージェントの名前を指定します。 *agent_name*は**nvarchar (100)**既定値はありません。  
  
 [  **@hours**  =]*時間*  
 履歴エージェント セッション情報を返す時間の範囲を時間単位で指定します。 *時間*は**int**、次の範囲のいずれかを指定することができます。  
  
|値|Description|  
|-----------|-----------------|  
|< **0**|過去のエージェント実行に関する情報を、最大 100 回分まで返します。|  
|**0** (既定値)|過去のすべてのエージェント実行に関する情報を返します。|  
|> **0**|情報を返しますエージェント実行発生した最後の*時間*時間数。|  
  
 [  **@session_type**  =] *session_type*  
 セッションの終了結果に応じて結果セットにフィルターを適用します。 *session_type*は**int**、これらの値のいずれかを指定できます。  
  
|値|Description|  
|-----------|-----------------|  
|**1** (既定値)|再試行されたか成功したエージェント セッション。|  
|**0**|失敗したエージェント セッション。|  
  
 [  **@publisher**  =] **'***パブリッシャー***'**  
 パブリッシャーの名前です。 *パブリッシャー*は**sysname**、既定値は NULL です。 実行時にこのパラメーターは使用**sp_replmonitorhelpmergesession**サブスクライバーです。  
  
 [  **@publisher_db**  =] **'***publisher_db***'**  
 パブリケーション データベースの名前です。 *publisher_db*は**sysname**、既定値は NULL です。 実行時にこのパラメーターは使用**sp_replmonitorhelpmergesession**サブスクライバーです。  
  
 [  **@publication=** ] **'***パブリケーション***'**  
 パブリケーションの名前です。 *パブリケーション*は**sysname**、既定値は NULL です。 実行時にこのパラメーターは使用**sp_replmonitorhelpmergesession**サブスクライバーです。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**Session_id**|**int**|エージェント ジョブ セッションの ID。|  
|**[状態]**|**int**|エージェント実行状態。<br /><br /> **1**開始を =<br /><br /> **2** = 成功<br /><br /> **3** = 実行中<br /><br /> **4** = アイドル状態<br /><br /> **5** = 再試行<br /><br /> **6** = 失敗|  
|**StartTime**|**datetime**|エージェント ジョブ セッションが開始した時刻。|  
|**EndTime**|**datetime**|エージェント ジョブ セッションが完了した時刻。|  
|**Duration**|**int**|ジョブ セッションの累積時間 (秒単位)。|  
|**UploadedCommands**|**int**|エージェント セッション中にアップロードされたコマンド数。|  
|**DownloadedCommands**|**int**|エージェント セッション中にダウンロードされたコマンド数。|  
|**エラー メッセージ**|**int**|エージェント セッション中に生成されたエラー メッセージ数。|  
|**ErrorID**|**int**|発生したエラーの ID です。|  
|**PercentageDone**|**decimal**|アクティブなセッションで既に配信された総変更数の割合を推定します。|  
|**TimeRemaining**|**int**|アクティブなセッションでの推定残り秒数。|  
|**CurrentPhase**|**int**|アクティブなセッションの現在のフェーズ。次のいずれかになります。<br /><br /> **1**アップロードを =<br /><br /> **2** = ダウンロード|  
|**LastMessage**|**nvarchar (500)**|セッション中にマージ エージェントによってログに記録された最後のメッセージです。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_replmonitorhelpmergesession**はマージ レプリケーションの監視に使用します。  
  
 サブスクライバーで実行されたときに**sp_replmonitorhelpmergesession**過去 5 回のマージ エージェント セッションに関する情報だけを返します。  
  
## <a name="permissions"></a>Permissions  
 メンバーにのみ、 **db_owner**または**replmonitor** 、ディストリビューターのディストリビューション データベースまたはサブスクライバー側でサブスクリプション データベースの固定データベース ロールが実行できる**sp _replmonitorhelpmergesession**です。  
  
## <a name="see-also"></a>参照  
 [Programmatically Monitor Replication (プログラムによるレプリケーションの監視)](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
