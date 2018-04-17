---
title: sp_change_agent_parameter (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_change_agent_parameter_TSQL
- sp_change_agent_parameter
helpviewer_keywords:
- sp_change_agent_parameter
ms.assetid: f1fbecc7-e64f-405c-8067-6b38c1f3c0a0
caps.latest.revision: 28
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fd6da586c282cae6a963bec1ae0c76a1609ce4b5
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="spchangeagentparameter-transact-sql"></a>sp_change_agent_parameter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  格納されているレプリケーション エージェント プロファイルのパラメーターの変更、 [MSagent_parameters](../../relational-databases/system-tables/msagent-parameters-transact-sql.md)システム テーブル。 このストアド プロシージャは、エージェントが動作しているディストリビューター側で任意のデータベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_change_agent_parameter [ @profile_id= ] profile_id, [ @parameter_name= ] 'parameter_name', [ @parameter_value= ] 'parameter_value'  
```  
  
## <a name="arguments"></a>引数  
 [  **@profile_id=**] *profile_id*、  
 プロファイルの ID を指定します。 *profile_id*は**int**、既定値はありません。  
  
 [  **@parameter_name=**] **'***parameter_name***'**  
 パラメーターの名前を指定します。 *parameter_name*は**sysname**、既定値はありません。 システム プロファイルの場合、変更できるパラメーターはエージェントの種類によって異なります。 このエージェントの種類を確認する*profile_id*を表す、検索、 *profile_id*内の列、 **Msagent_profiles**テーブル、およびに注意してください、 *agent_type*値。  
  
> [!NOTE]  
>  パラメーターがサポートされている場合、指定された*agent_type*、エージェント プロファイルで定義されていませんが、エラーが返されます。 実行する必要があります、エージェントのプロファイルにパラメーターを追加する[sp_add_agent_parameter](../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md)です。  
  
 スナップショット エージェント (*agent_type*=**1**)、プロファイルで定義されている場合、は、次のプロパティを変更できます。  
  
-   **70Subscribers**  
  
-   **BcpBatchSize**  
  
-   **HistoryVerboseLevel**  
  
-   **LoginTimeout**  
  
-   **MaxBcpThreads**  
  
-   **MaxNetworkOptimization**  
  
-   **出力**  
  
-   **OutputVerboseLevel**  
  
-   **PacketSize**  
  
-   **QueryTimeout**  
  
-   **StartQueueTimeout**  
  
-   **UsePerArticleContentsView**  
  
 ログ リーダー エージェント (*agent_type*=**2**)、プロファイルで定義されている場合、は、次のプロパティを変更できます。  
  
-   **HistoryVerboseLevel**  
  
-   **LoginTimeout**  
  
-   **MessageInterval**  
  
-   **出力**  
  
-   **OutputVerboseLevel**  
  
-   **PacketSize**  
  
-   **PollingInterval**  
  
-   **QueryTimeout**  
  
-   **ReadBatchSize**  
  
-   **ReadBatchThreshold**  
  
 ディストリビューション エージェント (*agent_type*=**3**)、プロファイルで定義されている場合、は、次のプロパティを変更できます。  
  
-   **BcpBatchSize**  
  
-   **CommitBatchSize**  
  
-   **CommitBatchThreshold**  
  
-   **FileTransferType**  
  
-   **HistoryVerboseLevel**  
  
-   **KeepAliveMessageInterval**  
  
-   **LoginTimeout**  
  
-   **MaxBcpThreads**  
  
-   **MaxDeliveredTransactions**  
  
-   **MessageInterval**  
  
-   **出力**  
  
-   **OutputVerboseLevel**  
  
-   **PacketSize**  
  
-   **PollingInterval**  
  
-   **QueryTimeout**  
  
-   **QuotedIdentifier**  
  
-   **SkipErrors**  
  
-   **TransactionsPerHistory**  
  
 マージ エージェント (*agent_type*=**4**)、プロファイルで定義されている場合、は、次のプロパティを変更できます。  
  
-   **AltSnapshotFolder**  
  
-   **BcpBatchSize**  
  
-   **ChangesPerHistory**  
  
-   **DestThreads**  
  
-   **DownloadGenerationsPerBatch**  
  
-   **DownloadReadChangesPerBatch**  
  
-   **DownloadWriteChangesPerBatch**  
  
-   **DynamicSnapshotLocation**  
  
-   **ExchangeType**  
  
-   **FastRowCount**  
  
-   **FileTransferType**  
  
-   **GenerationChangeThreshold**  
  
-   **HistoryVerboseLevel**  
  
-   **InputMessageFile**  
  
-   **InteractiveResolution**  
  
-   **InterruptOnMessagePattern**  
  
-   **KeepAliveMessageInterval**  
  
-   **LoginTimeout**  
  
-   **MaxBcpThreads**  
  
-   **MaxDownloadChanges**  
  
-   **MaxUploadChanges**  
  
-   **MetadataRetentionCleanup**  
  
-   **NumDeadlockRetries**  
  
-   **出力**  
  
-   **OutputMessageFile**  
  
-   **OutputVerboseLevel**  
  
-   **PacketSize**  
  
-   **ParallelUploadDownload**  
  
-   **PauseOnMessagePattern**  
  
-   **PauseTime**  
  
-   **PollingInterval**  
  
-   **ProcessMessagesAtPublisher**  
  
-   **ProcessMessagesAtSubscriber**  
  
-   **QueryTimeout**  
  
-   **QueueSizeMultiplier**  
  
-   **SrcThreads**  
  
-   **StartQueueTimeout**  
  
-   **SyncToAlternate**  
  
-   **UploadGenerationsPerBatch**  
  
-   **UploadReadChangesPerBatch**  
  
-   **UploadWriteChangesPerBatch**  
  
-   **UseInprocLoader**  
  
-   **[検証]**  
  
-   **ValidateInterval**  
  
 キュー リーダー エージェント (*agent_type*=**9**)、プロファイルで定義されている場合、は、次のプロパティを変更できます。  
  
-   **HistoryVerboseLevel**  
  
-   **LoginTimeout**  
  
-   **出力**  
  
-   **OutputVerboseLevel**  
  
-   **PollingInterval**  
  
-   **QueryTimeout**  
  
-   **ResolverState**  
  
-   **SQLQueueMode**  
  
 どのようなパラメーターは、指定されたプロファイルに対して定義されているを参照する実行**sp_help_agent_profile**とに注意してください、 *profile_name*に関連付けられている、 *profile_id*です。 適切な*profile_id*、次回の実行**sp_help_agent_parameters**が使用している*profile_id*プロファイルに関連付けられているパラメーターを確認します。 パラメーターは、実行することによって、プロファイルに追加することができます[sp_add_agent_parameter](../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md)です。  
  
 [  **@parameter_value=**] **'***パラメーター***'**  
 パラメーターの新しい値です。 *パラメーターおよび*は**nvarchar (255)**、既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_change_agent_parameter**はあらゆる種類のレプリケーションで使用します。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_change_agent_parameter**です。  
  
## <a name="see-also"></a>参照  
 [レプリケーション エージェント プロファイル](../../relational-databases/replication/agents/replication-agent-profiles.md)   
 [Replication Distribution Agent](../../relational-databases/replication/agents/replication-distribution-agent.md)   
 [レプリケーション ログ リーダー エージェント](../../relational-databases/replication/agents/replication-log-reader-agent.md)   
 [レプリケーション マージ エージェント](../../relational-databases/replication/agents/replication-merge-agent.md)   
 [レプリケーション キュー リーダー エージェント](../../relational-databases/replication/agents/replication-queue-reader-agent.md)   
 [Replication Snapshot Agent](../../relational-databases/replication/agents/replication-snapshot-agent.md)   
 [sp_add_agent_parameter &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md)   
 [sp_drop_agent_parameter &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-drop-agent-parameter-transact-sql.md)   
 [sp_help_agent_parameter &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-agent-parameter-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
