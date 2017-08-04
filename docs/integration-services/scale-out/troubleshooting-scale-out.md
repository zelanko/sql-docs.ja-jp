---
title: "Services (SSIS) のスケール アウトの SQL Server の統合のトラブルシューティング |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 1
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 41bb853dd08591596f6f5baa918e174d0c26a6b5
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="troubleshooting-scale-out"></a>スケール アウトのトラブルシューティング

SSIS のスケール アウト SSISDB、スケール アウト マスター サービスとスケール アウト Worker サービスの間で communtication が含まれます。 場合によっては、通信は、構成の誤り、アクセス許可がないその他の理由により解除されます。 このドキュメントでは、スケール アウト構成のトラブルシューティングを行うことができます。

発生する現象を調査するために、問題が解決されるまで、1 つずつ次の手順に従います。

### <a name="symptoms"></a>**現象** 
スケール アウト マスターが SSISDB に接続できません。 

マスター プロパティは、スケール アウト マネージャーで表示できません。

マスター プロパティは、[SSISDB] が入力されていません。[カタログ] です。[master_properties]

### <a name="solution"></a>**解決方法**
手順 1: スケール アウトが有効かどうを確認します。

右クリック**SSISDB** SSMS のオブジェクト エクスプ ローラー ノード**スケール アウト機能が有効になっている**です。

![有効なスケール アウトには](media\isenabled.PNG)

プロパティの値が False の場合 [SSISDB] のストアド プロシージャを呼び出すことによってスケールを有効にします。[カタログ] です。[enable_scaleout] です。

手順 2: スケール アウト マスター構成ファイルで指定された Sql Server 名が正しいかどうかを確認し、スケール アウト マスター サービスを再起動します。

### <a name="symptoms"></a>**現象** 
スケール アウト ワーカーは、スケール アウト マスターに接続できません。

スケール アウト ワーカーは、スケール アウト マネージャーに追加した後は表示されません。

スケール アウト ワーカーは、[SSISDB] には表示されません。[カタログ] です。[worker_agents]

スケール アウト Worker サービスが実行されている、スケール アウト ワーカーがオフラインの間

### <a name="solutions"></a>**ソリューション** 
スケール アウト ワーカー サービスのログのエラー メッセージを確認して\<ドライバー\>: \Users\\*[worker サービスを実行しているアカウント]*\AppData\Local\SSIS\Cluster\Agent です。

**場合** 

System.ServiceModel.EndpointNotFoundException: https:// でリッスンしているエンドポイントがありません*[コンピューター名]: [Port]*/ClusterManagement/メッセージを受け入れることができます。

手順 1: スケール アウト マスター サービス構成ファイルで指定されたポート番号が正しいかどうかを確認し、スケール アウト マスター サービスを再起動します。 

手順 2: スケール アウト ワーカー サーバーのサービス構成で指定されたマスター エンドポイントが正しいかどうかを確認し、スケール アウト Worker サービスを再起動します。

手順 3: では、ファイアウォール ポートがスケール アウト マスター ノード上で開いているかどうかを確認します。

手順 4: スケール アウト マスター ノードとスケール アウト ワーカー ノード間の接続の問題を解決します。

**場合**

System.ServiceModel.Security.SecurityNegotiationException: 証明機関と SSL/TLS のセキュリティで保護されたチャネルに対する信頼関係を確立できませんでした '*[マシン名]: [Port]*' です。 System.Net.WebException--->: 基になる接続が閉じられました: SSL/TLS セキュリティで保護されたチャネルに対する信頼関係を確立できませんでした。 System.Security.Authentication.AuthenticationException--->: リモート証明書が検証プロシージャに対して無効です。

手順 1: インストール スケール アウト マスター スケール アウト ワーカー ノード上のローカル マシンのルート証明書ストアに証明書しない場合まだインストールされていないし、スケール アウト Worker サービスを再起動します。

手順 2: は、マスター エンドポイント内のホスト名が Cn のスケール アウト マスター証明書に含まれているかどうかを確認します。 ない場合は、スケール アウト ワーカーの構成ファイル内のマスター エンドポイントをリセットし、スケール アウト Worker サービスを再起動します。 

> [!Note]
> DNS の設定のためのマスター エンドポイントのホスト名を変更することはできない場合、は、スケール アウト マスター証明書の変更が必要です。 参照してください[SSIS スケール アウトでの証明書を扱う](deal-with-certificates-in-ssis-scale-out.md)です。

手順 3: スケール アウト マスター証明書の拇印がマスターにスケール アウト ワーカー サーバーの構成で指定された拇印に一致するかどうかを確認します。 

**場合**

System.ServiceModel.Security.SecurityNegotiationException: は権限を持つ SSL/TLS のセキュリティで保護されたチャネルを確立できませんでした '*[マシン名]: [Port]*' です。 System.Net.WebException--->: 要求が中止されました: SSL/TLS セキュリティで保護されたチャネルを作成できませんでした。

手順 1: スケール アウト Worker サービスを実行するアカウントが次のコマンドでスケール アウト ワーカーの証明書へのアクセスがかどうかを確認します。

```dos
winhttpcertcfg.exe -l -c LOCAL_MACHINE\MY -s {CN of the worker certificate}
```

アカウントがアクセスできない場合は、以下のコマンドを許可し、スケール アウト Worker サービスを再起動します。

```dos
winhttpcertcfg.exe -g -c LOCAL_MACHINE\My -s {CN of the worker certificate} -a {the account running Scale Out Worker service}
```

**場合**

System.ServiceModel.Security.MessageSecurityException: クライアントの認証方式 'Anonymous' の HTTP 要求が禁止されています。 System.Net.WebException--->: リモート サーバーがエラーを返しました: (403) 許可されていません。

手順 1: スケール アウト ワーカーにインストール スケール アウト マスター ノード上のローカル マシンのルート証明書ストアに証明書のない場合まだインストールされていないし、スケール アウト Worker サービスを再起動します。

手順 2: スケール アウト マスター ノード上のローカル マシンのルート証明書ストアに不要な証明書をクリーンアップします。

手順 3: スケール アウト マスター ノードの下のレジストリ エントリを追加することで、TLS/SSL のハンドシェイク プロセス中に信頼されたルート証明機関の一覧を送信できなくに Schannel を構成します。

Hkey_local_machine \system\currentcontrolset\control\securityproviders\schannel

値の名前: SendTrustedIssuerList 

値の種類: REG_DWORD 

データの値: 0 (False)

**場合**

System.ServiceModel.CommunicationException: https:// への HTTP 要求を発行中にエラーが発生しました*[マシン名]: [Port]*ClusterManagement/です。 HTTP でサーバー証明書が正しく構成されていないという事実が原因が考えられます。HTTPS の場合も、SYS. これは、クライアントとサーバー間でセキュリティ バインドの不整合により原因でした。 

手順 1: は、次のコマンドのマスター ノードに、スケール アウト マスター証明書が正しくバインド マスター エンドポイントのポートにかどうかを確認します。 スケール アウト マスター証明書の拇印で表示される証明書のハッシュが一致するかどうかを確認してください。

```dos
netsh http show sslcert ipport=0.0.0.0:{Master port}
```

バインディングが正しくない場合は、次のコマンドでリセットし、スケール アウト Worker サービスを再起動します。

```dos
netsh http delete sslcert ipport=0.0.0.0:{Master port}
netsh http add sslcert ipport=0.0.0.0:{Master port} certhash={Master certificate thumbprint} certstorename=Root appid={random guid}
```

### <a name="symptoms"></a>**現象**
スケール アウトでの実行を開始しません。

### <a name="solution"></a>**解決方法**

[SSISDB] で、パッケージを実行時に選択したマシンの状態を確認してください。[カタログ] です。[worker_agents] です。 少なくとも 1 つのワーカーには、オンラインで有効なをする必要があります。

### <a name="symptoms"></a>**現象** 
パッケージが正常に動作しますが、記録されたメッセージはありません。

### <a name="solution"></a>**解決方法**

SQL Server 認証が許可されたかどうかは Sql Server から SSISDB をホストしていることを確認します。

> [!Note]  
> スケール アウト ログのアカウントを変更した場合は、次を参照してください。[スケール アウトのログ記録のアカウントの変更](change-logdb-account.md)ログに使用する接続文字列を確認してください。

### <a name="symptoms"></a>**現象**
パッケージ実行のレポート内のエラー メッセージでは不十分なトラブルシューティングします。

### <a name="solution"></a>**解決方法**
TasksRootFolder WorkerSettings.config で構成されている複数の実行ログを確認できます。 既定では\<ドライバー\>: \Users\\*[アカウント]*\AppData\Local\SSIS\ScaleOut\Tasks です。 *[アカウント]*は既定値は SSISScaleOutWorker140 スケール アウト Worker サービスを実行しているアカウントです。

使用して、パッケージ実行のログを検索する*[実行 id]*、取得する次の T-SQL コマンドを実行、 *[タスク id]*です。 いう名前のサブフォルダーを検索し、 *[タスク id]* TasksRootFolder <sup> 。1<sup>

```sql
SELECT [TaskId]
FROM [SSISDB].[internal].[tasks] tasks, [SSISDB].[internal].[executions] executions 
WHERE executions.execution_id = *Your Execution Id* AND tasks.JobId = executions.job_id
```
<sup>1</sup>このクエリは、スケール アウト ワーカーのログ記録/診断シナリオが今後強化されるときに変更する目的のみおよびオープンをトラブルシューティングします。 
