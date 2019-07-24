---
title: クラスターの状態を表示する
titleSuffix: SQL Server big data clusters
description: この記事では、Azure Data Studio、notebook、および azdata コマンドを使用して、ビッグデータクラスターの状態を表示する方法について説明します。
author: yualan
ms.author: alayu
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: c6dca94b8bd7547222394d7809cb003b9e936982
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419290"
---
# <a name="how-to-view-the-status-of-a-big-data-cluster"></a>ビッグデータクラスターの状態を表示する方法

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事では、サービスエンドポイントにアクセスして SQL Server ビッグデータクラスター (プレビュー) の状態を表示する方法について説明します。 Azure Data Studio と**azdata**の両方を使用できます。この記事では、両方の手法について説明します。

## <a id="datastudio"></a>Azure Data Studio を使用する

[Azure Data Studio](https://aka.ms/azdata-insiders)の最新の**insider ビルド**をダウンロードした後、SQL Server ビッグデータクラスターダッシュボードを使用して、サービスエンドポイントとビッグデータクラスターの状態を表示できます。 以下の機能の一部は、Azure Data Studio の insider ビルドでのみ使用できます。

1. まず、Azure Data Studio でビッグデータクラスターへの接続を作成します。 詳細については、「Azure Data Studio を使用した[SQL Server ビッグデータクラスターへの接続](connect-to-big-data-cluster.md)」を参照してください。

1. ビッグデータクラスターエンドポイントを右クリックし、 **[管理]** をクリックします。

   ![[管理] を右クリック](media/view-cluster-status/right-click-manage.png)

1. ビッグデータクラスターのダッシュボードにアクセスするには、 **[ビッグデータクラスターの SQL Server]** タブを選択します。

   ![ビッグデータクラスターダッシュボード](media/view-cluster-status/bdc-dashboard.png)

### <a name="service-endpoints"></a>サービスエンドポイント

ビッグデータクラスター内のさまざまなサービスに簡単にアクセスできるようにすることが重要です。 ビッグデータクラスターダッシュボードには、サービスエンドポイントを表示してコピーできるサービスエンドポイントテーブルが用意されています。

![サービスエンドポイント](media/view-cluster-status/service-endpoints.png)

最初のいくつかの行では、次のサービスが公開されています。

- アプリケーションプロキシ
- クラスタ管理サービス
- HDFS と Spark
- 管理プロキシ

これらのサービスには、これらのサービスに接続するためのエンドポイントが必要な場合に、コピーして貼り付けることができるエンドポイントが一覧表示されます。 たとえば、エンドポイントの右側にあるコピーアイコンをクリックして、そのエンドポイントを要求しているテキストウィンドウに貼り付けることができます。 クラスターの[状態 notebook](#notebook)を実行するには、クラスター管理サービスエンドポイントが必要です。

### <a name="dashboards"></a>ダッシュボード

サービスエンドポイントテーブルでは、監視用の複数のダッシュボードも公開されます。

- メトリック (Grafana)
- ログ (Kibana)
- Spark ジョブの監視
- Spark リソース管理

これらのリンクを直接クリックできます。 サービスに接続する前に、ユーザー名とパスワードを入力するように求められます。

### <a id="notebook"></a>クラスターの状態の notebook

1. クラスターの状態の notebook を起動して、ビッグデータクラスターのクラスターの状態を表示することもできます。 Notebook を起動するには、 **[クラスターの状態]** タスクをクリックします。

    ![開い](media/view-cluster-status/cluster-status-launch.png)

2. 開始する前に、次の項目が必要です。

    - ビッグデータクラスター名
    - コントローラーのユーザー名
    - コントローラーパスワード
    - コントローラーエンドポイント

    既定のビッグデータクラスター名は、展開時にカスタマイズしない限り、 **mssql クラスター**になります。 コントローラーエンドポイントは、サービスエンドポイントテーブルのビッグデータクラスターダッシュボードから見つけることができます。 エンドポイントが**クラスター管理サービス**として一覧表示されます。 資格情報がわからない場合は、クラスターをデプロイした管理者に問い合わせてください。

3. 上部のツールバーで **[セルの実行]** をクリックします。

4. プロンプトに従って資格情報を確認します。 ビッグデータクラスター名、コントローラーのユーザー名、およびコントローラーパスワードの各資格情報を入力したら、enter キーを押します。

    > [!Note]
    > ビッグデータが設定された構成ファイルがない場合は、コントローラーエンドポイントの指定を求められます。 入力するか貼り付け、enter キーを押して続行します。

5. 正常に接続している場合、ノートブックの残りの部分には、ビッグデータクラスターの各コンポーネントの出力が表示されます。 特定のコードセルを再実行する場合は、コードセルの上にマウスポインターを移動し、 **[実行]** アイコンをクリックします。

## <a name="use-azdata"></a>Azdata を使用する

[Azdata](deploy-install-azdata.md)コマンドを使用して、エンドポイントとクラスターの状態の両方を表示することもできます。

### <a name="service-endpoints"></a>サービスエンドポイント

ビッグデータクラスターの外部エンドポイントの IP アドレスを取得するには、次の手順に従ってください。

1. 次の**kubectl**コマンドの外部 ip 出力を参照して、コントローラーエンドポイントの ip アドレスを見つけます。

   ```bash
   kubectl get svc controller-svc-external -n <your-big-data-cluster-name>
   ```

   > [!TIP]
   > デプロイ中に既定の名前を変更しなかった場合`-n mssql-cluster`は、前のコマンドでを使用します。 " **mssql クラスター** " は、ビッグデータクラスターの既定の名前です。

1. [Azdata ログイン](reference-azdata.md)を使用してビッグデータクラスターにログインします。 **--Controller-endpoint**パラメーターをコントローラーエンドポイントの外部 IP アドレスに設定します。

   ```bash
   azdata login --controller-endpoint https://<ip-address-of-controller-svc-external>:30080 --controller-username <user-name>
   ```

   デプロイ中にコントローラー (CONTROLLER_USERNAME と CONTROLLER_PASSWORD) に対して構成したユーザー名とパスワードを指定します。

1. [Azdata bdc エンドポイントリスト](reference-azdata-bdc-endpoint.md)を実行して、各エンドポイントの説明とそれに対応する IP アドレスとポート値を一覧表示します。 

   ```bash
   azdata bdc endpoint list -o table
   ```

   次の一覧に、このコマンドからの出力例を示します。

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

[Azdata bdc status show](reference-azdata-bdc-status.md)コマンドを使用して、クラスターの状態を表示できます。

```bash
azdata bdc status show -o table
```

> [!TIP]
> Status コマンドを実行するには、最初に、前の「エンドポイント」セクションで示した**azdata login**コマンドを使用してログインする必要があります。

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

[Azdata bdc pool status show](reference-azdata-bdc-pool-status.md)コマンドを使用して、クラスター内のプールの状態を表示できます。 このコマンドを使用するには、 `--kind`パラメーターを使用してプールの種類を指定します。 プールの種類は次のとおりです。

- 判定
- data
- master
- 浮かぶ
- ・

たとえば、次のコマンドは、記憶域プールのプールの状態を表示します。

```bash
azdata bdc pool status show --kind storage
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

値`logsUrl`は、ログ情報を含む kibana ダッシュボードにリンクされます。

![Kibana ダッシュボード](./media/view-cluster-status/kibana-dashboard.png)

`nodeMetricsUrl` と`sqlMetricsUrl`の値は、ノードの正常性と SQL のメトリックを監視するための grafana ダッシュボードにリンクします。

![Grafana ダッシュボード](./media/view-cluster-status/grafana-dashboard.png)

![SQL](./media/view-cluster-status/grafana-sql-status.png)

### <a name="view-controller-status"></a>コントローラーの状態の表示

[Azdata bdc control status show](reference-azdata-bdc-control-status.md)コマンドを使用して、コントローラーの状態を表示できます。 ビッグデータクラスターのコントローラーノードに関連する監視ダッシュボードへのリンクも表示されます。

## <a name="next-steps"></a>次の手順

ビッグデータクラスターの詳細については、「 [SQL Server ビッグデータクラスターとは](big-data-cluster-overview.md)」を参照してください。
