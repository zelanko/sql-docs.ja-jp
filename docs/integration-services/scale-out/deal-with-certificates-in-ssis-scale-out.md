---
title: "Sql Server Integration Services スケール アウトでの証明書を扱う |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: scale-out
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 1
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 2970b2b2cc7cf30c18a203ebbb92b5418bfc9be5
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="deal-with-certificates-in-sql-server-integration-services-scale-out"></a>SQL Server Integration Services スケール アウトでの証明書を処理します。

スケール アウト マスターとスケール アウト ワーカー間の通信をセキュリティで保護するには、2 つの証明書はスケール アウト マスター証明書とスケール アウト ワーカーの証明書などにスケール アウトで使用されます。 

## <a name="scale-out-master-certificate"></a>スケール アウト マスター証明書

ほとんどの場合、スケール アウト master データベースのインストール中にスケール アウト マスター証明書を構成します。

**Integration Services スケール アウトの構成のマスター ノード**ページを新しい自己署名 SSL 証明書を作成または既存の SSL 証明書を使用して SQL Server インストール ウィザードの選択できます。

![マスターの構成](media/master-config.PNG)

証明書に対する特別な要件を持っていない場合は、新しい自己署名 SSL 証明書を作成できます。 さらに、証明書の Cn を指定できます。 後でスケール アウト ワーカーによって使用されるマスター エンドポイントのホスト名が Cn に含まれることを確認してください。 既定では、コンピューター名と ip アドレスのマスター ノードが含まれます。 

既存の証明書を使用する場合から SSL 証明書を選択するには [参照] をクリックして**ルート**ローカル コンピューターの証明書ストア。

### <a name="change-scale-out-master-certificate"></a>スケール アウト マスター証明書の変更

証明書の有効期限などの理由により、スケール アウト マスター証明書を変更することがあります。 下記の手順に従ってください。

#### <a name="1-create-a-ssl-certificate"></a>1.SSL 証明書を作成します。
作成し、マスターの SSL 証明書をインストールする次のコマンドを使用してノード。
```dos
MakeCert.exe -n CN={master endpoint host} SSISScaleOutMaster.cer -r -ss Root -sr LocalMachine
```
例:
```dos
MakeCert.exe -n CN=MasterMachine SSISScaleOutMaster.cer -r -ss Root -sr LocalMachine
```

#### <a name="2-bind-the-certificate-to-master-port"></a>2.マスターへの証明書のバインドのポート
コマンドを使用して、元のバインドを確認してください。
```dos
netsh http show sslcert ipport=0.0.0.0:{Master port}
```
例:
```dos
netsh http show sslcert ipport=0.0.0.0:8391
```
元のバインドを削除し、次のコマンドを含む新しいバインディングを設定します。
```dos
netsh http delete sslcert ipport=0.0.0.0:{Master port}
netsh http add sslcert ipport=0.0.0.0:{Master port} certhash={SSL Certificate Thumbprint} certstorename=Root appid={original appid}
```
例:
```dos
netsh http delete sslcert ipport=0.0.0.0:8391
netsh http add sslcert ipport=0.0.0.0:8391 certhash=01d207b300ca662f479beb884efe6ce328f77d53 certstorename=Root appid={a1f96506-93e0-4c91-9171-05a2f6739e13}
```
#### <a name="3-update-scale-out-master-service-configuration-file"></a>3.スケール アウト マスター サービス構成ファイルを更新します。
更新プログラムのスケール アウト マスター サービス構成ファイル、\<ドライバー\>: \Program Files\Microsoft マスター上での SQL Server\140\DTS\Binn\MasterSettings.config ノード。 更新**SSLCertThumbprint**新しい SSL 証明書のサムプリントにします。

#### <a name="4-restart-scale-out-master-service"></a>4.スケール アウト マスター サービスを再起動します。

#### <a name="5-reconnect-scale-out-worker-to-scale-out-master"></a>5.スケール アウトをスケール アウト マスター ワーカーを再接続します。
各スケール アウト作業者に、削除するか、ワーカーを再度追加すると[スケール アウト Manager](integration-services-ssis-scale-out-manager.md)または 5.1 を 5.3 以下の手順に従います。

5.1 ワーカー ノード上のローカル マシンのルート ストアに、クライアント SSL 証明書をインストールします。

5.2 ワーカー サービス構成ファイル更新スケール アウト ワーカー サービス構成ファイルをスケールの更新\<ドライバー\>: \Program Files\Microsoft SQL Server\140\DTS\Binn\WorkerSettings.config ワーカー ノードにします。 更新**MasterHttpsCertThumbprint**新しい SSL 証明書のサムプリントにします。

5.3 Worker サービスをスケールを再起動します。


## <a name="scale-out-worker-certificate"></a>スケール アウト ワーカーの証明書

スケール アウト ワーカーの証明書は、スケール アウト Worker のインストール中に自動生成されます。 

### <a name="change-scale-out-worker-certificate"></a>スケール アウト ワーカーの証明書の変更

スケール アウト ワーカーの証明書を変更する場合、次の手順に従います。

#### <a name="1-create-a-certificate"></a>1.証明書の作成します。
作成して、次のコマンドを使用して証明書をインストールします。
```dos
MakeCert.exe -n CN={worker machine name};CN={worker machine ip} SSISScaleOutWorker.cer -r -ss My -sr LocalMachine
```
例:
```dos
MakeCert.exe -n CN=WorkerMachine;CN=10.0.2.8 SSISScaleOutWorker.cer -r -ss My -sr LocalMachine
```
#### <a name="2-install-the-client-certificate-to-the-root-store-of-local-machine-on-worker-node"></a>2.Worker ノードのローカル コンピューターのルート ストアにクライアント証明書をインストールします。

#### <a name="3-give-service-access-to-the-certificate"></a>3.証明書をサービスのアクセス権を付与します。
古い証明書を削除して、コマンドを使用して新しい証明書をスケール アウト ワーカー サービスのアクセス権を付与します。
```dos
certmgr.exe /del /c /s /r localmachine My /n {CN of the old certificate}
winhttpcertcfg.exe -g -c LOCAL_MACHINE\My -s {CN of the new certificate} -a {the account running Scale Out Worker service}
```
例:
```dos
certmgr.exe /del /c /s /r localmachine My /n WorkerMachine
winhttpcertcfg.exe -g -c LOCAL_MACHINE\My -s WorkerMachine -a SSISScaleOutWorker140
```
#### <a name="4-update-scale-out-worker-configuration-file"></a>4.スケール アウト ワーカーの構成ファイルを更新します。
更新プログラムのスケール アウト ワーカーのサービス構成ファイル、\<ドライバー\>: \Program Files\Microsoft SQL Server\140\DTS\Binn\WorkerSettings.config ワーカー ノードにします。 更新**WorkerHttpsCertThumbprint**新しい証明書のサムプリントにします。

#### <a name="5-install-the-client-certificate-to-the-root-store-of-local-machine-on-master-node"></a>5.マスター上でローカル コンピューターのルート ストアにクライアント証明書をインストール ノード

#### <a name="6-restart-scale-out-worker-service"></a>6.スケール アウト Worker サービスを再起動します。

