---
title: "レプリケーション エージェント プロファイル | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ディストリビューション エージェント, プロファイル"
  - "レプリケーション [SQL Server], エージェントおよびプロファイル"
  - "レプリケーション エージェント プロファイル [SQL Server]"
  - "マージ エージェント, プロファイル"
  - "エージェント [SQL Server レプリケーション], プロファイル"
  - "キュー リーダー エージェント, プロファイル"
  - "プロファイル [SQL Server], レプリケーション エージェント"
  - "スナップショット エージェント, プロファイル"
  - "ログ リーダー エージェント, プロファイル"
ms.assetid: 0e980725-e42f-4283-94cb-d8a6dba5df62
caps.latest.revision: 44
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 44
---
# レプリケーション エージェント プロファイル
  レプリケーションを構成すると、エージェント プロファイルのセットがディストリビューターにインストールされます。 エージェント プロファイルには、エージェントが実行されるたびに使用されるパラメーターのセットが含まれています。スタートアップ処理中に各エージェントはディストリビューターにログインし、各エージェントのプロファイルのパラメーターをクエリします。 Web 同期を使用するマージ サブスクリプションの場合、プロファイルはダウンロードされてサブスクライバーに格納されます。 プロファイルが変更されると、次回マージ エージェントが実行されたときにサブスクライバーのプロファイルが更新されます。 Web 同期の詳細については、「 [Web Synchronization for Merge Replication](../../../relational-databases/replication/web-synchronization-for-merge-replication.md)」を参照してください。  
  
 レプリケーションでは、各エージェント用の既定のプロファイルの他に、ログ リーダー エージェント、ディストリビューション エージェント、およびマージ エージェント用の追加の定義済みプロファイルが利用できます。 提供されているプロファイルに加えて、アプリケーションの要件に合わせてプロファイルを作成することもできます。 エージェント プロファイルを利用すると、そのプロファイルに関連付けられたすべてのエージェントの主要なパラメーターを簡単に変更できます。 たとえば、20 個のスナップショット エージェントがあるし、クエリのタイムアウト値を変更する必要があります (、 **-querytimeout** パラメーター)、スナップショット エージェントが使用するプロファイルを更新することができ、その型のすべてのエージェントは自動的に次回に実行する際の新しい値を使用を開始します。  
  
 1 つのエージェントの別々のインスタンスに対して、別々のプロファイルを設定することもできます。 たとえば、ダイヤルアップ接続を介してパブリッシャーおよびディストリビューターに接続するマージ エージェントで使用して、低速通信リンクに適したパラメーターのセットを使用して、 **低速リンク** プロファイル。  
  
> [!NOTE]  
>  コマンド ラインでエージェント パラメーターの値を指定した場合、その値はエージェント プロファイルの同じパラメーターの設定値より優先されます。  
  
 **エージェント プロファイルを使用および変更するには**  
  
-   [Work with Replication Agent Profiles](../../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)  
  
## スナップショット エージェント プロファイル  
 次の表は、スナップショット エージェントの既定のプロファイルに定義されているパラメーターを示しています。 これらのパラメーターの詳細については、次を参照してください。 [レプリケーション スナップショット エージェント](../../../relational-databases/replication/agents/replication-snapshot-agent.md)します。  
  
||既定値 (default)|  
|-|-------------|  
|**-BcpBatchSize**|100000|  
|**-HistoryVerboseLevel**|2|  
|**-LoginTimeout**|15|  
|**-QueryTimeout**|1800|  
  
## ログ リーダー エージェント プロファイル  
 次の表は、ログ リーダー エージェントのプロファイルに定義されているパラメーターを示しています。 表の各列は名前付きプロファイルを表しています。 これらのパラメーターの詳細については、次を参照してください。 [レプリケーション ログ リーダー エージェント](../../../relational-databases/replication/agents/replication-log-reader-agent.md)します。  
  
||既定値 (default)|詳細履歴|  
|-|-------------|---------------------|  
|**-HistoryVerboseLevel**|1|2|  
|**-LoginTimeout**|15|15|  
|**-LogScanThreshold**|500000|500000|  
|**-PollingInterval**|5|5|  
|**-QueryTimeout**|1800|1800|  
|**-ReadBatchSize**|500|500|  
  
## ディストリビューション エージェント プロファイル  
 次の表は、ディストリビューション エージェントのプロファイルに定義されているパラメーターを示しています。 表の各列は名前付きプロファイルを表しています。 これらのパラメーターの詳細については、次を参照してください。 [レプリケーション ディストリビューション エージェント](../../../relational-databases/replication/agents/replication-distribution-agent.md)します。  
  
||既定値 (default)|詳細履歴|Windows 同期マネージャー|データ一貫性エラー時続行|OLE DB ストリーム用ディストリビューション プロファイル|  
|-|-------------|---------------------|-------------------------------------|-----------------------------------------|----------------------------------------------|  
|**-BcpBatchSize**|100000|100000|1000|100000|2147473647|  
|**-CommitBatchSize**|100|100|100|100|100|  
|**-CommitBatchThreshold**|1000|1000|1000|1000|1000|  
|**-HistoryVerboseLevel**|1|2|1|1|1|  
|**-KeepAliveMessageInterval**|300|300|300|300|300|  
|**-LoginTimeout**|15|15|15|15|15|  
|**-MaxBcpThreads**|1|1|1|1|1|  
|**-MaxDeliveredTransactions**|0|0|0|0|0|  
|**-OledbStreamThreshold**|NULL|NULL|NULL|NULL|32768|  
|**-PacketSize**|NULL|NULL|NULL|NULL|32768|  
|**-PollingInterval**|5|5|5|5|5|  
|**-QueryTimeout**|1800|1800|1800|1800|1800|  
|**-SkipErrors**|NULL|NULL|NULL|**-Skiperrors** 2601:2627:20598|NULL|  
|**-TransactionsPerHistory**|100|100|100|100|100|  
|**-UseOledbStreaming**|NULL|NULL|NULL|NULL|**-UseOledbStreaming**|  
  
## マージ エージェント プロファイル  
 次の表は、マージ エージェントのプロファイルに定義されているパラメーターを示しています。 表の各列は名前付きプロファイルを表しています。 これらのパラメーターの詳細については、次を参照してください。 [レプリケーション マージ エージェント](../../../relational-databases/replication/agents/replication-merge-agent.md)します。  
  
||既定値 (default)|詳細履歴|Windows 同期マネージャー|行数検証|行数とチェックサム検証|低速リンク|高ボリューム サーバー間|  
|-|-------------|---------------------|-------------------------------------|-------------------------|--------------------------------------|---------------|------------------------------------|  
|**-BcpBatchSize**|100000|100000|1000|100000|100000|100000|100000|  
|**-ChangesPerHistory**|100|50|50|100|100|100|1000|  
|**-DestThreads**|2|1|1|1|1|1|4|  
|**-DownloadGenerationsPerBatch**|50|50|50|50|50|1|500|  
|**-DownloadReadChangesPerBatch**|100|100|100|100|100|100|100|  
|**-DownloadWriteChangesPerBatch**|100|100|100|100|100|100|100|  
|**-FastRowCount**|1|1|1|1|1|1|1|  
|**-HistoryVerboseLevel**|2|3|1|1|2|1|2|  
|**-KeepAliveMessageInterval**|300|300|300|300|300|300|300|  
|**-LoginTimeout**|15|15|15|15|15|15|15|  
|**-MaxDownloadChanges**|0|0|0|0|0|0|0|  
|**-MaxUploadChanges**|0|0|0|0|0|0|0|  
|**-MetadataRetentionCleanup**|1|1|1|1|1|1|1|  
|**-NumDeadlockRetries**|5|5|5|5|5|5|5|  
|**-ParallelUploadDownload**|NULL|NULL|NULL|NULL|NULL|NULL|1|  
|**-PollingInterval**|60|60|60|60|60|60|60|  
|**-QueryTimeout**|300|300|300|300|300|300|600|  
|**-QueueSizeMultiplier**|NULL|NULL|NULL|NULL|NULL|NULL|5|  
|**-SrcThreads**|2|2|2|2|2|1|3|  
|**-StartQueueTimeout**|0|0|0|0|0|0|0|  
|**-UploadGenerationsPerBatch**|50|50|50|50|50|1|500|  
|**-UploadReadChangesPerBatch**|100|100|100|100|100|100|100|  
|**-UploadWriteChangesPerBatch**|100|100|100|100|100|100|100|  
|**-Validate**|0|0|0|1|3|0|0|  
|**-ValidateInterval**|60|60|60|60|60|60|60|  
  
## キュー リーダー エージェント プロファイル  
 次の表は、キュー リーダー エージェントの既定のプロファイルに定義されているパラメーターを示しています。 これらのパラメーターの詳細については、次を参照してください。 [レプリケーション キュー リーダー エージェント](../../../relational-databases/replication/agents/replication-queue-reader-agent.md)します。  
  
||既定値 (default)|  
|-|-------------|  
|**-HistoryVerboseLevel**|1|  
|**-LoginTimeout**|15|  
|**-PollingInterval**|5|  
|**-QueryTimeout**|1800|  
  
## 参照  
 [レプリケーション エージェントの管理](../../../relational-databases/replication/agents/replication-agent-administration.md)   
 [表示および変更のレプリケーション エージェント コマンド プロンプト パラメーターと #40 です。SQL Server Management Studio と #41 です。](../../../relational-databases/replication/agents/view and modify replication agent command prompt parameters.md)   
 [レプリケーション エージェント実行可能ファイルの概念](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)  
  
  