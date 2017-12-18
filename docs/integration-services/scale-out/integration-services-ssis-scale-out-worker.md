---
title: SQL Server Integration Services (SSIS) Scale Out Worker | Microsoft Docs
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: scale-out
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cb36dc89fbe8fbedc96e426d00f6982213d7d4c9
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="integration-services-ssis-scale-out-worker"></a>Integration Services (SSIS) Scale Out Worker

Scale Out Worker は、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion_md](../../includes/ssisnoversion-md.md)] Scale Out Worker サービスを実行して、Scale Out Master から実行タスクをプルし、ISServerExec.exe を使用してローカルでパッケージを実行します。

## <a name="configure-sql-server-integration-services-scale-out-worker-service"></a>SQL Server Integration Services Scale Out Worker サービスの構成
Scale Out Worker サービスは、 \<ドライバー\>:\Program Files\Microsoft SQL Server\140\DTS\Binn\WorkerSettings.config ファイルを使用して構成することができます。 構成ファイルの更新後に、サービスを再起動する必要があります。

構成  |Description  |既定値  
---------|---------|---------
DisplayName|Scale Out Worker の表示名。 **[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 2017 では使用しません。**|コンピューター名         
Description|Scale Out Worker の説明。 **[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 2017 では使用しません。**|空         
MasterEndpoint|Scale Out Master に接続するエンドポイント。|Scale Out Worker のインストール時に設定されるエンドポイント         
MasterHttpsCertThumbprint|Scale Out Master の認証に使用されるクライアント SSL 証明書のサムプリント|Scale Out Worker のインストール時に指定されるクライアント証明書のサムプリント。          
WorkerHttpsCertThumbprint|Scale Out Master の認証に使用される Scale Out Master 証明書のサムプリント。|Scale Out Worker のインストール時に自動的に作成され、インストールされる証明書のサムプリント          
StoreLocation|ワーカー証明書ストアの場所。|LocalMachine       
StoreName|ワーカー証明書ストアの名前。|My         
AgentHeartbeatInterval|Scale Out Worker ハートビートの間隔。|00:01:00         
TaskHeartbeatInterval|Scale Out Worker でのタスク状態のレポート間隔。|00:00:10         
HeartbeatErrorTollerance|最後の正常なタスク ハートビート以降、この時間が経過すると、ハートビートのエラー応答が受信された場合にタスクは終了します。|00:10:00      
TaskRequestMaxCPU|Scale Out Worker のタスク要求時の CPU の上限。 **[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 2017 では使用しません。**|70.0         
TaskRequestMinMemory|Scale Out Worker のタスク要求時のメモリの下限 (MB 単位)。 **[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 2017 では使用しません。**|100.0         
MaxTaskCount|Scale Out Worker が保持できるタスクの最大数。|10         
LeaseInternval|Scale Out Worker によって保持されているタスクのリース間隔。|00:01:00         
TasksRootFolder|タスク ログのフォルダー。 値が空の場合は、 \<ドライバー\>:\Users\\*[アカウント]*\AppData\Local\SSIS\Cluster\Tasks フォルダー パスが使用されます。 [アカウント] は、Scale Out Worker サービスを実行するアカウントです。 既定のアカウントは SSISScaleOutWorker140 です。|空         
TaskLogLevel|Scale Out Worker のタスク ログ レベル。 (Verbose 0x01、Information 0x02、Warning 0x04、Error 0x08、Progress 0x10、CriticalError 0x20、Audit 0x40)|126 (Information,Warning,Error,Progress,CriticalError,Audit)     
TaskLogSegment|タスク ログ ファイルの期間。|00:00:00         
TaskLogEnabled|タスク ログが有効かどうかを示します。|true         
ExecutionLogCacheFolder|パッケージ実行ログのキャッシュに使用するフォルダー。 値が空の場合は、 \<ドライバー\>:\Users\\*[アカウント]*\AppData\Local\SSIS\Cluster\Agent\ELogCache フォルダー パスが使用されます。 [アカウント] は、Scale Out Worker サービスを実行するアカウントです。 既定のアカウントは SSISScaleOutWorker140 です。|空         
ExecutionLogMaxBufferLogCount|メモリ内の 1 つの実行ログ バッファーの、キャッシュされる実行ログの最大数。|10000        
ExecutionLogMaxInMemoryBufferCount|実行ログ用のメモリ内の実行ログ バッファーの最大数。|10         
ExecutionLogRetryCount|実行ログに失敗した場合の再試行回数。|3
ExecutionLogRetryTimeout|実行ログに失敗した場合の再試行タイムアウト。 ExecutionLogRetryTimeout に達した場合、ExecutionLogRetryCount は無視されます。|7.00:00:00 (7 日)        
AgentId|Scale Out Worker の Worker Agent ID|自動生成        

## <a name="view-scale-out-worker-log"></a>Scale Out Worker ログの表示
Scale Out Worker サービスのログ ファイルは、\<ドライバー\>:\Users\\<*アカウント*>\AppData\Local\SSIS\ScaleOut\Agent フォルダー パスにあります。

各タスクのログの場所は、TasksRootFolder によって WorkerSettings.config ファイルで構成されます。 指定されていない場合、ログは \<ドライバー\>:\Users\\<*アカウント*>\AppData\Local\SSIS\ScaleOut\Tasks フォルダー パスにあります。 

<*アカウント*> は、Scale Out Worker サービスを実行するアカウントです。 既定のアカウントは SSISScaleOutWorker140 です。
