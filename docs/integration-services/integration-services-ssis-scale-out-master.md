---
title: "Integration Services (SSIS) Scale Out Master | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2e89803f-0471-40ba-b5e4-ddd2c815eecd
caps.latest.revision: 7
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 7
---
# Integration Services (SSIS) Scale Out Master
Scale Out Master では、SSISDB カタログと Scale Out Master サービスを利用して Scale Out システムが管理されます。 

SSISDB カタログでは、Scale Out Worker、パッケージ、実行に関するすべての情報が保存されます。 Scale Out Worker を有効にして、Scale Out でパッケージを実行するインターフェイスを提供します。 詳細については、「[チュートリアル: Integration Services Scale Out をセットアップする](../integration-services/walkthrough-set-up-integration-services-scale-out.md)」、「[Integration Services でパッケージを実行する](../integration-services/run-packages-in-integration-services-ssis-scale-out.md)」を参照してください。

Scale Out Master サービスは、Scale Out Worker との通信を担当する Windows サービスです。 HTTPS を利用して Scale Out Worker とパッケージ実行の状態を交換し、SSISDB のデータを操作します。 

## <a name="scale-out-related-sql-views-and-stored-procdures-in-ssisdb"></a>Scale Out 関連の SQL ビューと SSISDB のストアド プロシージャ

### <a name="views"></a>Views: 
[[catalog].[master_properties]](../integration-services/system-views/catalog-master-properties-ssisdb-database.md), [[catalog].[worker_agents]](../integration-services/system-views/catalog-worker-agents-ssisdb-database.md).
### <a name="stored-procedures"></a>ストアド プロシージャ: 

- Scale Out Worker 管理用:  
 [[catalog].[disable_worker_agent]](../integration-services/system-stored-procedures/catalog-disable-worker-agent-ssisdb-database.md), [[catalog].[enable_worker_agent]](../integration-services/system-stored-procedures/catalog-enable-worker-agent-ssisdb-database.md).
- Scale Out のパッケージ実行用:   
[[catalog].[create_execution]](../integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database.md), [[catalog].[add_execution_worker]](../integration-services/system-stored-procedures/catalog-add-execution-worker-ssisdb-database.md), [[catalog].[start_execution]](../integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database.md).   

## <a name="configure-sql-server-integration-services-scale-out-master-service"></a>SQL Server Integration Services Scale Out Master サービスの構成
Scale Out Master サービスは、\<ドライバー\>:\Program Files\Microsoft SQL Server\140\DTS\Binn\MasterSettings.config ファイルを使用して構成することができます。 構成ファイルの更新後に、サービスを再起動する必要があります。


構成  |Description  |[既定値]  
---------|---------|---------
PortNumber|Scale Out Worker との通信に利用されるネットワーク ポート番号。|8391         
SSLCertThumbprint|Scale Out Worker との通信の保護に利用される SSL 証明書のサムプリント。|Scale Out Master のインストール時に指定される SSL 証明書のサムプリント         
InstanceName|SSISDB カタログが含まれている [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] インスタンスの名前。 MSSQLSERVER が既定の [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] インスタンスの名前です。 |Scale Out Master と共にインストールされる SQL Server インスタンスの名前         
CleanupCompletedJobsIntervalInMs|完了した実行ジョブを消去する間隔 (ミリ秒単位)。|43200000         
DealWithExpiredTasksIntervalInMs|期限切れ実行ジョブを処理する間隔 (ミリ秒単位)。|300000
MasterHeartbeatIntervalInMs|Scale Out Master ハートビートの間隔 (ミリ秒単位)。 これにより、Scale Out Master が SSISDB カタログでのそのオンライン ステータスを更新する間隔が指定されます。|30000        

## <a name="view-scale-out-master-service-log"></a>Scale Out Master サービス ログを表示する
Scale Out Master サービスのログ ファイルは、\<ドライバー\>:\Users\\*[アカウント]*\AppData\Local\SSIS\Cluster\Master フォルダー パスにあります。 

*[アカウント]* フォルダーは、Scale Out Master サービスを実行するアカウントです。 既定のアカウントは SSISScaleOutMaster140 です。