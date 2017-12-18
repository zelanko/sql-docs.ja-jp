---
title: "SQL Server Integration Services (SSIS) Scale Out のトラブルシューティング | Microsoft Docs"
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
ms.openlocfilehash: 56d61bc6ba76514ba2291243002a7423ec8e265c
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="troubleshooting-scale-out"></a>Scale Out のトラブルシューティング

SSIS Scale Out には、SSISDB、Scale Out Master サービス、および Scale Out Worker サービス間の通信が含まれます。 この通信は、構成の誤り、アクセス許可がない、およびその他の理由により切断される場合があります。 このドキュメントは、Scale Out 構成のトラブルシューティングを支援します。

発生した現象を調査するため、問題が解決されるまで、以下の手順を 1 つずつ実行してください。

### <a name="symptoms"></a>**現象** 
Scale Out Master が SSISDB に接続できない。 

Scale Out Manager にマスター プロパティが表示できない。

[SSISDB].[catalog].[master_properties] にマスター プロパティが入力されない。

### <a name="solution"></a>**解決方法**
手順 1: Scale Out が有効になっているかどうかを確認します。

SSMS のオブジェクト エクスプローラーで **[SSISDB]** ノードを右クリックして、**[Scale Out 機能が有効です]** を確認します。

![Scale Out が有効になっているか](media\isenabled.PNG)

プロパティの値が False の場合、ストアド プロシージャ [SSISDB].[catalog].[enable_scaleout] を呼び出すことによって、Scale Out を有効にします。

手順 2: Scale Out Master 構成ファイルで指定された SQL Server 名が正しいかどうかを確認し、Scale Out Master サービスを再起動します。

### <a name="symptoms"></a>**現象** 
Scale Out Worker が Scale Out Master に接続できない

Scale Out Worker が、Scale Out Manager に追加した後に表示されなくなる

Scale Out Worker が、[SSISDB].[catalog].[worker_agents] に表示されない

Scale Out Worker のオフライン中に、Scale Out Worker サービスが実行されている

### <a name="solutions"></a>**ソリューション** 
\<ドライブ\>:\Users\\*[account running worker service]*\AppData\Local\SSIS\Cluster\Agent にある Scale Out Worker サービスのログでエラー メッセージを確認します。

**ケース** 

System.ServiceModel.EndpointNotFoundException: メッセージを受信できる https://*[MachineName]:[Port]*/ClusterManagement/ でリッスンしているエンドポイントがありませんでした。

手順 1: Scale Out Master のサービス構成ファイルで指定されたポート番号が正しいかどうかを確認し、Scale Out Master サービスを再起動します。 

手順 2: Scale Out Worker サービスの構成で指定されたマスター エンドポイントが正しいかどうかを確認し、Scale Out Worker サービスを再起動します。

手順 3: Scale Out Master ノードでファイアウォール ポートが開いているかどうかを確認します。

手順 4: Scale Out Master ノードと Scale Out Worker ノード間のその他の接続の問題を解決します。

**ケース**

System.ServiceModel.Security.SecurityNegotiationException: 機関 '*[Machine Name]:[Port]*' との SSL/TLS のセキュリティで保護されているチャネルに対する信頼関係を確立できませんでした。 ---> System.Net.WebException: 基になる接続が閉じられました: SSL/TLS のセキュリティで保護されているチャネルに対する信頼関係を確立できませんでした。 ---> System.Security.Authentication.AuthenticationException: 検証プロシージャによると、リモート証明書は無効です。

手順 1: Scale Out Master 証明書を Scale Out Worker ノード上のローカル コンピューターのルート証明書ストアにインストールして (まだインストールしていない場合)、Scale Out Worker サービスを再起動します。

手順 2: マスター エンドポイント内のホスト名が Scale Out Master 証明書の CN に含まれているかどうかを確認します。 含まれていない場合は、Scale Out Worker の構成ファイル内のマスター エンドポイントをリセットし、Scale Out Worker サービスを再起動します。 

> [!Note]
> DNS の設定が原因でマスター エンドポイントのホスト名を変更できない場合は、Scale Out Master 証明書を変更する必要があります。 「[Deal with certificates in SSIS Scale Out](deal-with-certificates-in-ssis-scale-out.md)」 (SSIS Scale Out における証明書の処理) を参照してください。

手順 3: Scale Out Worker の構成で指定されたマスター サムプリントが Scale Out Worker 証明書のサムプリントと一致するかどうかを確認します。 

**ケース**

System.ServiceModel.Security.SecurityNegotiationException: オーソリティ '*[Machine Name]:[Port]*' と、セキュリティで保護された SSL/TLS のチャネルを確立できませんでした。 ---> System.Net.WebException: 要求は中止されました: SSL/TLS のセキュリティで保護されているチャネルを作成できませんでした。

手順 1: 次のコマンドを使用して、Scale Out Worker サービスを実行するアカウントが、Scale Out Worker 証明書へのアクセス権を持っているかどうかを確認します。

```dos
winhttpcertcfg.exe -l -c LOCAL_MACHINE\MY -s {CN of the worker certificate}
```

アカウントにアクセス権がない場合は、次のコマンドでアクセス権を付与して、Scale Out Worker サービスを再起動します。

```dos
winhttpcertcfg.exe -g -c LOCAL_MACHINE\My -s {CN of the worker certificate} -a {the account running Scale Out Worker service}
```

**ケース**

System.ServiceModel.Security.MessageSecurityException: この HTTP 要求は、クライアントの認証方式 'Anonymous' で許可されませんでした。 ---> System.Net.WebException: リモート サーバーがエラーを返しました: 403 許可されていません。

手順 1: Scale Out Worker 証明書を Scale Out Master ノード上のローカル コンピューターのルート証明書ストアにインストールして (まだインストールしていない場合)、Scale Out Worker サービスを再起動します。

手順 2: Scale Out Master ノード上のローカル コンピューターのルート証明書ストア内の不要な証明書をクリーンアップします。

手順 3: Scale Out Master ノードに次のレジストリ エントリを追加することで、TLS/SSL のハンドシェイク プロセス中に信頼されたルート証明機関の一覧を送信しないように、Schannel を構成します。

HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL

値の名前: SendTrustedIssuerList 

値の型: REG_DWORD 

値のデータ: 0 (False)

**ケース**

System.ServiceModel.CommunicationException: https://*[Machine Name]:[Port]*/ClusterManagement/ に対する HTTP 要求の発行中にエラーが発生しました。 これは、HTTPS ケースの HTTP.SYS でサーバー証明書が正しく構成されていないという事実が原因と考えられます。 またはクライアントとサーバーの間でセキュリティ バインドが整合していないことも原因になり得ます。 

手順 1: Scale Out Master 証明書が、次のコマンドを使用してマスター ノード上のマスター エンドポイントのポートに正しくバインドされているかどうかを確認します。 表示される証明書ハッシュが Scale Out Master 証明書のサムプリントと一致しているかどうかを確認します。

```dos
netsh http show sslcert ipport=0.0.0.0:{Master port}
```

バインドが正しくない場合は、次のコマンドを使ってリセットし、Scale Out Worker サービスを再起動します。

```dos
netsh http delete sslcert ipport=0.0.0.0:{Master port}
netsh http add sslcert ipport=0.0.0.0:{Master port} certhash={Master certificate thumbprint} certstorename=Root appid={random guid}
```

### <a name="symptoms"></a>**現象**
Scale Out Manager で Scale Out Worker を Scale Out Master に接続したときに、"マシン上で証明書ストアを開けません" のエラー メッセージが出て検証が失敗した。

### <a name="solution"></a>**解決方法**

手順 1: 管理者として Scale Out Manager を実行します。 SSMS で開く場合は、SSMS を管理者として実行する必要があります。

手順 2: マシンでリモート レジストリ サービスを起動します (実行されていない場合)。

### <a name="symptoms"></a>**現象**
Scale Out で実行が開始されない。

### <a name="solution"></a>**解決方法**

[SSISDB].[catalog].[worker_agents] でパッケージを実行するために選択したマシンの状態を確認してください。 少なくとも 1 つのワーカーがオンラインで有効になっている必要があります。

### <a name="symptoms"></a>**現象** 
パッケージは正常に実行されているが、メッセージがログに記録されない。

### <a name="solution"></a>**解決方法**

SSISDB をホストしている SQL Server により SQL Server 認証が許可されているかどうかを確認します。

> [!Note]  
> Scale Out ログのアカウントを変更した場合は、「[Scale Out ログのアカウントの変更](change-logdb-account.md)」を参照し、ログ記録に使用する接続文字列を確認します。

### <a name="symptoms"></a>**現象**
パッケージ実行レポート内のエラー メッセージが、トラブルシューティングには不十分。

### <a name="solution"></a>**解決方法**
WorkerSettings.config で構成されている TasksRootFolder の下には、さらに多くの実行ログがあります。既定では \<ドライブ\>:\Users\\*[account]*\AppData\Local\SSIS\ScaleOut\Tasks です。 *[account]*は、既定値が SSISScaleOutWorker140 の Scale Out Worker サービスを実行しているアカウントです。

*[execution id]* を持つパッケージ実行のログを見つけるには、次の T-SQL コマンドを実行し、*[task id]* を取得します。 次に、TasksRootFolder の下で *[task id]* という名前のサブフォルダーを見つけます。<sup>1<sup>

```sql
SELECT [TaskId]
FROM [SSISDB].[internal].[tasks] tasks, [SSISDB].[internal].[executions] executions 
WHERE executions.execution_id = *Your Execution Id* AND tasks.JobId = executions.job_id
```
<sup>1</sup> このクエリは、トラブルシューティング目的のみで、Scale Out Worker のログ記録/診断シナリオが今後強化されるときに変更される可能性があります。 
