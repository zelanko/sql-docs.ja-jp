---
title: sp_replmonitorhelpmergesession (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replmonitorhelpmergesession_TSQL
- sp_replmonitorhelpmergesession
helpviewer_keywords:
- sp_replmonitorhelpmergesession
ms.assetid: a0400ba8-9609-4901-917e-925e119103a1
author: stevestein
ms.author: sstein
ms.openlocfilehash: 95d45e34c5e32e2ace95c2f0e86684aa0e5b575c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67950627"
---
# <a name="spreplmonitorhelpmergesession-transact-sql"></a>sp_replmonitorhelpmergesession (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  フィルター選択条件に一致するセッションごとに返される 1 つの行には、過去の特定のレプリケーション マージ エージェント セッションに関する情報を返します。 マージ レプリケーションの監視に使用される、このストアド プロシージャは、ディストリビューション データベースで、ディストリビューターまたはサブスクライバーのサブスクリプション データベースで実行されます。  
  
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
`[ @agent_name = ] 'agent_name'` エージェントの名前です。 *agent_name*は**nvarchar (100)** 既定値はありません。  
  
`[ @hours = ] hours` 履歴エージェント セッション情報が返される時間の範囲です。 *時間*は**int**、次の範囲のいずれかを指定することができます。  
  
|値|説明|  
|-----------|-----------------|  
|< **0**|最大 100 回に、構成の過去のエージェント実行に関する情報を返します。|  
|**0** (既定値)|過去のすべてのエージェント実行に関する情報を返します。|  
|> **0**|情報を返しますエージェント実行発生した最後の*時間*時間数。|  
  
`[ @session_type = ] session_type` セッションの最終結果に基づく結果セットをフィルター処理します。 *session_type*は**int**、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**1** (既定値)|再試行されたか成功したエージェント セッション。|  
|**0**|失敗したエージェント セッション。|  
  
`[ @publisher = ] 'publisher'` パブリッシャーの名前です。 *パブリッシャー*は**sysname**、既定値は NULL です。 実行するときに、このパラメーターは使用**sp_replmonitorhelpmergesession**サブスクライバー。  
  
`[ @publisher_db = ] 'publisher_db'` パブリケーション データベースの名前です。 *publisher_db*は**sysname**、既定値は NULL です。 実行するときに、このパラメーターは使用**sp_replmonitorhelpmergesession**サブスクライバー。  
  
`[ @publication = ] 'publication'` パブリケーションの名前です。 *パブリケーション*は**sysname**、既定値は NULL です。 実行するときに、このパラメーターは使用**sp_replmonitorhelpmergesession**サブスクライバー。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**Session_id**|**int**|エージェント ジョブ セッションの ID。|  
|**状態**|**int**|エージェントの状態を実行します。<br /><br /> **1** = 開始<br /><br /> **2** = 成功<br /><br /> **3** = 実行中<br /><br /> **4** = アイドル状態<br /><br /> **5** = 再試行<br /><br /> **6** = 失敗|  
|**StartTime**|**datetime**|時間のエージェント ジョブ セッションが開始されました。|  
|**EndTime**|**datetime**|エージェント ジョブ セッションの時間が完了しました。|  
|**Duration**|**int**|累積的な期間 (秒)、このジョブ セッションのです。|  
|**UploadedCommands**|**int**|エージェント セッション中にアップロードされたコマンド数。|  
|**DownloadedCommands**|**int**|エージェント セッション中にダウンロードされたコマンド数。|  
|**エラー メッセージ**|**int**|エージェント セッション中に生成されたエラー メッセージ数。|  
|**ErrorID**|**int**|発生したエラーの ID です。|  
|**PercentageDone**|**decimal**|アクティブなセッションで既に配信された総変更数の割合を推定します。|  
|**TimeRemaining**|**int**|アクティブなセッションの残りの秒の推定数。|  
|**CurrentPhase**|**int**|アクティブなセッションの現在のフェーズ。次のいずれかになります。<br /><br /> **1** = アップロード<br /><br /> **2** = ダウンロード|  
|**LastMessage**|**nvarchar(500)**|セッション中にマージ エージェントによってログに記録された最後のメッセージです。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_replmonitorhelpmergesession**マージ レプリケーションを監視するために使用します。  
  
 サブスクライバーで実行されたときに**sp_replmonitorhelpmergesession**のみ、最後の 5 つのマージ エージェント セッションに関する情報が返されます。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **db_owner**または**replmonitor**ディストリビューターでディストリビューション データベースまたはサブスクライバー側でサブスクリプション データベースの固定データベース ロールが実行できる**sp _replmonitorhelpmergesession**します。  
  
## <a name="see-also"></a>関連項目  
 [Programmatically Monitor Replication (プログラムによるレプリケーションの監視)](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
