---
title: クラスターの状態を表示する
titleSuffix: SQL Server big data clusters
description: この記事では、Azure Data Studio、ノートブック、および azdata コマンドを使用して、ビッグ データ クラスターの状態を表示する方法について説明します。
author: yualan
ms.author: alayu
ms.reviewer: mikeray
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 028864712658e35913fa04fb1a85e4ca960ad573
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/20/2019
ms.locfileid: "69653270"
---
# <a name="how-to-view-the-status-of-a-big-data-cluster"></a>ビッグ データ クラスターの状態を表示する方法

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事では、サービス エンドポイントにアクセスして SQL Server ビッグ データ クラスター (プレビュー) の状態を表示する方法について説明します。 Azure Data Studio と **azdata** の両方を使用できます。この記事では、両方の手法について説明します。

## <a id="datastudio"></a> Azure Data Studio を使用する

[Azure Data Studio](https://aka.ms/azdata-insiders) の最新の **Insider ビルド**をダウンロードしたら、SQL Server ビッグ データ クラスター ダッシュボードを使用して、サービス エンドポイントとビッグ データ クラスターの状態を表示できます。 以下の機能の一部については、最初は Azure Data Studio の Insider ビルドでのみ使用可能となりますので注意してください。

1. まず、Azure Data Studio でご利用のビッグ データ クラスターへの接続を作成します。 詳細については、「[Azure Data Studio を使用して SQL Server ビッグ データ クラスターに接続する](connect-to-big-data-cluster.md)」を参照してください。

1. ビッグ データ クラスター エンドポイントを右クリックし、 **[管理]** をクリックします。

   ![[管理] を右クリックする](media/view-cluster-status/right-click-manage.png)

1. **[SQL Server Big Data Cluster]\(SQL Server ビッグ データ クラスター\)** タブを選択して、ビッグ データ クラスターのダッシュボードにアクセスします。

   ![ビッグ データ クラスター ダッシュボード](media/view-cluster-status/bdc-dashboard.png)

### <a name="service-endpoints"></a>サービス エンドポイント

ビッグ データ クラスター内のさまざまなサービスに簡単にアクセスできるようにすることが重要です。 ビッグ データ クラスター ダッシュボードには、サービス エンドポイントを表示してコピーすることを可能にするサービス エンドポイント テーブルが用意されています。

![サービス エンドポイント](media/view-cluster-status/service-endpoints.png)

最初のいくつかの行には、次のサービスが公開されます。

- アプリケーション プロキシ
- クラスター管理サービス
- HDFS と Spark
- 管理プロキシ

これらのサービスに接続するためにエンドポイントが必要なときにコピーして貼り付けることができるエンドポイントが、それらのサービスに一覧表示されます。 たとえば、エンドポイントの右側にあるコピー アイコンをクリックして、そのエンドポイントを要求するテキスト ウィンドウに貼り付けることができます。 [クラスターの状態ノートブック](#notebook)を実行するには、クラスター管理サービスのエンドポイントが必要です。

### <a name="dashboards"></a>ダッシュボード

サービス エンドポイント テーブルには、次の項目を監視するためのダッシュボードもいくつか公開されます。

- メトリック (Grafana)
- ログ (Kibana)
- Spark ジョブの監視
- Spark リソースの管理

これらのリンクを直接クリックできます。 サービスに接続する前に、ご自分のユーザー名とパスワードを入力するように 2 回求められます。

### <a id="notebook"></a> クラスターの状態ノートブック

1. クラスターの状態ノートブックを起動して、ビッグ データ クラスターのクラスターの状態を表示することもできます。 ノートブックを起動するには、 **[クラスターの状態]** タスクをクリックします。

    ![起動する](media/view-cluster-status/cluster-status-launch.png)

2. 開始する前に、次の項目が必要です。

    - ビッグ データのクラスター名
    - コントローラーのユーザー名
    - コントローラーのパスワード
    - コントローラー エンドポイント

    既定のビッグ データ クラスター名は、展開時にカスタマイズしない限り、**mssql-cluster** となります。 コントローラー エンドポイントは、サービス エンドポイント テーブル内のビッグ データ クラスター ダッシュボードから見つけることができます。 エンドポイントは、**クラスター管理サービス**として一覧表示されます。 資格情報がわからない場合は、ご利用のクラスターを展開した管理者に問い合わせてください。

3. 上部のツールバーで **[セルの実行]** をクリックします。

4. ご利用の資格情報を求めるプロンプトに従います。 ビッグ データのクラスター名、コントローラーのユーザー名、コントローラーのパスワードの各資格情報を入力したら、Enter キーを押します。

    > [!Note]
    > ご利用のビッグ データを使用して設定された構成ファイルがない場合は、コントローラー エンドポイントの指定を求められます。 それを入力するか貼り付けてから、Enter キーを押して続行します。

5. 正常に接続された場合、ノートブックの残りの部分には、ビッグ データ クラスターの各コンポーネントの出力が表示されます。 特定のコード セルを再実行する場合は、コード セル上にマウス ポインターを移動し、 **[実行]** アイコンをクリックします。

## <a name="use-azdata"></a>azdata を使用する

[azdata](deploy-install-azdata.md) コマンドを使用して、エンドポイントとクラスターの状態の両方を表示することもできます。

### <a name="service-endpoints"></a>サービス エンドポイント

ビッグ データ クラスター用の外部エンドポイントの IP アドレスを取得するには、次の手順に従ってください。

1. 次の **kubectl** コマンドの EXTERNAL-IP 出力を参照して、コントローラー エンドポイントの IP アドレスを見つけます。

   ```bash
   kubectl get svc controller-svc-external -n <your-big-data-cluster-name>
   ```

   > [!TIP]
   > 展開中に既定の名前を変更していない場合は、前のコマンド内の `-n mssql-cluster` を使用します。 **mssql-cluster** は、ビッグ データ クラスターの既定の名前です。

1. [azdata login](reference-azdata.md) を使用して、ビッグ データ クラスターにログインします。 **--controller-endpoint** パラメーターをコントローラー エンドポイントの外部 IP アドレスに設定します。

   ```bash
   azdata login --controller-endpoint https://<ip-address-of-controller-svc-external>:30080 --controller-username <user-name>
   ```

   展開中にコントローラー (CONTROLLER_USERNAME と CONTROLLER_PASSWORD) に対して構成したユーザー名とパスワードを指定します。

1. [azdata bdc endpoint list](reference-azdata-bdc-endpoint.md) を実行して、各エンドポイントの説明とそれに対応する IP アドレスおよびポート値を示した一覧を取得します。 

   ```bash
   azdata bdc endpoint list -o table
   ```

   次の一覧は、このコマンドからの出力例を示しています。

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

[azdata bdc status show](reference-azdata-bdc-status.md) コマンドを使用して、クラスターの状態を表示できます。

```bash
azdata bdc status show -o table
```

> [!TIP]
> status コマンドを実行するには、最初に、前述のエンドポイントのセクションに示した **azdata login** コマンドを使ってログインする必要があります。

このコマンドからの出力例を、次に示します。

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

### <a name="view-pool-status"></a>プールの状態を表示する

[azdata bdc pool status show](reference-azdata-bdc-pool-status.md) コマンドを使用して、クラスター内のプールの状態を表示できます。 このコマンドを使用するには、`--kind` パラメーターによってプールの種類を指定します。 プールの種類は次のとおりです。

- compute
- data
- master
- spark
- storage

たとえば、次のコマンドを実行すると、ストレージ プールにおけるプールの状態が表示されます。

```bash
azdata bdc pool status show --kind storage
```

次の出力によく似たテキストが表示されます。

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

`logsUrl` 値は、ログ情報を含む次の kibana ダッシュボードにリンクされます。

![Kibana ダッシュボード](./media/view-cluster-status/kibana-dashboard.png)

`nodeMetricsUrl` 値と `sqlMetricsUrl` 値は、ノードの正常性と SQL のメトリックを監視するための次の grafana ダッシュボードにリンクします。

![grafana ダッシュボード](./media/view-cluster-status/grafana-dashboard.png)

![SQL](./media/view-cluster-status/grafana-sql-status.png)

### <a name="view-controller-status"></a>コントローラーの状態を表示する

[azdata bdc control status show](reference-azdata-bdc-control-status.md) コマンドを使用して、コントローラーの状態を表示できます。 ビッグ データ クラスターのコントローラー ノードに関連する監視ダッシュボードへの同様のリンクが表示されます。

## <a name="next-steps"></a>次の手順

ビッグデータクラスターの詳細について[は[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] ](big-data-cluster-overview.md)、「」を参照してください。
