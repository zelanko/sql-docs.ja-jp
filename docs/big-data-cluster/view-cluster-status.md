---
title: クラスターの状態を表示する
titleSuffix: SQL Server big data clusters
description: この記事では、Azure Data Studio、ノートブック、および mssqlctl コマンドを使用してビッグ データ クラスターの状態を表示する方法について説明します。
author: yualan
ms.author: alayu
ms.reviewer: mikeray
manager: jroth
ms.date: 06/27/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: b3cc78e36fe427966c7730533104c63aa3ed9332
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727324"
---
# <a name="how-to-view-the-status-of-a-big-data-cluster"></a>ビッグ データ クラスターの状態を表示する方法

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事では、サービス エンドポイントにアクセスして、SQL Server のビッグ データ クラスター (プレビュー) の状態を表示する方法について説明します。 両方の Azure Data Studio を使用して**mssqlctl**、この記事では、両方の方法を説明しています。

## <a id="datastudio"></a> Azure Data Studio を使用して、

最新のダウンロード後に**insider ビルド**の[Azure Data Studio](https://aka.ms/azdata-insiders)ビッグ データの状態がクラスターで SQL Server のビッグ データ クラスター ダッシュ ボード、サービス エンドポイントを表示することができます。 以下の機能の一部がのみ最初の Azure Data Studio insider ビルドで使用できるに注意してください。

1. 最初に、Azure Data Studio で、ビッグ データ クラスターへの接続を作成します。 詳細については、次を参照してください。 [Azure データ Studio を使用した SQL Server クラスターのビッグ データへの接続](connect-to-big-data-cluster.md)します。

1. ビッグ データ クラスターのエンドポイントを右クリックし、をクリックして**管理**します。

   ![右クリックを管理します。](media/view-cluster-status/right-click-manage.png)

1. 選択、 **SQL Server のビッグ データ クラスター**ビッグ データ クラスター ダッシュ ボードにアクセスするには、タブ。

   ![ビッグ データ クラスター ダッシュ ボード](media/view-cluster-status/bdc-dashboard.png)

### <a name="service-endpoints"></a>サービス エンドポイント

ビッグ データ クラスター内のさまざまなサービスを簡単にアクセスできるようにする重要です。 ビッグ データ クラスター ダッシュ ボードを表示し、サービス エンドポイントをコピーできるようにするサービス エンドポイントのテーブルを提供します。

![サービス エンドポイント](media/view-cluster-status/service-endpoints.png)

最初のいくつかの行では、次のサービスを公開します。

- アプリケーション プロキシ
- Cluster Management Service
- HDFS と Spark
- プロキシの管理

これらのサービスには、コピーおよびそれらのサービスに接続するため、エンドポイントが必要なときの貼り付け可能なエンドポイントが一覧表示します。 など、エンドポイントの右側にコピー アイコンをクリックして、そのエンドポイントを要求するテキスト ウィンドウに貼り付けます。 Cluster Management Service のエンドポイントが実行に必要な[クラスター状態 notebook](#notebook)します。

### <a name="dashboards"></a>ダッシュボード

サービス エンドポイントのテーブルには、監視するためのいくつかのダッシュ ボードも公開します。

- メトリック (Grafana)
- ログ (Kibana)
- Spark ジョブの監視
- Spark のリソースの管理

これらのリンクを直接クリックできます。 サービスに接続する前に、ユーザー名とパスワードを指定するには、2 回求められます。

### <a id="notebook"></a> クラスターの状態のノートブック

1. クラスターの状態の notebook を起動することで、ビッグ データ クラスターのクラスターの状態を表示することもできます。 Notebook を起動する をクリックして、**クラスター状態**タスク。

    ![起動](media/view-cluster-status/cluster-status-launch.png)

2. 開始する前に、次のものを必要となります。

    - ビッグ データ クラスター名
    - コント ローラーのユーザー名
    - コント ローラーのパスワード
    - コント ローラー エンドポイント

    既定のビッグ データ クラスター名は**mssql クラスター**の展開時にカスタマイズした場合を除き、します。 サービス エンドポイントの表に、ビッグ データ クラスター ダッシュ ボードからエンドポイントをコント ローラーが表示されます。 エンドポイントがになっている**Cluster Management Service**します。 資格情報がわからない場合は、クラスターをデプロイした管理者に問い合わせてください。

3. クリックして**セルの実行**上部のツールバー。

4. 資格情報のプロンプトに従います。 キーを押して ENTER キーを押してした後は、ビッグ データ クラスター名、コント ローラーのユーザー名およびコント ローラーのパスワードの各資格情報を入力します。

    > [!Note]
    > 場合は、ビッグ データと構成ファイルのセットアップがない、コント ローラー エンドポイントになります。 入力または貼り付けし、続行するには ENTER キーを押します。

5. 正常に接続されている場合、notebook の残りの部分には、ビッグ データ クラスターの各コンポーネントの出力が表示されます。 特定のコード セルを再実行する場合は、コード セルをポイントし、をクリックして、**実行**アイコン。

## <a name="use-mssqlctl"></a>mssqlctl を使用する

使用することも[mssqlctl](deploy-install-mssqlctl.md)両方のエンドポイントおよびクラスターの状態を表示するコマンド。

### <a name="service-endpoints"></a>サービス エンドポイント

次の手順を使用してビッグ データ クラスターの外部エンドポイントの IP アドレスを取得することができます。

1. 次の外部 IP の出力を調べることで、コント ローラー エンドポイントの IP アドレスを見つける**kubectl**コマンド。

   ```bash
   kubectl get svc controller-svc-external -n <your-big-data-cluster-name>
   ```

   > [!TIP]
   > デプロイ時に既定の名前を変更しなかった場合は、使用`-n mssql-cluster`前のコマンド。 **mssql クラスター**はビッグ データ クラスターの既定の名前です。

1. 使用して、ビッグ データ クラスターにログイン[mssqlctl ログイン](reference-mssqlctl.md)します。 設定、 **-コント ローラー エンドポイント**コント ローラーのエンドポイントの外部 IP アドレスへのパラメーター。

   ```bash
   mssqlctl login --controller-endpoint https://<ip-address-of-controller-svc-external>:30080 --controller-username <user-name>
   ```

   デプロイ時にユーザー名とコント ローラー (CONTROLLER_USERNAME および CONTROLLER_PASSWORD) 用に構成したパスワードを指定します。

1. 実行[mssqlctl bdc エンドポイント リスト](reference-mssqlctl-bdc-endpoint.md)の各エンドポイントと対応する IP アドレスとポート値の説明の一覧を取得します。 

   ```bash
   mssqlctl bdc endpoint list -o table
   ```

   このコマンドからの出力例を次に示します。

   ```output
   Description                                             Endpoint                                                   Ip              Name               Port    Protocol
   ------------------------------------------------------  ---------------------------------------------------------  --------------  -----------------  ------  ----------
   Gateway to access HDFS files, Spark                     https://11.111.111.111:30443                               11.111.111.111  gateway            30443   https
   Spark Jobs Management and Monitoring Dashboard          https://11.111.111.111:30443/gateway/default/sparkhistory  11.111.111.111  spark-history      30443   https
   Spark Diagnostics and Monitoring Dashboard              https://11.111.111.111:30443/gateway/default/yarn          11.111.111.111  yarn-ui            30443   https
   Application Proxy                                       https://11.111.111.111:30778                               11.111.111.111  app-proxy          30778   https
   Management Proxy                                        https://11.111.111.111:30777                               11.111.111.111  mgmtproxy          30777   https
   Log Search Dashboard                                    https://11.111.111.111:30777/kibana                        11.111.111.111  logsui             30777   https
   Metrics Dashboard                                       https://11.111.111.111:30777/grafana                       11.111.111.111  metricsui          30777   https
   Cluster Management Service                              https://11.111.111.111:30080                               11.111.111.111  controller         30080   https
   SQL Server Master Instance Front-End                    11.111.111.111,31433                                       11.111.111.111  sql-server-master  31433   tcp
   HDFS File System Proxy                                  https://11.111.111.111:30443/gateway/default/webhdfs/v1    11.111.111.111  webhdfs            30443   https
   Proxy for running Spark statements, jobs, applications  https://11.111.111.111:30443/gateway/default/livy/v1       11.111.111.111  livy               30443   https
   ```

### <a name="view-cluster-status"></a>クラスターの状態を表示する

クラスターの状態を表示することができます、 [mssqlctl bdc ステータス表示](reference-mssqlctl-bdc-status.md)コマンド。

```bash
mssqlctl bdc status show -o table
```

> [!TIP]
> 状態のコマンドを実行する必要があります最初でログインする、 **mssqlctl ログイン**エンドポイントの前のセクションで示したコマンド。

このコマンドからの出力例を次に示します。

```output
Kind     Name           State
-------  -------------  -------
BDC      mssql-cluster  Ready
Control  default        Ready
Master   default        Ready
Compute  default        Ready
Data     default        Ready
Storage  default        Ready
```

### <a name="view-pool-status"></a>プールの状態の表示

使用して、クラスター内のプールの状態を表示することができます、 [mssqlctl bdc プール状態表示](reference-mssqlctl-bdc-pool-status.md)コマンド。 このコマンドを使用するには、プールの種類を指定、`--kind`パラメーター。 プールの種類は次のとおりです。

- コンピューティング
- data
- master
- Spark
- ストレージ

たとえば、次のコマンドは、記憶域プールのプールの状態を表示します。

```bash
mssqlctl bdc pool status show --kind storage
```

次の出力のようなテキストが表示されます。

```output
[
  {
    "kind": "Pod",
    "logsUrl": "https://11.111.111.111:30080/clusters/mssql-cluster/pods/storage-0-0/logs/ui",
    "name": "storage-0-0",
    "nodeMetricsUrl": "https://11.111.111.111:30080/clusters/mssql-cluster/pods/storage-0-0/nodemetrics/ui",
    "sqlMetricsUrl": "https://11.111.111.111:30080/clusters/mssql-cluster/pods/storage-0-0/sqlmetrics/ui",
    "state": "Running"
  },
  {
    "kind": "Pod",
    "logsUrl": "https://11.111.111.111:30080/clusters/mssql-cluster/pods/storage-0-1/logs/ui",
    "name": "storage-0-1",
    "nodeMetricsUrl": "https://11.111.111.111:30080/clusters/mssql-cluster/pods/storage-0-1/nodemetrics/ui",
    "sqlMetricsUrl": "https://11.111.111.111:30080/clusters/mssql-cluster/pods/storage-0-1/sqlmetrics/ui",
    "state": "Running"
  }
]
```

`logsUrl`ログ情報を kibana ダッシュ ボードへのリンクの値します。

![Kibana ダッシュ ボード](./media/view-cluster-status/kibana-dashboard.png)

`nodeMetricsUrl`と`sqlMetricsUrl`値は、ノードの正常性と SQL のメトリックを監視するための grafana ダッシュ ボードにリンクします。

![Grafana ダッシュ ボード](./media/view-cluster-status/grafana-dashboard.png)

![SQL](./media/view-cluster-status/grafana-sql-status.png)

### <a name="view-controller-status"></a>ビュー コント ローラーの状態

コント ローラーの状態を表示することができます、 [mssqlctl bdc コントロールの状態表示](reference-mssqlctl-bdc-control-status.md)コマンド。 ビッグ データ クラスターのコント ローラーのノードに関連する監視ダッシュ ボードへのようなリンクを提供します。

## <a name="next-steps"></a>次の手順

ビッグ データ クラスターに関する詳細については、次を参照してください。 [SQL Server のビッグ データ クラスターは](big-data-cluster-overview.md)します。
