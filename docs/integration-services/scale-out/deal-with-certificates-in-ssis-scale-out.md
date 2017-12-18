---
title: "SQL Server Integration Services Scale Out における証明書の処理 | Microsoft Docs"
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
ms.openlocfilehash: e09fec1fcf9cf0221dad50d708adef773b297237
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="deal-with-certificates-in-sql-server-integration-services-scale-out"></a>SQL Server Integration Services Scale Out における証明書の処理

Scale Out Master と Scale Out Worker 間の通信をセキュリティで保護するため、Scale Out では Scale Out Master 証明書と Scale Out Worker 証明書の 2 つの証明書が使用されます。 

## <a name="scale-out-master-certificate"></a>Scale Out Master 証明書

ほとんどの場合、Scale Out Master 証明書は、Scale Out Master のインストール時に構成されます。

SQL Server インストール ウィザードの **[Integration Services Scale Out の構成 - マスター ノード]** ページで、新しい自己署名 SSL 証明書を作成するか、既存の SSL 証明書を使用するかを選択できます。

![マスターの構成](media/master-config.PNG)

証明書に対して特別な要件がない場合は、新しい自己署名 SSL 証明書の作成を選択できます。 さらに、証明書で CN を指定できます。 後で Scale Out Worker によって使用されるマスター エンドポイントのホスト名が CN に含まれていることを確認してください。 既定では、マスター ノードのコンピューター名と IP が含まれます。 

既存の証明書を使用することを選択する場合は、[参照] をクリックし、ローカル コンピューターの**ルート**証明書ストアから SSL 証明書を選択します。

### <a name="change-scale-out-master-certificate"></a>Scale Out Master 証明書の変更

証明書の有効期限などの理由により、Scale Out Master 証明書を変更する場合があります。 下記の手順に従ってください。

#### <a name="1-create-a-ssl-certificate"></a>1.SSL 証明書を作成する
次のコマンドを使用して、SSL 証明書を作成し、マスター ノードにインストールします。
```dos
MakeCert.exe -n CN={master endpoint host} SSISScaleOutMaster.cer -r -ss Root -sr LocalMachine
```
例:
```dos
MakeCert.exe -n CN=MasterMachine SSISScaleOutMaster.cer -r -ss Root -sr LocalMachine
```

#### <a name="2-bind-the-certificate-to-master-port"></a>2.証明書をマスター ポートにバインドする
次のコマンドを使用して、元のバインドを確認します。
```dos
netsh http show sslcert ipport=0.0.0.0:{Master port}
```
例:
```dos
netsh http show sslcert ipport=0.0.0.0:8391
```
次のコマンドを使用して、元のバインドを削除し、新しいバインドを設定します。
```dos
netsh http delete sslcert ipport=0.0.0.0:{Master port}
netsh http add sslcert ipport=0.0.0.0:{Master port} certhash={SSL Certificate Thumbprint} certstorename=Root appid={original appid}
```
例:
```dos
netsh http delete sslcert ipport=0.0.0.0:8391
netsh http add sslcert ipport=0.0.0.0:8391 certhash=01d207b300ca662f479beb884efe6ce328f77d53 certstorename=Root appid={a1f96506-93e0-4c91-9171-05a2f6739e13}
```
#### <a name="3-update-scale-out-master-service-configuration-file"></a>3.Scale Out Master サービス構成ファイルを更新する
マスター ノードで、Scale Out Master サービス構成ファイル \<ドライバー\>:\Program Files\Microsoft SQL Server\140\DTS\Binn\MasterSettings.config を更新します。 **SSLCertThumbprint** を新しい SSL 証明書のサムプリントに更新します。

#### <a name="4-restart-scale-out-master-service"></a>4.Scale Out Master サービスを再起動する

#### <a name="5-reconnect-scale-out-worker-to-scale-out-master"></a>5.Scale Out Worker を Scale Out Master に再接続する
各 Scale Out Worker に対し、Worker を削除して [Scale Out Manager](integration-services-ssis-scale-out-manager.md) を使用して再度追加するか、次の手順の 5.1 から 5.3 を実行します。

5.1 ワーカー ノードのローカル コンピューターのルート ストアにクライアント SSL 証明書をインストールします。

5.2 ワーカー ノードのワーカー サービス構成ファイル \<ドライバー\>:\Program Files\Microsoft SQL Server\140\DTS\Binn\WorkerSettings.config を更新します。 **MasterHttpsCertThumbprint** を新しい SSL 証明書のサムプリントに更新します。

5.3 Scale Out Worker サービスを再起動します。


## <a name="scale-out-worker-certificate"></a>Scale Out Worker 証明書

Scale Out Worker 証明書は、Scale Out Worker のインストール時に自動的に生成されます。 

### <a name="change-scale-out-worker-certificate"></a>Scale Out Worker 証明書の変更

Scale Out Worker 証明書を変更する場合は、次の手順に従います。

#### <a name="1-create-a-certificate"></a>1.証明書を作成する
次のコマンドを使用して、証明書を作成してインストールします。
```dos
MakeCert.exe -n CN={worker machine name};CN={worker machine ip} SSISScaleOutWorker.cer -r -ss My -sr LocalMachine
```
例:
```dos
MakeCert.exe -n CN=WorkerMachine;CN=10.0.2.8 SSISScaleOutWorker.cer -r -ss My -sr LocalMachine
```
#### <a name="2-install-the-client-certificate-to-the-root-store-of-local-machine-on-worker-node"></a>2.クライアント証明書をワーカー ノードのローカル コンピューターのルート ストアにインストールする

#### <a name="3-give-service-access-to-the-certificate"></a>3.証明書にサービスのアクセス権を付与する
次のコマンドを使用して、古い証明書を削除して、新しい証明書に Scale Out Worker サービスのアクセス権を付与します。
```dos
certmgr.exe /del /c /s /r localmachine My /n {CN of the old certificate}
winhttpcertcfg.exe -g -c LOCAL_MACHINE\My -s {CN of the new certificate} -a {the account running Scale Out Worker service}
```
例:
```dos
certmgr.exe /del /c /s /r localmachine My /n WorkerMachine
winhttpcertcfg.exe -g -c LOCAL_MACHINE\My -s WorkerMachine -a SSISScaleOutWorker140
```
#### <a name="4-update-scale-out-worker-configuration-file"></a>4.Scale Out Worker の構成ファイルを更新する
ワーカー ノードで、Scale Out Worker サービス構成ファイル \<ドライバー\>:\Program Files\Microsoft SQL Server\140\DTS\Binn\WorkerSettings.config を更新します。 **WorkerHttpsCertThumbprint** を新しい証明書のサムプリントに更新します。

#### <a name="5-install-the-client-certificate-to-the-root-store-of-local-machine-on-master-node"></a>5.クライアント証明書をマスター ノードのローカル コンピューターのルート ストアにインストールする

#### <a name="6-restart-scale-out-worker-service"></a>6.Scale Out Worker サービスを再起動する
