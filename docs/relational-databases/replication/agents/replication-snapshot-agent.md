---
title: "レプリケーション スナップショット エージェント | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "スナップショット エージェント, 実行可能ファイル"
  - "エージェント [SQL Server レプリケーション], スナップショット エージェント"
  - "コマンド ライン プロンプト [SQL Server レプリケーション]"
  - "スナップショット エージェント, パラメーター参照"
ms.assetid: 2028ba45-4436-47ed-bf79-7c957766ea04
caps.latest.revision: 41
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 41
---
# レプリケーション スナップショット エージェント
  レプリケーション スナップショット エージェントは、パブリッシュされたテーブルおよびデータベース オブジェクトのスキーマとデータを含むスナップショット ファイルを作成し、これらのファイルをスナップショット フォルダーに格納し、同期ジョブをディストリビューション データベースに記録する実行可能ファイルです。  
  
> [!NOTE]  
>  パラメーターは任意の順序で指定できます。  
  
## 構文  
  
```  
  
snapshot [ -?]   
-Publisher server_name[\instance_name]   
-Publication publication_name   
[-70Subscribers]   
[-BcpBatchSize bcp_batch_size]  
[-DefinitionFile def_path_and_file_name]  
[-Distributor server_name[\instance_name]]  
[-DistributorDeadlockPriority [-1|0|1] ]  
[-DistributorLogin distributor_login]  
[-DistributorPassword distributor_password]  
[-DistributorSecurityMode [0|1] ]  
[-DynamicFilterHostName dynamic_filter_host_name]  
[-DynamicFilterLogin dynamic_filter_login]  
[-DynamicSnapshotLocation dynamic_snapshot_location]   
[-EncryptionLevel [0|1|2]]  
[-FieldDelimiter field_delimiter]  
[-HistoryVerboseLevel [0|1|2|3] ]  
[-HRBcpBlocks number_of_blocks ]  
[-HRBcpBlockSize block_size ]  
[-HRBcpDynamicBlocks ]  
[-KeepAliveMessageInterval keep_alive_interval]  
[-LoginTimeOut login_time_out_seconds]  
[-MaxBcpThreads number_of_threads ]  
[-MaxNetworkOptimization [0|1]]  
[-Output output_path_and_file_name]  
[-OutputVerboseLevel [0|1|2] ]  
[-PacketSize packet_size]  
[-ProfileName profile_name]  
[-PublisherDB publisher_database]  
[-PublisherDeadlockPriority [-1|0|1] ]  
[-PublisherFailoverPartner server_name[\instance_name] ]  
[-PublisherLogin publisher_login]  
[-PublisherPassword publisher_password]   
[-PublisherSecurityMode [0|1] ]  
[-QueryTimeOut query_time_out_seconds]  
[-ReplicationType [1|2] ]  
[-RowDelimiter row_delimiter]  
[-StartQueueTimeout start_queue_timeout_seconds]  
[-UsePerArticleContentsView use_per_article_contents_view]  
```  
  
## 引数  
 **-?**  
 使用できるすべてのパラメーターを表示します。  
  
 **-パブリッシャー**  *server_name*[**\\***instance_name*]    
 パブリッシャーの名前です。 既定のインスタンスのサーバー名を指定 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] そのサーバーにします。 指定 *server_name***\\***instance_name* の名前付きインスタンスの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] そのサーバーにします。  
  
 **-パブリケーション** *パブリケーション*  
 パブリケーションの名前です。 このパラメーターは、新規または再初期化されたサブスクリプションのスナップショットを常に利用できるようにパブリケーションを設定している場合にのみ有効です。  
  
 **-70Subscribers**  
 すべてのサブスクライバーが実行されている場合に使用する必要があります [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] バージョン 7.0 です。  
  
 **-BcpBatchSize** *bcp*_ *バッチ*\_ *サイズ*  
 一括コピー操作によって送られる行の数です。 **bcp in** 操作を実行する場合、バッチ サイズは 1 つのトランザクションとしてサーバーに送る行数です。ディストリビューション エージェントが **bcp** 実行状況メッセージをログに記録する前に、これらの行数を送る必要があります。 実行するときに、 **bcp out** 操作、1000 個単位の固定バッチ サイズを使用します。 値 0 は、メッセージをログに記録しないことを示します。  
  
 **-Definitionfile** *def_path_and_file_name*  
 エージェント定義ファイルのパスです。 エージェント定義ファイルには、エージェントのコマンド ライン引数が含まれます。 ファイルの内容は実行可能ファイルとして解析されます。 二重引用符 (") を使用して、任意の文字を含む引数値を指定します。  
  
 **-ディストリビューター** *server_name*[**\\***instance_name*]  
 ディストリビューターの名前です。 指定 *server_name* の既定のインスタンスの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] そのサーバーにします。 指定 *server_name***\\***instance_name* の名前付きインスタンスの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] そのサーバーにします。  
  
 **-DistributorDeadlockPriority** [**-1**|**0**|**1**]  
 デッドロックが発生した場合のディストリビューターへのスナップショット エージェント接続の優先度です。 このパラメーターは、スナップショットの生成中にスナップショット エージェントとユーザー アプリケーション間で発生する可能性のあるデッドロックを解決するために指定します。  
  
|DistributorDeadlockPriority の値|説明|  
|---------------------------------------|-----------------|  
|**-1**|ディストリビューター側でデッドロックが発生した場合、スナップショット エージェント以外のアプリケーションが優先されます。|  
|**0** (既定)|優先度は割り当てられません。|  
|**1**|ディストリビューター側でデッドロックが発生した場合、スナップショット エージェントが優先されます。|  
  
 **-Distributorlogin** *distributor_login*  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証を使用してディストリビューターに接続するときに使用されるログインです。  
  
 **-Distributorpassword** *distributor_password 用途*  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証を使用してディストリビューターに接続するときに使用されるパスワードです。 」を参照してください。  
  
 **-Distributorsecuritymode** [ **0**| **1**]  
 ディストリビューターのセキュリティ モードを指定します。 値 **0** 示す [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証モード (既定)、および値の **1** Windows 認証モードを示します。  
  
 **-Dynamicfilterhostname** *dynamic_filter_host_name*  
 値の設定に使用される [HOST_NAME & #40 です。Transact SQL と #41;](../../../t-sql/functions/host-name-transact-sql.md) フィルターを適用するときに動的スナップショットが作成されます。 たとえば、サブセット フィルター句 `rep_id = HOST_NAME()` アーティクルについては、指定されたを設定して、 **DynamicFilterHostName** プロパティを"FBJones"をマージ エージェントを呼び出す前にある行だけ"FBJones"を持つ、 **rep_id** 列がレプリケートされます。  
  
 **-Dynamicfilterlogin** *dynamic_filter_login*  
 値の設定に使用される [SUSER_SNAME & #40 です。Transact SQL と #41;](../../../t-sql/functions/suser-sname-transact-sql.md)フィルターを適用するときに動的スナップショットが作成されます。 たとえば、サブセット フィルター句 `user_id = SUSER_SNAME()` アーティクルについては、指定されたを設定して、 **DynamicFilterLogin** プロパティを呼び出す前に"rsmith"、 **実行** のメソッド、 **SQLSnapshot** オブジェクトを"rsmith"行のみ、 **user_id** 列は、スナップショットに含まれます。  
  
 **-Dynamicsnapshotlocation** *dynamic_snapshot_location*  
 動的スナップショットの生成先の場所です。  
  
 **-Encryptionlevel** [ **0** | **1** | **2** ]  
 スナップショット エージェントが接続時に使用する SSL (Secure Sockets Layer) 暗号化レベルです。  
  
|EncryptionLevel の値|説明|  
|---------------------------|-----------------|  
|**0**|SSL は使用されません。|  
|**1**|SSL は使用されますが、信頼できる発行者によって SSL サーバー証明が署名されているかどうかを検証しません。|  
|**2**|SSL が使用され、証明書の確認が行われます。|  
  
 詳細については、次を参照してください。 [セキュリティの概要と #40 です。レプリケーションと #41;](../../../relational-databases/replication/security/security-overview-replication.md)します。  
  
 **-FieldDelimiter** *field_delimiter*  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 一括コピーで扱うデータ ファイルのフィールドの末尾を示す 1 文字または文字列です。 既定値は \n\<x$3>\n です。  
  
 **-Historyverboselevel** [ **1**| **2**| **3**]  
 スナップショット操作中にログに記録する履歴の量を指定します。 履歴を選択してログのパフォーマンスへの影響を最小限に抑えることができます **1**します。  
  
|HistoryVerboseLevel の値|説明|  
|-------------------------------|-----------------|  
|**0**|進行状況メッセージがコンソールまたは出力ファイルに書き込まれます。 履歴レコードは、ディストリビューション データベースのログに記録されません。|  
|**1**|同じ状態 (startup、progress、success など) を示している以前の履歴メッセージを常に更新します。 前回の記録に同じ状態がない場合は、新しい記録を挿入します。|  
|**2** (既定値)|アイドル状態や長時間実行を示すメッセージでない場合、新しい履歴レコードを挿入します。アイドル状態などを示すメッセージの場合には、以前のレコードを更新します。|  
|**3**|アイドル状態を示すメッセージの場合以外は、常に新しいレコードを挿入します。|  
  
 **-HRBcpBlocks** *number_of_blocks*  
 数は、 **bcp** ライターとリーダー スレッド間でキューに入れられているデータ ブロックです。 既定値は 50 です。 **HRBcpBlocks** は Oracle パブリケーションでのみ使用します。  
  
> [!NOTE]  
>  このパラメーターを使用して、パフォーマンスのチューニングの **bcp** 、Oracle パブリッシャーからのパフォーマンス。  
  
 -**HRBcpBlockSize***block_size*  
 それぞれのサイズをキロバイト (KB) では、 **bcp** データ ブロックです。 既定値は 64 KB です。 **HRBcpBlocks** は Oracle パブリケーションでのみ使用します。  
  
> [!NOTE]  
>  このパラメーターを使用して、パフォーマンスのチューニングの **bcp** 、Oracle パブリッシャーからのパフォーマンス。  
  
 **-HRBcpDynamicBlocks**  
 かどうかの各サイズ **bcp** データ ブロックが動的に拡張することができます。 **HRBcpBlocks** は Oracle パブリケーションでのみ使用します。  
  
> [!NOTE]  
>  このパラメーターを使用して、パフォーマンスのチューニングの **bcp** 、Oracle パブリッシャーからのパフォーマンス。  
  
 **-KeepAliveMessageInterval** *keep_alive_interval*  
 "Waiting for backend message"ログオンする前に、スナップショット エージェントが待機する秒単位の時間が、 [MSsnapshot_history](../../../relational-databases/system-tables/mssnapshot-history-transact-sql.md) テーブルです。 既定値は 300 秒です。  
  
 **-Logintimeout** *login_time_out_seconds*  
 ログインがタイムアウトになるまでの秒数です。 既定値は **15** 秒です。  
  
 **-Maxbcpthreads** *number_of_threads*  
 並列実行できる一括コピーの操作数を指定します。 同時に存在するスレッドと ODBC 接続の最大数は、 **MaxBcpThreads** の値と、ディストリビューション データベースの同期トランザクションに示されている一括コピー要求の数の小さい方の値になります。 **MaxBcpThreads** より大きい値を持つ必要があります **0** ハード コーディングされた上限がないです。 既定値は **1**します。  
  
 \- **MaxNetworkOptimization** [ **0**| **1**]  
 無関係な削除がサブスクライバーに送られたかどうかを示します。 無関係な削除とは、サブスクライバーのパーティションに属さない行に対する DELETE コマンドがサブスクライバーに送られたことを表します。 無関係な削除はデータの整合性や収束には影響しませんが、不要なネットワーク トラフィックを生じます。 既定値の **MaxNetworkOptimization** は **0**です。 設定 **MaxNetworkOptimization** に **1** 無関係な削除される可能性を最小限に抑え、それによってネットワーク トラフィックが減少し、最大限に高めるネットワーク最適化します。 このパラメーターに設定 **1** もメタデータの記憶域を増やすし、パフォーマンスが複数レベルの結合フィルターや複雑なサブセット フィルターが存在する場合は、パブリッシャー側で低下することができます。 慎重にレプリケーション トポロジを評価し、設定する **MaxNetworkOptimization** に **1** 無関係な削除からのネットワーク トラフィックが許容範囲を超える場合にのみです。  
  
> [!NOTE]  
>  このパラメーターに設定 **1** のみマージ パブリケーションの同期最適化オプション設定されている場合便利ですが **true** (、 **@keep_partition_changes** のパラメーター [sp_addmergepublication & #40 です。Transact-SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md))。  
  
 **-出力** *output_path_and_file_name*  
 エージェントの出力ファイルのパスです。 ファイル名が指定されていない場合、出力はコンソールに送られます。 指定された名前のファイルが存在する場合、出力はそのファイルに追加されます。  
  
 **-Outputverboselevel** [ **0**| **1**| **2**]  
 出力を詳細表示にするかどうかを指定します。  
  
|OutputVerboseLevel の値|説明|  
|------------------------------|-----------------|  
|**0**|エラー メッセージのみが記録されます。|  
|**1** (既定値)|すべての進行状況レポート メッセージが出力されます (既定)。|  
|**2**|すべてのエラー メッセージと進行状況レポート メッセージが出力されます。これはデバッグの際に役立ちます。|  
  
 **-PacketSize** *packet_size*  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] への接続中にスナップショット エージェントが使用するパケット サイズ (バイト) です。 既定値は 8,192 バイトです。  
  
> [!NOTE]  
>  パフォーマンスの向上が明確でない限り、パケット サイズは変更しないでください。 多くのアプリケーションでは、既定のパケット サイズが最適です。  
  
 **-ProfileName** *profile_name*  
 エージェント パラメーターに使用するエージェント プロファイルを指定します。 **ProfileName** が NULL の場合、このエージェント プロファイルは無効になります。 **ProfileName** を指定しない場合、エージェントの種類に応じた既定のプロファイルが使われます。 詳細については、次を参照してください。 [レプリケーション エージェント プロファイル](../../../relational-databases/replication/agents/replication-agent-profiles.md)します。  
  
 **-Publisherdb** *publisher_database*  
 パブリケーション データベースの名前です。 *このパラメーターは、Oracle パブリッシャーに対してはサポートされません*します。  
  
 **-PublisherDeadlockPriority** [**-1**|**0**|**1**]  
 デッドロックが発生した場合のパブリッシャーへのスナップショット エージェント接続の優先度です。 このパラメーターは、スナップショットの生成中にスナップショット エージェントとユーザー アプリケーション間で発生する可能性のあるデッドロックを解決するために指定します。  
  
|PublisherDeadlockPriority の値|説明|  
|-------------------------------------|-----------------|  
|**-1**|パブリッシャー側でデッドロックが発生した場合、スナップショット エージェント以外のアプリケーションが優先されます。|  
|**0** (既定)|優先度は割り当てられません。|  
|**1**|パブリッシャー側でデッドロックが発生した場合、スナップショット エージェントが優先されます。|  
  
 **-PublisherFailoverPartner** *server_name*[**\\***instance_name*]  
 パブリケーション データベースとのデータベース ミラーリング セッションに参加する、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] フェールオーバー パートナー インスタンスを指定します。 詳細については、次を参照してください。 [データベース ミラーリングとレプリケーション/#40 です。SQL Server と #41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md)します。  
  
 **-Publisherlogin** *publisher_login*  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証を使用してパブリッシャーに接続するときに使用されるログインです。  
  
 **-PublisherPassword**  *publisher_password*  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証を使用してパブリッシャーに接続するときに使用されるパスワードです。 」を参照してください。  
  
 **-Publishersecuritymode** [ **0**| **1**]  
 パブリッシャーのセキュリティ モードを指定します。 値 **0** 示す [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証 (既定値) と値の **1** Windows 認証モードを示します。  
  
 **-Querytimeout** *query_time_out_seconds*  
 クエリがタイムアウトになるまでの秒数です。 既定値は 1800 秒です。  
  
 **-Replicationtype** [ **1**| **2**]  
 レプリケーションの種類を指定します。 値 **1** トランザクション レプリケーション、およびの値を示す **2** マージ レプリケーションを示します。  
  
 **-[Rowdelimiter]** *row_delimiter*  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 一括コピーで扱うデータ ファイルの各行の末尾を示す 1 文字または文字列です。 既定値は \n\<,@g>\n です。  
  
 **-StartQueueTimeout** *start_queue_timeout_seconds*  
 スナップショット エージェントが実行されている同時実行スナップショット プロセスの数がによって設定された制限を待機する秒数の最大数は、 **@max_concurrent_dynamic_snapshots** プロパティの [sp_addmergepublication & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md)します。 最大秒数に達したときにスナップショット エージェントがまだ待機している場合、スナップショット エージェントは待機を終了します。 値が 0 の場合は、このエージェントが無期限に待機することを意味しますが、取り消すこともできます。  
  
 \- **UsePerArticleContentsView** *use_per_article_contents_view*  
 このパラメーターは推奨されません。旧バージョンとの互換性のためにサポートされています。  
  
## 解説  
  
> [!IMPORTANT]  
>  ドメイン ユーザー アカウント (既定値) ではなくローカル システム アカウントで実行するように [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェントをインストールした場合、サービスはローカル コンピューターにだけアクセスできます。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェント下で実行するスナップショット エージェントで、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] へのログイン時に Windows 認証モードを使用するように構成すると、スナップショット エージェントは異常終了します。 既定の設定は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証です。  
  
 スナップショット エージェントを起動する実行 **snapshot.exe** コマンド プロンプトからです。 詳細については、次を参照してください。 [レプリケーション エージェント実行可能ファイル](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)します。  
  
## 参照  
 [レプリケーション エージェントの管理](../../../relational-databases/replication/agents/replication-agent-administration.md)  
  
  