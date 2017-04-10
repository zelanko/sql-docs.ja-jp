---
title: "レプリケーション マージ エージェント | Microsoft Docs"
ms.custom: ""
ms.date: "08/24/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "マージ エージェント, 実行可能ファイル"
  - "マージ エージェント, パラメーター参照"
  - "エージェント [SQL Server レプリケーション], マージ エージェント"
  - "コマンド ライン プロンプト [SQL Server レプリケーション]"
ms.assetid: fe1e7f60-b0c8-45e9-a5e8-4fedfa73d7ea
caps.latest.revision: 64
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 64
---
# レプリケーション マージ エージェント
  レプリケーション マージ エージェントは、データベース テーブルに保持された初期スナップショットをサブスクライバーに適用するユーティリティ実行可能ファイルです。 さらに、初期スナップショットの作成後にパブリッシャーで発生したデータの増分変更をマージし、ユーザーが構成したルールに従って、またはユーザーが作成したカスタム競合回避モジュールを使用して、競合を調整します。  
  
> [!NOTE]  
>  パラメーターは任意の順序で指定できます。 省略可能なパラメーターを省略する場合、ローカル コンピューターであらかじめ定義されているレジストリ設定の値が使用されます。  
  
## 構文  
  
```  
  
replmerg [-?]   
-Publisher server_name[\instance_name]  
-PublisherDB publisher_database  
-Publication publication  
-Subscriber server_name[\instance_name]  
-SubscriberDB subscriber_database  
[-AltSnapshotFolder alt_snapshot_folder_path]  
[-Continuous]  
[-DefinitionFile def_path_and_file_name]  
[-DestThreads number_of_destination_threads]  
[-Distributor server_name[\instance_name]]  
[-DistributorLogin distributor_login]  
[-DistributorPassword distributor_password]  
[-DistributorSecurityMode [0|1]]  
[-DownloadGenerationsPerBatch download_generations_per_batch]  
[-DownloadReadChangesPerBatch download_read_changes_per_batch]  
[-DownloadWriteChangesPerBatch download_write_changes_per_batch]  
[-DynamicSnapshotLocation dynamic_snapshot_location]  
[-EncryptionLevel [0|1|2]]  
[-ExchangeType [1|2|3]]  
[-FastRowCount [0|1]]  
[-FileTransferType [0|1]]  
[-ForceConvergenceLevel [0|1|2 (Publisher|Subscriber|Both)]]  
[-FtpAddress ftp_address]  
[-FtpPassword ftp_password]  
[-FtpPort ftp_port]  
[-FtpUserNameftp_user_name]  
[-HistoryVerboseLevel [0|1|2|3]]  
[-Hostname host_name]  
[-InteractiveResolution [0|1]]  
[-InternetLogin internet_login]  
[-InternetPassword internet_password]  
[-InternetProxyLogin internet_proxy_login]  
[–InternetProxyPassword internet_proxy_password]  
[-InternetProxyServer internet_proxy_server]  
[-InternetSecurityMode [0|1]]  
[-InternetTimeout internet_timeout]  
[-InternetURL internet_url]  
[-KeepAliveMessageInterval keep_alive_message_interval_seconds]  
[-LoginTimeOut login_time_out_seconds]  
[-MakeGenerationInterval make_generation_interval_seconds]  
[-MaxBcpThreads number_of_threads]  
[-MaxDownloadChanges number_of_download_changes]  
[-MaxUploadChanges number_of_upload_changes]  
[-MetadataRetentionCleanup [0|1]]  
[-Output]  
[-OutputVerboseLevel [0|1|2]]  
[-ParallelUploadDownload [0|1]]  
[-PacketSize packet_size]   
[-PollingInterval polling_interval]  
[-ProfileName profile_name]  
[-PublisherFailoverPartner server_name[\instance_name] ]  
[-PublisherLogin publisher_login]  
[-PublisherPassword publisher_password]  
[-PublisherSecurityMode [0|1]]  
[-QueryTimeOut query_time_out_seconds]  
[-SrcThreads number_of_source_threads]  
[-StartQueueTimeout start_queue_timeout_seconds]  
[-SubscriberConflictClean [0|1]]  
[-SubscriberDatabasePath subscriber_path]  
[-SubscriberDBAddOption [0|1|2|3]]  
[-SubscriberLogin subscriber_login]  
[-SubscriberPassword subscriber_password   
[-SubscriberSecurityMode [0|1]]  
[-SubscriberType [0|1|2|3|4|5|6|7|8|9]]  
[-SubscriptionType [0|1|2]]  
[-SyncToAlternate [0|1]  
[-UploadGenerationsPerBatch upload_generations_per_batch]  
[-UploadReadChangesPerBatch upload_read_changes_per_batch]  
[-UploadWriteChangesPerBatch upload_write_changes_per_batch]  
[-UseInprocLoader]  
[-Validate [0|1|2|3]]  
[-ValidateInterval validate_interval]  
```  
  
## 引数  
 **-?**  
 使用できるすべてのパラメーターを表示します。  
  
 **-パブリッシャー** *server_name*[**\\***instance_name*]  
 パブリッシャーの名前です。 指定 *server_name* の既定のインスタンスの [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] そのサーバーにします。 指定 *server_name***\\***instance_name* の名前付きインスタンスの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] そのサーバーにします。  
  
 **-Publisherdb** *publisher_database*  
 パブリッシャー データベースの名前です。  
  
 **-パブリケーション** *パブリケーション*  
 パブリケーションの名前です。 このパラメーターは、新規または再初期化されたサブスクリプションのスナップショットを常に利用できるようにパブリケーションを設定している場合にのみ有効です。  
  
 **-サブスクライバー** *server_name*[**\\***instance_name*]  
 サブスクライバーの名前です。 指定 *server_name* の既定のインスタンスの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] そのサーバーにします。 指定 *server_name***\\***instance_name* の名前付きインスタンスの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] そのサーバーにします。  
  
 **-SubscriberDB** *subscriber_database*  
 サブスクライバー データベースの名前です。  
  
 **-Altsnapshotfolder** *alt_snapshot_folder_path*  
 サブスクリプションの初期スナップショットが含まれるフォルダーへのパスです。  
  
 **-Continuous**  
 エージェントがレプリケートされたトランザクションの呼び出しを継続的に試みるかどうかを指定します。 このパラメーターを指定する場合、保留されているトランザクションがなくても、エージェントはポーリング間隔でレプリケートされたトランザクションをソースから呼び出します。  
  
 **-DestThreads** *number_of_destination_threads*  
 マージ エージェントが変更の対象で変更を適用するために使用する対象スレッドの数を指定します。 変更の対象は、アップロード実行時はパブリッシャーであり、ダウンロード実行時はサブスクライバーです。 既定値は 4 です。  
  
 **-Definitionfile** *def_path_and_file_name*  
 エージェント定義ファイルのパスです。 エージェント定義ファイルには、エージェントのコマンド プロンプト引数が含まれます。 ファイルの内容は実行可能ファイルとして解析されます。 二重引用符 (") を使用して、任意の文字を含む引数値を指定します。  
  
 **-ディストリビューター** *server_name*[**\\***instance_name*]  
 ディストリビューターの名前です。 指定 *server_name* の既定のインスタンスの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] そのサーバーにします。 指定 *server_name***\\***instance_name* の名前付きインスタンスの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] そのサーバーにします。 ディストリビューター (プッシュ) ディストリビューションの場合、既定の名前は、ローカル コンピューターの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の既定のインスタンス名です。  
  
 **-Distributorlogin** *distributor_login*  
 ディストリビューターのログイン名です。  
  
 **-Distributorpassword** *distributor_password 用途*  
 ディストリビューターのパスワードです。  
  
 **-Distributorsecuritymode** [ **0**| **1**]  
 ディストリビューターのセキュリティ モードを指定します。 値 **0** 示す [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証モード (既定)、および値の **1** Windows 認証モードを示します。  
  
 **-DownloadGenerationsPerBatch** *download_generations_per_batch*  
 パブリッシャーからサブスクライバーに変更をダウンロードする間に、1 つのバッチで処理される生成結果の数です。 生成結果は、アーティクルごとに変更の論理グループとして定義されます。 信頼性の高い通信リンクの既定値は 100 です。 信頼性の低い通信リンクの既定値は 10 です。  
  
 **-DownloadReadChangesPerBatch** *download_read_changes_per_batch*  
 パブリッシャーからサブスクライバーに変更をダウンロードする間に、1 つのバッチで読み取られる変更の数です。 既定値は、100 です。  
  
 **-DownloadWriteChangesPerBatch** *download_write_changes_per_batch*  
 パブリッシャーからサブスクライバーに変更をダウンロードする間に、1 つのバッチで適用される変更の数です。 既定値は、100 です。  
  
 **-Dynamicsnapshotlocation** *dynamic_snapshot_location*  
 パブリケーションでパラメーター化された行フィルターを使用する場合のフィルター選択されたデータ スナップショット ファイルの位置です。  
  
 **-Encryptionlevel** [ **0** | **1** | **2** ]  
 接続時にマージ エージェントで使用される SSL (Secure Sockets Layer) 暗号化のレベルです。  
  
|EncryptionLevel の値|説明|  
|---------------------------|-----------------|  
|**0**|SSL は使用されません。|  
|**1**|SSL は使用されますが、信頼できる発行者によって SSL サーバー証明が署名されているかどうかを検証しません。|  
|**2**|SSL が使用され、証明書の確認が行われます。|  
  
 詳細については、次を参照してください。 [セキュリティの概要と #40 です。レプリケーションと #41;](../../../relational-databases/replication/security/security-overview-replication.md)します。  
  
 **-Exchangetype** [ **1**| **2**| **3**]  
 > [!WARNING]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../../includes/ssnotedepfuturedontuse-md.md)] 使用してアップロードを制限、 **@subscriber_upload_options** の **sp_addmergearticle** 代わりにします。  
  
 同期中のデータ交換の種類を指定します。次のいずれかを指定できます。  
  
|ExchangeType の値|説明|  
|------------------------|-----------------|  
|**1**|エージェントは、サブスクライバーからパブリッシャーにデータ変更をアップロードします。|  
|**2**|エージェントは、パブリッシャーからサブスクライバーにデータ変更をダウンロードします。|  
|**3** (既定値)|エージェントは最初にサブスクライバーからパブリッシャーにデータ変更をアップロードし、次にパブリッシャーからサブスクライバーにデータ変更をダウンロードします。 このオプションは、Web 同期で使用する必要があります。|  
  
 ダウンロード専用のアーティクルによって、パブリケーション内の個別のアーティクルの同期の動作を制御して、パフォーマンスを向上させることができます。 詳細については、次を参照してください。 [Download-Only アーティクルを使用したマージ レプリケーション パフォーマンスの最適化](../../../relational-databases/replication/merge/optimize-merge-replication-performance-with-download-only-articles.md)します。  
  
 使用して場合 **ExchangeType** アップロードを分離し、個別のセッションにマージ レプリケーションのフェーズをダウンロードするにはマージ エージェントを実行する必要があります **ExchangeType** 最初が 1 に設定し、値 2 を持つマージ エージェントを再度実行します。 どちらのパラメーターを使用してもマージ エージェントの実行が失敗する場合、メタデータが削除され、サブスクリプションの再初期化 (アップロードは行わない) を要求される可能性があります。  
  
 **-FastRowCount** [**0**|**1**]  
 行数の検証に使用する行数計算方法の種類を指定します。 値 **1** (既定値) が高速の方法を示します。 値 **0** 完全行数計算法を示します。  
  
 **-FileTransferType** [**0**|**1**]  
 ファイル転送の種類を指定します。 値 **0** UNC (汎用名前付け規則)、およびの値を示す **1** FTP (ファイル転送プロトコル) を示します。  
  
 **-Forceconvergencelevel** [**0**|**1**|**2** ( **パブリッシャー**| **サブスクライバー**| **両方**)]  
 マージ エージェントが使用する収束のレベルを指定します。次のいずれかを指定できます。  
  
|ForceConvergenceLevel の値|説明|  
|---------------------------------|-----------------|  
|**0** (既定値)|既定値です。 追加の収束なしで標準のマージを実行します。|  
|**1**|すべての生成結果の収束を強制します。|  
|**2**|すべての生成結果の収束を強制し、破損した系列を修正します。 この値を指定する場合は、系列を修正する場所 (パブリッシャー、サブスクライバー、またはパブリッシャーとサブスクライバーの両方) を指定します。|  
  
 **-FtpAddress** *ftp_address*  
 ディストリビューター用の FTP サービスのネットワーク アドレスです。 指定しない場合、 **ディストリビューター** を使用します。  
  
 **-FtpPassword** *ftp_password*  
 FTP サービスに接続するときに使用するユーザー パスワードです。  
  
 **-FtpPort** *ftp_port*  
 ディストリビューター用の FTP サービスのポート番号です。 このパラメーターを指定しない場合、FTP サービスの既定のポート番号 (21) が使用されます。  
  
 **-FtpUserName** *ftp_user_name*  
 FTP サービスに接続するときに使用するユーザー名です。 この引数を指定しない場合は、匿名が使用されます。  
  
 **-Historyverboselevel** [**1**|**2**|**3**]  
 マージ操作中にログに記録する履歴の量を指定します。 履歴を選択してログのパフォーマンスへの影響を最小限に抑えることができます **1**します。  
  
|HistoryVerboseLevel の値|説明|  
|-------------------------------|-----------------|  
|**0**|エージェントの状態の最終メッセージ、最終のセッションの詳細、およびすべてのエラーをログに記録します。|  
|**1**|各セッションの状態における増分セッションの詳細をログに記録します。エージェントの状態の最終メッセージ、最終のセッションの詳細、およびすべてのエラーに加えて、進行状況が含まれます。|  
|**2**|既定値です。 各セッションの状態における増分セッションの詳細、およびアーティクル レベルのセッションの詳細をログに記録します。エージェントの状態の最終メッセージ、最終のセッションの詳細、およびすべてのエラーに加えて、進行状況が含まれます。 エージェントの状態のメッセージもログに記録されます。|  
|**3**|同じ **-historyverboselevel** = **2**, 点が複数のエージェント進行状況メッセージが記録されます。|  
  
 **-Hostname** *host_name*  
 ローカル コンピューターのネットワーク名です。 既定値は、ローカル コンピューターの名前になります。  
  
 **-Interactiveresolution** [**0**|**1**]  
 同期中に競合が発生した場合に、インタラクティブ競合回避を使用するかどうかを指定します。 既定値は **0**, 、インタラクティブな競合解決が使用されないことを示します。  
  
 **-Internetlogin** *internet_login*  
 認証を必要とする [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] レプリケーション リスナー ISAPI DLL への接続時に使用されるログイン名を指定します。  
  
 **-InternetPassword** *internet_password*  
 認証を必要とする [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] レプリケーション リスナー ISAPI DLL への接続時に使用されるパスワードを指定します。  
  
 **-InternetProxyLogin**  *internet_proxy_login*  
 指定するプロキシ サーバーに接続するときに使用するログイン名がで定義されている *internet_proxy_server*, 、認証が必要です。  
  
 **– InternetProxyPassword**  *internet_proxy_password*  
 定義されているプロキシ サーバーへの接続時に使用するパスワードを指定 *internet_proxy_server*, 、認証が必要です。  
  
 **-Internetproxyserver**  *internet_proxy_server*  
 指定された HTTP リソースにアクセスするときに使用するプロキシ サーバーを指定 *internet_url*します。  
  
 **-InternetSecurityMode** [**0**|**1**]  
 Web 同期時の Web サーバーとの接続に使用される IIS セキュリティ モードを指定します。 値 **0** 基本認証を示し、値 **1** Windows 統合認証 (既定値) を示します。  
  
 **-InternetTimeout** *internet_timeout*  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] レプリケーション リスナー ISAPI DLL がタイムアウトになるまでの秒数です。  
  
 **-InternetURL** *internet_url*  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] レプリケーション リスナー ISAPI DLL への接続に使用される URL を指定します。 このプロパティの指定は必須です。  
  
 **-KeepAliveMessageInterval** *keep_alive_message_interval_seconds*  
 既存の接続がサーバーからの応答を待機しているかどうかを、履歴スレッドがチェックするまでの秒数です。 長時間実行のときに、照合エージェントがマージ エージェントに SUSPECT のマークを付けないようにするには、この値を小さくします。 既定値は **300** 秒です。  
  
 **-Logintimeout** *login_time_out_seconds*  
 ログインがタイムアウトになるまでの秒数です。 既定値は **15** 秒です。  
  
 **-MakeGenerationInterval** *make_generation_interval_seconds*  
 クライアントにダウンロードする生成結果 (変更のバッチ) を作成する間隔 (秒) です。 既定値は **1** 2 番目です。  
  
 Makegeneration は、パブリッシャーの変更をサブスクライバーにダウンロードするように準備するプロセスです。また、ダウンロード中にパフォーマンスのボトルネックになる場合があります。 Makegeneration プロセスがで指定した間隔で既に実行されたかどうかは **- MakeGenerationInterval**, 、現在の同期セッションのプロセスがスキップされました。 これは、同期の同時実行に役立つ場合があります。特に、サブスクライバーが変更をダウンロードしない場合に役立ちます。  
  
 **-Maxbcpthreads** *number_of_threads*  
 並列実行できる一括コピーの操作数を指定します。 スレッドと同時に存在する ODBC 接続の最大数が小さい方の **MaxBcpThreads** または数一括コピー システム テーブルに表示される要求 **sysmergeschemachange** 、パブリケーション データベースです。 **MaxBcpThreads** 0 より大きい値を持つ必要があり、ハード コーディングされた上限がありません。 既定値は **1**します。  
  
 **-MaxDownloadChanges** *number_of_download_changes*  
 パブリッシャーからサブスクライバーにダウンロードする必要のある変更済みの行の最大数を指定します。 ダウンロードする行数が、指定した最大数より多くなる場合があります。完全な生成結果が処理されること、および並列の対象スレッドが実行されて最初のパスでそれぞれ 100 以上の変更が処理されることが原因です。 既定では、ダウンロードの準備が整っている変更がすべて送信されます。  
  
 **-MaxUploadChanges** *number_of_upload_changes*  
 サブスクライバーからパブリッシャーにアップロードする必要のある変更済みの行の最大数を指定します。 アップロードする行数が、指定した最大数より多くなる場合があります。完全な生成結果が処理されること、および並列の対象スレッドが実行されて最初のパスでそれぞれ 100 以上の変更が処理されることが原因です。 既定では、アップロードの準備が整っている変更がすべて送信されます。  
  
 **-Metadataretentioncleanup** [**0**|**1**]  
 メタデータが削除を指定 [MSmerge_genhistory](../../../relational-databases/system-tables/msmerge-genhistory-transact-sql.md), 、[MSmerge_contents](../../../relational-databases/system-tables/msmerge-contents-transact-sql.md), 、[MSmerge_tombstone](../../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md), 、[MSmerge_past_partition_mappings](../../../relational-databases/system-tables/msmerge-past-partition-mappings-transact-sql.md), 、および [MSmerge_current_partition_mappings](../../../relational-databases/system-tables/msmerge-current-partition-mappings.md) パブリケーション保有期間に基づいています。 既定値は **1**, 、そのクリーンアップを行うことを示します。 値 **0** がクリーンアップされが自動的に行われないことを示します。  
  
 **-出力** *output_path_and_file_name*  
 エージェントの出力ファイルのパスです。 ファイル名が指定されていない場合、出力はコンソールに送られます。 指定された名前のファイルが存在する場合、出力はそのファイルに追加されます。  
  
 **-Outputverboselevel** [**0**|**1**|**2**]  
 出力を詳細表示にするかどうかを指定します。 詳細レベルが **0**の場合、エラー メッセージだけが出力されます。 詳細レベルが場合 **1**, 、すべての進行状況の報告メッセージが出力されます。 詳細レベルが場合 **2** (既定)、すべてのエラー メッセージと進行状況レポート メッセージが出力されます。 これはデバッグに役立ちます。  
  
 **-Paralleluploaddownload** [**0**|**1**]  
 パブリッシャーにアップロードする変更とサブスクライバーにダウンロードする変更をマージ エージェントが並列で処理するかどうかを指定します。帯域幅が広いネットワークを使用している大容量環境で有用です。 場合 **ParallelUploadDownload** は **1**, 、並列処理が有効にします。  
  
 **-PacketSize**  
 パケット サイズをバイト単位で指定します。 既定値は 4096 (バイト) です。  
  
 **-PollingInterval** *polling_interval*  
 パブリッシャーまたはサブスクライバーへのデータ変更をクエリする間隔 (秒数) を示します。 既定値は 60 秒です。  
  
 **-ProfileName** *profile_name*  
 エージェント パラメーターに使用するエージェント プロファイルを指定します。 **ProfileName** が NULL の場合、このエージェント プロファイルは無効になります。 **ProfileName** を指定しない場合、エージェントの種類に応じた既定のプロファイルが使われます。 詳細については、次を参照してください。 [レプリケーション エージェント プロファイル](../../../relational-databases/replication/agents/replication-agent-profiles.md)します。  
  
 **-PublisherFailoverPartner** *server_name*[**\\***instance_name*]  
 パブリケーション データベースとのデータベース ミラーリング セッションに参加する、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] フェールオーバー パートナー インスタンスを指定します。 詳細については、次を参照してください。 [データベース ミラーリングとレプリケーション/#40 です。SQL Server と #41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md)します。  
  
 **-Publisherlogin** *publisher_login*  
 パブリッシャーのログイン名です。 場合 **PublisherSecurityMode** は **0** (の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証)、このパラメーターを指定する必要があります。  
  
 **-PublisherPassword** *publisher_password*  
 パブリッシャーのパスワードです。 場合 **PublisherSecurityMode** は **0** (の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証)、このパラメーターを指定する必要があります。  
  
 **-Publishersecuritymode** [**0**|**1**]  
 パブリッシャーのセキュリティ モードを指定します。 値 **0** 示す [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証 (既定値) と値の **1** Windows 認証モードを示します。  
  
 **-Querytimeout** *query_time_out_seconds*  
 クエリがタイムアウトになるまでの秒数です。 既定では 300 秒です。 マージ エージェントの値にも使用 **QueryTimeout** この値が 1800年を超えるパーティション スナップショットの生成を待機する期間を特定します。  
  
 **-SrcThreads** *number_of_source_threads*  
 マージ エージェントが変更元から変更を列挙するために使用するソース スレッドの数を指定します。 変更元は、アップロード実行時はサブスクライバーであり、ダウンロード実行時はパブリッシャーです。 既定値は **3**します。  
  
 **-StartQueueTimeout** *start_queue_timeout_seconds*  
 実行中の同時実行マージ プロセス数が設定された制限にある場合、マージ エージェントが待機する秒数の最大数は、 **@max_concurrent_merge** の **sp_addmergepublication**します。 最長秒数に達したときにマージ エージェントが待機中である場合、マージ エージェントは終了します。 値 0 は、エージェントが無制限に待機することを示します。ただし、キャンセルできます。  
  
 **-SubscriberDatabasePath** *subscriber_database_path*  
 Jet データベース (.mdb ファイル) へのパスは、場合 **SubscriberType** は **2** (Jet データベースせず、ODBC データ ソース名 (DSN) への接続を許可する)。  
  
 **-Subscriberdbaddoption** [**0**| **1**| **2**| **3**]  
 既存のサブスクライバー データベースがあるかどうかを指定します。  
  
|SubscriberDBAddOption の値|説明|  
|---------------------------------|-----------------|  
|**0**|既存のデータベースを使用します (既定値)。|  
|**1**|新しい空のサブスクライバー データベースを作成します。|  
|**2**|新しいデータベースを作成して、指定されたファイルにアタッチします。|  
|**3**|新しいデータベースを作成し、データベースをアタッチして、ファイルに存在する可能性のあるすべてのサブスクリプションを有効にします。|  
  
> [!NOTE]  
>  値を使用すると **2** と **3**, で、サブスクライバーのデータベースのパスを指定する必要があります、 **SubscriberDatabasePath** オプション。  
  
 **-SubscriberLogin** *subscriber_login*  
 サブスクライバーのログイン名です。 場合 **SubscriberSecurityMode** は **0** (の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証)、このパラメーターを指定する必要があります。  
  
 **-SubscriberPassword** *subscriber_password*  
 サブスクライバーのパスワードです。 場合 **SubscriberSecurityMode** は **0** (の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証)、このパラメーターを指定する必要があります。  
  
 **-Subscribersecuritymode** [ **0**| **1**]  
 サブスクライバーのセキュリティ モードを指定します。 値 **0** 示す [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証 (既定値) と値の **1** Windows 認証モードを示します。  
  
 **-Subscriberconflictclean** [ **0**| **1**]  
 かどうかは競合テーブルはクリーンアップ、サブスクライバーの同期処理中に値が **1** サブスクライバーで競合テーブルがクリーンアップであることを示します。 このパラメーターは、競合のログ記録が集中管理されていないパブリケーションに対するサブスクリプションにのみ使用されます。  
  
 **-SubscriberType** [ **0**| **1**| **3**| **4**| **5**| **6**| **7**| **8**]  
 マージ エージェントによって使用されるサブスクライバー接続の種類を指定します。 既定の値だけ **0** はこのパラメーターはサポートされています。  
  
 **-Subscriptiontype**[ **0**| **1**| **2**]  
 ディストリビューションのサブスクリプションの種類を指定します。 値 **0** プッシュ サブスクリプション (既定値) の値を示す **1** プル サブスクリプションを示し、値 **2** 匿名サブスクリプションを示します。  
  
 **-Synctoalternate** [ **0 | 1**]  
 マージ エージェントがサブスクリプションと代替パブリッシャー間での同期を実行しているかどうかを指定します。 値 **1** 代替パブリッシャーであることを示します。 既定値は **0**です。  
  
 **-UploadGenerationsPerBatch** *upload_generations_per_batch*  
 サブスクライバーからパブリッシャーに変更をアップロードする間に、1 つのバッチで処理される生成結果の数です。 生成結果は、アーティクルごとに変更の論理グループとして定義されます。 信頼性の高い通信リンクの既定値は **100**します。 信頼性の低い通信リンクの既定値は **1**します。  
  
 **-UploadReadChangesPerBatch** *upload_read_changes_per_batch*  
 サブスクライバーからパブリッシャーに変更をアップロードする間に、1 つのバッチで読み取られる変更の数です。 既定値は **100**します。  
  
 **-UploadWriteChangesPerBatch** *upload_write_changes_per_batch*  
 サブスクライバーからパブリッシャーに変更をアップロードする間に、1 つのバッチで適用される変更の数です。 既定値は **100**します。  
  
 **-UseInprocLoader**  
 マージ エージェントでスナップショット ファイルをサブスクライバーに適用するときに BULK INSERT コマンドを使用することによって、初期スナップショットのパフォーマンスが向上します。 このパラメーターは XML データ型との互換性がないため推奨されません。 XML データをレプリケートしない場合にのみ、このパラメーターを使用できます。 このパラメーターは、キャラクター モードのスナップショットでは使用できません。 このパラメーターを使用する場合は、サブスクライバー側の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービス アカウントに、スナップショットの .bcp データ ファイルが格納されたディレクトリの読み取り権限が必要です。 このパラメーターを使用しない場合、エージェントによって読み込まれた ODBC ドライバーがファイルから読み取るので、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービス アカウントのセキュリティ コンテキストは使用されません。  
  
 **-Validate** [**0**|**1**|**2**|**3**]  
 マージ セッションの最後に検証を行うかどうかを指定し、行う場合は検証の種類も指定します。 値 **3** 推奨される値です。  
  
|Validate の値|説明|  
|--------------------|-----------------|  
|**0** (既定値)|検証なし。|  
|**1**|行数のみの検証。|  
|**2**|行数とチェックサムの検証。|  
|**3**|行数とバイナリ チェックサムの検証。|  
  
> [!NOTE]  
>  バイナリ チェックサムまたはチェックサムを使用した検証では、データ型がサブスクライバー側とパブリッシャー側とで異なる場合には、誤ってエラーを報告することがあります。 詳細については、「データ検証の考慮事項」セクションを参照してください [レプリケート データの検証](../../../relational-databases/replication/validate-replicated-data.md)します。  
  
 **-ValidateInterval** *validate_interval*  
 サブスクリプションが継続モードで検証される間隔 (分) です。 既定値は **60** 分です。  
  
## 解説  
  
> [!IMPORTANT]  
>  ドメイン ユーザー アカウント (既定値) ではなくローカル システム アカウントで実行するように [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェントがインストールされている場合、サービスがアクセスできるのはローカル コンピューターのみです。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェントの下で実行するマージ エージェントで、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] へのログイン時に Windows 認証モードが使用されるように構成すると、マージ エージェントは失敗します。 既定の設定は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証です。  
  
 マージ エージェントを開始するには、実行 **replmerg.exe** コマンド プロンプトからです。 詳細については、次を参照してください。 [レプリケーション エージェント実行可能ファイル](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)します。  
  
 現在のセッションのマージ エージェントの履歴は、連続モードでの実行中には削除されません。 エージェントが長時間実行されると、マージ履歴テーブルに多数のエントリが発生し、パフォーマンスに影響する可能性があります。 この問題を解決するには、スケジュールされたモードに切り替えるか、引き続き連続モードを使用する場合は、定期的にマージ エージェントを再起動するための専用のジョブを作成するか、履歴の詳細レベルを下げて行数を減らして、パフォーマンスへの影響を軽減してください。  
  
## 参照  
 [レプリケーション エージェントの管理](../../../relational-databases/replication/agents/replication-agent-administration.md)  
  
  